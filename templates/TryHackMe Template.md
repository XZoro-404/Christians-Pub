---
header_type: hero
header_img: 
title: 
subtitle: 
last_modified_at: <% tp.file.last_modified_date() %>
created: <%tp.file.creation_date("YYYY-MM-DD")%>
tags: 
categories: "[TryHackMe]"
---
<%* 
let title = tp.file.title 
if (title.startsWith("Untitled")) { title = await tp.system.prompt("Title"); } await tp.file.rename(title) 
-%>
# <% title %>
---
