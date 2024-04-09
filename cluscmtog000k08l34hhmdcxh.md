---
title: "Frontend Interview Experience at Cars24"
seoTitle: "Frontend Interview Experience at Cars24"
seoDescription: "Hello folks, I am sharing my recent interview experience for the role of Software Development Engineer 2 - Frontend at Cars24 India"
datePublished: Tue Apr 09 2024 12:19:49 GMT+0000 (Coordinated Universal Time)
cuid: cluscmtog000k08l34hhmdcxh
slug: frontend-interview-experience-at-cars24
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1711798210996/827b7597-66c1-43e7-b1d6-d8f784742908.webp
tags: interview, interviews, javascript, frontend, reactjs, frontend-development, interview-questions, interview-preparations, cars24

---

Hello folks,  
I had the opportunity to interview recently at [Cars24](https://www.linkedin.com/company/cars24/) for the Software Engineer 2 - Frontend role. This role is more inclined towards the frontend domain & I will share my interview experience in this post.

## **How did I get to know about this opportunity?**

I created my profile on [Naukri](https://www.naukri.com/) to look for new opportunities. Cars24 recruiter viewed my profile on Naukri & contacted me to inform me about this opportunity. I enquired more about the role & interview process. The recruiter scheduled the interview rounds a week after this discussion.

## **Interview Rounds**

In total, there are 3 rounds:

* Javascript Fundamentals Round
    
* React Machine Coding Round
    
* Frontend System Design Round
    

## JS Fundamentals Round

Duration: 60 minutes

Javascript output-based questions were asked in this round, including hoisting, let, var, const, and temporal dead zone. I was asked to explain call, bind & apply methods. I wrote a polyfill for `bind` method with an example to demonstrate it.

The usages of debouncing vs throttling in real-world applications were discussed. I was asked to write a polyfill for `throttle` & explain it's working.

IIFE concept in javascript was discussed & below output-based question was asked related to it:

```javascript
const myObject = {
    abc: "bar",
    func() {
        const self = this;
        console.log(`outer func: this.abc = ${  this.abc}`);
        console.log(`outer func: self.abc = ${  self.abc}`);
        (function() {
            console.log(`inner func: this.abc = ${  this.abc}`);
            console.log(`inner func: self.abc = ${  self.abc}`);
        }());
    }
};

/*
outer func: this.abc = bar
outer func: self.abc = bar
inner func: this.abc = undefined
inner func: self.abc = bar
*/
```

Moving to React, the interviewer touched upon the commonly used hooks including `useEffect`, `useMemo`, `useCallback` & discussed the usage of each one.  
Usage of `React.memo()` function & its role in preventing component re-renders was asked. Using `useCallback` hook to wrap functions passed as props to ensure props are updated only if there is a change in dependencies.

Lastly, we talked about the best practices that can be followed to optimize browser performance.

## React Machine Coding Round

Duration: 90 minutes

The problem statement was to create a nested checkbox feature similar to a brand filter on an e-commerce website where we have multiple brands & sub-brands associated with each brand. I was expected to complete the solution using React & vanilla CSS (external CSS library was not allowed).

> You can find the code for the above problem statment in this [CodeSandBox Link](https://codesandbox.io/s/cars24-react-coding-t44zmr). However, the preview is not showing up since mock API is not working anymore.

Follow-up questions include `useCallback` vs `useMemo` hook usage with an example. I was asked about `useLayoutEffect` hook & its usage in React components.

## Frontend System Design Round

Duration: 60 minutes

This interviewer grilled me in-depth on every concept asked in this round. It started with introductions & my previous experience & projects I've worked on.

Discussed about authentication mechanism used in the current project. An in-depth discussion on token-based authentication & cookie storage for the same. Mitigation of security risks while storing tokens in cookie storage & access of the auth token across different sites. Refer to this [MDN article](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies#security) to read more on the security part.

Discussed the usage of Axios interceptors to read the auth token received in the response & verify authenticated users. The difference between local & session storage was discussed along with the implications of storing auth tokens in local or session storage. Security concerns of not encoding user email & password while sending them as part of body parameters in a login API request.

Automatically logout user after 7 days if the token expiry is 30 days from frontend without storing timestamps was one of the problem statements asked in this round. We discussed the improvements which can be made in the solution code of the question asked in the previous round.

Lastly, the interviewer enquired about my reasons for leaving the current company.

## Conclusion

Two days after finishing the interviews, the recruiter informed me that I couldn't clear the final round due to expectations mismatch. The last round didn't go as expected & perhaps the interviewer didn't find me fit for the role.

Nonetheless, I got the experience of giving interviews at one of the top product-based startups in India. On top of this, I got a lot of learnings & areas to improve from this interview experience.

Thank you, guys, for reading up till here, I hope you enjoyed and learnt something new! You can connect with me on [**X**](https://twitter.com/Jaynil_Gaglani), [**LinkedIn**](https://www.linkedin.com/in/jaynilgaglani/) & [**GitHub**](https://github.com/Jaynil1611).

Happy Coding! ✌️

## [**Interview Experience Series**](https://jaynil-gaglani.hashnode.dev/series/interview-experience)

In this series on Hashnode, I've compiled advice, resources, and real-world interview experiences to help you prepare for your front-end developer interview.