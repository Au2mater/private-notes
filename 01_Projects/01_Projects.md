---
urgency_threshold: 15
todo_urgency_threshold: "7"
---

> [!NOTE]- Reference
> A list of active projects
> * **Actionable**: I can act on this project today
> 	* **Urgent**: I need to act on this project soon?
> 		* **Urgency threshold**: this.urgency_threshold days
> 	* **Important**: There are significant consequences if I don't act on this project?  
> * **Dormant**: I cannot act on this project today. 
> * **Upcoming**: Projects I have decided to work on, but are not yet active. 

>[!info] Urgent TODOs of actionable projects  
>```dataview
TASK 
FROM "01_Projects"
WHERE !completed 
AND date(active_again_from) <= date(today) 
AND (date(duedate) - date(today)) <= dur( string(this.todo_urgency_threshold)+ " days" )
AND (date(duedate) - date(today))  > dur("-1 days")
GROUP BY file.link
>```

## Actionable Projects

>[!info] Important and urgent
>```dataview
TABLE 
min(date(next_deadline),date(deadline))  as "next deadline",  
(date(deadline) - date(today)) as "due in"
FROM "01_Projects"
WHERE 
regexmatch("^\\d{4}", file.name) 
AND date(active_again_from) <= date(today)
AND (min(date(next_deadline),date(deadline)) - date(today)) <= dur( string(this.urgency_threshold)+"days" )
AND important
SORT deadline
>```

>[!Warning ] Important, not urgent 
>```dataview
TABLE 
min(date(next_deadline),date(deadline))  as "next deadline",  
(date(deadline) - date(today)) as "due in"
FROM "01_Projects"
WHERE 
regexmatch("^\\d{4}", file.name) 
AND date(active_again_from) <= date(today)
AND (min(date(next_deadline),date(deadline)) - date(today)) > dur( string(this.urgency_threshold)+"days" )
AND important
SORT deadline
>```

>[!Warning] Not important, urgent 
>```dataview
TABLE 
min(date(next_deadline),date(deadline))  as "next deadline",  
(date(deadline) - date(today)) as "due in"
FROM "01_Projects"
WHERE 
regexmatch("^\\d{4}", file.name) 
AND date(active_again_from) <= date(today)
AND (min(date(next_deadline),date(deadline)) - date(today)) <= dur( string(this.urgency_threshold)+"days" )
AND !important
SORT deadline
>```

>[!Quote] Neither important , nor urgent 
>```dataview
TABLE 
min(date(next_deadline),date(deadline))  as "next deadline",  
(date(deadline) - date(today)) as "due in"
FROM "01_Projects"
WHERE 
regexmatch("^\\d{4}", file.name) 
AND date(active_again_from) <= date(today)
AND (min(date(next_deadline),date(deadline)) - date(today)) > dur( string(this.urgency_threshold)+"days" )
AND !important
SORT deadline 
>```



## Non-actionable projects
### Dormant

```dataview
TABLE 
active_again_from as "start date"
, mål
FROM "01_Projects"
WHERE date(active_again_from) > date(today)
SORT active_again_from 
```

### Upcoming

```dataview
TABLE 
active_again_from as "start date"
, mål
FROM "03_Resources/00_upcomingProjects" 
WHERE date(active_again_from) > date(today)
SORT active_again_from 
```

>[!Note] Overdue
>```dataview
TABLE 
min(date(next_deadline),date(deadline))  as "next deadline",  
(date(deadline) - date(today)) as "due in"
FROM "01_Projects"
WHERE 
regexmatch("^\\d{4}", file.name) 
AND (date(deadline) - date(today)) < dur("1d")
SORT deadline
>```


## All active projects 

```dataview
TABLE 
min(date(next_deadline),date(deadline))  as "next deadline",  
(date(deadline) - date(today)) as "due in"

FROM "01_Projects"
WHERE regexmatch("^\\d{4}", file.name)
SORT deadline
```