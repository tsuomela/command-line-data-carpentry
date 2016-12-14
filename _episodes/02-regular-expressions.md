---
title: "regular expressions - matching and searching by patterns"
teaching: 0
exercises: 0
questions:
- "Key question"
objectives:
- "First objective."
keypoints:
- "First key point."
---

## Why regular expressions?

Searching for information in a file is something many of us have done.  The most common way to search for information is through a search engine, such as Google.  When you enter a query into Google the computers at Google essentially search through a big index of the words used in pages from across the web.  The results are returned to you based on a quantitative rank to determine the best result for your query.

We have all done similar searches on our own computers.  Perhaps you have had to edit a document to change some word into another.  You can use find and replace to locate the word you wish to change and then tell the computer to change all the instances of that word through an entire document.

The examples can gradually become more complex which is when it becomes useful to think in terms of a _pattern_ that you want to match in a file instead of an individual word.  Suppose you want to find all the occurrences of the word "color", but you are working with a set of documents which use both British and American English spellings.  In this case you could perform a search twice, once for "color" and again for "colour", but using a regular expression allows you to do a single search and get results for both variations.

Suppose you have a document which includes phone numbers for some people but not everyone.  You want to find just the records which contain a phone number.  You can think of a phone number as a pattern, a certain number of digits, usually recorded in a particular format.

In the United States phone numbers are 10 digits long and are usually chunked into three separate parts: an area code, an exchange, and the number.  So a phone number in the U.S. typically looks something like 555-555-5555.  You don't necessarily know in advance the actual phone numbers of the people you want to find but you can search the document for the phone number pattern using a regular expression and you will get back a match for every phone number in the file regardless of the digits in each individual number.

## History of regular expressions.

Regular expressions were invented in 1956 by Stephen Cole Kleene who was working on the mathematical notation for regular sets which are involved in the field of formal languages.  Computer scientists later adapted this work to be used for searching computer files.

Early text editors, such as vi, emacs, and sed, used the syntax of regular expressions to standardize the way people searched for information within and across files.

Today regular expressions are commonly used in most programming languages, especially when text needs to be searched or altered in order to perform some task.  Many text editors, especially those designed for programming, also include options to use regular expressions for searching.

## Creating a regular expression.

The simplest type of regular expression is a word.  "Obama", "McCain" are two examples of regular expressions that could be used to search through the election data set example used in this lesson.

## Modifiers for regular expressions

### Quantifying

The number of matches.

### Metacharacters

Types of characters: digits, alphanumeric, etc.

### Anchors

^ and $ for matching the start and end of a line.


## Regular expression examples.


### Matching social security numbers

### Election data

### Roman Numerals

### British vs. American English

color and colour


## Resources: regular expression testers online

* [regexpal](http://www.regexpal.com/)
* [Regular Expression Tester](http://www.roblocher.com/technotes/regexp.html)
* [RegExr](http://www.regexr.com/) - this is the most successful online training example I've seen.
