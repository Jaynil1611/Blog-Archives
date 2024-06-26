---
title: "Developing an Infinitely Nested Comment & Reply Feature"
seoTitle: "Infinitely Nested Comment & Reply Feature"
seoDescription: "Developing an Infinitely Nested Comment & Reply Feature similar to Reddit Comments"
datePublished: Sun Sep 11 2022 11:11:22 GMT+0000 (Coordinated Universal Time)
cuid: cl7x8k5a70dpuw8nv2zbd477d
slug: infinitely-nested-comment-reply-feature
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1662890927271/dlqNIl1h6.png
tags: javascript, reactjs, problem-solving, reddit, tailwind-css

---

## What are we going to cover today? 
We will develop a nested comment & reply feature of Nth depth where n can be any finite number. First, the following section will discuss the problem statement in more detail. Let's get started!


## Problem Statement
We need to create a nested comment & reply feature that allows users to start a conversation by adding a comment. Users should be able to make replies at any nested level within the same comment. Deleting any comment or reply should delete all subsequent replies made to that comment or reply. If the user deletes the top-level comment, then all the nested replies associated with it get deleted.


## Approaches for solving the above problem
For solving this problem, we need to take care of the first-level comments that the user adds.
Then, we need to create a parent(comment) - child(reply) relation for capturing all the replies made to the first-level comments.
Similarly, for each subsequent reply, we need to create a parent-child relationship where the parent is a reply created a level above.
A parent comment can have multiple replies & each reply can have multiple child replies which can go on at any level of nesting. It forms a tree structure where each node at any level of depth can have multiple children.

There are 2 approaches for solving this problem which is as follows:

1. This problem is a prime example of recursion which you'd have guessed until now which forms our first approach to solve this problem. 
We will store all the first-level comments in an array where each comment will be represented as
```javascript
  const comment = {
        id: "1001",
        text: "This is a first-level comment",
        children: [child],  // To store all replies at the next level
        parentId: null,
     };

  const reply = {
        id: "1002",
        text: "This is a reply",
        children: [],
        parentId: "1001",  // To store the id of parent
     };

  const commentList = [parent];
```
Here, `parentId` will be null for the first level comment added by the user. It will be the `id` of the parent's comment for the reply which forms a parent-child relationship between them.
`commentList` forms the array of the first-level comments whose `parentId` is always `null`. This array is used to render the parent comments on UI (user interface) & the child replies associated with each of them.

2. The second approach is derived from the above approach itself. Instead of creating an array of objects, we use an object to store all the comments & replies where the key is their unique `id` & value is the comment or reply object which is represented as follows:
```javascript
  const comment = {
        id: "1001",
        text: "This is a first-level comment",
        childrenIds: ["1002"],  // To store all ids of replies at the next level
        parentId: null,
     };

  const reply = {
        id: "1002",
        text: "This is a reply",
        childrenIds: [],
        parentId: "1001",  // To store the id of parent
     };

  const commentList = {
        firstLevelIds: ["1001"],  // To store ids of only first-level comments
        1001: comment,
        1002: reply,
     };
```
Here, `firstLevelIds` is an array of ids of only first-level comments which are used to render the comment along with their child replies on UI.  You can notice here that `commentList` is an object with key-value pair being the id of comment/reply & the comment/reply object respectively. Also, here `childrenIds` is an array which only stores the ids of corresponding replies at the next level as opposed to storing the entire reply object.


## Comparison of approaches & deciding on the optimised approach
Let's compare the above two approaches based on time complexity. Let's consider the basic operations of creating and deleting comments or replies.

1. **Creation**: 
  - *1st Approach*: Adding a new first-level comment will be in the constant time i.e. O(1) since we are just appending the new comment to the array. However, while adding a reply we need to traverse the entire array recursively & find the parent comment/reply to whom we are adding the newly created reply. Once, the parent is found we need to update the `children` array in parent & append the newly created reply to this array. This operation of adding a new reply has the worst-case time complexity of O(n) where `n` is the total number of comments & replies present.

  - *2nd Approach*: In the second approach, adding a first-level comment requires adding an entry to `commentList` & appending its id in the `firstLevelIds` array.
For adding a new reply, while rendering the entire feature, we have the parent id of the newly created reply at the time of its creation. We only need to create a new object for the reply & add an entry in`commentList`. Also, appending the id of the newly created reply in the `childrenIds` array of its parent takes O(1) time since we can access its parent easily given the id of the parent. The overall operation happens in constant time i.e. O(1) & it is independent of the total number of comments present.

2. **Deletion**: 
  - *1st Approach*: Deleting any first-level comment takes O(1) time as we just remove the entry from the array after traversing for the required id to be deleted. To delete nested replies, we need to traverse the array recursively to find the parent comment/reply & delete all the child replies recursively till the reply with no children has a worst-case time complexity of O(n).

 - *2nd Approach*: Deleting any first-level comment takes O(1) time as we have all the ids of child replies made to this comment which we need to remove from `commentList`. Also, the id of this comment needs to be deleted from the list of `firstLevelIds`.
For deleting, nested replies, we remove the entry of this reply from the parent's `childrenIds` array, remove the entries for all of its child replies & finally remove the entry of this reply from `commentList`. This operation's time complexity is dependent on the number of children present but it definitely takes less time compared to the deletion process of the above approach. We can consider the average-case time complexity to be O(1).

We will go ahead with the optimized approach & write the code for it in the following sections.


## Let's start coding! 
%[https://giphy.com/gifs/cat-hacker-webs-o0vwzuFwCGAFO]

I have used react & created a small app to display the solution for the nested comment feature. I will be explaining the code of the app. I have used the create react app with typescript [template](https://create-react-app.dev/docs/getting-started/#creating-a-typescript-app). Also, I have used tailwind [css](https://tailwindcss.com/) to simplify the styling for the app. Once, you have the setup for react & tailwind completed, you can start coding the components required for the functioning of the comment feature. We will see the breakdown of the components in the next section. I have attached links to the GitHub repository of the app in the resources section where I have written the code for both approaches.


## Breaking the problem into various components
I have broken the problem into 4 components:
1. `CommentList`: to render a list of all the comments with their associated replies.
2. `Comment`: to show a single comment or reply with two action buttons for deleting & replying
3. `AddComment`: to display a comment input widget for adding first-level comments
4. `AddReply`: to display a reply input widget for adding replies to the parent comment

Let's understand the major functions of each of these components.
- **`CommentList`**  
  This component initializes the state object which is used to store all the comments, replies & `firstLevelIds`. It renders the `AddComment` & maps through all the first-level comments using the `firstLevelIds` array & renders `Comment` component for each comment.
  ```jsx
  // CommentList.tsx
  
  const CommentList = () => {
    const [commentList, setCommentList] = useState({
      firstLevelIds: [],
    });
    return (
      <div>
        <AddComment setCommentList={setCommentList} />
        {commentList.firstLevelIds.map((id) => {
          return (
            <div key={id}>
              <Comment
                commentId={id}
                commentList={commentList}
                setCommentList={setCommentList}
              />
            </div>
          );
        })}
      </div>
    );
  };
  ```

- **`AddComment`**  
  This component renders the comment input widget along with an `Add Comment` action button for adding first-level comments. The major function of this component is to add a new comment to the state object & append the newly created comment's id to the `firstLevelIds` array. The below code snippet is of the `handleAddComment` function.    

```javascript  
 // AddComment.tsx
            
  const handleAddComment = () => {
    const newId = getUniqueId();
    const newComment = {
      id: newId,
      text: commentText,
      children: [],
      parentId: null,
    };
    setCommentList((prevList) => ({
      ...prevList,
      firstLevelIds: prevList.firstLevelIds.concat(newId),
      [newId]: newComment,
    }));
    setCommentText("");
  };
```
You'll find the entire source code of this file from the GitHub repository link in the resources section.

- **`AddReply`**   
This component shows a reply input widget for adding a new reply to a parent comment. The major function of this file is to create a new reply & update the state object. Append this newly created reply's id to the children's array of parent comment & update the parent comment in the state object. The below code snippet is for the same function.  

```javascript
// AddReply.tsx

 const updateCommentList = (prevList, newComment) => {
   const updatedParentComment = {
     ...parentComment,
     children: parentComment.children.concat(newComment.id),
   };
   return {
     ...prevList,
     [parentComment.id]: updatedParentComment,
     [newComment.id]: newComment,
   };
 };
```

- **`Comment`**  
  This component renders each comment & their associated replies with two action buttons `Delete` &  `Reply`. It calls the `AddToReply` component on clicking the reply button. The major function of this component is to delete the comment along with the subsequent child replies & update the state object. Firstly, we check the child replies to the current comment & delete all of them iteratively & then delete the current comment. Next, we remove this comment's id from `firstLevelIds` if the parent of this comment is null & return the updated comments object.
Otherwise, we remove this comment's id from the children array of the parent comment & update the parent comment while returning the final object. The below code snippet is of `updateCommentList` function.

```javascript
// Comment.tsx

  const updateCommentList = (prevList, currentComment) => {
    const updatedComments = prevList;
    const currentId = currentComment.id;
    const childComments = updatedComments[currentId].children;
    const parentId = currentComment.parentId;
    const parentComment = updatedComments[parentId];
    if (childComments.length !== 0) {
      childComments.forEach((id) => delete updatedComments[id]);
    }
    delete updatedComments[currentId];

    if (parentId === null) {
      updatedComments.firstLevelIds = prevList.firstLevelIds.filter(
        (id) => id !== currentId
      );
      return { ...updatedComments };
    }
    const updatedParentComment = {
      ...parentComment,
      children: parentComment.children.filter((id) => id !== currentId),
    };
    return {
      ...updatedComments,
      [parentId]: updatedParentComment,
    };
  };
```

## Final Solution
The final solution after stitching all the components together looks like this:  
You can view the final solution in this code sandbox:

%[https://codesandbox.io/s/optimised-nested-comments-4cqcbx?fontsize=14&hidenavigation=1&theme=dark&view=preview]


## Conclusion
In this article, we solved the problem of an infinitely nested comment & reply feature & also created a small app to visualize the solution. We compared two approaches to solve this problem & decided on the optimized approach that takes O(1) time for the basic operations of creating & deleting comments. Finally, we looked at the breakdown of the problem into different components & codes for each of them.

Thank you guys for reading up till here, I hope you enjoyed and learnt something new! 
You can connect with me on [**Twitter**](https://twitter.com/Jaynil_Gaglani), [**LinkedIn**](https://www.linkedin.com/in/jaynilgaglani/) & [**GitHub**](https://github.com/Jaynil1611). 

Happy Coding! ✌️

## Resources
- [CodeSandbox Link for Optimized Solution](https://codesandbox.io/s/optimised-nested-comments-4cqcbx?fontsize=14&hidenavigation=1&theme=dark)
- [CodeSandbox Link for Recursive Solution](https://codesandbox.io/s/recursive-comments-oz4r26?fontsize=14&hidenavigation=1&theme=dark)
- [Github Link for Optimized Solution](https://github.com/Jaynil1611/Nested-Comment-Reply-Feature/tree/optimised-nested-comments)
- [Github Link for Recursive Solution](https://github.com/Jaynil1611/Nested-Comment-Reply-Feature/tree/recursive-comments)
