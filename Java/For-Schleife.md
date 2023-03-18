---
tags: practical-cs
sources: "Java ist auch eine Insel 17"
cards-deck: Private::Books::JiaeI
completed: true
aliases: For-Schleife
linter-yaml-title-alias: For-Schleife
date-of-creation: 2022-10-08
mod-date: 2022-10-08
---

# For-Schleife

## Auf einem Iterator:
```java
LinkedHashSet<Integer> set = new LinkedHasSet<>();
set.addAll(Arrays.asList(1,2,3,4));

for(Iterator<Integer> iter = set.iterator(); iter.hasNext(); ){
	iter.next();
	...
}
```
