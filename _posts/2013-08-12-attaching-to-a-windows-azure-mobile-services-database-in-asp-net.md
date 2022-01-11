The preferred way to talk to the database you are using for you Windows Azure Mobile Services is through the REST APIs and by using the Clients we supply for you.&#160; The reason you should go through the REST APIs is to ensure you are hitting the Scripts you defined in your Mobile Service.&#160; I had a case where someone wanted to directly connect to the SQL Azure database in the backend to list data in a grid view.&#160; The call would fail with this error: “invalid object name‘tablename’" where ‘tablename’ was the name of the table in the SQL Azure database.

The fix was very simple if you understand how database tables are created for Mobile Services.&#160;&#160; Have you ever wondered for instance how you can have several Mobile Services with ‘TodoItem’ tables in them and they are all hosted in the same SQL Azure database?&#160; The reason this works is because we use the schema property of the database to scope the table to the Mobile Service.&#160; If I have two mobile services ‘JeffMobileFirst’ and ‘JeffMobileSecond’ both with a ‘TodoItem’ table and look in the SQL Azure database you will see tables ‘JeffMobileFirst.TodoItem’ and ‘JeffMobileSecond.TodoItem’.&#160; To access the database table of either simple ensure you include the schema along with the table name.&#160; For example: 

string sql = "select * from <font style="background-color: rgb(255, 255, 0);">JeffMobileFirst</font>.TodoItem";

SqlConnection connection = new SqlConnection(@"Server=tcp:x0etablf0pp.database.windows.net,1433;Database=jsanders_db;User <ID=dbadmin@x0etablf0pp;Password=mypassword;Trusted_Connection=False;Encrypt=True;Connection> Timeout=30;");

&#160;

Let me know if this helped you!