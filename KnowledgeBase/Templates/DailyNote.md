---
creation date: <% tp.file.creation_date() %>
tags: DailyNote <% tp.file.title.split('-')[0] %>
---

modification date: <%+ tp.file.last_modified_date("dddd Do MMMM YYYY HH:mm:ss") %> 

# <% tp.file.title %>

<< [[<% tp.date.now("YYYY-MM-DD", -1, tp.file.title, "YYYY-MM-DD") %>]] | [[<% tp.date.now("YYYY-MM-DD", 1, tp.file.title, "YYYY-MM-DD") %>]]>>


### [[OEM - COOP Tools]]


### [[Law - Academic]]

## Tasks



#### Done Today

```tasks
done on <% tp.date.now("YYYY-MM-DD") %>
```

