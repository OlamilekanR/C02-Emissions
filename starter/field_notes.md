# Data Literacy Field Notes & Terminal Log

**The scenario:** A climate-and-energy nonprofit wants to use this
country-level energy and emissions dataset to help decide where to direct
community-protection and climate-support efforts — but the file just
landed with zero documentation. Before anyone can trust a decision built
on top of it, you need to figure out what's actually in it — what each
column really holds, and anything that looks off. That's what this whole
file walks through: the real, everyday first pass any analyst runs on an
unfamiliar file, and the real answers you need before this data is safe
to act on.

Dataset: `../data/co2_emissions_2022.csv` (see `../data/SOURCE.md`). Each
section below describes what you're trying to find out — **figuring out
which command (and which flags) actually gets you there is part of what
this project tests**, so the exact command isn't given. Where a command
belongs, you'll see a `# TODO:` comment describing the goal instead of a
ready-to-run command; replace the comment with the real command you used.
Paste the **real output** you got underneath, then write your answer based
on what you actually saw, not what you'd expect. Work through this in
order; open the raw file before anything else.

Run all commands from the repo root — the top-level folder you land in
after cloning *your own* copy of this repo (`git clone ...` then `cd
your-repo-name`, see `README.md` Step 3; not this template) — or `cd` into
`data/` first and drop the `data/` prefix — your choice, just be
consistent.

**This one file is your whole record** — the commands you ran, their real
output, and your written answers, all together in the order you actually
did the work. There's no separate log file to keep in sync with this one;
whenever you write a command down anywhere in this file, use a fenced code
block tagged `bash`, like this:

````
```bash
git status
```
````

Three backticks, the word `bash`, your command, three backticks to close —
it renders with syntax highlighting and makes the command copy-pasteable.

## Setup log

Before jumping into the dataset, log the commands you actually ran to set
this repo up (see `README.md`) — `git init`/clone, creating your
`.gitignore`, your first commit. Add to this as you go, don't
reconstruct it from memory at the end.

```bash
# TODO: the commands you actually ran to set up this repo
```

## 1. First look at the raw file

Before trusting anything about this file's structure, you want a quick,
safe peek at it — not the whole 254-row file, just the **first 5 lines**,
enough to see the shape of it without scrolling past everything.

```bash
# TODO: a command that prints just the first 5 lines of the raw file
# head -n 5 co2_emissions_2022.csv 
```

**Output:**
_TODO: paste what you actually got_
# country,iso_code,year,population,gdp,co2
# Afghanistan,AFG,2022,40578847,53303471617,10.170
# Africa,,2022,1445862695,,1459.114
# Africa (GCP),,2022,,,1459.103
# Albania,ALB,2022,2827614,36171005594,4.498
**What I notice:** _TODO — your raw observations, in your own words_
# I noticed it started one value placement back , allowing it to push the header down into the dataset.

## 2. Column names

Next you want to see just the column names by themselves — one per line is
a lot easier to scan than one long comma-separated row.

```bash
# TODO: a command (or combination of commands) that prints just the header
# head -n 1 co2_emissions_2022.csv 
# row, one column name per line
# head -n 1 co2_emissions_2022.csv | tr ',' '\n'
```

**Output:**
# country
# iso_code
# year
# population
# gdp
# co2
_TODO_

## 3. Column-by-column data type table

For each column, you want to preview real values — **the first 6 values**
of just that one column — without scrolling through every field on every
row. Column numbers for reference: `country`=1, `iso_code`=2, `year`=3,
`population`=4, `gdp`=5, `co2`=6.

```bash
# TODO: a command that prints the first 6 values from a single column
# head -n 1 co2_emissions_2022.csv | tr ',' '\n' | nl

# (repeat this for at least 5 of the 6 columns, swapping in each column's number)
```

Fill in the table from what you actually saw — not a guess from the column
name alone:

| Column | Inferred type | How I can tell |
|country|String|I tell because they are formatted as letters|
| Iso-code | Str indexed | I tell because they are formatted as letters |
| Year | Int | I tell because they are formatted as Numbers |
| Population| Int  | I tell because they are formatted as Numbers |
| Gdp | Int | I tell because they are formatted as Numbers |
| C02 | Float | I tell because they are formatted as Decimals. |

**In your own words:** what's the actual difference between a list/array
and a table? (Not a definition you looked up — explain it the way you'd
explain it to a friend who's never coded. No command needed for this one,
just think about the table you just filled in above.)

# A list is a set of either numbers, letters, or data this allows for indexing, with each place having a number starting from 0- however long. An array is a set of instructions, code and packages a program runs on, for example python runs on python packages with num.py and other packages installed in the array to calculate functions and create visualizations. A table is an "Arrayed list " combining both ideas since lists are horizontal and are the list part of the word, to pull them we would identify them the array does this part. putting both ideas together having more rows allows you to pull from the top of a list to the bottom, and from left to the right; hence adding dimensions.
_TODO_

## 4. Structured or unstructured?

State whether this dataset is structured or unstructured, and why.

# "In my Opinion the data is of some structure, as it tells a story thorugh the use of rows to accomodate data and columns to categorize them. The Story I derived through a Quick analysis goes. 
# We are tracking C02 Emissions, from my background of learning about carbon dioxide from chem class and environmental science. All teachers tell of the close and deliberate interaction between living beings and other living beings who breath a different "Breath of life". 
# I learned Trees took in as much C02 i expended taking it in as nourishment and discarding of Oxygen(O2). my mind erupted, we all ought to have Trees for more 02. however that in itself is more complicated than the process of Oxidization. Gdp. decides if or not a resources is allocatede funds to exist. 
# No funds No Trees. Low funds Low Trees. Small correlation though. To fully flesh out the story or find a root cause of C02 emissions and someday fully utilize it we must go deeper and find relationships in the data "

_TODO_

## 5. Before you trust this data

Your first look (see section 1) turned up a row with a suspiciously
**blank** `iso_code`. Before you build anything on this data, you want to
know exactly how many of the 254 rows share that blank — is it a one-off,
or a real pattern worth flagging before anyone draws conclusions from it?
You may need more than one command for this — piping (`|`) feeds one
command's output into the next as input.

```bash
# TODO: a command (or combination) that counts how many rows have a
# BLANK iso_code
```

**Output:**
_TODO_

```bash
# TODO: the same idea, but for the gdp column
```

**Output:**
_TODO_

List **at least 2** specific things you'd want to know about how this
dataset was collected, before trusting any conclusion drawn from it — ground
at least one in the counts you just found.

**My 2 concerns:**
1. _TODO_ 
# "Is the Population data an accurate and diverse representation of social, political and economic status in the country as a whole? i.e more united/unified under a leader like kim jun un or a more free country like Canada"
2. _TODO_
# "The Gdp calculation is as a whole, i wonder if calculating the Gdp per capita or creating a table for it is viable?"

## 6. Data-quality question for the source

Take the **most specific and checkable** of the two concerns above, and
phrase it as a real question you'd send to the data's source/maintainer. A
good test: could they actually answer it with a concrete yes/no or fact —
not "is this data good?"

_TODO_
# is a relationship between gdp and population show a relationship explaining the   unequal distribution of C02 Emissions.

## 7. Something you're actually curious about

Different question from #6 — that one was about checking the data's
trustworthiness. This one's about you: what's something you're genuinely
curious to explore using this data? Pick two specific countries you're
curious to compare, and look up their full rows.

```bash
# TODO: a command that finds a specific country's row by name (repeat for
# a second country of your choice)
```

**Output:**
_TODO_

**My question:** _TODO_

## 8. AI-literacy reflection

Name **2 concrete risks** of trusting an AI assistant's output about this
dataset (or any data question) without checking it yourself. Then state
**one specific personal rule** for when you'll double-check an AI-provided
fact before relying on it professionally — specific enough that you could
actually follow it, not "I'll be careful."

**Risks:**
1. _TODO_
# The first risk is a data leak, the chance of losing information to outsiders is dangerous especially to hackers, pirates and other competing cooporations. it is important to check everything twice and make sure sensitive files and information is not sent into a public server.
2. _TODO_
# My second rule is to ask the use of a code and other iterations of it. A code Ovveriding data or code in a terrible way leads to bugs and even worse a shutdown of the buisness. Imagine the Mta all over NYC Shutting Down Simultenously... So I like to test in multiple coding languages; I know steps to find things or do actions are numerous. i like to know i'm not limited to one answer and at the very least i am knowledgeable in the answer.
**My rule:** _TODO_

## 9. Something that went wrong (and how you figured it out)

Somewhere in this project you're going to run a command that either throws
an error or gives you output that isn't what you expected — everyone hits
this at least once. Paste the actual command and what actually happened
(not a paraphrase), then explain what that told you and how it led to the
fix — not "I googled it and it worked."

```bash
# git add -u "yoooo you see this "
# git commit -u
# The code didn't work due to the -u's presence it is used in updating and not required in every commit for messages.
```

**What happened:**


# _TODO: the actual error message, or the unexpected output you got_
# On branch main
# Your branch is ahead of 'origin/main' by 2 commits.
 # (use "git push" to publish your local commits)

# Changes not staged for commit:
 #  (use "git add <file>..." to update what will be committed)
 # (use "git restore <file>..." to discard changes in working directory)
 #        modified:   ../README.md

# no changes added to commit (use "git add" and/or "git commit -a")

**What it told me and how I fixed it:** _TODO_
 # To fix it I copied my error into gemini, It told me the format was wrong and I had to redo it for it to run. Apparently the -u is only for pushes and to commit requires -m"