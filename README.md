# GALI: Gender Associations in Language Inventory

GALI is a large-scale lexicon of implicit gender-word associations in English. The resource captures how adjectives, verbs, and nouns are used to describe male and female subjects in large-scale text corpora.

Unlike co-occurrence-based gender bias resources, GALI focuses on words that directly modify or describe gendered subjects using POS and dependency-based linguistic patterns extracted from the Google Web 1T n-gram corpus.

## Overview

Language used to describe individuals can reflect implicit gender biases that influence both human judgment and NLP model predictions. Existing gender-word lexicons are often domain-specific and rely primarily on distributional co-occurrence statistics, limiting their ability to capture implicit stereotypes, characteristic traits, gender roles, and identity descriptors.

GALI introduces:

- a large-scale lexicon of implicit gender associations
- adjective, verb, and noun association scores
- gender seed word lists
- POS and dependency-based extraction patterns
- support for identifying implicit gender stereotypes and gender bias in text

The resource includes archaic, slang, colloquial, and contemporary English associations.

---

# Repository Structure

```text
GALI/
│
├── adjective_pos_patterns.json
├── noun_pos_patterns.json
├── verb_pos_patterns.json
│
├── adjectives.csv
├── nouns.csv
├── verbs.csv
│
├── female_gender_seed_words.csv
├── male_gender_seed_words.csv
│
└── README.md
```

---

# Lexicon Files

## `adjectives.csv`

Contains adjective gender association scores.

## `verbs.csv`

Contains verb gender association scores.

## `nouns.csv`

Contains noun gender association scores.

Each CSV file contains:

```text
word,score
```

where:

- `word` = lexical item
- `score` = gender association score

## Score Interpretation

```text
score < 0  → more female-associated
score > 0  → more male-associated
score ≈ 0  → relatively neutral
```

The scores are computed using relative usage frequencies with male and female subjects in the Web 1T corpus.

---

# Gender Seed Words

The repository includes:

- `male_gender_seed_words.csv`
- `female_gender_seed_words.csv`

These seed words were used to identify gendered subjects during pattern extraction.

The lists include:

- kinship terms
- occupational titles
- pronouns
- honorifics
- slang expressions
- archaic forms

---

# POS Pattern Resources

The repository includes POS and dependency-based linguistic templates used to identify words that directly modify gendered subjects:

- `adjective_pos_patterns.json`
- `verb_pos_patterns.json`
- `noun_pos_patterns.json`

Each JSON file contains:

```json
{
  "category": "NOUN follows ADJ",
  "pattern": "ADJ_amod - NOUN_nsubj - X - X - X",
  "example": "young girl said to her"
}
```

## Pattern Notation

- `ADJ_amod` → adjective with dependency relation `amod`
- `NOUN_nsubj` → noun with dependency relation `nsubj`
- `VERB_ROOT` → verb serving as sentence root
- `X` → wildcard token

The patterns were constructed using spaCy POS tagging and dependency parsing.

---

# Method Summary

Using the Google Web 1T n-gram corpus, we extract adjectives, verbs, and nouns that directly modify male and female subjects through POS and dependency-based linguistic templates.

For each lexical item, a gender association score is computed from relative frequency differences between male- and female-associated contexts.

Unlike standard embedding-based approaches relying on global co-occurrence statistics, GALI focuses on direct modifier relationships and subject descriptions, enabling more interpretable analysis of implicit gender stereotypes and gender bias.

---

# Example Usage

```python
import pandas as pd

adjectives = pd.read_csv("adjectives.csv")

female_words = adjectives[
    adjectives["score"] < 0
].sort_values("score")

male_words = adjectives[
    adjectives["score"] > 0
].sort_values("score", ascending=False)

print(female_words.head())
print(male_words.head())
```

---

# Applications

GALI may be useful for:

- implicit gender bias analysis
- stereotype detection
- fairness evaluation in NLP systems
- lexicon-based bias scoring
- linguistic bias analysis
- social bias research
- explainable bias detection methods

---

# Content Warning

This repository contains words and phrases that may be:

- offensive
- sexually explicit
- stereotypical
- derogatory
- archaic

These terms are included for research purposes because they occur in real-world language data.

---

# Limitations

The current resource focuses only on English-language corpora and uses English-specific POS tagging and dependency patterns. The lexicon captures statistical associations observed in text and should not be interpreted as normative or causal statements about gender.

---

# License

Please specify the repository license, for example:

- MIT License
- Apache 2.0
- CC BY 4.0

---

# Contact

For questions, please contact: manuela.n.jeyaraj@mytudublin.ie

# Citation and Usage

If you use the GALI resource, lexicon files, gender seed word lists, POS pattern resources or derived resources from this repository in your research or applications, please cite this repository and acknowledge the author:

```text
GALI: Gender Associations in Language Inventory
Author: Manuela Jeyaraj
Repository: https://github.com/manuelanjeyaraj/GALI
```

This includes use of:

- `adjectives.csv`
- `verbs.csv`
- `nouns.csv`
- `male_gender_seed_words.csv`
- `female_gender_seed_words.csv`
- `adjective_pos_patterns.json`
- `verb_pos_patterns.json`
- `noun_pos_patterns.json`

A formal citation entry and accompanying publication details will be added after the corresponding paper is published.
