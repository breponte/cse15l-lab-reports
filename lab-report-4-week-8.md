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

- I believe that my MarkdownParse would require a more complicated change/addition because my current program does not consider any functionality with backticks; so on top of adding the actual conditionals and code required to accomodate for backticks, there is still bug fixing that may require more lines of code. However, implementing backticks initially may be done in less than 10 lines of code since I would just have to check for its presence outside of the link structure.

2) Do you think there is a small (<10 lines) code change that will make your program work for snippet 2 and all related cases that nest parentheses, brackets, and escaped brackets?

- Perhaps there is a small code adjustment that would take less than 10 lines of change/addition. I would adjust the code that finds open brackets and closed brackets by trying to find a pair of open and closed brackets with the largest character span (largest distance from each other) before the first valid pair of parenthesis. Afterwards, I would find the pair of open and closed parentheses with the largest character span following immediately after the chosen closed bracket. That will be the structure of the link.

3) Do you think there is a small (<10 lines) code change that will make your program work for snippet 3 and all related cases that have newlines in brackets and parentheses?

- To accomodate for newlines in brackets and parentheses might seem simple at first as I could use String.trim to solve the problem; however, according to [CommonMark demo site](https://spec.commonmark.org/dingus/) a link should only be valid if there is only one new line between the same link structure. If there exists a line gap between the link's components then the link is no longer valid. So potentially I will have to make code that checks for new lines in succession in order to determine which links are not valid.