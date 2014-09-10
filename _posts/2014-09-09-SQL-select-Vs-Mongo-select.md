---
layout: post
title: SQL select vs. Mongo find
---

One of the most basic queries we can do in a database is to read records in a table. In this post, i shall show you how it is done in SQL and in MongoDB. Let's assume that we have the following Users table in our MySQL database:

| userId        | firstName     | lastName  |
| ------------- |---------------| --------	|
| 1      		| Rob			| Stark 	|
| 2		        | Brandon     	| Stark 	|
| 3				| Theon         | Greyjoy 	|

---

To find all of the records in the Users table and if we want all of the columns back:
{% highlight sql %}
-- returns all of the records in table Users
SELECT * 
FROM Users;
{% endhighlight %}

To find a specific record using the userId (int key):
{% highlight sql %}
-- returns Rob Stark's record
SELECT * 
FROM Users
WHERE userID = 1;
{% endhighlight %}

To find a specific record using the firstName (nvarchar):
{% highlight sql %}
-- returns Rob Stark's record
SELECT * 
FROM Users
WHERE firstName LIKE 'Rob';
{% endhighlight %}

---
Moving on to MongoDb, let's pretend that we have a collection called Users where we have userId, firstName, lastName defined in each document.

To find all of the documents in our Users collection with all of the defined attributes of the document:
{% highlight js%}
// returns all of the users 
db.users.find()
{% endhighlight %}

To find a specific record using the userID:
{% highlight js%}
// returns Rob Stark's record
db.users.find({ "userId" : 1 })
{% endhighlight %}

To find a specific record using the firstName :
{% highlight js %}
// returns Rob Stark's record
db.users.find({ "firstName" : "Rob" })
{% endhighlight %}