[home](../../index) | [blogs](../../blogs)

# Neat XOR trick (in C#)
## 2022/12/18

Most developers are familiar with the XOR operation but I want to demonstrate a little C# trick I learned some time ago from the StackOverflow chat (does this still exist?) some years ago.

XOR is, in my opinion, somewhat obsure and Ive encountered the need to use it only few times in the domains I've encountered. As a refresher, here is a truth table for the operation as a function of its inputs.

| A | B | Result |
| ----------- | ----------- | ------- |
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

In C# there is a built-in operator that we don't see too much in the wild for XOR. To reproduce the truth table above we can construct the following statement...

`var result = a ^ b`

This operator in my opinion is quite obscure because we don't see it too often in production code. This can lead to confusion and the need to analyze its impact further than the usual operators. However, there's a little trick I learned that is equivalent to the obscure syntax which can be formulated into the following statement...

`var result = a != b`

Now, first thing any developer of salt will say is "does this really produce the same result?" Let's find out using a truth table...

| A | B | Result |
| ----------- | ----------- | ------- |
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

After some quick mental cycles, yes it does! So as much as I'd love to use the `^` operator I almost always fallback on `!=` to get the same result so that people reading my code can figure out what its doing without needing to lookup syntax.

I haven't tested this broadly but I suspect this is applicable to a broad range of other languages as well.