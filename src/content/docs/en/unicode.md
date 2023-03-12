---
title: "The Unicode Standard"
description: "I don't want to think about vision in these notes."
---

## Goals

The Unicode standard is one of the greatest triumphs in human intellectual history.

See [Unicode Standard 15.0](https://www.unicode.org/versions/Unicode15.0.0/UnicodeStandard-15.0.pdf)
for reference.

```markdown
The Unicode Standard began with a simple goal: to unify the many hundreds of 
conflicting ways to encode characters, replacing them with a single, 
universal standard.
```

```markdown
The Unicode Standard is the universal character encoding standard for written
characters and text. It defines a consistent way of encoding multilingual text
that enables the exchange of text data internationally and creates the 
foundation for global software.
```


```markdown
The Unicode Standard was designed to be:
  - Universal. The repertoire must be large enough to encompass all characters
    that are likely to be used in general text interchange, including those in 
    major international, national, and industry character sets.
  - Efficient. Plain text is simple to parse: software does not have to 
    maintain state or look for special escape sequences, and character 
    synchronization from any point in a character stream is quick and 
    unambiguous. A fixed character code allows for efficient sorting, 
    searching, display, and editing of text.
  - Unambiguous. Any given Unicode code point always represents the same 
    character.
```

The "unambiguity" also guarrantees backward compatibility, so that the "version"
of unicode one is using is not-so-important. Not all standards have this property.
As of the writing of these notes, Unicode is on semantic version "0.15".

Question: Does DNA encoding have these properties? I don't think it satisfies 
everything in the second bullet.

## Implementation

The Unicode standard is powerfully simple.

```markdown
It provides the capacity to encode all characters used for the written
languages of the world—more than 1 million characters can be encoded. No 
escape sequence or control code is required to specify any character in any 
language. The Unicode character encoding treats alphabetic characters, 
ideographic characters, and symbols equivalently, which means they can be 
used in any mixture and with equal facility.
```

In summary

```markdown
The Unicode Standard specifies a numeric value (code point) and a name for 
each of its characters.
```

Every unicode "code point" can be represented as a 32 bit integer. One
can think of a code point as either a natural number (a mathematical abstraction 
independent of a base representation) or a sequence of 0/1 of length 32
(it's binary representation). Computers obviously prefer the latter.

For example, the character `A` is `0000000001000001`. While `0000011000110011`
represents a character not in the English alphabet.

There are interesting subsets of unicode numbers that are only 8 or 16 bits.
You go from the 8/16 bit representation to a 32 bit representation by "padding
with zeros". As Unicode is compatible with ASCII (an 8 bit representation that 
contains English characters) the number assigned a character is not random.

Not all numbers represent "valid unicode characters". They are distributed 
in a somewhat (but not totally) random way throughout the number line. 


## Coverage

There are things left out from the unicode standard:

```markdown
Unicode Standard does not encode idiosyncratic, personal, novel, or
private-use characters, nor does it encode logos or graphics. Graphologies 
unrelated to text, such as dance notations, are likewise outside the scope of
the Unicode Standard. Font variants are explicitly not encoded.
```

For example, we don't have a code point corresponding to that drawing I did
of myself when I was eight years old.

The lack of typeface variants is unfortunate, as typeface variants are often
used in the mathematical literature to distinguish types. 

More generally, the unicode standard does not provide "post-coordinated
expressions", which (by definition?) require state to parse. Below is an 
example of a post-coordinated expression in [SNOMED-CT](https://confluence.ihtsdotools.org/display/DOCGLOSS/postcoordinated+expression):

```text
125605004 |fracture of bone| : 363698007 |finding site|  =  71341001 |bone structure of femur|
```

Fortunately,

```markdown
The Unicode Standard, Version 15.0, contains 149,186 characters from the
world’s scripts. These characters are more than sufficient not only for 
modern communication for the world’s languages, but also to represent the 
classical forms of many languages.
```

## Key Take Away

The unicode standard takes "text" and produces a sequence of natural numbers 
that is:

- tech-stack independent (e.g. it's the responsibility of a programming
  language to know about Unicode, not vice-versa)
- encompassing many forms of written human expression.
- loosely coupled to legal bodies ("don't need to ask an authority for
  permission to use Unicode")

Therefore, if we're doing NLP with computers, we can think of a text as
an ordered sequence of **certain** natural numbers. These numbers might as well
be some fixed finite set, held together by a web of tech stacks that will break
if there's disagreement.

I like to think of this finite set as a global variable within the NLP community
that can only mutate over time via subset inclusions.

## History

```python
# TODO can someone write about the history of Unicode?
```
