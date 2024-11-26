---
header_type: "hero"
header_img: 
title: <% title %>
created: <%tp.file.creation_date("YYYY-MM-DD")%>
last_modified_at: <% tp.file.last_modified_date() %>
tags:
categories:
---
<%* 
let title = tp.file.title 
if (title.startsWith("Untitled")) { title = await tp.system.prompt("Title"); } await tp.file.rename(title) 
-%>
# <% title %>
---
### Description
---

### Hints
---

> [!hint]- Hint(s)
> 1. 

### Step(s)
---

### Flag
---
> [!question]- Flag
> 







