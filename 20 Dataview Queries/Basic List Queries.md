---
description: Showcase basic syntax of LIST queries
topics:
  - basics
---
#dv/list #dv/from #dv/where #dv/sort #dv/groupby 


# Basic List Queries

## Basic 
**List pages from a folder**
```dataview
LIST
FROM "10 Example Data/games"
```

**List pages from a tag**
```dataview
LIST
FROM #type/books 
```

**Combine multiple tags**
```dataview
LIST
FROM #dvjs/el OR #dv/min 
```

**Combine multiple folders**
```dataview
LIST
FROM "10 Example Data/books" OR "10 Example Data/games"
```

**Combine tags and folders**
```dataview
LIST
FROM "10 Example Data/games" AND #genre/action  
```

**List all pages**

> [!attention] Add `dataview` to code block
> The output of this is pretty long. If you want to see it, add `dataview` to the code block - like on the examples above!
> Please note: There needs to be a **space** behind `LIST` to see results!

```
LIST 
```

## Variants

### List pages from a certain author

```dataview
LIST
FROM #type/books 
WHERE author = "Conrad C"
```

### List pages and show a meta data field

> [!attention] Only one additional information
> For lists, you can only add **one** additional output. For more, you need to use a [[Basic Table Queries|table]] or [[How to create custom outputs in queries|create a custom output]].

```dataview
LIST author
FROM #type/books
```

### List meta data values instead of the pages

i.e. list source links of your recipes:

```dataview
LIST WITHOUT ID source
FROM "10 Example Data/food"
WHERE source
```

### Group list elements

> [!info] New "first level"
> When grouping lists, your "first level" changes. Without grouping, the first level are the file links you get back from your `FROM/WHERE` statement, so they automatically get displayed if you give no additional information to the `LIST` command.
> After grouping though, your _groups_ become the first level, meaning that without adding an additional information you'll see the groups in your list instead of the file links. To still see the file names, you need to pass them as your additional information to display. Find out more about this in [[How GROUP BY works]]

```dataview
LIST rows.file.link
FROM "10 Example Data/books"
GROUP BY author
```

### Sort list elements

```dataview
LIST author
FROM "10 Example Data/books"
SORT author
```

---
%% === end of query page === %%
> [!help]- Similar Queries
> Maybe these queries are of interest for you, too:
> ```dataview
> LIST
> FROM "20 Dataview Queries"
> FLATTEN topics as flattenedTopics
> WHERE contains(this.topics, flattenedTopics)
> AND file.name != this.file.name
> ```

```dataviewjs
const inlinksFromUseCases = dv.current().file.inlinks.filter(link => link.path.contains("33 Use Cases"));

const header = `> [!info] Part of Use Cases`;

if (inlinksFromUseCases.length > 1) {
	const list = inlinksFromUseCases.array().reduce((acc, curr) => `${acc}</br> - ${curr}`,"")

	dv.span(`${header}
    > This query is part of following use cases:
    > ${list}
    > 
	`)
} else if (inlinksFromUseCases.length === 1) {
	dv.span(`${header}
    > This query is part of use case ${inlinksFromUseCases[0]}.
	`)
}
```