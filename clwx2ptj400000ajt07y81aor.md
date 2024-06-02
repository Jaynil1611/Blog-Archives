---
title: "Frontend Interview Experience at Healthify"
seoTitle: "Frontend Interview Experience at Healthify"
seoDescription: "Hello folks, I am sharing my frontend interview experience at healthify in this blog."
datePublished: Sun Jun 02 2024 05:00:28 GMT+0000 (Coordinated Universal Time)
cuid: clwx2ptj400000ajt07y81aor
slug: frontend-interview-experience-at-healthify
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1716712007104/af5d1fee-187e-46fe-9a51-cb2838d71a0f.png
tags: interview, startups, javascript, frontend, frontend-development, interview-questions, healthify

---

Hello folks,  
I had the opportunity to interview recently at [Healthify](https://www.linkedin.com/company/healthifyme) for the **Software Engineer 2 - Frontend role**. This role is more inclined towards the frontend domain & I will share my interview experience in this post.

## **How did I get to know about this opportunity?**

The recruiter contacted me directly through LinkedIn InMail. I showed interest in the opportunity, and we discussed it further over a call, which led to scheduling the interview rounds.

## **Interview Rounds**

In total, there are 5 rounds:

* React Coding Round
    
* Javascript Coding Round
    
* Frontend System Design Round
    
* Hiring Manager Round
    
* HR Round
    

## React Coding Round

Duration: 60 minutes

The problem statement included a timer component with pause, resume, lap & reset features. All the lap values should be shown below the timer. Creating a new timer with the same features and deleting an existing timer were additional tasks introduced by the interviewer at the end. The interviewer wanted to check the scalability of the code I had written by introducing create & delete features at the end. So, it would be wise to plan the component structure before writing any code. You can view the complete solution to this problem at the link below.

> Refer to this [CodeSandBox Link](https://codesandbox.io/p/sandbox/healthifyme-react-coding-t45s39) for solution

## Javascript Coding Round

Duration: 60 minutes

This round involved solving a problem statement using vanilla Javascript. Problem Statement: Create a function that limits how many times a given function can be called within a specific time period. I took the time to understand the exact requirements of this problem and realized that it is similar to rate-limiting functionality i.e. throttling in JS. It was a challenging question.  
I have attached the solution below.

> Refer to this [CodeSandBox Link](https://codesandbox.io/s/healthifyme-js-coding-n3jzmx) for solution

## Frontend System Design Round

Duration: 60 minutes

Problem Statement: Design a dynamic form which renders all the fields received from the backend API response. Design the backend API response structure to render the form and support dynamic configuration options.

The form should have the following features:

* Render the form, user should be able to interact with the form.
    
* Form validations for different types of fields & error messages
    
* User should be able to submit the form
    

The below snippet mentions the different configuration options to render the form. I was asked to add password & confirm password field. Normalized API response for a state-based document ID selector field was discussed.  
For example, if the state of Karnataka is selected, only the eligible documents for that state should be shown in the document selector dropdown.

```javascript
/*
Configuration:
Fetching all the fields at once for the form
Show different UI depending on type of form
Resuable Field depending on type of input
TextField (text, number, email, password, textarea)
DateField (date, month, time, range)
Dropdown / Select (Single, Multiselect, Autocomplete)
Submit Buton
State management (React context, useReducer)
Tech Stack (React)
Styling (Styled components)
*/


// Sample API Response 
{
	"name": "Signin",
	"type": "Signin",
	"fields": [
		{
			"id": "",
			"type": "text",
			"name": "",
			"placeholder": "",
			"value": "",
			"validationRegex": "",
			"options": [
				{
					"id": "",
					"value": ""
				}
			],
			"typeOfSelect": "single/multiple",
			"typeOfDate": "month/time/range/date",
			"lowerDateTimeStamp": 12223,
			"highestDateTimeStamp": 21312
		}
	]
}
```

## Hiring Manager Round

Duration: 45 minutes

This round was taken by the VP of Technology at Healthify. He shared the feedback from the previous rounds with me and mentioned that there are some areas where I need to improve. They were overall satisfied with my candidature. I enquired about the team structure, project & culture at the company. Also, we discussed the responsibilities of the role and the expectations. There were only a handful of frontend engineers working in the company & they were looking to expand the web team. The company follows a flat hierarchy structure & team members switch pods frequently. Salary negotiations also took place during this round.

## HR Round

Duration: 30 minutes

After a round of introductions, we discussed the company culture, employee wellness benefits, latest funding round. I mentioned my expectations from the company & vice versa.

## **Conclusion**

Since the feedback was positive, as discussed in the hiring manager round, I was selected for the role and given an offer at the end of the final round. I gained many insights and identified areas for improvement from this interview experience.

Thank you, guys, for reading up till here, I hope you enjoyed and learnt something new! You can connect with me on [**X**](https://twitter.com/Jaynil_Gaglani), [**LinkedIn**](https://www.linkedin.com/in/jaynilgaglani/) & [**GitHub**](https://github.com/Jaynil1611).

Happy Coding! ✌️

## [**Interview Experience Series**](https://jaynil-gaglani.hashnode.dev/series/interview-experience)

In this series on Hashnode, I've compiled advice, resources, and real-world interview experiences to help you prepare for your front-end developer interview.