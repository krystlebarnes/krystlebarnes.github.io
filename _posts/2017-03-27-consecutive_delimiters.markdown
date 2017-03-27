---
layout: post
title:  "Consecutive Delimiters"
date:   2017-03-27 15:57:57 +0000
---


I recently found myself stuck on an assignment that required splitting a string based on two delimiters, a space and a comma. With a quick google search I was able to figure out how to do this using RegEx: `/[\s,]/`. This worked great if the string was something like `"foo bar,baz"`, as it would produce the desired array of `["foo", "bar", "baz"]`. But what would happen if the string was `"foo, bar, baz"`? I would end up with `["foo", "", "bar", "", "baz"]` when I was hoping for `["foo", "bar", "baz"]`.

So what was the problem? It wasn't treating consecutive delimiters as one delimiter. I tried searching for solutions, but wasn't finding a clear answer. I came across one blog that suggested adding an asterisk to my RegEx like this: `/[\s,]*/`, but an `*` in RegEx matches the preceding expression *zero* or more times. Using the asterisk in my expression for splitting the string `"foo, bar, baz"` would have resulted in: `["f", "o", "o", "b", "a", "r", "b", "a", "z"]`. Yikes.

What I really needed it to do was match the preceeding expression *one* or more times. In other words, if the preceeding expression, which in this case is a space *or* a comma, appears *one* time (rather than zero times) or more than one time consecutively, treat that as one matched expression (or in this context where we are using it with the `#split` method, treat it as one delimiter). Luckily that's just as easy by adding a plus sign instead of an asterisk: `/[\s,]+/`. Using the `+` finally gives the desired result of `["foo", "bar", "baz"]`. Thank goodness.

