<div align="center">

## DirectDB Direct Connection with Database in Java


</div>

### Description

(Please Vote Me) Make Direct Database Connection in Java without any DSN. Just give your Access .mdb Database file path and start using Database.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Faisal Basra](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/faisal-basra.md)
**Level**          |Advanced
**User Rating**    |3.7 (22 globes from 6 users)
**Compatibility**  |Java \(JDK 1\.1\), Java \(JDK 1\.2\), Java \(JDK 1\.3\), Java \(JDK 1\.4\), Java \(JDK 1\.5\)
**Category**       |[Databases/ JDBC](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/databases-jdbc__2-61.md)
**World**          |[Java](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/java.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/faisal-basra-directdb-direct-connection-with-database-in-java__2-5482/archive/master.zip)





### Source Code

```
import java.sql.*;
public class DirectDB{
	public static void main(String args[]){
		System.out.println("Starting");
		try{
			Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
			// set this to a MS Access DB you have on your machine
			String filename = "z:/sis.mdb";
			String database = "jdbc:odbc:Driver={Microsoft Access Driver (*.mdb)};DBQ=";
			database+= filename.trim() + ";DriverID=22;READONLY=true}"; // add on to the end
			// now we can get the connection from the DriverManager
			Connection con = DriverManager.getConnection( database ,"","");
			 // try and create a java.sql.Statement so we can run queries
			 Statement s = con.createStatement();
			 s.execute("create table profile ( userid integer )"); // create a table
			 s.execute("insert into profile values(1)"); // insert some data into the table
			 s.execute("select column_name from profile"); // select the data from the table
			 ResultSet rs = s.getResultSet(); // get any ResultSet that came from our query
			 if (rs != null) // if rs == null, then there is no ResultSet to view
			 while ( rs.next() ) // this will step through our data row-by-row
			  {
			  /* the next line will get the first column in our current row's ResultSet
			  as a String ( getString( columnNumber) ) and output it to the screen */
			  System.out.println("Data from column_name: " + rs.getString(1) );
			 }
			 //s.execute("drop table profile");
			 s.close(); // close the Statement to let the database know we're done with it
 con.close(); // close the Connection to let the database know we're done with it
			}
		catch(Exception ex){
			System.out.println(ex.getMessage());
			}
		}
	}
```

