# Database Drill Many To Many Schema 
 
##Learning Competencies 

* Design database schema from problem data
* Model a one-to-many relationship in a relational database

##Summary 

 Many-to-many relationships are relatively easy to understand, but slightly more complicated to implement.  We recommend that you solve the one-to-many challenge before moving into
the many-to-many relationships.

A newsletter has many subscribers, and a subscriber might subscribe to many newsletters.  A blog post can have many tags ("funny", "politics", etc.), and a given tag can be on many blog posts.  A book can have multiple authors, and an author can write many books.

We model this relationship by creating a **join table**.  It looks like this:

<pre>
+------------+       +---------------+       +--------------+
| authors    |       | authors_books |       | books        |
+------------+       +---------------+       +--------------+
| id         |&lt;--\   | id            |    /-&gt;| id           |
| first_name |    \--| author_id     |   /   | title        |
| last_name  |       | book_id       |--/    | published_at |
| created_at |       +---------------+       | created_at   |
| updated_at |                               | updated_at   |
+------------+                               +--------------+
</pre>

Here <code>authors_books</code> is the join table and it tells us which authors wrote which books.  The actual data about each author and each book is stored in one place: the <code>authors</code> and <code>books</code> tables, respectively.

You might notice a ["Don't repeat yourself" priciple](http://en.wikipedia.org/wiki/Don't_repeat_yourself) at work.  Removing redundancy from a database schema so that each bit of data is stored in one and only one place is called **normalization**.  We'll learn more about that later.

If you want, you can read about [database normalization on Wikipedia](http://en.wikipedia.org/wiki/Database_normalization) or [this decent article from Microsoft](http://support.microsoft.com/kb/283878).  The goal of normalization is to remove data redundancy.

##Releases

###Release 0 : Implement the schema

Implement the above author/book schema.
Remember to add the appropriate foreign keys!  

Each book also has one publisher, and a publisher can publish many books.  Add a <code>publishers</code> table to the schema above so it and <code>books</code> are in a one-to-many relationship.  

The <code>publishers</code> table should have a <code>name</code> field, in addition to the fields we include by convention (primary key, timestamps, etc.). 

Use [SQL Designer][] to create your schema.  When you are done, save the XML of your schema and copy it to the source file `many_to_many_schema.md`. Then, take a screenshot of your final schema design, and upload it using a free image-upload service like [Min.us](http://minus.com).  Paste the URL of the screenshot into your file (before your XML code). 

<!-- ##Optimize Your Learning  -->

##Resources

* [SQL Designer](https://socrates.devbootcamp.com//sql.html)