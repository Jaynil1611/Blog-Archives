---
title: "Frontend Interview Experience at Clipboard Health"
seoTitle: "Frontend Interview Experience at Clipboard Health"
seoDescription: "A detailed frontend interview experience at Clipboard Health, covering React and JavaScript coding rounds with insights and solutions"
datePublished: Fri Aug 16 2024 15:32:33 GMT+0000 (Coordinated Universal Time)
cuid: clzwvbkgj000d0am79idcf1mr
slug: frontend-interview-experience-at-clipboard-health
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1723793950655/45eabf23-e5e9-4a73-80d0-4f58f1a8bdfe.jpeg
tags: interview, startups, javascript, frontend, reactjs, frontend-development, problem-solving

---

Hello folks,  
I had the opportunity to interview recently at [**Clipboard Health**](https://www.linkedin.com/company/clipboard-health/) (a US-based healthcare startup) for the **Frontend** **Software Engineer role**. This role is more inclined towards the frontend domain, and I will share my interview experience in this post.

## **How did I get to know about this opportunity?**

An employee from the company contacted me on LinkedIn, introducing me to the startup and its work culture. He then referred me for the open position, and shortly after, the recruiter reached out to schedule the interviews.

## **Interview Rounds**

In total, there are 3 rounds:

* React Machine Coding Round
    
* Javascript Problem-Solving Round 1
    
* Problem-Solving Round 2
    

## **React** Machine **Coding Round**

Duration: 60 minutes

**Problem Statement**: Create a React application that allows users to input a number between 0 and 1 and display multiples of that number. For example, if the user inputs 0.5, the app should show:

* 0.5 times 5 is 2.5
    
* 0.5 times 7 is 3.5
    
* 0.5 times 20 is 10
    

Additionally, include a button labelled "Add next multiplicand." When clicked, this button should double the previous multiplicand and add it to the list, continuing the sequence:

* 0.5 times 40 is 20
    
* 0.5 times 80 is 40
    
* 0.5 times 160 is 80
    

> ***Refer to this*** [***CodeSandBox Link***](https://codesandbox.io/p/sandbox/clipboard-health-react-machine-coding-round-whrmv9) ***for solution***

This problem checks basic react knowledge including splitting logic into different components, managing state across parent & child components & input validations.

## Javascript Problem-Solving Round 1

Duration: 60 minutes

**Problem Statement**: Create a function that parses an integer from a given input string without using the built-in `Number` constructor or `parseInt` function. The function should convert a string of numeric characters (e.g., '123') into its corresponding integer value (e.g., 123) by leveraging the character codes of the digits.

**Example:**

```javascript
/* 
Input: '-1234.0001'
Output: -1234.0001

Input: '12ABC'
Output: ERROR: Input string is not a valid number

Hint:
 console.log('123'.charCodeAt(0)) // 49
 console.log('123'.charCodeAt(1)) // 50
 console.log('123'.charCodeAt(2)) // 51
*/
```

> ***Refer to this*** [***CodeSandBox Link***](https://codesandbox.io/p/devbox/clipboard-health-problem-solving-round-1-9lqmxm) ***for solution***

This problem included many edges including fractional numbers and negative numbers. It was expected to handle all the edge case scenarios without using in-built `Number` function. The hint about using ASCII character codes helped me quickly devise a solution for this problem.

## Javascript Problem-Solving Round 2

Duration: 60 minutes

The problem statement involved finding the top 3 interesting articles from a paginated API. The top 3 articles will be ranked according to the number of likes and comments each article has received.

**Example:** API Response Structure  
The metadata object will contain information on the number of pages, total articles & link to the next page. Using this link, the next set of articles should be queried till the next page is `undefined` i.e. the last page.

```javascript
// nextPage variable will be absent in case of last page
{
  "metadata": {
    "page": 1,
    "pageCount": 5,
    "totalCount": 21, 
    "nextPage": "http://interview-api.jazeee.com/data/articles/page-2.json"
  },
  "articles": [
    {
      "id": 1,
      "title": "The Fall of Gondolin",
      "content": "The Fall of Gondolin was a major event in the First Age of Middle-earth. It was the destruction of the city of Gondolin by Morgoth, the Dark Lord. The city was founded by Turgon, a son of Fingolfin, and was one of the greatest cities of the Noldor. It was hidden from Morgoth by a great spell, but he eventually found it and destroyed it.",
      "author": "Galadriel",
      "publishedAt": "2942-07-26T06:24:50Z",
      "likes": 9,
      "comments": [
        "Nice article."
      ]
    },
    {
      "id": 2,
      "title": "The Battle of the Five Armies",
      "content": "The Battle of the Five Armies was a major battle in the Third Age of Middle-earth. It was fought between the Dwarves, Elves, Men, and Goblins of the Misty Mountains. The battle was caused by the Dwarves' attempt to reclaim their lost treasure from Smaug the Dragon. The battle ended with the death of Smaug and the defeat of the Goblins.",
      "author": "Eowyn",
      "publishedAt": "2942-07-25T06:24:50Z",
      "likes": 5,
      "comments": [
        "This is a great article!",
        "I really enjoyed this."
      ]
    },
    {
      "id": 3,
      "title": "The Scouring of the Shire",
      "content": "The Scouring of the Shire was a series of events that took place in the Shire at the end of the Third Age of Middle-earth. It was a hobbit rebellion against the forces of Saruman, who had taken control of the Shire. The rebellion was led by Frodo Baggins and Samwise Gamgee, who had returned from their quest to destroy the One Ring. The Scouring of the Shire ended with the defeat of Saruman and the restoration of peace to the Shire.",
      "author": "Arwen",
      "publishedAt": "2942-07-24T06:24:50Z",
      "likes": 3,
      "comments": [
        "I don't agree with this article.\nWe should have succeeded. - Wraiths Rule."
      ]
    },
    {
      "id": 4,
      "title": "The Last Alliance of Elves and Men",
      "content": "The Last Alliance of Elves and Men was a military alliance formed in the Second Age of Middle-earth to defeat Sauron. The alliance was led by Elendil, the High King of the Noldor, and Gil-galad, the High King of the Elves. The alliance was victorious in the War of the Last Alliance, but both Elendil and Gil-galad were killed in the battle.",
      "author": "Glorfindel",
      "publishedAt": "2942-07-23T06:24:50Z",
      "likes": 1
    },
    {
      "id": 5,
      "title": "The Destruction of the One Ring",
      "content": "The Destruction of the One Ring was the final event of the Third Age of Middle-earth. It was the destruction of the One Ring by Frodo Baggins and Samwise Gamgee.",
      "author": "Galadriel",
      "publishedAt": "2942-07-22T06:24:50Z",
      "likes": 0
    }
  ]
}
```

The solution involved fetching all articles from a paginated API, storing them in an array, and sorting the array based on the combined count of likes and comments. Finally, the top 3 articles were printed. This solution was implemented using Vanilla JS. Covering the entire solution to this problem isn't feasible in this blog, but I plan to write a detailed solution in a separate post.

## **Conclusion**

A week after finishing the interviews, the recruiter informed me that I couldn't clear the final round due to expectations mismatch. The last round didn't go as expected & perhaps the interviewer didn't find me fit for the role.

Nevertheless, I gained many insights and identified areas for improvement from this interview experience.

Thank you, guys, for reading up till here, I hope you enjoyed and learnt something new! You can connect with me on [**X**](https://twitter.com/Jaynil_Gaglani), [**LinkedIn**](https://www.linkedin.com/in/jaynilgaglani/) & [**GitHub**](https://github.com/Jaynil1611).

Happy Coding! ✌️

## [**Interview Experience Series**](https://jaynil-gaglani.hashnode.dev/series/interview-experience)

In this series on Hashnode, I've compiled advice, resources, and real-world interview experiences to help you prepare for your front-end developer interview.