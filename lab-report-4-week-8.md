# More Test Cases

## Repositories

[My Repository](https://github.com/breponte/markdown-parse)

[Reviewed Repository](https://github.com/yi113/markdown-parse)

---
## Test Case #1

```
`[a link`](url.com)

[another link](`google.com)`

[`cod[e`](google.com)

[`code]`](ucsd.edu)
```
Expected Output : ```["`google.com","google.com", "ucsd.edu"]```

Test Case #1 Implementation : 
![Snip1Test](images\Snip1Test.png)

My MarkdownParse Output : 
![Snip1Fail](images\Snip1Fail.png)

Reviewed MarkdownParse Output : 
![OtherSnip1Fail](images\OtherSnip1Fail.png)


---
## Test Case #2
```
[a [nested link](a.com)](b.com)

[a nested parenthesized url](a.com(()))

[some escaped \[ brackets \]](example.com)
```
Expected Output : ```["a.com","a.com(())", "example.com"]```

Test Case #2 Implementation : 
![Snip2Test](images\Snip2Test.png)

My MarkdownParse Output : 
![Snip2Fail](images\Snip2Fail.png)

Reviewed MarkdownParse Output : 
![OtherSnip2Fail](images\OtherSnip2Fail.png)


---
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
Expected Output : ```["https://ucsd-cse15l-w22.github.io/"]```

Test Case #3 Implementation : 
![Snip3Test](images\Snip3Test.png)

My MarkdownParse Output : 
![Snip3Fail](images\Snip3Fail.png)

Reviewed MarkdownParse Output : 
![OtherSnip3Fail](images\OtherSnip3Fail.png)



## Additional Questions
1) Do you think there is a small (<10 lines) code change that will make your program work for snippet 1 and all related cases that use inline code with backticks?

    -

2) Do you think there is a small (<10 lines) code change that will make your program work for snippet 2 and all related cases that nest parentheses, brackets, and escaped brackets?

    -

3) Do you think there is a small (<10 lines) code change that will make your program work for snippet 3 and all related cases that have newlines in brackets and parentheses?

    -