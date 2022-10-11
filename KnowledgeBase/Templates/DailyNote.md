---
creation date: <% tp.file.creation_date() %>
tags: DailyNote <% tp.file.title.split('-')[0] %>
---

modification date: <%+ tp.file.last_modified_date("dddd Do MMMM YYYY HH:mm:ss") %> 

# <% tp.file.title %>

<< [[<% tp.date.now("YYYY-MM-DD", -1, tp.file.title, "YYYY-MM-DD") %>]] | [[<% tp.date.now("YYYY-MM-DD", 1, tp.file.title, "YYYY-MM-DD") %>]]>>

## Tasks


#### New Today
- [ ]


## Daily Log

### [[Project 1]]


### [[Project 2]]


### [[Project 3]]

## Daily Check List

### Start of Day

- [ ] Check Email
- [ ] Check Teams
- [ ] Check showing online
- [ ] Check Calendar - Time Block

### End of Day

- [ ] Show Offline
- [ ] Clean Unused Headings in Daily Log
- [ ] Check tomorrow's calendar
- [ ] Update Timesheet

## Other Tasks



#### No Due Date

```tasks
not done
no due date
```

#### Done Today

```tasks
done on <% tp.date.now("YYYY-MM-DD") %>
```

 ![](chrome-extension://annlhfjgbkfmbbejkbdpgbmpbcjnehbb/images/saveicon.png) Save