---
title: MySql tutorial 
date: 2020-12-19 20:28:53
tags:
---

{% codeblock%}
mysql --auto-rehash -u root //set up tab completion
select <column_name> from <table_name>;
select <column_name> from <table_name> order by <column_name> ASC/DESC;
(use databases //first) Describe orders; // to show table's columns/fields
// sort data based on statuse
select <column_name> status from <table_name>
order by field(status, <'statuses'>); (in process, on hold, canceled, resolved, disputed, shipped)
// search rows
select <column_name> from <table_name> where <search_condition>;

{% endcodeblock %}
