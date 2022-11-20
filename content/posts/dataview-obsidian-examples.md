---
title: 'Dataview Obsidian Examples'
date: 2022-09-03T02:36:48+04:00
draft: false
tags: ["Obsidian", "how-to"]
---

When I add posts written not by me in my Obsidian, I usually title them like ‘Name - Post Title’ and backlink them to the note named after the author. I was looking for any automated option to list them inside the note, not inside the Backlink pane, and discovered the DataView plugin. It helps you to work with your knowledge base as if it were data base. Means: to make queries and get lists and tables of notes you need.

For example:

![Andy's Note in Obsidian](/images/andy-note.webp "Note and list of sub-notes")

This is a note about Andy Matuschak. I have ‘Andy’s Notes Copies’ headline here and everything that goes after it was automatically put there by querying notes with the filename ‘Andy Matuschak -‘. Moreover: every time I save some other post, that Andy’ll write this note will update automatically. 
This is how it looks in code:

<code>
```dataview<br/>
LIST WHERE contains(file.name, "Andy Matuschak -") <br/>SORT DESC<br/>
```
</code>

![Dataview query Obsidian](/images/andy-note-source.webp)

Put three backticks, write dataview, and then write your query. Syntax reminds me of MySQL. If you are not familiar with database queries, let me explain: this code means something like ‘show me the list of every file containing ‘Andy Matuschak - ‘ in the file name, sort it descending’.
This is probably, one of the easiest ways of using Dataview, which I’ve tried first, back in the days, when I discovered it. A good place to start.

My next experiment was about music albums:

![Dataview query Obsidian select and sort](/images/listened.webp)

This is the list of albums, that I’ve listened to for the first time in 2022. Query is litle bit more complicated now:

<code>
```dataview<br/>
TABLE artist as "Artist", title as "Title", <br/> first-listen-date as "🎧", type as "Type", rating as "⭐️"<br/>
WHERE first-listen-date >= date(2022-01-01)<br/>
AND first-listen-date < date(2023-01-01) <br/>SORT first-listen-date ASC ```<br/>
</code>

And to make it work you should put something in YAML-block at the begining of your notes:

![Dataview YAML section parameters](/images/liars.webp)

Can’t recommend Dataview more, this couple of examples are just starters.

