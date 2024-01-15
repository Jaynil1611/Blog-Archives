---
title: "Frontend Interview Experience at Intuit"
seoTitle: "Frontend Interview Experience at Intuit"
seoDescription: "Hello folks, I am sharing my recent interview experience for the role of Software Development Engineer 2 - Frontend at Intuit India"
datePublished: Mon Jan 15 2024 03:42:05 GMT+0000 (Coordinated Universal Time)
cuid: clredpm5r000109lhep34eru0
slug: frontend-interview-experience-at-intuit
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1705226535968/653b0dc9-c257-4053-8de0-9d95d3625951.jpeg
tags: interview, interviews, frontend, reactjs, ui, frontend-development, interview-questions, interview-tips, intuit, interview-preparations

---

Hello folks,  
I had the opportunity to interview recently at **Intuit** for the Software Development Engineer 2 - Frontend role. This role is more inclined towards the frontend domain & I will share my interview experience in this post.

## **How did I get to know about this opportunity?**

Intuit had posted an opening on LinkedIn for the SWE2 - Frontend role. I had purchased a free trial of LinkedIn Premium. I reached out to the recruiter directly via the LinkedIn InMail feature. The recruiter contacted me over a call to discuss more about this opportunity & interview rounds.

> You can read more about the free trial of LinkedIn premium [here](https://premium.linkedin.com/)

## Interview Rounds

In total, there are 5 rounds:

* Javascript & DSA Round
    
* Machine Coding & Craft Demonstration Round
    
* Javascript Deep Dive Round
    
* DSA Problem Solving Round
    
* Hiring Manager Round
    

## Javascript & DSA Round

Duration: 60 minutes

This round was a combination of DSA & Javascript problems. One DSA question which was asked was the famous [2 Sum](https://leetcode.com/problems/two-sum/) problem. I was able to explain & write the solution for it in JavaScript. The interviewer verbally asked the 3 sum variation of this problem. The interviewer switched to react questions including `useEffect` hook & its various usages. As an extension to this question, I was asked about object referential equality while using the `useEffect` hook & discussed different scenarios where it could impose a problem.

> You can read more about object referential equality in this [blog](https://dev.to/vicnovais/understanding-referential-equality-in-reacts-useeffect-2m7o).

I was asked to write a `memoize` function in Javascript. The interviewer extended it to accept any number of parameters in this memoize function.

> You can find a similar memoize question solved in this [blog](https://javascriptinterviewquestions.com/2020/05/how-to-memoize-any-function-in-javascript.html).

The next question involved the use of **Promises** in Javascript. This question was to be solved using vanilla javascript only.  
The question was basically to find all the cities belonging to all the states in a country given the list of states & list of cities belonging to each state. The assumption here is that the state & city arrays will be provided by a backend API.  
Here's an example to explain it better:

```javascript
// e.g. 'USA' is the country for which we need to find all the cities
// Input: city names are kept same with number for simplicity
// States API response
getStates('USA') -> ['CA', 'NY', 'WA']

// City API response
getCities('CA') -> ['LA', 'SF', 'SD']
getCities('NY') -> ['LA1', 'SF1', 'SD1']
getCities('WA') -> ['LA2', 'SF2', 'SD2']

// Problem Requirement
// You need to find all the cities in a given country by calling both APIs
getAllCities('USA') -> [
                        'LA', 'SF', 'SD',
                        'LA1', 'SF1', 'SD1', 
                        'LA2', 'SF2', 'SD2',
                       ];
```

This question wants to check if you can handle all the API calls using `Promise.all()` for states & then cities for each state. You can search for a solution to this problem on the internet. Covering the entire solution of this problem won't be possible in this blog, will try to write a detailed solution for this in a separate one.

## Machine Coding & Craft Demonstration Round

### Part 1: Machine Coding

This round has two parts to it. First, the recruiter shared the machine coding problem statement with me over the mail after the first round. I communicated 3 days to complete the entire assignment. Second, after confirmation, the recruiter scheduled the craft demonstration round.

### What is expected out of this round?

> We expect you to  prepare solution and put it on any tech platform/PPT/log *that you are comfortable with. (We are interested in your approach to the problem. It is alright if you don’t have a beautiful PPT. Pics of design done using pen and paper, description in a word doc are acceptable)*

I completed the solution for this assignment using React & styled components along with a few libraries. I deployed the solution to the web using Vercel to make it easily accessible to the interviewers.

> I have documented the entire solution along with the presentation of this assignment in this [GitHub](https://github.com/Jaynil1611/sports-events) repo.

Things to keep in mind before finalising the solution approach for this problem:

* Performance
    
* Error handling (loaders, fallback UI, data missing in API response)
    
* Reusability
    
* Pagination
    
* Testing (unit, integration, end-to-end)
    
* Mobile Responsiveness
    
* Accessibility
    

### Part 2: Craft Demonstration

Duration: 75 minutes

The interview panel consisted of 3 interviewers in this round. Presented the PPT prepared earlier & showcased the working solution of the problem statement.

I was questioned about my state management choice of using React Context API & `useReducer` hook versus Redux. The interviewer asked me to run a test coverage report to get the overall code coverage percentage of the unit tests written.

As a part of a live coding exercise, I was asked to implement search functionality & category dropdown filter as additional features on top of the existing assignment solution.

## Javascript Deep Dive Round

Duration: 90 minutes

2 interviewers together conducted this round. There were many questions asked in this round, I have tried to share most of them.

**Object prototypes** were the first topic. I was grilled on the usage, working & application of prototypes. Prototypical inheritance & its usage was also touched upon.

**Function Currying** was the next. I was given a problem statement which implied the use of function currying which can accept infinite number of arguments.

```javascript
// Create a currying function which adds all the numbers passed as arguments
addSub(1,2)(3)(4,5,6)(7,9)(); // 1+2+3+4+5+6 = 21
```

**Function polyfills** of `call` & `bind` were asked. I had to explain the appropriate working of the polyfills using examples.

**Debouncing** was the next concept to be explained. I wrote a debounce polyfill with an example to explain this concept. A variation of debounce to register the first call & ignore the rest was asked as well.

> You can find solution for debounce questions in this [article](https://www.freecodecamp.org/news/javascript-debounce-example).

Output-based questions on **SetTimeout & Promises** involving micro-task & task queues were asked. Priority of browser `fetch` functional call over `setTimeout` call was discussed implying that `fetch` calls are part of the micro-task queue.

## DSA Problem Solving Round

Duration: 60 minutes

The interviewer told me that you can expect a maximum of 3 questions in this round.  
However, I messed up this round. I was asked a medium-complexity question similar to the [Minimum Number of Platforms for a station](https://www.geeksforgeeks.org/minimum-number-platforms-required-railwaybus-station/). I couldn't come up with the optimal approach for this problem & got stuck in loops :(

The 5th round would be a Hiring Manager Round which is a mix of technical & managerial questions as suggested by the recruiter.

## Conclusion

As expected, DSA round feedback was negative as I wasn't able to solve questions of medium complexity. I had scheduled the craft demo, javascript deep dive & DSA round all on the same day back to back. I was exhausted after the first two rounds & should have kept the DSA round on a separate day. So, my advice would be to space out the interview rounds especially DSA on separate days.

Nonetheless, I got the experience of giving interviews at one of the top product-based MNCs. On top of this, I got a lot of learnings & areas to improve from this interview experience.

Thank you, guys, for reading up till here, I hope you enjoyed and learnt something new! You can connect with me on [**X**](https://twitter.com/Jaynil_Gaglani), [**LinkedIn**](https://www.linkedin.com/in/jaynilgaglani/) & [**GitHub**](https://github.com/Jaynil1611).

Happy Coding! ✌️

### Previous Posts

I have shared my interview preparation strategy & resources in my previous posts:

1. [**Frontend Interview Experience at Salesforce**](https://jaynil-gaglani.hashnode.dev/frontend-interview-experience-at-salesforce)
    
2. [Frontend Interview Experience at Walmart](https://jaynil-gaglani.hashnode.dev/frontend-interview-experience-at-walmart)