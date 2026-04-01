---
title: "Sending patches with git and a USP email"
date: 2026-04-01 10:52:00 -0300
categories: [Development, Open Source]
tags: [free software, learning]
---

## Goals
 In this tutorial, the goal was to be able to send patches using a USP email. In order to do that, we needed to use OAuth 2.0, a widely used protocol for authentication. Normaly, since we are using,
 a gmail, we would just use an App Password provided by google. However, to get this App Password, we need first to enable 2FA on our account, which is not possible with USP emails. That's why we 
 needed to use OAuth 2.0 as an alternative in this tutorial.

## Problems and Difficulties
 I didn't have problems with this tutorial itself, because the most difficult part was undo what I have done in my last tutorial. When I was doing the tutorial 5 (Sending patches by email with git),
 I didn't see the title of this one (Sending patches with git and a USP email) and, because of that, I was already looking for ways to sending patches with my university email. But, I was not 
 successful and decided to use my personal email. Now, in this tutorial, I needed to unset my personal email and set my university email again using OAuth 2.0 as an alternative.

Some other small problems I had were:
- Undo the work I have done in the last tutorial 
