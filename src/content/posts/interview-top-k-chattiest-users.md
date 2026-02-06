---
title: Top K Chattiest Users from a Chat Log in TypeScript
published: 2025-06-28
description: 'Learn how to parse chat logs and find the top K chattiest users by word count using TypeScript. This practical coding exercise helps you practice regex, string processing, and efficient map sorting for interview preparation.'
image: ''
tags: ['Interview','Bjak']
category: 'Interview'
draft: false 
---

# Background

Just one month ago, I received an interview invite from Bjak – a Malaysian company. The interview was pretty simple and fast: you introduce yourself, complete one coding problem, then both say bye-bye.

So, let's go straight to the coding problem ->

# Top K Chattiest Users from a Chat Log

## Problem Description

Given a chat log file and a number `k`, determine the **top k chattiest users**.

**“Chattiest” means** the users who have typed the most words in total.

A **word** is anything separated by whitespace.

The **log file format** is as follows (format **cannot be changed**):

```
<user1> this is some chat word
<user2> the sky is blue
This line is still attributed.
<user1> more chat from me! 38g
```

* The entire text above is given as a string in this exact format.
* You can assume that the characters `<` and `>` only appear in the file to denote a username.

Your task is to parse this log and return a list of the **top k chattiest users in descending order**.

## Example

Input:

* `log`:

  ```
  <user1> this is some chat word
  <user2> the sky is blue
  This line is still attributed.
  <user1> more chat from me! 38g
  ```
* `k = 2`

Output:

```ts
["user2", "user1"]
```

## Requirements

* Use **Node.js or TypeScript** for your solution.
* Focus on clarity and efficiency.
* Be prepared to explain your approach and test your implementation.

# Solution

```typescript
// Function to get the top K users who have typed the most words in a chat log
function getTopKChattiestUsers(log: string, k: number): string[] {
  const wordCounts = new Map<string, number>(); // Map to store word counts per user
  const userRegex = /<([^>]+)>([^<]*)/g; // Regex to match <username> message
  let match;

  // Iterate over all matches in the log
  while ((match = userRegex.exec(log)) !== null) {
    const username = match[1].trim(); // Extract and trim username
    const message = match[2].trim(); // Extract and trim message
    const wordCount = message.split(/\s+/).filter(Boolean).length; // Count words in message

    // Update the word count for the user
    wordCounts.set(username, (wordCounts.get(username) || 0) + wordCount);
  }

  // Sort users by word count in descending order, take top K, and return usernames
  return Array.from(wordCounts.entries())
    .sort((a, b) => b[1] - a[1])
    .slice(0, k)
    .map(([username]) => username);
}

// Example usage
const chatLog = `<user1> this is some chat word
<user2> the sky is blue
This line is still attributed.
<user1> more chat from me! 38g`;

const topUsers = getTopKChattiestUsers(chatLog, 2);
console.log(topUsers); // Expected output: ['user2', 'user1']
```

BTW, even though I solved this problem, I still did not receive an offer.

Good luck to you!
