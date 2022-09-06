# Vault To Do

## Organization

- [ ] Write MOCs or similar that encourage exploration, the current ones are awful (sorry!)
- [ ] [[Use Cases]]
	- [ ] Daily Notes
	- [ ] Weekly Notes
	- [ ] A Person page (last contact, birthday, ...)

## Example Data
- [ ] Add more example data for "Collection" queries (book/game/food notes)

## Queries
- [ ] Add the examples from the Dataview documentation (with back reference) for easy try-outs
- [ ] Add TASK queries that showcase the basic syntax
- [ ] Add the [possibility to burn out dataview queries with markdownTable and templater](https://github.com/blacksmithgu/obsidian-dataview/discussions/1241) (also [here](https://forum.obsidian.md/t/dataviewjs-snippet-showcase/17847/225) ) with a back reference, explanation and example code
- [ ] Add [the usage of Object.assign for duplicating entries into custom made groups](https://discord.com/channels/686053708261228577/875721010144477204/1003404078233178263) and [the metadata based groups](https://discord.com/channels/686053708261228577/875721010144477204/1005498669719638119) as a variant - and try if [dv.clone](https://blacksmithgu.github.io/obsidian-dataview/api/code-reference/#dvclonevalue) is a good alternative to Object.assign
- [ ] Add a example of the different frontmatter possibilities (list, multiline, escaped links ("[[link]]") etc.) and how they get rendered in lists and tables
- [ ] Add an example that explains [the behaviour of metadata fields after a GROUP BY](https://discord.com/channels/686053708261228577/875721010144477204/1004654445348532234)
- [ ] Add an example about [how to render custom strings in tables or lists](https://discord.com/channels/686053708261228577/875721010144477204/1004658573009227836)
- [ ] Add [this thing about the earlierst and latest outlink I don't fully understand](https://discord.com/channels/686053708261228577/875721010144477204/1004254235812184124)
- [ ] Add [this thing](https://discord.com/channels/686053708261228577/875721010144477204/1003433672780808212)
- [ ] Add [grouped, nested tables](https://discord.com/channels/686053708261228577/875721010144477204/1002958739705438288)
- [ ] Add [the dynamic query based on a tag in an inline field](https://discord.com/channels/@me/973972301127249950/1001569802629951640)
- [ ] Add an example about indexing through a link, see [here](https://discord.com/channels/686053708261228577/875721010144477204/1006970754375614635) 
- [ ] Create  syntax examples/explanations that apply to all types
	- [ ] How to select or exclude the current file
	- [ ] What does GROUP BY and how to deal with it [[How GROUP BY works]]
	- [ ] What does FLATTEN and how to use it [[How FLATTEN works]]
	- [ ] What does SORT and how to use it [[How SORT works]]
	- [ ] Where is file.day coming from, how to set and how to use it
	- [ ] What are implicits fields and how to use them 
	- [ ] What are inline fields and their types [[Inline Field Overview]]
 - [ ] Explain what inline queries can do (and what not) [[Basic Inline Queries]]
 - [ ] Add [sum up number of pages fulfilling certain criteria](https://discord.com/channels/686053708261228577/875721010144477204/1010262245755858994)
 - [ ] Add a page about [transforming dates](https://discord.com/channels/686053708261228577/875721010144477204/1011564039639404584) into a [format dataview recognizes](https://blacksmithgu.github.io/obsidian-dataview/data-annotation/#field-types)
 - [ ] Add [List activity log from projects in daily note via a date header](https://discord.com/channels/686053708261228577/1014259487445622855/1014949689394741370)
 - [ ] Add [student assignment overview](https://discord.com/channels/686053708261228577/1014259487445622855/1014879231743893525)
 - [ ] Add a page how to format dates with reference to https://moment.github.io/luxon/#/formatting?id=table-of-tokens (see also [here](https://discord.com/channels/686053708261228577/1014259487445622855/1016131007923097641))
 - [ ] Add a page about sub tasks and their behaviour

## Missing but linked pages

> [!info] 
> A note is referring to a non-existing file, probably to a file that explains something in detail. Find out the context of the unresolved link and see if you either can create the fitting file or exchange the dead link with a in-place explanation.

```dataview
TABLE WITHOUT ID key AS "unresolved link", rows.file.link AS "referencing file"
FROM "20 Dataview Queries"
FLATTEN file.outlinks as outlinks
WHERE !(outlinks.file) AND !(contains(meta(outlinks).path, "/"))
GROUP BY outlinks
```