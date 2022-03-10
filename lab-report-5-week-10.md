# Comparing Different `MarkdownParse.java` Functionality

## Finding Differences

I stored the output of the provided `MarkdownParse.java` and my `MarkdownParse.java` output in separate files called `joe-results.txt` and `my-results.txt` respectively. Before that, I used the provided `script.sh` that ran every test in a folder using a bash for loop with the `MarkdownParse.java` in the same overall directory and modified it to print the file that the test case belonged to. With two text files storing the output of the same test cases, I used the bash `diff` command to output the different lines of output between the text files.

## Test File `489.md`

Test Case :

```
[link](foo
bar)
```

Outputs (First is my output) :

```
864,865c866
< [foo
< bar]
---
> []
```

Expected Output : []

The provided repository's implementation is correct according to [CommonMark Rules](https://spec.commonmark.org/dingus/). My implementation is incorrect because it does not account for new lines within links, and new lines within links break the link structure in CommonMark. A possible fix could be searching for the existence of `\n` which denotes a new line, and skip the current set of brackets and parentheses if the index of `\n` is not -1, or exists. Ideally, check this if a potential link does exist, meaning if all brackets and parentheses are present, but before any complex checks.

```
...

// For test case 5 (test-file3)
if(openParen == -1 || closeParen == -1) {
    break;
}

// FIX !!!
// Check if there exists a new line in between the brackets and parentheses
// If so, mark the link as invalid
if (markdown.indexOf("\n") != -1) {
    flag = true;
}

// For test case 2 (bug for paren inside link)
if(markdown.charAt(closeParen - 1) == '(') {
    closeParen = markdown.indexOf(")", closeParen + 1);
} ...
```

## Test File `577.md`

Test Case :

```
![foo](train.jpg)
```

Outputs (First is my output) :

```
1062c1062
< []
---
> [train.jpg]
```

Expected Output : []

My repository's implementation is correct according to [CommonMark Rules](https://spec.commonmark.org/dingus/). The provided implementation is incorrect because it counts images as links as it does not check for an exclamation mark preceding the open bracket. A possible fix is to simply check the index before the open bracket to see if it is an exclamation mark, and if so just update currentIndex to be after the nextOpenBracket, bypassing the current set of brackets and parentheses, and skipping the rest of the commands in the current iteration of the while loop. Ideally, check this as one of the first checks, because `![` automatically assumes an image is being made.

```
...

while(currentIndex < markdown.length()) {
    int nextOpenBracket = markdown.indexOf("[", currentIndex);
    int nextCodeBlock = markdown.indexOf("\n```");
    // FIX !!!
    // Check if there exists an "!" before the open bracket, meaning image
    if(nextOpenBracket > 0 && markdown.charAt(nextOpenBracket - 1) == '!') {
        currentIndex = nextOpenBracket + 1;
        continue;
    }
    if(nextCodeBlock < nextOpenBracket && nextCodeBlock != -1) {
        int endOfCodeBlock = markdown.indexOf("\n```");
        currentIndex = endOfCodeBlock + 1;
        continue;
    } ...
```