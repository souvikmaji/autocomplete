# Autocomplete

HTTP service for fuzzy search /autocomplete of English words.

## Installation

```sh
make init
```

## Run Instruction

### HTML View

### API Usage

GET /search?word=input

Where input is the (partial) word that the user has typed so far. 

For example, if the user is lookingup procrastination, the service might receive this sequence of requests:
GET /search?word=pro
GET /search?word=procr
GET /search?word=procra

and so on.

The response should be a JSON array containing upto 25 results, ranked by some criteria (seebelow).

## Constraints

1.Matches can occur anywhere in the string, not just at the beginning. For example, eryxshould match archaeopteryx (among others).

2.The ranking of results should satisfy the following:

a. We assume that the user is typing the beginning of the word. Thus, matches at thestart of a word should be ranked higher. For example, for the input pract, the resultpractical should be ranked higher than impractical.

b. Common words (those with a higher usage count) should rank higher than rarewords.

c. Short words should rank higher than long words. For example, given the inputenviron, the result environment should rank higher than environmentalism.i.As a corollary to the above, an ​exact match​ should always be ranked as thefirst result.

3.The search algorithm you develop should ideally incorporate some form of a weightedaverage of all qualifying parameters. The perfect weights, in production systems, arehowever derived through the use of ML algorithms.

## TODO

- POC fuzzy search. Test performance with fuzzywuzzy.
- select2 based autocomplete
- django autocomplete light?
- makefile
- requirements.txt file
- unit tests
- static analyzer
- Hosting (Heroku).
