# More Test Cases

## Repositories

[My Repository](https://github.com/breponte/markdown-parse)

[Reviewed Repository](https://github.com/yi113/markdown-parse)

## Test Case #1

```
`[a link`](url.com)

[another link](`google.com)`

[`cod[e`](google.com)

[`code]`](ucsd.edu)
```
***Expected Output***

***Show MarkdownParseTest.java Implementation***

***YOUR Output of Test (explain failure is occurred)***

***OTHER'S Output of Test (explain failure is occurred)***



## Test Case #2
```
[a [nested link](a.com)](b.com)

[a nested parenthesized url](a.com(()))

[some escaped \[ brackets \]](example.com)
```
***Expected Output***

***Show MarkdownParseTest.java Implementation***

***YOUR Output of Test (explain failure is occurred)***

***OTHER'S Output of Test (explain failure is occurred)***



## Test Case #3
```
[this title text is really long and takes up more than 
one line

and has some line breaks](
    https://www.twitter.com
)

[this title text is really long and takes up more than 
one line](
    https://ucsd-cse15l-w22.github.io/
)


[this link doesn't have a closing parenthesis](github.com

And there's still some more text after that.

[this link doesn't have a closing parenthesis for a while](https://cse.ucsd.edu/



)

And then there's more text
```
***Expected Output***

***Show MarkdownParseTest.java Implementation***

***YOUR Output of Test (explain failure is occurred)***

***OTHER'S Output of Test (explain failure is occurred)***



## Additional Questions
1) Do you think there is a small (<10 lines) code change that will make your program work for snippet 1 and all related cases that use inline code with backticks?

    -

2) Do you think there is a small (<10 lines) code change that will make your program work for snippet 2 and all related cases that nest parentheses, brackets, and escaped brackets?

    -

3) Do you think there is a small (<10 lines) code change that will make your program work for snippet 3 and all related cases that have newlines in brackets and parentheses?

    -