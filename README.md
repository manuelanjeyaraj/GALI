# GALI: Lexicon of Implicit Gender Associations in Language

This repository contains **GALI**, a large-scale lexicon of implicit gender-word associations in English. The lexicon captures how adjectives, verbs, and nouns are used to describe male and female subjects in large-scale text, with association scores derived from relative usage frequencies in the Web 1T n-gram corpus.

GALI is designed to support research on implicit gender bias, gender stereotype detection, lexical bias analysis, and bias measurement in NLP systems.

## Overview

Language used to describe individuals can reflect implicit gender biases that influence both human judgment and model predictions. Unlike lexicons that rely primarily on word co-occurrence or domain-specific bias terms, GALI focuses on words that directly modify or describe gendered subjects.

The lexicon includes:

- adjective, verb, and noun association scores
- male and female gender seed words
- POS and dependency-based patterns used to extract modifier words
- words spanning archaic, slang, and contemporary English usage

A negative gender association score indicates that a word is more **female-associated**, while a positive score indicates that a word is more **male-associated**.

## Repository Contents

```text
.
├── adjectives.csv
├── verbs.csv
├── nouns.csv
├── male_gender_seed_words.csv
├── female_gender_seed_words.csv
├── adjective_pos_patterns.csv
├── verb_pos_patterns.csv
├── noun_pos_patterns.csv
└── README.md
