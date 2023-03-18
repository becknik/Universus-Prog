---
tags: practical-cs
sources: "Java ist auch eine Insel 17"
cards-deck: Private::Books::JiaeI
completed: false
aliases: Reflections
linter-yaml-title-alias: Reflections
date-of-creation: 2022-07-14
mod-date: 2022-10-08
mod-date: 2022-07-14
---

# Reflections

## Arrays

### Nützliches:
- `static Object newInstance(Class<?> componentType, int… dimensions)`
	→ Macht dynamisch das, was bei `new` statisch festgelegt wird
	→ Muss noch entsprechend gecastet werden
```java
Object[] b = (Object[]) Array.newInstance( array.getClass().getComponentType(), len );
```
