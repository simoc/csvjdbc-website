##Introduction

CsvJdbc is a read-only JDBC driver that uses Comma Separated Value (CSV) files
or DBF files as database tables. It is ideal for writing data import programs
or analyzing log files.

The driver enables a directory or a ZIP file containing CSV or DBF files to be
accessed as though it were a database containing tables. However, as there is
no real database management system behind the scenes, not all JDBC
functionality is available.

##Usage

The CsvJdbc driver is used just like any other JDBC driver:

1. download `csvjdbc.jar` and add it to the Java CLASSPATH.
2. load the driver class, (its full name is `org.relique.jdbc.csv.CsvDriver`)
3. use `DriverManager` to connect to the database (the directory or ZIP file)
4. create a statement object
5. use the statement object to execute an SQL SELECT query
6. the result of the query is a `ResultSet`

The following example puts the above steps into practice.

    import java.sql.*;
    import org.relique.jdbc.csv.CsvDriver;

    public class DemoDriver
    {
      public static void main(String[] args)
      {
        try
        {
          // Load the driver.
          Class.forName("org.relique.jdbc.csv.CsvDriver");
    
          // Create a connection. The first command line parameter is
          // the directory containing the .csv files.
          // A single connection is thread-safe for use by several threads.
          Connection conn = DriverManager.getConnection("jdbc:relique:csv:" + args[0]);
    
          // Create a Statement object to execute the query with.
          // A Statement is not thread-safe.
          Statement stmt = conn.createStatement();
    
          // Select the ID and NAME columns from sample.csv
          ResultSet results = stmt.executeQuery("SELECT ID,NAME FROM sample");
    
          // Dump out the results to a CSV file with the same format
          // using CsvJdbc helper function
          boolean append = true;
          CsvDriver.writeToCsv(results, System.out, append);
    
          // Clean up
          conn.close();
        }
        catch(Exception e)
        {
          e.printStackTrace();
        }
      }
    }

