---
tags: practical-cs cpu asm
cards-deck: 
completed: true
aliases:
  - RDRAMD
  - Intel Security Key
linter-yaml-title-alias: RDRAMD
date-of-creation: 2023-03-08
mod-date: 2023-03-08
---

# RDRAMD

## Eigenschaften
- Produziert eine fast vollkommen zufällige Bitfolge
- Ist signifikant langsamer als C's `std::mt19973` & es demnach nicht wert verwendet zu werden, außer bei [[../../../../Uni/DSA/Algorithmen/Muster/Monte-Carlo|Monte-Carlo-Algorithmen]], die sehr stark von perfekten Zufall abhängen[^1]
	→ Es wurde ein *i7-37xx* getestet

[^1]: [Radio-flaring Ultracool Dwarf Population Synthesis](https://arxiv.org/abs/1707.02212)
