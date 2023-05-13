# The Anatomy of a URL: Using Regular Expressions to Target URLs

URLs, or Uniform Resource Locators, are the addresses we use to access web pages, images, videos, and other online resources. We see them every day in our web browsers and apps, yet many people don't fully grasp how they work or what they consist of. In fact, URLs can be quite complex and vary in format and length depending on the website or service they belong to. They often include various parts, such as the protocol (http, https, ftp), the domain name (e.g., google.com), the path (the location of the resource on the server), and query parameters (additional information passed to the server).

Despite their diversity, however, URLs actually follow certain conventions and patterns that make them easier to understand and manipulate. For example, most URLs start with a protocol and end with a top-level domain (e.g., .com, .org, .edu), and they use slashes, dots, and query strings to organize and specify their content. Understanding these conventions and patterns is essential for working with URLs, especially if you need to manipulate or extract information from them using regular expressions. With the right knowledge and tools, you can easily parse, validate, and transform URLs to suit your needs.

In this tutorial, we'll explore the common features and conventions of URLs and show you how to use regular expressions to match and extract them from text. By the end, you'll have a solid understanding of how URLs work and how to work with them using regular expressions.

## Summary

Today we will be exploring the following regular expression for identifying URLs in text:

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

This regex uses a combination of grouping, character classes, quantifiers, and anchors to match URLs. Specifically it matches for strings that start with an optional "http://" or "https://" protocol, followed by a domain name consisting of one or more letters, digits, dots, and hyphens, and ending with a top-level domain of two to six letters or dots (e.g., .com, .org, .co, .uk, .gov, .edu). The regex also matches any optional path or query parameters after the domain name.

| HTTP Protocol    | Domain          | Top-level Domain   | Optional path/Query Parameters |
| ---------------- | --------------- | ------------------ | ------------------------------ |
| `(https?:\/\/)?` | `([\da-z\.-]+)` | `\.([a-z\.]{2,6})` | `([\/\w \.-]*)*\/?$`           |

We will break down the regex into its individual components and examine what each one does, including anchors, quantifiers, character classes, grouping and capturing, and look-ahead and look-behind assertions. By the end of this tutorial, you will have a solid understanding of how this regex works and how to use it in your own projects.

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

With this information in mind, the regular expression being explored in this tutorial takes advantage of several regex components to provide it with a robust capacity for detecting URLs. These components will be discussed in more detail below and are as follows:

    (1) anchors
    (2) quantifiers
    (3) character classes
    (4) grouping and capturing
    (5) bracket expressions
    (6) greedy and lazy matching

Alternatively, the following regex components are not used in this particular regular expression:

    (1) OR operator
    (2) flags
    (3) back-references
    (4) look-ahead and look-behind

For the purpose of this tutorial and to provide a more complete overview of regular expressions in general, brief sections will still be dedicated to these components despite their disuse in this particular example. Further, please note that although not necessarily a part of the regular expression syntax itself, the (`/`) characters used in the example above at the beginning and end of the regular expression are used to indicate the beginning and end of the regular expression pattern. Specifically, when a regular expression is written in JavaScript, the (`/`) indicate to the interpreter that the enclosed text is a regular expression and separate the regular expression from any flags that may modify its behaviour (e.g., `/my regular expression/i`, where (`i`) is the flag and renders the regular expression case insensitive).

## Part-by-Part-Breakdown

Before analyzing each regular expression component individually, it may be helpful to proceed through the expression step-by-step from left to right to look at each part and gain a better understanding of the information that is to come further below.

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

1. (`/`): The forward slashes at the beginning and end are delimiters that signify the start and end of the regular expression pattern.

2. (`^`): This caret symbol indicates the start of the line. The pattern must start matching from the beginning of the input.

3. (`(https?:\/\/)?`): This section represennts a capturing group, denoted by the parentheses (). The (`?`) after the group makes it optional.

- (`https?`): This matches the string "http" followed by an optional "s", making it able to match both "http" and "https".
- (`:\/\/`): This matches the string "://". The backslashes are escape characters that cause the forward slashes treated as literal characters.

4. ([\da-z\.-]+): This is section represents another capturing group.

- (`\d`): Matches any digit (0-9).
- (`a-z`): Matches any lowercase letter (a-z).
- (`\.`): Matches a literal period ".". The backslash is an escape character.
- (`-`): Matches the hyphen character.
- (`[]`): The square brackets define a character set, meaning it will match any single character inside the brackets.
- (`+`): The plus symbol indicates that the preceding character set should match one or more times.
- (`\.`): This again matches a literal period ".", with the backslash used as an escape character.

6. (`([a-z\.]{2,6})`): This is another capturing group.

- (`a-z`): Matches any lowercase letter (a-z).
- (`\.`): Matches a literal period ".". The backslash is an escape character.
- (`{2,6}`): This is a quantifier that specifies the preceding character set must match at least 2 and at most 6 times.

7. (`([\/\w \.-]\*)`): This is another capturing group.

- (`\/`): Matches a literal forward slash "/". The backslash is an escape character.
- (`\w`): Matches any word character (alphanumeric, including underscore).
- ( ): Matches a space character.
- (`\.`): Matches a literal period ".". The backslash is an escape character.
- (`-`): Matches the hyphen character.
- (`\*`): The asterisk indicates that the preceding character set should match zero or more times.

8. (`\*`): The asterisk outside the capturing group indicates that the entire group should match zero or more times.

9. (`\/?`): This matches an optional forward slash "/". The backslash is an escape character, and the question mark "?" indicates the preceding character is optional.

10. (`$`): This symbol indicates the end of the line. The pattern must match until the end of the input.

11. (`/)`: The forward slash at the end is the delimiter that signifies the end of the regular expression pattern. Together with the opening forward slash, it encloses the regular epression.

### Anchors

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

Anchors are a type of special character used in regular expressions that allow users to match text from specific *positions* within a string rather than specific characters. The two most commonly used anchors are the caret `^` and dollar sign `$`. Notably, these anchors are in fact used in this very regular expression.

1.  The carat `^` anchor is used to match the beginning of a line (or an entire string in single-line mode). In this example it is used to indicate the beginning of our url.
2.  The dollar sign `$` anchor is used to match the end of a line or string. In this example it is used to indicate the end of our URL. Note that, though not used for this purpose in the regular expression above, `$` is also sometimes used for back-references in the replacement part of a regular expression operation. More information on its use in back-references is provided below in the section on back-references.

Although they are not used in this particular case, additional examples of anchors include `\b` and `\A`, which search for word boundaries and for the beginning of strings, respectively. To put it another way, `b` lets one perform whole-word searches using regular expressions in the form of `\bmyWord\b` (e.g., `\bapple\b` could be used to match the word *apple* as a stand alone word in text, but would not match if apple is part of anoter word such as *pineapple*). Using this anchor at the beginning or end of a word also allows users to specify that a word must have a boundary before or following certain pattern (e.g., to find words that end with "ing", you can use the pattern \w+ing\b. This will match words like "running", "jumping", but not "bring").  Alternatively, `\B\` is the negated version of `\b` and allow for selection of any position that is not a word boundary. For instance, to match the letter "a" only if it is not at a word boundary, you can use `\Ba\B`. This will match the "a" in "banana", but not in "apple".

Whereas `\b` searches for word boundaries, `\A` detects the beginning of strings of text. In this regard, `\A` functions quite similarly to the caret `^`, discussed above, with a slight nuance in how they each function. Specifically, `\A` matches the start of the entire string, no matter what and ensures that the pattern that follows must start at the very beginning of the entire string. `^` on the other hand, usually matches the start of a line, but can also match the start of the entire string. By default, `^` matches the start of a line in multiline mode, but in regular mode, it matches the start of the entire string.
However, some regex flavors allow modifying `^` to always match the start of the entire string, regardless of multiline mode.

Due to their versatility, anchors are useful in many different types of regular expressions ranging from those for simple string matching all the way to complex text processing tasks. For more information on anchors, see [here](https://www.rexegg.com/regex-anchors.html).

### Quantifiers

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

Quantifiers are a category of special characters that allow for matching of a certain number of occurrences of a character, group, or class in a string. Quantifiers are applied by appending to an individual character or a character class, and the simplest quantifier is simply a number contained within curly braces (e.g., `a{n}`, where n could be any number -> a{5} is equivalent to [aaaaa]). This is known as specifying an exact count and features a few variations. As seen previously, we can specify a specific number. However, we may also specify a range using our curly brackets (e.g., \d{3,5} -> here we are using `\d` to target any digit from 0-9, in any combination of 3 to 5 characters, thus it would match 982, 4678, or even 28045 but would *not* match 99 or 343201), where we specify the lower value separated from the higher value by a comma. In effect, provides greater control when targeting patters of variable length, as rather than knowing a head of time specifically how long the targets are that we wish to select, this provides improved flexibility to target diverse values. In addition, using a similar syntax users may even omit the upper limit, specifying only a minimum number of digits/characters followed by a comma (e.g., \d{3,} matches any number with three or more characters in effect specifies that the target must contain "three or more" digits). 

In addition to these basic quantifiers, (`+`), (`?`), and (`*`) are further used to specify the number of occurrences of the preceding element in the pattern. The (`+`) quantifier specifies that the preceding element must occur one or more times. It matches if the preceding element appears at least once but is not strict in the number of occurrences it requires, meaning that the pattern can occur multiple times. For example, the pattern "a+" matches "a", "aa", "aaa", and so on, but it does not match an empty string or a string without any "a" characters. Similarly, the pattern "ab+c" matches "abc", "abbc", "abbbc", and so on, but not "ac" or "ab". The (`?`) quantifier specifies that the preceding element is optional, meaning it can occur zero or one time. It matches regardless of if the preceding element is present is absent. For example, the pattern (`/colou?r/`) matches both "color" and "colour". The "u" in "colour" is optional. Likewise, the pattern (`/dogs?/`) matches both "dog" and "dogs". The "s" at the end is optional. Finally, the (`*`) quantifier indicates that the preceding character or group can occur zero or more times. For example, (`/a*/`) can match "", "a", "aa", "aaa", and so on. Overall, it is similar to the (`+`) quantifier, but it can also match zero occurrences.

As noted above, in our example we take advantage of the plus (`+`) quantifier to match one or more occurrences of the preceding set of characters, in our case (`[\da-z\.-]`), because it allows us to flexibly target an unspecified number of characters and account for the wide variety in sub domain names on the web. To put it another way, the (`+`) is what allows us to account for domain names that may be 6 characters long (e.g., google), while also being able to manage much longer domains (e.g., MyDogAteMyHomework). In our example, we also take advantage of the question mark (`?`) quantifier to include optional features, specifically (`(https?:\/\/)`) and (`([\/\w \.-]*)*\/`), as it is used to search for the presence or absence (i.e., zero or one occurrences) of the peceding character, group, or class. I our case, we take advantage of it to detect optional components of urls, these being the http protocol and the optional path/query parameters. This regular expression also takes advantage of curly braces containing a range of values to target a specific numer of occrrences of a preceding character, group, or class. Specifically, (`{2,6}`) is used to target a string of 2 to 6 characters from a to z and which include a period (`[a-z\.]`), allowing this expression to target any top-level domain name (e.g., ".com", ".net", ".edu", ".gov", ".io").

Overall, quantifiers are useful because they allow matching of patterns that may repeat a certain of times in a string and because quantifiers can be combined with other regex elements to create more complex patterns for pattern matching and text manipulation.

### OR Operator

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

The OR operator (`|`) is used within regular expressions to match from among two or more possible patterns. The OR operator is not used in this particular regular expression, and its use is generally less common than many other regex components. When using the or operator in regular expressions, each possible pattern is enclosed in parentheses and separated by the | symbol. For example, the regular expression (`(dog|cat)`) would match either "dog" or "cat". The OR operator can be useful when searching for multiple variations of a word or phrase and can be used in combination with other regular expression components, such as character classes and quantifiers. For instance, the regular expression (`[A-Z]|[0-9]){3}`) would match any three-character string that contains either an uppercase letter or a number.

It is important to note that the OR operator is case-sensitive, unless it is modified by the (`i`) flag (see the section on [flags](#flags)), which makes the regular expression case-insensitive. Additionally, the OR operator only matches the first pattern that it finds, even if there are multiple matches in the text being searched. A final note about the OR operator is that it has a higher precedence than other regular expression operators, such as anchors and quantifiers. In regular expressions, precedence determines the order in which operators and constructs are evaluated. Operators with higher precedence are evaluated before those with lower precedence. To demonstrate what this means, consider the following regular expression: (`^\d+|abc$`). This regular expression matches either a sequence of digits at the start of the string or the string "abc" at the end. Here's how the evaluation occurs: (`^\d+`) matches one or more digits (`\d+`) at the start of the string. This matches patterns like "123" or "456789". Conversely, (`abc$`) matches the exact string "abc" at the end of the string. Thus, if you have the input string "123abc", the regular expression (`^\d+|abc$`) will match "123" as well as "abc". If you have the input string "abc123", however, only "abc" will match, not "123".

Specific to our case, the OR operator is not used in our regular expression for matching URLs. This operator remains unused because rather than using a single regex pattern with multiple OR operators to match URLs, our expression takes advantage of multiple separate regex patterns for matching the HTTP protocol, domain, top-level domain, and path/query parameters individually. This allows for more specific validation and easier adjustment if requirements change and means that the OR operator is not needed. Overall, although it not used in this instance, the case remains that OR operators can be a powerful tool for specifying multiple alternative patterns and matching only the first one that applies.

### Character Classes

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

Character classes, also referred to as *character sets* are a robust feature of regular expressions that specifies a set of characters which may be matched by any single character in the string being searched. To put it another way, character classes tell the regex engine to match all occurrences of only certain characters. Most regular expression engines provide a set of a few predefined character classes that are default to regular expressions, including:

- (`\d`): This class matches any digit character. Equivalent to (`[0-9]`).
- (`\D`): This class matches any non-digit character. Equivalent to ()`[^0-9]`).
- (`\w`): This class matches any word character, which includes alphanumeric characters and underscores. Equivalent to (`[a-zA-Z0-9_]`).
- (`\W`): This class matches any non-word character. Equivalent to (`[^a-zA-Z0-9_]`).
- (`\s`): This class matches any whitespace character, including spaces, tabs, and line breaks. Equivalent to (`[ \t\n\r\f]`).
- (`\S`): This class matches any non-whitespace character. Equivalent to (`[^ \t\n\r\f]`).
- (`.`): This class matches any and all characters with the exception of a new line.

Overall, these character classes can be used within regular expressions, either alone or in combination, to represent specific sets of characters without explicitly listing them. For example, the regular expression (`\d+`) matches one or more digits, whereas (`\w+`) matches one or more alphanumeric characters or underscores.

Our URL matching expression takes advantage of this property by employing the (`\w`) character class in the (`[\/\w \.-]`) bracket expression to target any alphaneumeric character.

### Flags

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

The regular expression above does not contain any flags, which are an optional feature of regular expressions that may be added to the end of a regular expression to modify how the pattern is matched. Commonly used flags include: (`i`), (`g`), and (`m`). Flags are added by placing them after the final `/` as so: `/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/i`. To better understand how flags work, let us consider each of these in more detail.

- The (`i`) flag offers case-insensitive matching capability. With this flag in place, the associated regular expression will match characters irrespective of their case (e.g., (`/happy/i`) would match each of the following: "happy", "Happy", "HaPpy", "happY"). 

- The (`g`) flag is used for global matching of patterns, allowing the pattern to match all instances of the input pattern, rather than just the first instance. For example, If we had the following string: "The quick brown fox jumps over the lazy dog. The dog is not amused", and we want to find all occurrences of the word "the" (case-insensitive) in the string using the g flag, we can construct the regular expression (`/the/gi`). Here, the pattern the matches the lowercase letters "the" exactly. The (`g`) flag at the end of the regular expression enables global matching, meaning it will match all occurrences of the pattern rather than just the first one. Finally, the (`i`) flag after the final delimiter / makes the match case-insensitive, meaning that it will match "the" regardless of whether it is uppercase or lowercase.

- The (`m`) flag allow for multi-line matching by modifying how the (`^`) and (`$`) anchors work. By default, these anchors match the beginning and end of an entire string. When (`m`) flag is used, however, not only do they continue to perform this function, but they also match the start and end of each *line* within the string. This can be useful when the input string has multiple lines. For instance, in the string:

```
Start reading your books, class.
Start now or else you may be late.
Start, stop, begin again.
```

(`/^start/m`) would match "start" at the beginning of each line rather than just the initial start.

Overall, flags are a useful tool for modifying the behavior of pattern matching within a regular expression to suit specific requirements by providing additional flexibility and control over how the regular expression engine interprets and applies a given pattern.

### Grouping and Capturing

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

Grouping and capturing in regular expressions is used to match and extract parts of a pattern. By containing a piece of a regular expression within parentheses (e.g., (`/(inbrackets)/`)), parts of a regular expression may be grouped together for the purpose of applying quantifiers or other modifications to the entire set. For example, the current regular expression includes three instances of grouping:

1. `(https?:\/\/)`: This first instance of grouping is to allow the (`?`) quantifier to be applied to the entire group of characters collectively.
2. `([\da-z\.-]+)`: This instance of grouping is to allow the (`+`) quantifier to be applied to the entire group.
3. `([\/\w \.-]*)`: This instance of grouping is to allow the (`*`) quantifier to be applied to the entire group.

Please note that only parentheses may be used for grouping characters, as curly brackets are used for quantifying and square brackets are reserved for declaring character classes.

### Bracket Expressions

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

Like character classes, bracket expressions are used to define a set of characters that match a pattern. Unlike character classes, however, bracket expressions features slightly different syntax, notation, and use cases. Whereas character classes provide prederined categories of characters using escape sequences, bracket expressions allow users to define custom character sets or ranges defined within square brackets. Specifically, character classes are defined by enclosing characters within a set of square brackets (`[]`) and can be used to specify specific characters (e.g., (`[abc]`) would match any instance of a, b, or c), or to define a range of characters that encloses any characters in between (e.g., (`[a-z]`) all instances of lowercase letters in a given string). Character classes are useful because they allow users to specify multiple characters in a condensed syntax, such that they do not need to write out (`[a,b,c,d,e,f...z]`). 

Another important feature of regex related to bracket expressions are negated bracket expressions, which are created by placing a carat (`^`) after the open square bracket. Negated bracket expressions result in the expression matching any character *not* included in the character class. For instance, the regular expression (`[^a-z]`) matches any character that is *not* a lowercase letter. To put it another way, excludes the range of characters from "a" to "z". Thus, if we had the string "Hello123!". Applying the regular expression (`[^a-z]`) to this string would match the "1", "2", "3", and "!".The lowercase letters "H", "e", "l", "l", and "o", however, would not be matched because they fall within the negated range.

Our regular expression for detecting URLs uses bracket expressions to great effect for concisely matching a great variety of characters. Specifically, it takes advantage of three classes:  1. (`[\da-z\.-]`), 2. (`[a-z\.]`), and 3. (`[\/\w \.-]`). 

Why don't we break these bracket expressions down in more detail? First up is, (`[\da-z\.-]`). This bracket expression uses (`\d`) to match any digit from 0 to 9. Additionally, its use of (`a-z`) allows it to match any lowercase letter. Finally, (`\. -`) escapes and matches a dot (`.`), a hyphen (`-`), and a blank space. Together, these smaller portions allow this expression to match any alphanumeric characters, dots, hyphens, and spaces that might be used in a URL. Moving on, next up we have (`[a-z\.]`). In this bracket expression, like before,(`a-z`) allows matching of any lowercase letter and (`\.`) escapes and matches the literal dot character. Together, these patterns allow this expression to match lowercase letters and dots for matching top-level domain names (e.g., .com, .edu). Last but not least we have (`[\/\w \.-]`). This bracket expression first uses (`\/`) to escape and match literal forward slashes (`/`). Next, it uses the predefined `\w` character class (note how character classes and bracket expressions can be used synergystically) to match any word character. Then it leaves a blank space to match any empty spaces, before finally using (`\. -`) in a fashion similar to bracket expression 1 to  match a dot (`.`), a hyphen (`-`), and a blank space. Overall, this bracket expression allows matching of forward slashes, word characters, spaces, dots, and hyphens to target the wide variety of additional URL query parameters. 
     
Hopefully, with this example now in place you can see how overall, character classes are a highly useful tool for writing more concise and powerful regular expressions.

Generally speaning, when attempting to match a set of characters that follow a specific pattern or order, bracket expressions may be a better choice, as they provide a greater degree of flexibility, though overall, the choice between character classes and bracket expressions depends on the specific requirements of your pattern, and often a combination of both may provide the best solution.

### Greedy and Lazy Match

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

In regular expressions, greedy and lazy matching refer to two different applications of quantifiers responsible for controlling how much text can be matched by particular patterns. For more information on quantifiers see the section on [quantifiers](#quantifiers). To put it simply, greedy matching matches as *much* text as possible while still allowing the overall pattern to match, whereas lazy matching, also referred to as non-greedy matching, matches as *little* text as possible while still allowing the overall pattern to match. Another way to consider the difference between greedy and lazy matching is that, as a greedy property owner may attempt to possess as much realestate as possible, greedy matching attempts to possess the maximum number of characters. Alternatively, as a lazy land owner may not be bothered to attempt to claim extra land, lazy matching only attempts to possess the minimum nuber of characters possible.  

    Greedy Matching
Greedy matching is generally the default in regular expressions, meaning that they by their nature, regular expressions attempt to match as much text as possible while still satisfying the specified pattern. This makes sense, as since regular expressions are designed as tool that uses patterns to search, match, and manipulate text, it stands to reason that they would attempt to match as much text as possible by default. When applying greedy matching regular expressions takes advantage of the (`*`), (`+`), and (`?`) quantifiers to allow them to match text. To reiterate in the context of greedy and lazy matching: 
- Asterisk (`*`) matches zero or more occurrences of the preceding element, matching as many occurrences as possible. This quantifier allows the preceding element to repeat any number of times, including zero. For example, the pattern (`/ab*/`) will match "a", "ab", "abb", "abbb", and so on. 
- Plus (`+`) matches one or more occurrences of the preceding element, matching as many occurrences as possible. This quantifier requires the preceding element to appear at least once, but it can repeat any number of times. For example, consider the pattern (`fo+d`) will match "fod", "food", "foood" and so on. In all these instances, there must be at least one "o" between "f" and "d". Thus, the expression will not match "fd" since there is no "o" and it will not match "fodod" because "od" appears twice, and the pattern specifies that "d" should only occur once after after "o" once.
- Question mark (`?`) matches zero or one occurrence of the preceding element, matching as many occurrences as possible. This quantifier allows the preceding element to appear either zero times or once. For example, the pattern (`/ho?p?e?/`) will match "h" (as o and e are optional), "ho" (as "e" is optional), "he" (as "o" is optional), "hope" (all characters are present). It will not match "hoppe" or "hoee", however, because in both cases, letters appear twice that the pattern specifies should only appear once or less.

In all cases, these quantifiers are greedy because they attempt to consume the maximum number of characters that still allow the overall pattern to match. If there are multiple occurrences of the preceding element, they will match as many occurrences as possible.

    Lazy Matching

Although the default for regular expressions is to generally attempt to match as much text as possible, there are certain situations where this may not be desirable, such as when using regular expressions for input validation, text extraction, or for performance optimization purposes when matching agains large quantities of text. Further, lazy matching is useful in certain situations where you may need to match text that contains nested patterns and where greedy matching would match too much text and result in unexpected matches. Overall, lazy matching is denoted by the additino of (`?`) after quantifiers. Consequently, each of the quantifiers outlined above may be converted from greedy matchers to lazy matchers by adding a (`?`) after them. The reason this happens is related to how regular expression engines process patterns. When a quantifier is encountered, the regex engine initially matches as much text as possible to satisfy the quantifier. However, with a (`?`) added after the quantifier, the engine now attempts to match as little text as possible while still allowing the overall pattern to match. This transformation allows for more precise control over matching behavior. Returning to the quantifiers discussed in the section on greedy matching, let us explore what would happen if one was to add (`?`) after them:
- (`*?`): Matches zero or more occurrences of the preceding element, but as few occurrences as possible. It matches zero or more occurrences of the preceding element, attempting to match as little text as possible.
It will stop matching as soon as the overall pattern was satisfied. For instance, given the pattern (`/a.*?b/`) and the string "aabab", the match will be "aab" instead of the greedy match "aabab". The lazy quantifier stops at the first occurrence of "b".

- (`+?`): Matches one or more occurrences of the preceding element, attempting to match as little text as possible. It stops matching as soon as the overall pattern has been satisfied. To see what I mean, consider this. Given the pattern (`/ba+?/`) and the string "baaaa", the match will be "ba" instead of the greedy match "baaaa". The lazy quantifier stops after matching "ba" but does not match the additional repeating "a" characters.

- (`??`): Matches zero or one occurrence of the preceding element, attempting to match as little text as possible.
Once again, it stops matching as soon as the overall pattern can still be satisfied.
Example: Given the pattern (`/\d+??/`) and the string "123456", the match will be "1", as it matches as little as possible, rather than the greedy match "123456". The lazy quantifier matches only the "1" and does not proceed to match the additional digits.

In our regular expression for matching URLs, greedy matching is used in two parts. First to match one or more alphanumeric characters, dots, or dashes using the pattern (`[\da-z\.-]+`). The second instance of greedy matching is to match zero or more characters that are either a forward slash, a word character (alphanumeric or underscore), a space, a dot, or a dash using the pattern (`([\/\w \.-]*)`). Our pattern does not employ any instances of lazy matching since it wants to be as inclusive as possible to allow it to detect any and all possible URL variations.

Overall, it is important to remember that neither greedy or lazy matching is inherently superior, and to acknowledge that the choice between greedy and lazy matching depends on the specific requirements of one's pattern and the desired behavior when multiple matches are possible. In this regard it is important users consider the context and expected results when deciding whether to use greedy or lazy quantifiers in your regular expressions.

### Boundaries

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

Boundaries are a type of special character that allow for matching of patterns at a specific location within a string and are useful for ensuring that matches only occur where intended. It is important to note that boundaries do not match specific characters themselves, but rather only allow for characters at certain positions to be matched. Regex features multiple types of boundaries, however, (1) word boundaries, (2) start- and end-of-line boundaries, and (3) start- and end-of-string boundaries are the most common.

- Word boundaries: Word boundaries are represented by the (`b`) metacharacter, and match the transition between word characters (i.e., letters, digits, and underscores) and character that does not fall under one of the previously mentioned categories. Word boundaries are useful when specifically matching a word that may sometimes be found inside of other words (e.g., you could use (`\bcat\b`) when only want to select that word cat but not its use in the word *cat*egory). Alternatively, word boundaries may also be made negative using the (`\B`) metacharacter. This can be useful for excluding specific unintended matches and searches specifically for the transition between two word characters or non-word characters.
- Start- and end-of-line: The anchors (`^`) and (`$`) discussed above are used to establish boundaries, specifically to match the beginning and end of a line, respectively. For instance, (`^what`) would match the word "what" only if it appears at the start of a line (e.g., Selecting what in "what is going on here?" but not in "I do not know what is the matter").
- Start- and end-of-string: Denoted by the (`\A`) and (`\Z`) matacharacters to represent the start and end of an entire string, respectively. These metacharacters can be useful when working with input that contains multiple lines or paragraphs.

As noted above, our regex for matching URLs takes advantage of the carat (`^`) and (`$`) to indicate start- and end-of-line boundaries to identify our URLs as their own unique entity and means a URL that is contained mid-sentence would not be detected. This is likely done since the regex is primarily intended to detect urls from a search bar, rather than from the body content of a webpage.

### Back-references

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

As noted above, this regular expression does not use any back-references. Regardless, it may still be helpful to provide just a brief overview of what back-references are and how they work to understand *why* they are not necessary in this particular expression.

The use of back-references is a method of referring back to a previously matched group within the same regular expression pattern to allow for matching repeated patterns. Back-references take advantage of capturing groups (see [Grouping and Capturing](#grouping-and-capturing)) to easily refer to repeated patterns or to ensure that two parts of a pattern match the same text. Back-references are denoted by backslash followed by the number of the capturing group (e.g., `\2` refers to the second capturing group in the pattern). For this reason, back-references are commonly used for text validation, data extraction tasks, and in search and replace. Additionally, another common use of back-references is to check for the presence of repeated words when editing text, specifically using the regex `\b(\w+)\S+\1\b`. Since the regular expression above does not need to target repeated text, however, and urls do not typically include matching segments, back-references are not required when targeting our URLs.

Tip: It is important to note that parentheses are unable to be used as metacharacters in character classes, such that were you to attempt to match `(a)` inside of a character class as so: `[(a)bc]` it would match a, b, c, and also ( and ), since it treats the parentheses as literal characters. Similarly, back-references also cannot be used inside character classes (e.g,. `(regex)[\1p]` would escape the 1 rather than functioning as a back-reference).

For further reading on back-references please see [here](https://www.regular-expressions.info/backref.html).

### Look-ahead and Look-behind

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

Look-ahead and look-behind, collectively referred to as 'lookaround' allow matching of text based on what comes before and after a specific pattern, specifically without including the text that comes before and after the text in the final match, respectively. Critically, the reason to use lookarounds rather than merely specifying that something should be present in your string is when you would like to match a pattern *only* if it is followed or preceded by another specific pattern, and you do not want to include the other pattern in the match. Lookarounds are considered *zero-width assertions*, meaning that they do not consume characters in a string and merely asserting whether a match is possible.

 Concerning our URL detecting regex for a moment, as noted above, this regular expression does not rely upon lookarounds. Regardless, for the sake of being thorough let us briefly discuss the two categoreis of lookaround in slightly more detail.

#### Look-ahead

When discussing lookahead, there are two varieties to consider: standard look-ahead denoted by the syntax (`?=`) and negative look-ahead, denoted by the syntax (`?!`). Standard look-ahead (`?=`) specifies matches only when a string is followed by a specific pattern (e.g., (`dog(?=house)`) only matches *"dog"* if it is followed by *"house"*, while not including "house" in the match). Conversely, negative look-ahead (`?!`) does the opposite, matching a group of characters *not* followed by a specific pattern, while not including it in the match (e.g., (`dog(?!house)`) only matches "dog" if it is not immediately followed by "house"). Look-aheads are similarly useful when you would like to match a pattern *only* if it is followed by a specific number of characters but do not want to include the characters in the match (e.g., If you wanted to match all occurrences of "open" only if it is followed by three characters you could use the pattern (`/open(?=.{3})/`). In this positive look-ahead the (`.`) matches any character except a newline, and (`{3}`) specifies exactly three of whatever character is being considered. So, (`.{3}`) matches any three characters. Thus, in the string "opening", "open" will match because it's followed by exactly three characters "ing". In the string "openabcd", "open" will still match because it's followed by at least three characters "abc". The fourth character "d" does not affect the match. In the string "openab", "open" will not match because it's followed by only two characters "ab".

#### Look-behind

As with look-ahead, look-behind also features two varieties: positive look-behind, denoted by the syntax (`?<=`) and negative look-ahead, denoted by the (`?<!`) syntax. Look-behind matches a group of characters preceded by a specific pattern without including the pattern in the match (e.g., (`(?<=dog)food`) matches the string *food* only if it is preceded by *"dog"*, while not including dog in the match). Alternatively, nagative look-behind matches a group of characters that are *"not"* preceded by a specific pattern (e.g., (`(?<!air)plane`) matches the string plane, but only if it is not immediately preceded by air).

For more information on lookarounds see [here](https://www.regular-expressions.info/lookaround.html) and [here](https://www.rexegg.com/regex-lookarounds.html)

## Author

This Gist was authored and published by Jared Green. I am a full-stack software developer based in New Brunswick, Canada and I enjoy creating resources such as this gist that help solidify my own learning and assist others in their own web development journies! If you are interested in exploring my other projects please visit my [GitHub](https://github.com/Pilotguide9897).

## Additional Reading

Those interested in reading more about regular expressions may be interested in exploring regular-expressions.info, a website dedicated to providing in-depth tutorials for a variety of regex concepts. The site may be accessed [here](https://www.regular-expressions.info/wordboundaries.html). Please note that the exact behavior of certain regex characters may vary in different regex flavors and with different options or modes, so it's important to consult the documentation or reference guide specific to your regex implementation for precise details!
