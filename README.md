Download Link: https://assignmentchef.com/product/solved-eecs484-project1-database-design-for-social-network-data
<br>
In Project 1, you will design a relational database for storing information about your Fakebook social network. You will begin with a detailed description of the content. Then, you will need to systematically go through the conceptual and logical database design process you learned about in class. You can do the project either alone or in a group of two. If working in a group, a single submission is required.

<strong>Part 1: ER Design</strong>

As a starting point, we have done the initial “requirements analysis” for you. The following is a brief description of the data that you will store in your database. (In real life, you would probably begin with much fuzzier information.) <strong>All IDs in the specs below are, of course, unique.</strong>

<strong>User Information</strong>

There can be an unlimited number of users. Each user has the following information:

<ul>

 <li><strong>Profile information </strong></li>

</ul>

This includes the following attributes: user ID, first name, last name, year of birth, month of birth, day of birth, gender.

<ul>

 <li><strong>Hometown Location </strong></li>

</ul>

A user’s hometown includes the following attributes: city, state, country.

<ul>

 <li><strong>Current Location</strong></li>

</ul>

Exactly the same attributes as hometown location.

<ul>

 <li><strong> Education History</strong></li>

</ul>

A user’s educational history contains information on each college program attended, if any, with each college program attended containing the following attributes: name of the institution (e.g., University of Michigan), year of graduation, concentration (e.g., CS, EE, etc.), and degree (e.g., BS, MS, PhD, etc.).

<ul>

 <li><strong> Friendship information</strong></li>

</ul>

Each user can have any number of friends. Each friend must also be a Fakebook user.

<strong>Photos</strong>

“Photos” is an important Fakebook application. It records the following information:

<ul>

 <li><strong> Album information</strong></li>

</ul>

Each photo MUST belong to exactly one album. An album has the following attributes:

album_ID, owner_ID (this refers to the owner’s Fakebook ID), album_name, cover_photo_ID (this refers to a photo ID), album_created_time, album_modified_time , album_link and album_visibility.

<ul>

 <li><strong> Other information</strong></li>

</ul>

Each photo has the following attributes: photo_ID, photo_caption, photo_created_time, photo_modified_time, and photo_ link.

<ul>

 <li><strong> Photo Tags</strong></li>

</ul>

Users can also interact by tagging each other. A photo tag identifies a Fakebook user in a photo. It has the following associated attributes:

tag_photo_id (a Fakebook photo ID), tag_subject_id (a Fakebook user ID), tag_x_coordinate and tag_y_coordinate, and tag_created_time

The database does not track who did the tagging.

Note that there can be multiple tags at exactly the same (x, y) location. However, there can be only ONE tag for each subject in the photo; Fakebook doesn’t allow multiple tags for the same subject in a single photo. For example, you cannot tag Lady Gaga twice in a photo, even if she appears to be at two separate locations in the photo.

<strong>Messages</strong>

Users can also send private messages to each other.

<ul>

 <li><strong> Message information</strong></li>

</ul>

sender_ID (a Fakebook user ID), receiver_id (a Fakebook user ID), message_content (the text of the message), and sent_time

In this version of Fakebook, there are no group messages. A user can, of course, send zero or more messages to different users.

<strong>Events</strong>

“Events” is another useful Fakebook feature.

<ul>

 <li><strong> Basic event information</strong></li>

</ul>

event_ID, event_creator_id (Fakebook user who created the event), event_name, event_tagline, event_description, event_host (this is a string, not a Fakebook user), event_type, event_subtype, event_location, event_city, event_state, event_country, event_start_time, and event_end_time

<ul>

 <li><strong> Event participants</strong></li>

</ul>

Participants in an event must be Fakebook users. Each participant must have a confirmation status value (attending, declined, unsure, or not‐replied). The sample data does not have information on Event Participants, so you can leave the information on Participants empty.




<strong>Task for Part 1 </strong>

Your task in Part 1 is to perform “Conceptual Database Design” using ER Diagrams. There are many ER variants, but for this project, we expect you to use the conventions from the textbook and lecture. You are encouraged to use free diagramming tools like draw.io, Lucidchart or so.




<strong>Hints for Part 1</strong>

You need to identify the entity sets and relationship sets in a reasonable way. We expect there to be multiple correct solutions; ER design is somewhat subjective. Your goal should be to capture the given information using ER constructs that you have learned about in class (participation constraints, key constraints, weak entities, ISA hierarchies and aggregation) as necessary.

For the entity set, relationship set and attribute names, you can use the ones we have provided here, or you may also choose your own names, as long as they are intuitive and unambiguous.

Before you get started, you should also read the Appendix to understand the specifics of the data. Some of the ER diagram constraints are in the Appendix.

Also, when you are not sure about some constraints, <strong>think about the case as in Facebook</strong>. (For example, can people have multiple hometowns?)




<strong>Part 2: Logical Database Design</strong>

For the second part of the project, your task is to convert your ER diagrams into relational tables. You are required to write SQL DDL statements for this part. You should turn in two files:

<ol>

 <li>sql</li>

 <li>sql</li>

</ol>

As a starting point, we are giving you a set of tables, along with some columns. Your design must use these tables. But, you will need to add any integrity constraints so that the schema is as close to enforcing the requirements as is practical.<strong><span style="text-decoration: line-through;"> You can add additional columns as well. Use the most appropriate types for the fields as well.</span></strong><strong> Notice that we might do some insertion to your table while grading, so please make sure that your table is identical to the schema given in the spec, or at least it allows inserting only on the columns given in the spec.</strong>




The required tables and their schema are given below:

USERS:

USER_ID (NUMBER)

FIRST_NAME (VARCHAR2(100))

LAST_NAME (VARCHAR2(100))

YEAR_OF_BIRTH (INTEGER)

MONTH_OF_BIRTH (INTEGER)

DAY_OF_BIRTH (INTEGER)

GENDER (VARCHAR2(100))

FRIENDS:

USER1_ID (NUMBER)

USER2_ID(NUMBER)

CITIES:

CITY_ID (INTEGER)

CITY_NAME(VARCHAR2(100))

STATE_NAME (VARCHAR2(100))

COUNTRY_NAME (VARCHAR2(100))

USER_CURRENT_CITY:

USER_ID (NUMBER)

CURRENT_CITY_ID (INTEGER)

USER_HOMETOWN_CITY:

USER_ID (NUMBER)

HOMETOWN_CITY_ID (INTEGER)

MESSAGE:

MESSAGE_ID (INTEGER)

SENDER_ID (NUMBER)

RECEIVER_ID(NUMBER)

MESSAGE_CONTENT (VARCHAR2(2000))

SENT_TIME (TIMESTAMP)

PROGRAMS:

PROGRAM_ID (INTEGER)

INSTITUTION (VARCHAR2(100))

CONCENTRATION (VARCHAR2(100))

DEGREE (VARCHAR2(100))

EDUCATION:

USER_ID (NUMBER)

PROGRAM_ID (INTEGER)

PROGRAM_YEAR (INTEGER)

USER_EVENTS:

EVENT_ID (NUMBER)

EVENT_CREATOR_ID (NUMBER)

EVENT_NAME (VARCHAR2(100))

EVENT_TAGLINE (VARCHAR2(100))

EVENT_DESCRIPTION (VARCHAR2(100))

EVENT_HOST (VARCHAR2(100))

EVENT_TYPE (VARCHAR2(100))

EVENT_SUBTYPE (VARCHAR2(100))

EVENT_LOCATION (VARCHAR2(100))

EVENT_CITY_ID (INTEGER)

EVENT_START_TIME (TIMESTAMP)

EVENT_END_TIME (TIMESTAMP)

PARTICIPANTS:

EVENT_ID (NUMBER)

USER_ID (NUMBER)

CONFIRMATION (VARCHAR2(100))

ALBUMS:

ALBUM_ID (VARCHAR2(100))

ALBUM_OWNER_ID (NUMBER)

ALBUM_NAME (VARCHAR2(100))

ALBUM_CREATED_TIME (TIMESTAMP)

ALBUM_MODIFIED_TIME (TIMESTAMP)

ALBUM_LINK (VARCHAR2(2000))

ALBUM_VISIBILITY (VARCHAR2(100))

COVER_PHOTO_ID (VARCHAR2(100))

PHOTOS:

PHOTO_ID (VARCHAR2(100))

ALBUM_ID (VARCHAR2(100))

PHOTO_CAPTION (VARCHAR2(2000))

PHOTO_CREATED_TIME (TIMESTAMP)

PHOTO_MODIFIED_TIME (TIMESTAMP)

PHOTO_LINK (VARCHAR2(2000))

TAGS:

TAG_PHOTO_ID (VARCHAR2(100))

TAG_SUBJECT_ID (NUMBER)

TAG_CREATED_TIME (TIMESTAMP)

TAG_X (NUMBER)

TAG_Y (NUMBER)




Keep the table and field names exactly as written above. Also, make sure you use the correct field types (e.g., number or integer) as specified above. Failure to do so may result in failing the autograder since the database is case and type sensitive. (Note: The ID types for various fields would normally be INTEGERs in practice, but they are not in this project for reasons other than technical, primarily,  that the input data sets we are importing contains non-integer types for keys  — use it as a learning moment  to deal with IDs of different types!)

You need to decide what fields will be primary keys and what fields will be foreign keys(if necessary). Use the smallest candidate keys when possible for primary keys.




<strong>Hints for Part 2 </strong>

You should capture as many constraints from your ER diagrams as possible in your createTables.sql file. In your dropTables.sql, you should write the DROP TABLE statements necessary to destroy the tables you have created.

Using Oracle SQL*Plus, you can run your .sql files with the following commands:

sqlplus &lt;accountName&gt;/&lt;password&gt; @ dropTables.sql

sqlplus &lt;accountName&gt;/&lt;password&gt; @ createTables.sql

You can also just type the following commands within sqlplus:

SQL&gt; @createTables.sql

SQL&gt; @dropTables.sql

Please double‐check that you can run the following sequence without errors in a single sql script. Otherwise, you may fail our auto‐grading scripts. Also remember to drop any triggers, constraints, etc., that you created.

<ul>

 <li>sql</li>

 <li>sql</li>

 <li>sql</li>

 <li>sql</li>

</ul>




<strong>Part 3: Populate Your Database </strong>

For this part of the project, you will populate your database with Fakebook data, described in Appendix. You should turn in the set of SQL statements (DML) to load data from the public tables (PUBLIC_USER_INFORMATION , etc.) into your tables. You should put all the statements into a file called “loadData.sql”.




<strong>Hints for Part 3</strong>

There will be some variations depending on the schema that you choose. In most cases, however, you can load data into your tables using very simple SQL commands.

Please double‐check that you can run the following sequence without errors in a single sql script. Otherwise, you may fail our auto‐grading scripts. Also remember to drop any triggers, constraints, etc., that you created.

<ul>

 <li>sql</li>

 <li>sql</li>

 <li>sql</li>

 <li>sql</li>

 <li>sql</li>

 <li>sql</li>

</ul>




Your loadData.sql must load from our PUBLIC datasets, not from a private copy. We will be testing your system against hidden datasets and therefore need your loadData.sql to be loading from the specified dataset. Otherwise, you will fail our tests.

One concern you might have is how to handle the constraint on Friend data. For this project, when loading the data, ensure that only the necessary data is loaded. For example, if the original data contains (2,7) and (7,2), only load one of these two values. Loading both or neither would be incorrect. After the data has been loaded, you only need to ensure that any insertion of new data does not break the no duplication constraint. This can either be done by rejecting any insert or batch insert which would violate the constraint or only accepting valid data and rejecting the rest. The first option tends to be easier.




<strong>Part 4: Create views on your database</strong>

As a final task, you will create some views on your tables. Here is what we would like:

Define views to recreate the same schemas as the PUBLIC tables (see Appendix). The rows in a view do not have to be in exactly the same order as in the corresponding table in the PUBLIC datasets, but <strong>the schema must be identical.</strong> <strong>The columns must have identical names and types.</strong> You can check the schema of the PUBLIC tables by using the “DESC TableName” command. For the public dataset, the original data satisfied all the integrity constraints, each view will have the same set of rows as in the corresponding input table. Name your view tables as follows (correspondence to the public tables should be obvious ‐‐ See Appendix later)

<ul>

 <li><strong> VIEW_USER_INFORMATION</strong></li>

 <li><strong> VIEW_ARE_FRIENDS</strong></li>

 <li><strong> VIEW_PHOTO_INFORMATION</strong></li>

 <li><strong> VIEW_TAG_INFORMATION</strong></li>

 <li><strong> VIEW_EVENT_INFORMATION</strong></li>

</ul>

Turn in the following files that create and drop the views:

<ul>

 <li>createViews.sql</li>

 <li>dropViews.sql</li>

</ul>




<strong>Hints for Part 4</strong>

<ol>

 <li>You should check that the following sequence works correctly in a single script (no errors).</li>

</ol>

<ul>

 <li>createTables.sql</li>

 <li>loadData.sql</li>

 <li>createViews.sql</li>

 <li>dropViews.sql</li>

 <li>dropTables.sql</li>

 <li>createTables.sql</li>

 <li>loadData.sql</li>

 <li>createViews.sql</li>

 <li>dropViews.sql</li>

 <li>dropTables.sql</li>

</ul>

<ol start="2">

 <li>You should also check for the provided dataset that createViews.sql results in identical tables to the provided tables. For example, the following checks should result in an empty result:</li>

</ol>

<ul>

 <li>SELECT * FROM weile.PUBLIC_USER_INFORMATION</li>

</ul>

MINUS

SELECT * FROM VIEW_USER_INFORMATION;

<ul>

 <li>SELECT * FROM VIEW_USER_INFORMATION</li>

</ul>

MINUS

SELECT * FROM weile.PUBLIC_USER_INFORMATION;

You should apply the same checks for all the public and view tables.

<ol start="3">

 <li>You may also wish to further test your system to make sure it is observing the specified integrity constraints with your own test input tables. Attempting to insert data that violates the specified constraints should fail.</li>

 <li>It is not necessary to exactly recreate the <strong>PUBLIC_ARE_FRIENDS </strong>table since it is not guaranteed that for every (x,y) row entry, there is a corresponding (y,x) entry. For the <strong>VIEW_ARE_FRIENDS</strong>, the requirement is that for every (x,y) entry in the public dataset, it either has a (x,y) or (y,x) entry, but not both. For example, if the public dataset has both (2,7) and (7,2), your view should contain only (2,7) or (7,2).</li>

</ol>


