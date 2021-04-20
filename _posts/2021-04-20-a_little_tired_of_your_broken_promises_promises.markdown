---
layout: post
title:      "A little tired of your broken promises, promises"
date:       2021-04-20 17:36:17 +0000
permalink:  a_little_tired_of_your_broken_promises_promises
---

[Name that 90's song.](https://www.youtube.com/watch?v=drvS9w-lTMc) This lyric sums up how I felt as I was going through my JS project running into errors mentioning promises. The most frustrating part about it was that I wasn't really sure what a promise is in Javascript, so anytime I saw that word it just confused me more. In fact, I felt the most frustrating thing about learning Javascript was all the new vocabulary that just seemed so foreign. 

In trying to learn more about JS promises, many of the articles I came across talked about them in a very literal sense. But with the word "promise" being so common in  our English language, I really struggled to make sense of it until I came across [this video](https://www.youtube.com/watch?v=OXpZfyVXeI8), where vlogger Cem Eygi starts off by explaining that just like a promise in real life, a promise in JS guarantees something is going to happen. That promise will either be kept (or "resolved") or broken (or "rejected"). 

According to the [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise), the syntax for creating a Promise is the following:
```
const myPromise = new Promise((resolve, reject) => {
// This is where you code whatever you're promising will execute. This example uses a setTimeout method.
  setTimeout(() => {
    resolve('foo');
  }, 300);
});
```

If you were to look at my JS project, you might think, "Wait, but there aren't any promises defined in your code? So why are we even talking about this?" Actually, anytime I used  `fetch()` in my code, a promise is actually being returned. That's because fetching an API could take a little while, and a promise allows that to process asynchronously and not hold up any other code from running. 

The examples I've shared are basically saying "I promise to execute this code," and that promise is in a pending state as that code is being processed. It eventually gets to a point where that promise is kept or that promise is broken, or in Javascript terminology: resolved or rejected. It's at this point where `.then` and `.catch` come into play. When you chain `.then` to your promise, it's like saying "when that promise is kept then do this." When you chain `.catch` you're saying "if the promise is broken, do this." The `.then` method can actually take two arguments: a callback function if the promise is resolved and a callback function if it's rejected, but it is easier to use a `.catch` statement to handle the rejected promise. The  [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) go into greater detail on how those methods work.

Instead of just being completely scared and lost any time I see the word "promise," I can now actually understand what it is, what it entails, and how it's used with the fetch() method.





