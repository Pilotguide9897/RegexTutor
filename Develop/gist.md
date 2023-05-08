# The Anatomy of a URL: Using Regular Expressions to Break It Down

URLs, or Uniform Resource Locators, are the addresses we use to access web pages, images, videos, and other online resources. We see them every day in our web browsers and apps, yet many people don't fully grasp how they work or what they consist of. In fact, URLs can be quite complex and vary in format and length depending on the website or service they belong to. They often include various parts, such as the protocol (http, https, ftp), the domain name (e.g., google.com), the path (the location of the resource on the server), and query parameters (additional information passed to the server).

Despite their diversity, however, URLs actually follow certain conventions and patterns that make them easier to understand and manipulate. For example, most URLs start with a protocol and end with a top-level domain (e.g., .com, .org, .edu), and they use slashes, dots, and query strings to organize and specify their content. Understanding these conventions and patterns is essential for working with URLs, especially if you need to manipulate or extract information from them using regular expressions. With the right knowledge and tools, you can easily parse, validate, and transform URLs to suit your needs.

In this tutorial, we'll explore the common features and conventions of URLs and show you how to use regular expressions to match and extract them from text. By the end, you'll have a solid understanding of how URLs work and how to work with them using regular expressions.

## Summary

Today we will be exploring the following regular expression for identifying URLs in text:

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

This regex matches URLs that start with an optional "http://" or "https://" protocol, followed by a domain name consisting of one or more letters, digits, dots, and hyphens, and ending with a top-level domain of two to six letters or dots (e.g., .com, .org, .co.uk). The regex also matches any optional path or query parameters after the domain name.

| HTTP Protocol    | Domain          | Top-level Domain   | Optional path/Query Parameters |
| ---------------- | --------------- | ------------------ | ------------------------------ |
| `(https?:\/\/)?` | `([\da-z\.-]+)` | `\.([a-z\.]{2,6})` | `([\/\w \.-]*)*\/?$`           |

We will break down the regex into its individual components and explain what each one does, including anchors, quantifiers, character classes, grouping and capturing, and look-ahead and look-behind assertions. By the end of this tutorial, you will have a solid understanding of how this regex works and how to use it in your own projects.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

Regular expressions are a powerful and robust tool for pattern matching and text manipulation. They provide a wide range of features and options that can be used to match complex patterns and extract specific information from text. Not every regular expression needs to take advantage of all these features, however. In fact, many simple regular expressions can be written using just a few basic elements, such as character classes, quantifiers, and anchors. Sometimes, a straightforward regular expression can be more effective than a complex one that uses every available feature. Still, as a software developer it is important to be aware of the full range of regular expression features and how they can be used to solve different pattern matching problems. Knowing how to use back-references, look-ahead/behind assertions, and other advanced features can make it easier to write efficient and effective regular expressions for more complex pattern matching tasks. Overall, the key to using regular expressions effectively is to understand the problem one is trying to solve, and to use the appropriate regular expression features to match the patterns and extract the information you need.

With this knowledge in mind, the regular expression being scrutinized in this tutorial takes advantage of several Regex components to provide it with a robust capacity for detecting URLs; These components will be discussed in more detail below and are as follows:

    (1) anchors
    (2) quantifiers
    (3) character classes
    (4) grouping and capturing
    (5) bracket expressions
    (6) greedy and lazy matching
    (7) look-ahead and look-behind

Alternatively, the following regex components are not used in this particular regular expression:

    (1) OR operator
    (2) flags
    (3) back-references

For the purpose of this tutorial and to provide a more complete overview of regular expressions in general, brief sections will still be dedicated to these components.

- Please note that although not necessarily a part of the regular expression syntax itself, the `/` characters used in the example above at the beginning and end of the regular expression are used to indicate the beginning and end of the regular expression pattern. Specifically, when a regular expression is written in JavaScript, the `/` indicate to the interpreter that the enclosed text is a regular expression and separate the regular expression from any flags that may modify its behaviour (e.g., `/my regular expression/i`, where `i` is the flag and renders the regular expression case insensitive).

## Part-by-Part-Breakdown

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

1. /: The forward slashes at the beginning and end are delimiters that signify the start and end of the regular expression pattern.

2. ^: This caret symbol indicates the start of the line. The pattern must start matching from the beginning of the input.

3. (https?:\/\/)?: This part is a capturing group, denoted by the parentheses (). The ? after the group makes it optional.

- https?: This matches the string "http" followed by an optional "s", making it able to match both "http" and "https".
- :\/\/: This matches the string "://". The backslashes are escape characters that make the forward slashes treated as literal characters.

4. ([\da-z\.-]+): This is another capturing group.

- \d: Matches any digit (0-9).
- a-z: Matches any lowercase letter (a-z).
- \.: Matches a literal period ".". The backslash is an escape character.
- -: Matches the hyphen character.
- []: The square brackets define a character set, meaning it will match any single character inside the brackets.
- +: The plus symbol indicates that the preceding character set should match one or more times.
- \.: This matches a literal period ".". The backslash is an escape character.

6. ([a-z\.]{2,6}): This is another capturing group.

- a-z: Matches any lowercase letter (a-z).
- \.: Matches a literal period ".". The backslash is an escape character.
- {2,6}: This is a quantifier that specifies the preceding character set must match at least 2 and at most 6 times.

7. ([\/\w \.-]\*): This is another capturing group.

- \/: Matches a literal forward slash "/". The backslash is an escape character.
- \w: Matches any word character (alphanumeric, including underscore).
- : Matches a space character.
- \.: Matches a literal period ".". The backslash is an escape character.
- -: Matches the hyphen character.
- \*: The asterisk indicates that the preceding character set should match zero or more times.

8. \*: The asterisk outside the capturing group indicates that the entire group should match zero or more times.

9. \/?: This matches an optional forward slash "/". The backslash is an escape character, and the question mark "?" indicates the preceding character is optional.

10. $: This symbol indicates the end of the line. The pattern must match until the end of the input.

11. /: The forward slash at the end is the delimiter that signifies the end of the regular expression pattern.

### Anchors

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

Anchors are a type of special character used in regular expressions that allow users to match text from specific _positions_ within a string rather than specific characters. The two most commonly used anchors are the caret `^` and dollar sign `$`, and these are in fact used in this very regular expression.

1.  The carat `^` anchor is used to match the beginning of a line or string. In this example it is used to indicate the beginning of our url.
2.  The dollar sign `$` anchor is used to match the end of a line or string. In this example it is used to indicate the

Although they are not used in this particular case, additional examples of anchors include `\b` and `\A`, which search for word boundaries and for the beginning of strings, respectively. To put it another way, `b` lets one perform whole-word searches using regular expressions in the form of `\bmyWord\b`. Alternatively, `\B\` is the negated version of `\b` and allow for selection of any position that is not a word boundary.

whereas `\A` is similar to `^`

Due to their versatility, anchors are useful in many different types of regular expressions ranging from those involved in simple string matching all the way to complex text processing tasks.

### Quantifiers

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

Quantifiers are a category of special characters that allow for matching of a certain number of occurrences of a character, group, or class in a string. As noted above, within our example we take advantage of the plus `+` quantifier to match one or more occurrences of the preceding set of characters, in our case [\da-z\.-], because it allows us to flexibly target an unspecified number of characters and account for the wide variety in sub domain names on the web. Further, we also take advantage of the question mark `?` to include optional features, specifically `(https?:\/\/)?` and `([\/\w \.-]*)*\/` as it is used to search for the presence or absence (i.e., zero or one occurrences) of the peceding character, group, or class. I our case, we take advantage of it to detect optional components of urls, these being the http protocol and the optional path/query parameters. This regular expression also takes advantage of curly braces containing a range of values to target a specific numer of occrrences of a preceding character, group, or class. Specifically, `{2,6}` is used to target a string of 2 to 6 characters from `[a-z\.]`, allowing this expression to target any top-level domain name (e.g., `com`, `net`, `edu`, `gov`, `io`).

Overall, quantifiers are useful because they allow matching of patterns that may repeat a certain of times in a string.

### OR Operator

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

The or operator `|` is used within regular expressions to match from amongst two or more possible patterns. The or operator is not used in this particular regular expression, and is generally less common than many other regex components. An important note about the or operator is that it has a lower precedence than other regular expression operators, such as anchors and quantifiers, meaning that

### Character Classes

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

Character classes, also referred to as _character sets_ are a robus feature of regular expressions that specifies a set of characters which may be matched by any single character in the string being searched. To put it another way, character classes tell the regex engine to match all occurrences of only certain characters. For example, Character classes are defined by enclosing characters within a set of square brackets `[]` and can be used to specify specific characters (e.g., `[abc]` would match any instance of a, b, or c), or to define a range of characters that encloses any

Another feature of regex related to character classes are negated character classes, which are created by placing a carat `^` after the open square bracket in a regular character class. Negated character classes result in the expression matching any character _not_ included in the character class

there are also a select few predefined character classes that are default to regular expressions, including:

`\d`
`\w`
`\s`
`\s` : Matches any whitespace character (including spaces, tabs, and line breaks)
`\D` : Matches any non-digit character
`\W` : Matches any non-word character
`\S` : Matches any non-whitespace character

Character classes are a useful tool for writing more concise regular expressions

### Flags

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

The regular expression above does not contain any flags, which are an optional feature of regular expressions that may be added to the end of a regular expression to modify how the pattern is matched. Commonly used flags include: `i`, `g`, and `m`. `i`: This flag offers case-insensitive matching capability. With this flag in place, the associated regular expression will match characters irrespective of their case (e.g., `/happy/i` would match each of the following: happy, Happy, HaPpy, happY). `g`: This flag is used for global matching of patterns, allowing the pattern to match all instances of the input pattern, rather than just the first instance. `m`: This flag allow for multi-line matching. Specifically,

Flags are added by placing them after the final `/` as so: `/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/i`.

### Grouping and Capturing

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

Grouping and capturing in regular expressions is used to match and extract parts of a pattern. By containing a piece of a regular expression within parentheses (e.g., `/(inbrackets)/`), parts of a regular expression may be grouped together for the purpose of applying quantifiers or other modifications to the entire set. For example, the current regular expression includes three instances of grouping: 

1. `(https?:\/\/)`: This first instance of grouping is to allow the `?` quantifier to be applied to the entire group of characters collectively.
2. `([\da-z\.-]+)`: This instance of grouping is to allow the `+` quantifier to be applied to the entire group.
3. `([\/\w \.-]*)`: This instance of grouping is to allow the `*` quantifier to be applied to the entire group.


Please note that only parentheses may be used for grouping characters, as curly brackets are used for quantifying and square brackets are reserved for declaring character classes.

### Bracket Expressions

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

Like character classes, bracket expressions are used to define a set of characters that match a pattern, but features slightly different syntax, notation, and use cases.

Generally speaning, when attempting to match a set of characters that follow a specific pattern or order, bracket expressions may be a better choice, as they provide a greater degree of flexibility

Overall, the choice between character classes and bracket expressions depends on the specific requirements of your pattern, and often a combination of both may prove the best solution.

### Greedy and Lazy Match

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

### Boundaries

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

Boundaries are a type of special character that allow for matching of patterns at a specific location within a string.

### Back-references

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

As noted above, this regular expression does not use any back-references. Nonetheless, it may still be helpful to provide just a brief overview of what back-references are and how they work to understand _why_ they are not included here.

Back-references are a method of referring back to a previously matched group within the same regular expression pattern to allow for matching repeated patterns. They are denoted by backslash followed by the number of the capturing group (e.g., `\2` refers to the second capturing group in the pattern.)

For this reason, back-references are commonly used for text validation, data extraction tasks, and in search and replace.

### Look-ahead and Look-behind

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

This regular expression uses a positive look-ahead assertion `(?=...)` to match the top-level domain name, as well as any optional path or query parameters.

## Author

This Gist was authored and published by Jared Green. I am a full-stack software developer based in New Brunswick, Canada and I enjoy creating resources such as this gist that help solidify my own learning and may assist others in their own development journies! If you are interested in exploring my other projects please visit my [GitHub](https://github.com/Pilotguide9897).

## Additional Reading

Those interested in reading more about regular expressions may be interested in exploring regular-expressions.info, a website dedicated to providing in-depth tutorials for a variety of regex concepts. The site may be accessed [here](https://www.regular-expressions.info/wordboundaries.html).
