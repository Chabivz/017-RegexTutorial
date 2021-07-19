# 017 - Regex Tutorial: Computer Science for Javascript

Regex or Regular Expression is a sequence of characters that specifies a search patter. Usually such patterns are used by string-searching algorithm for "find" or "find and replace" operations on strings or for input validation. It is a technique developed in theoretical computer science and formal language theory. Regular expression is not inherently to a specific programming language, you could use Regular Expression on Java, Javascript, Python, C++, C#, Perl...

The concept arose in the 1950s, when the American mathematician Stephen Kleene formalized the description of a regular language, and came into common use with the Unix text processing utilities ed (a line editor for the Unix operating system), an editor, and grep (a  command-line utility for searching plain-text data sets for lines matching a regular expression), a filter (a computer program or subroutine to process a stream, producing another stream). This is an excerpt from [Wikipedia](https://en.wikipedia.org/wiki/Regular_expression) used to define the regular expression.

## Table of Contents

- [Anchor and Bounderies](#anchors-and-bounderies)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Class](#character-class)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Greedy and Lazy Match](#greedy-and-lazy-match)

## Regex Components

- Matching an HTML Tag: `/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/`

## Anchors and Bounderies

- Matching an HTML Tag: `/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/`
- Anchors are what we typically use to start and end our REgex searches. More specifically, Anchors are set of Regex token that are not interpreted as characters, but instead are used to create the parameters in which a Regex is written.
- Taking our code as an example `/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/`, our `^` and `$` would be our anchor tokens.
- `^` Use to indicate the beinnging of a Regex expression. Meaning whatever character or characters that would proceed after the `^` is where our Regex would begin. 
  - Example `^ch` would match any string that begins with a `ch`. Such as `ch`heese or `ch`ocolate.
- `$` Is used to indicate the end of a Regex expression. Meaning whatever character or characters that wound proceed before the `$` is where our Regex expression would end. 
  - Example wound be `te$` that finds any word that ends with `te`. Such chocola`te` or pomegrana`te`
## Quantifiers

- Matching an HTML Tag: `/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/`
- Quantifiers are used to measure the nu,ber of expressions or characters that we are looking to match up in our Regex.

|Quantifier|Legend|Example|Sample Match|
|---|---|---|---|
| `+` |The + (one or more) |Version `\w-\w+`|Version A-b1_1|
|`{3}`| Exactly three times|`\D{3}`| ABC |
|`{2,4}`| Two to four times| `\w{2,4}`   | abcd   |
|`{3,}`|Three or more times|`\w{3,}`|javascript|
|`*`|The * (zero or more ) |`A*`|AAA|
|`?`|Once or none|plurals`?`|plural|

- Our matching an HTML Tag `/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)` contain three of these `+`, `?` and `*`

## OR Operator

- Matching an HTML Tag: `/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/`
- `[]` is the OR Operator in our `/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)` matching html tag Regex seen in the following. 
  - /^<(`[`a-z`]`+)(`[`^<`]`+)*(?:>(.*)<\/\1>|\s+\/>)
  - Essentialy, what we put in the `[]` is what we are searching for. 
  
  - In our first OR Operator `([a-z]+)`. We are searching for ASCII characacters from `a` to `z`. 
  - This can also be done by doing `[A-z]`. When you are looking at the ASCII table, you will see the following A = `65`, Z = `90`, a = `97` and z = `122`.
  - In our second OR Operator `[^<]`. We are capturing previous token between zero and unlimeted times, as many time as possible. 
  - In our third OR Operator will be `(.*)`. It will match any characters (except for line terminators.)
## Characters Class

- Matching an HTML Tag: `/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/`
A character class is a special notation that matches any symbol from a certain set.

1. `\d` - Digits
2. `\D` - Non-digits
3. `\s` - Space symbols, tabs, newlines.
4. `\S` - All but `\s`
5. `\w` - Latin letters, digits, underscore '_'.
6. `\W` - All but `\w`.
7. `\.` – Any character if with the regexp 's' flag, otherwise any except a newline \n .


## Flags

- Matching an HTML Tag: `/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/`

- `/ /` Flags are how we start and end our Regex Expression. `/sample-expression/`. The `/ /` let's javascript know that we are creating a Regex expression. While more advanced flags exist, we don't need to use any here.

## Grouping and Capturing

- Matching an HTML Tag: `/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/`
`()` represents how we "Group and Capture" seperate parts of our code. 
- In the case of our Matching HTML Regex , we have three sections being "grouped and captured"
 `([a-z]+)`, `([^<]+)` and `(.*)`. 
- These three groupings represent the three different parts that make up our email
  
- Example: `<a href=`"https://amazon.com"`>`Amazon`</a>`
  - `([a-z]+)` First group will be `a` tag at the beginning of `href` will be our first group.
  - `([^<]+)` Second grpi[] will be `href="https://amazon.com"`.
  - `(.*)` Third match will be `Amazon`. 

## Greedy and Lazy Match
- Matching an HTML Tag: `/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/`
- A greedy match exists whenver a `+`, `*`, `?`, is used in a Regex expression, which our matching html expression has six.

  - Example: `<a href=`"https://amazon.com"`>`Amazon`</a>`
  - `/^<([a-z]+)` First is looking for an for a characters that start with `<` and begins with a letter. In this sample it will be `a`.
  - `([^<]+)*` Second and Third is looking for all the character after the first group. In this sample it will be `href="https://amazon.com"`.
  - `(?:>(` Forth will disabling the capturing group before the ending "`>`" before `>Amazon`. 
  - `.*)<\/\1>|\s+\/>)` Fifth and Sixth "`.*`" matches any characters from 0 to unlimited times.
    - `\/\1>` Matches the text as most recent matched by the 1st capturing group that ends with "`>`"


|Quantifier|Legend|Example|Sample Match|
|---|---|---|---|
| `+` |The + (one or more) is 'greedy'|`\d+`|12345|
| `?` |Makes quantifiers 'lazy'|`\d+?`|1 in `1`2345|
|`*`|The * (zero or more ) is 'greedy'|`A*`|AAA|
|`?`|Makes quantifier 'lazy'   |`A*?`|empty in AAA|
|`{2,4}`| Two to four times 'greedy'  | `\w{2,4}`   | abcd   |
|`?`| Makes quantifier 'lazy'  | `\w{2,4}`   | ab in `ab`cd   |
## Author 

Chris Abiva is aspiring to be a Full Stack Web Developer through the University of Washington Online Bootcamp. 
### Question 

- Github [Chabivz](https://github.com/Chabivz)
- Email [chrisabiva@hotmail.com](mailto:chrisabiva@hotmail.com)