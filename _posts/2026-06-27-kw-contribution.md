---
title: "First kw Contribution"
date: 2026-06-27 20:25:00 -0300
categories: [Development, Open Source]
tags: [free software, learning, kw]
---

# Goals

For a university assignment, I had to contribute to the Kworkflow (kw) project. I chose to work on issue #1142, which reported a bug in a test utility function called compare_command_sequence. The 
goal was to fix the function so it would return the correct exit status (0) for single-line outputs, and to update the function's documentation to recommend the use of assertEquals for these specific
cases.

# Experience Summary

The bug was caused by a specific behavior in Bash arithmetic evaluations. Inside the function's while loop, a counter was being incremented using ((count++)). Because count was initialized to 0, the 
first evaluation of this postfix expression resulted in 0. In Bash, if an arithmetic expression evaluates to zero, it returns an exit status of 1 (failure). Since a single-line output only runs the 
loop once, the function finished with that failure status, breaking the tests.
The fix was straightforward. I changed the postfix increment to a prefix increment ((++count)). This way, the expression evaluates to 1 on the first iteration, ensuring a successful exit status (0). 
I also added a comment to the function header explicitly recommending assertEquals over compare_command_sequence for single-line comparisons, as requested by the issue author.
Right now, the PR is open and I am waiting for the maintainers to review the code. I will update this post once I get their feedback.

# Feedback

After almost a month of waiting for a reply, I got an email from Rodrigo Siqueira, one of the project maintainers. He accepted the contribution, noting that he made some minor adjustments to the original code before merging it. The patch has now been officially pushed to the `unstable` branch of the repository. He apologized for the late response, but I think it must have been because of the amount of work with the repository. I don't know if my experience waiting for an answer would apply to everyone, or if it was just an isolated incident.

# Conclusion

In general, the experience contributing to the Kworkflow (kw) project was very good. Aside from the time waiting for a reply, all the other aspects like finding an issue, understanding the issue, learning how to test my contribution were pretty easy to adapt and understand. 
