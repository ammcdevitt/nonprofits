# How to create relational databases in MySQL
Sample that is used here is joining a list of executive directors to an existing list of nonprofits

## Using Python to Run a Query in MySQL
This reads data from a local mysql database using Python. Be sure that you have installed mysql connector and update security/privacy settings (as needed) to allow it to download.

```import mysql.connector```

```conn = mysql.connector.connect(user='root', database='test')```

```cursor = conn.cursor(buffered=True)```

```query = ('SELECT * FROM tbl_nonprofits')```
Note: * means all data

```
cursor.execute(query)
for result in cursor:
print result
```

## Shell
If you would rather use the Python shell, please use the following commands.

<p> The line below creates a new table by defining it, listing the column names (including their data type and max length). At this point, the are no rows (data) assigned to the columns. </p>

```create table tbl_nonprofits (Id int, org_name varchar(100), address varchar(100), exec_dir varchar(30));```

<p> Now we define each exective directors & stores each as an int value </p>

```create table tbl_exec_dir (id int, first_name varchar(30), last_name varchar(50));```

<p> Altering Tables: Creating Primary Keys </p>
```alter table tbl_nonprofits add primary key (ID);```
```alter table tbl_exec_dir add primary key (ID);```

<p> Altering Tables: Changing Data Type </p>
```alter table tbl_nonprofits modify exec_dir int(30);```

<p> Altering Tables: Creating a Foreign Key </p>
```alter table tbl_nonprofits add foreign key (exec_dir) references tbl_exec_dir(id);```

<p> Inserting Data: into Executive Director Table </p>
```insert into tbl_exec_dir (id, first_name, last_name) values (1, 'bob', 'johnson');```
```insert into tbl_exec_dir (id, first_name, last_name) values (2, 'john', 'smith');```
```insert into tbl_exec_dir (id, first_name, last_name) values (3, 'jane', 'doe');```

<p> Inserting Data: into Nonprofit Table </p>
```insert into tbl_nonprofits (id, org_name, address, exec_dir) values (1, 'Do-Gooders', '123 Main St', 1);```
```insert into tbl_nonprofits (id, org_name, address, exec_dir) values (2, 'Helping Others', '456 George St', 2);```
```insert into tbl_nonprofits (id, org_name, address, exec_dir) values (3, 'Tech for Good', '768 Main St', 3);```
