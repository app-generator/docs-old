# Sample Next.js Project

In this page, we’ll make a quick introduction to `Next.js` and build a simple page using `Next.js`, Material UI, and the fetch API.

Here will be the result of this tutorial.

![Home page of the Next.js project](<../../.gitbook/assets/Screenshot 2022-08-15 at 22-41-56 Products page.png>)

## Structuring the project

We have already seen how to create a `Next.js` project. Inside the newly created project, run the following command to run the development server of the project.

```bash
yarn dev
```

Once the project is running, we can install the needed packages. We need to install the Material U`I library using` yarn\`.

```bash
yarn add @mui/material @emotion/react @emotion/styled
```

After the installation, we need to configure the project for the data we will use. In the `public` directory, create a file called `products.json`.

This file will contain a list of product objects with data we’ll display to the user using `Next.js` and Material UI. You can have an example of this file [here](https://github.com/app-generator/sample-next-js-getting-started/blob/main/public/products.json).

We need to create the product.json file in the `public` directory, so it can be served from the server and we’ll be able to fetch the data using the fetch API. After adding the `products.json` file, create a new file named `product.js` in `pages/api/` directory. This file will contain a function we’ll write to fetch data from the server at `http://localhost:3000/products.json`.

```jsx
const getProducts = () => {
  return fetch(`products.json`).then((response) => response.json());
};

export default getProducts;
```

The function to fetch data is ready now, we can write the `Product` component to display information about the products.

## Writing the Product component

In the `pages` directory, create a new directory called `components`. This directory will contain the components for this project.

Inside the newly created directory, create a new file called `Product.jsx`. This file will contain the code for the Product component. We’ll use Material UI to build a simple card that will display the name, the image, and the price of the product.

```jsx
import * as React from "react";
import Card from "@mui/material/Card";
import CardContent from "@mui/material/CardContent";
import CardMedia from "@mui/material/CardMedia";
import Typography from "@mui/material/Typography";
import { CardActionArea } from "@mui/material";

export default function Product(props) {
  const { product } = props;

  return (
    <Card sx={{ maxWidth: 250, maxHeight: 250, margin: 4 }}>
      <CardActionArea>
      <CardMedia
          component="img"
          image={product?.image}
          height={100}
          width={100}
        />
        <CardContent>
          <Typography gutterBottom variant="h5" component="div">
            {product?.name}
          </Typography>
          <Typography gutterBottom variant="h6" component="p">
            {product?.price}$
          </Typography>
        </CardContent>
      </CardActionArea>
    </Card>
  );
}
```

The `Product` component should receive `product` props to work properly. As said earlier, we are using Material UI components to create a card and thankfully, MUI provides components for Typography, Card content, and Card image. This makes the task much easier.

## List all products

We will use the `Product` component in the `index.js` file in the `pages` directory. It represents the main page of the application.

Let’s start with importing the `getProducts` function and initiate some important states that will be used on the page.

```jsx
import React from "react";
import Head from "next/head";
import styles from "../styles/Home.module.css";
import Product from "./components/Product";
import getProducts from "./api/products";

export default function Home() {
  const [products, setProducts] = React.useState([]);

  React.useEffect(() => {
    getProducts().then((res) => setProducts(res));
  }, []);

  return (
    ...
  );
}
```

Here we are defining the `products` state, which will normally contain the list of the product objects. After that, we use the `useEffect` hook to make some computations before the component is mounted. We are basically calling the `getProducts` function and retrieving the response.

Let’s through this response now and display the products.

```jsx
...
return (
    <div className={styles.container}>
      <Head>
        <title>Products page</title>
        <link rel="icon" href="/favicon.ico" />
      </Head>

      <main className={styles.main}>
        <h1 className={styles.title}>
          Welcome to <a href="https://nextjs.org">Products!</a>
        </h1>
        {products &&
          products.map((product) => (
            <Product key={product?.id} product={product} />
          ))}
      </main>
    </div>
  );
...
```

Open the page at [http://localhost:3000/](http://localhost:3000/), and you will see the result. And voilà, we have successfully created a simple project with `Next.js`.

The next documentation will concern how to deploy a `Next.js` application on [Netlify](https://netlify.com/). In the meantime, you can find the code for this sample project [here](https://github.com/app-generator/sample-next-js-getting-started).
