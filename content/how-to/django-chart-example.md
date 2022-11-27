---
description: How To showcase information in Django
---

# Django Chart Example

To display data on a chart, you must extract data from your model or anywhere else and send it to the JS function as JSON. For example, I did this through the following work flow:


> **Step #1 -** Make a Model

I want to show my product sales report on the Chart. To do this, I created a model with the following structure in `models.py`:

```python
from django.db import models


class Sale(models.Model):
    amount = models.FloatField()
    product_name = models.CharField(max_length=40)
    created_time = models.DateTimeField()
    updated_time = models.DateTimeField(auto_now=True)

    class Meta:
        verbose_name = 'sale'
        verbose_name_plural = 'sales'
```



**Import Data**

I used [`django-import-export`](https://django-import-export.readthedocs.io/en/latest/installation.html) package to add data through csv, xls, and etc.



**Extract Data**

In this part, I want to display the annual sales information for each product in the chart (By how much of each product has been sold each year) - the structure of data is as follows:

```python
# Example
data = {
    'YEAR1': {'PRODUCT_NAME1': 'AMOUNT', 'PRODUCT_NAME2': 'AMOUNT', 'PRODUCT_NAME3': 'AMOUNT'}, 
    'YEAR2': {'PRODUCT_NAME1': 'AMOUNT', 'PRODUCT_NAME2': 'AMOUNT', 'PRODUCT_NAME3': 'AMOUNT'},
    'YEAR3': {'PRODUCT_NAME1': 'AMOUNT', 'PRODUCT_NAME2': 'AMOUNT', 'PRODUCT_NAME3': 'AMOUNT'},
}
```

To do this, We add a function to our model to extract the data:

```python
from django.db import models
from django.db.models import Sum
from django.db.models.functions import TruncYear

class Sale(models.Model):
    ...

    @classmethod
    def get_sales_report(cls):
        annotates = {'total_amount': Sum('amount')}

        sales = cls.objects.annotate(
            year=TruncYear('created_time')
        ).values('product_name', 'year').order_by().annotate(**annotates)

        data = {}
        for sale in sales:  # This loop is for building data structures.
            if sale['year'].year not in data:
                data[sale['year'].year] = {}

            data[sale['year'].year][sale['product_name']] = sale['total_amount']

        # The labels are our product names. these gonna be shown in the chart
        labels = list(sales.values_list('product_name', flat=True).distinct())
        return data, labels
```



> **Step #2 -**  Create View

In `view.py`, we just need to call this function and create the structure needed for the chart. As follows:

```python
import json
from django.shortcuts import render
from app.models import Sale


def index(request):
    context = {'segment': 'index'}

    sales, labels = Sale.get_sales_report()

    # We need to change the data based on how it is displayed on the chart.
    data = [
        {
            'y': year,
            'a': '{:.2f}'.format(sales[year].get('A')),
            'b': '{:.2f}'.format(sales[year].get('B')),
            'c': '{:.2f}'.format(sales[year].get('C'))
        } for year in sales
    ]

    # This is the structure of our chart, And it must be in JSON to be displayed in JS function.
    context['chart_data'] = json.dumps({
        'element': 'morris-bar-chart',
        'data': data,
        'xkey': 'y',
        'barSizeRatio': 0.70,
        'barGap': 3,
        'resize': True,
        'responsive': True,
        'ykeys': ['a', 'b', 'c'],  # it can be custom
        'labels': labels,
        'barColors': ['0-#1de9b6-#1dc4e9', '0-#899FD4-#A389D4', '#04a9f5']  # it can be custom
    })

    return render(request, 'YOUR_TEMPLATE', context)
```

This is the structure of our chart, And it must be in JSON to be displayed in JS function.

###

> **Step #3** - Show in Template

In your template, just call your chart and send the data to JS Function. For example:

```markup
{% raw %}
{% load static %}

<div class="col-xl-12">
    <div class="card">
        <div class="card-header">
            <h5>Products Sales Report</h5>
        </div>
        <div class="card-block">
            <div id="morris-bar-chart" style="height:300px"></div>
        </div>
    </div>
</div>

...

<!-- Load your JS files  -->
<script src="{% static 'assets/plugins/chart-morris/js/raphael.min.js' %}"></script>
<script src="{% static 'assets/plugins/chart-morris/js/morris.min.js' %}
{% endraw %}"></script>

<script>
    Morris.Bar({{ chart_data|safe }});
</script>
```

In this example, I used `Morris.Bar` Chart to display the information.

