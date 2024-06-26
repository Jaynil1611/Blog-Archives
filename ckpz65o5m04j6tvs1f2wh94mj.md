---
title: "Infinite Scrolling Made Easy: Intro to Intersection Observer API"
seoTitle: "Infinite Scrolling Made Easy: Intro to Intersection Observer API"
seoDescription: "Infinite Scrolling Made Easy: Intro to Intersection Observer API"
datePublished: Wed Jun 16 2021 07:44:58 GMT+0000 (Coordinated Universal Time)
cuid: ckpz65o5m04j6tvs1f2wh94mj
slug: infinite-scrolling-made-easy-intro-to-intersection-observer-api
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1623694752346/TNnQ9kLsY.jpeg
tags: browser, javascript, apis, reactjs, web-api

---

Hello Everyone!

Today, I am sharing an easy and quick way to implement infinite scrolling in your websites using the Intersection Observer API. 
Let's understand what is Intersection Observer API and what does it comprise.

## What is Intersection Observer API?

Here's what MDN docs say,
> The Intersection Observer API provides a way to asynchronously observe changes in the intersection of a target element with an ancestor element or with a top-level document's viewport.

In simple terms, Intersection Observer API makes it easy to detect when an element enters the viewport and take an action when it appears. There is no more need to bind events & keep performance optimization in mind while calculating the existence of an element in the viewport. Intersection Observer API removes all the overhead and delivers great performance out of the box. 


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1623820391575/RwrTZPk51.png)


## What are the possible applications of the Intersection Observer API?

The Intersection Observer API can be used in a variety of different applications such as:

1. Lazy-loading of images or other content as a page is scrolled.

2. Implementing "infinite scrolling" websites

3. Reporting of visibility of advertisements in order to calculate ad revenues.

4. Telling the browser to only execute the code once the element is visible at the viewport


## What are the key concepts of the Intersection Observer API?

#### `IntersectionObserver` Interface

This interface is used to create a new observer which will keep track of changes in the intersection of a target element.

```
let options = {
  root: document.querySelector('#scrollArea'),
  rootMargin: '0px',
  threshold: 1.0
}

let observer = new IntersectionObserver(callback, options)
```

The above code snippet creates a new intersection observer using the `IntersectionObserver` constructor. The first argument is a `callback` function that is called when our target element enters the viewport. We'll look more into the callback function later with the example. The second argument is the `options` object which helps you control the situations under which the callback function is called. It contains the following fields:

- `root`: The element that is set as a viewport for checking the visibility of the target element which must be a parent (ancestor) of the target element.

- `rootMargin`: This is equivalent to the CSS margin property which is defined on the root element.

- `threshold`: A number or an array of numbers indicating at what percentage of the target's visibility the callback function should be invoked.


## How to implement Infinite Scrolling using the Intersection Observer API?

Let's start implementing Infinite Scrolling of images using Intersection Observer API.
I am going to implement it using [react](https://reactjs.org/docs/getting-started.html) & [javascript](https://developer.mozilla.org/en-US/docs/Web/JavaScript). 

1. `App.js` Component

We first define an imageList variable that contains a list of image URLs to show images on the browser. Then define a `div` which will be the parent element in this case. The `Image` component renders each image by taking the `src` prop from the parent. Also, it takes key to differentiate each child image component and the `setImageList` function which we will see in a while.

Here's our App.js file

```
export default function App() {
  const root = useRef(null);
  const [imageList, setImageList] = useState(getImageList(true));

  return (
    <div ref={root} className="App">
      <h1>Lazy loading</h1>
      {imageList.map((url) => {
        return <Image key={url} src={url} setImageList={setImageList} />;
      })}
    </div>
  );
}
```

2. `Image` Component

This is where we employ the Intersection Observer API to lazily load images and make them scroll infinitely.  Here `useRef` is used to point to the current `img` element defined at the last. Similarly, the observer variable is used to point to the observer returned by the Intersection Observer API. Inside the `useEffect()` we call the `IntersectionObserver` constructor and pass a callback function. This function receives a `entries` array which contains a list of [`IntersectionObserverEntry`](https://developer.mozilla.org/en-US/docs/Web/API/IntersectionObserverEntry) objects. It has `intersectionRatio` property which determines the visibility of `currentElement` in the viewport. The value 0.5 suggests that when the visibility of `currentElement` is at least 50%, then display this image & load the next images in `imageList` array.

The root option is provided with the value of rootElement i.e. parent. Threshold receives an array of values. Threshold value is defined as:
 
> A threshold of 1.0 means that when 100% of the target is visible within the element specified by the root option, the callback is invoked.

Here's our `Image.js` file

```
export const Image = ({ src, rootElement, setImageList }) => {
  const ref = useRef(null);
  const observer = useRef(null);

  useEffect(() => {
    const currentElement = ref.current;
    if (currentElement) {
      observer.current = new IntersectionObserver(
        (entries) => {
          entries.forEach((entry) => {
            if (entry.intersectionRatio > 0.5) {
              ref.current.src = src;
              observer.current.unobserve(currentElement);
              setImageList((imageList) => [...imageList, ...getImageList()]);
            }
          });
        },
        {
          root: rootElement,
          threshold: [0, 0.5, 1]
        }
      );

      observer.current.observe(currentElement);
    }

    return () => {
      observer.current.unobserve(currentElement);
    };
  }, [ref]);

  return <img ref={ref} width="200px" height="200px" alt="" />;
};

```

## Final Output

%[https://codesandbox.io/s/react-lazy-loading-infinite-scroll-l0h16]


## Conclusion

There are infinite possibilities using the Intersection Observer API. You can greatly improve the performance & overall user experience of your web apps by reducing load time. You can lazy load images, implement infinite scrolling, link-prefetching and so on.

Browser support for the Intersection Observer API is strong & a majority of modern browsers are supporting it. You can try out this API in your web apps and you'll see the difference it makes.

Thank you guys for reading up till here, I hope you enjoyed and learnt something new! 
You can connect with me on [**Twitter**](https://twitter.com/Jaynil_Gaglani), [**LinkedIn**](https://www.linkedin.com/in/jaynilgaglani/) & [**GitHub**](https://github.com/Jaynil1611). 

Happy Coding!

**References:**

- [MDN - Intersection Observer API](https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API)

- [LogRocket](https://blog.logrocket.com/lazy-loading-using-the-intersection-observer-api/)



