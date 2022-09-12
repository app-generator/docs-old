---
description: >-
  This page documents simple practices you can use to ease development flow with
  Nextjs but to also help increase performances.
---

# Best Practices for NextJS projects

Next.js has changed the way web applications are built with React and deployed. The developer experience guaranteed by the framework allows to develop with better architecture and allows custom optimization. Let's explore 4 best practices that can be used in a Next.js project from development to deployment.

### 1 - Dynamic Imports

Dynamic import also called code splitting is a practice of dividing bundles of JavaScript code into smaller chunks, which are then pieced together and charged into the runtime of an application and can boost your website performance. But how dynamic imports are different from static imports? Dynamic imports work by applying the code splitting method. It's the division of code into various bundles, which are arranged in parallel using a three format, where modules are loaded dynamically. You can learn more about code splitting [here](https://nextjs.org/learn/foundations/how-nextjs-works/code-splitting). Next.js provides an extension called `dynamic` from `next/dynamic`. It enables lazy loading of external libraries improving the loading performance of these libraries.

```jsx
import dynamic from 'next/dynamic'
import { Suspense } from 'react'

export default function Home() {
  const DynamicFooter = dynamic(
    () => import("./components/DynamicFooter"), {
  suspense: true,
 }));

  return (
    <div>
      <Suspense fallback={<div>Loading...</div>}>
        <DynamicFooter />
      </Suspense>
    </div>
  )
}
```

By using `next/dynamic` in the example above, the footer component will not be included in the page's initial JavaScript bundle. The page will render the Suspense fallback first, followed by the Footer component when the Suspense boundary is resolved.

You can learn more from the dynamic imports on the official [documentation](https://nextjs.org/docs/advanced-features/dynamic-import).

### 2 - Optimization of Images

Image optimization with Next.js improves the user experience but is also essential in **Search Engine Optimization** (SEO) ranking when done right. `Next.js` provides an image component `<Image />` that is very flexible and scalable. We made use of this component in the recent [document](https://docs.appseed.us/technologies/next-js/deploy-a-next.js-application-on-netlify) while deploying the Next.js application. But here is an example using a component using the `<Image />` component.

```jsx
import Image from 'next/image'

const loader = ({ src, width, quality }) => {
  return `https://website.com/${src}?w=${width}&q=${quality || 50}`
}

const BannerImage = (props) => {
  return (
    <Image
      loader={loader}
      src="banner.png"
      alt="Banner of product"
      width={1200}
      height={500}
    />
  )
}
```

### 3 - Rendering mode

Next.js has three rendering modes:

* **Server Side Rendering** (SSR): In this mode, pages are generated and returned after each page view. It is similar to how pages are returned in WordPress but in a much faster way. SSR is used to fetch data and pre-populate a page with custom content, leveraging the server's reliable internet connection.
* **Static Site Generation** (SSG): This is the way early websites used to work. HTML files are just stored on disc on a web server and each request on a URL returns a page that loads in the browser. With SSG, your pages are generated during `Next.js` build step. These pages are then served on a server. This is really fast.
* **Incrementation Site Regeneration** (ISR): ISR will create each page using SSR initially and store the response the same way SSG does. Subsequent requests for the same page will now be read from disc and be, you know, super-fast. ISR enables you to use static generation on a per-page basis, without needing to rebuild the entire site. With ISR, you can retain the benefits of static while scaling to millions of pages.

### 4 - Lazy loading

You might want to load data only under certain circumstances. For example, you want to charge more data when the user scrolls to the bottom of the page or clicks a button. It can also happen when you have external scripts you want to charge on the page. This can increase the loading time of the web page and causes a poor user experience.

Using Next.js, you have four loading strategies with [`next/script`](https://nextjs.org/docs/api-reference/next/script):

* `afterInteractive` which loads the script immediately after the page is made interactive. This is the default mode.
* `beforeInteractive` loads the script before the page becomes interactive.
* `lazyOnload` which loads when the page is idle.
* `worker` loads the script in a web worker.

```jsx
import { useState } from 'react'
import Script from 'next/script'

export default function Home() {
  const [stripe, setStripe] = useState(null)

  return (
    <>
      <Script
        id="stripe-js"
        strategy="beforeInteractive"
        src="https://js.stripe.com/v3/"
        onLoad={() => {
          setStripe({ stripe: window.Stripe('pk_test_12345') })
        }}
      />
    </>
  )
}
```

### Conclusion

Following the best practices above will help you make powerful Next.js websites. These practices are used to better the developer experience but also make it easier for the user to navigate your website, thus creating a rich user experience.
