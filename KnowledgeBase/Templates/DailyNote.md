---
creation date: <% tp.file.creation_date() %>
tags: DailyNote 
---

modification date: <%+ tp.file.last_modified_date("dddd Do MMMM YYYY HH:mm:ss") %> 

# {{title}}


<< [[<% tp.date.now("YYYY-MM-DD", -1, tp.file.title, "YYYY-MM-DD") %>]] | [[<% tp.date.now("YYYY-MM-DD", 1, tp.file.title, "YYYY-MM-DD") %>]]>>

### [[Campus - my UMB Portal]]


### [[OEM - COOP Tools]]


### [[Law - Academic]]


## Tasks


#### Done Today

```tasks
done on <% tp.date.now("YYYY-MM-DD") %>
```

