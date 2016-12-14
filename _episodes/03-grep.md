---
title: "grep - the global regular expression parser/printer"
teaching: 0
exercises: 0
questions:
- "Key question"
objectives:
- "First objective."
keypoints:
- "First key point."
---

_grep_ is a command line program which can be used to search any file for a pattern.  Patterns are usually expressed using regular expressions, a special syntax for defining patterns to match against a file, input, or some form of data.

The form of a grep command is :

~~~
grep <command options> <pattern> <filename(s)>
~~~
{: .bash}

## Command Options

Command options are used to tell grep to perform a function in a particular way.  For example you can use the -f or --file= options to specify the particular file you wish to search for the <pattern>.

A more common use of the options is to invert the search pattern. Inversion is useful if you want to find all the lines that do not the match the pattern.  In other words you want to find everything else in the file except what you trying to match.  This could be used to filter a dataset to exclude a particular set of data.

> ## Example Data (from 2008 election)
>       PRESIDENT / VICE PRES
>      Vote For  1
>       Chuck Baldwin .  .  .  .  .  .  .  .  .  .      1     .26
>       Bob Barr.  .  .  .  .  .  .  .  .  .  .  .      1     .26
>       Richard Duncan.  .  .  .  .  .  .  .  .  .      0
>       John McCain.  .  .  .  .  .  .  .  .  .  .    132   33.76
>       Cynthia McKinney .  .  .  .  .  .  .  .  .      1     .26
>       Brian Moore.  .  .  .  .  .  .  .  .  .  .      0
>       Ralph Nader.  .  .  .  .  .  .  .  .  .  .      3     .77
>       Barack Obama  .  .  .  .  .  .  .  .  .  .    251   64.19
>       WRITE-IN.  .  .  .  .  .  .  .  .  .  .  .      2     .51
>               Total .  .  .  .  .  .  .  .  .  .    391
{: .callout}

In the case of this particular set of data we may want to search for the pattern "Obama".

~~~
grep "Obama" data.txt
~~~
{: .bash}

The results for this command would be.

~~~
       Barack Obama  .  .  .  .  .  .  .  .  .  .    251   64.19
~~~
{: .output}

Using a -v or --invert-match option would look like this

~~~
grep -v "Obama" data.txt
~~~
{: .bash}

~~~
       PRESIDENT / VICE PRES
      Vote For  1
       Chuck Baldwin .  .  .  .  .  .  .  .  .  .      1     .26
       Bob Barr.  .  .  .  .  .  .  .  .  .  .  .      1     .26
       Richard Duncan.  .  .  .  .  .  .  .  .  .      0
       John McCain.  .  .  .  .  .  .  .  .  .  .    132   33.76
       Cynthia McKinney .  .  .  .  .  .  .  .  .      1     .26
       Brian Moore.  .  .  .  .  .  .  .  .  .  .      0
       Ralph Nader.  .  .  .  .  .  .  .  .  .  .      3     .77
       WRITE-IN.  .  .  .  .  .  .  .  .  .  .  .      2     .51
               Total .  .  .  .  .  .  .  .  .  .    391
~~~
{: .output}


Here are some common options you may need to use.

1. -i ignore case (upper and lower case letters)
2. -v invert search
3. -w match whole words
4. -c print a count of matching lines (useful for verifying the results of your search)
5. -l print the name of each file which contains a match.  Useful when searching across multiple files.
6. -n print a line number before each matching line.
7. -r recursive search, read all files in a given directory and subdirectories.


## Pattern

The second part of a grep command is the pattern.  The pattern is a regular expression which we learned about in the last episode.

If you look at examples of using grep from the command line you will see a couple of different formats for the pattern.  In particular you will see times when people may type the expression with or without quotes.  The particular effect of quotes depends on the type of interactive shell you are using.  For most people starting out at the command line the default shell will be _bash_.  In bash the best practice is to put the pattern inside of normal quotation marks - "".

Building a regular expression is usually an iterative process as you start with one character you want to match and then build in more complexity.  So in the election example we need to extract the precinct name from the file.  When you examine the file you can see that the first precinct name (0001 HUR A) begins with a string of 4 numbers, a space, then three letters, another space, and then another letter.  The name is printed on its own line and is indented from the left margin.

In order to build an expression to map to this string we start with the numbers :

> \d{4}
> \s
> [A-Z]{2,3}
> .\*$
{:callout}

We can match numbers using a metacharacter - in this case a lower-case d for digits.  We also want to match just 4 digits in a row, so we can use a quantifier to indicate that we want {4} digits.

The second step is to match the single space.

Next are the letters.  A quantification is again used to limit the letter match to a a certain number.  The comma allows us to specify an 'or' action so the program will match 2 or 3 letters in a row.  Also note that [A-Z] uses capital letters which means that the matches returned will also be capitalized.

The remainder of the expression uses three metacharacters to tell grep to match any character (.), 0 or more times (\*), until the end of the line is reached ($).


## Files

The


## Specialist greps: egrep, fgrep, etc.
