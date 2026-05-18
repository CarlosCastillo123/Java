# Database
## Code
``` java
import java.sql.*;
public class Database {
    public static void main(String[] args)
        throws SQLException, ClassNotFoundException {
        Class.forName("com.mysql.cj.jdbc.Driver");
        System.out.println("Driver loaded");
        Connection connection = DriverManager.getConnection
                ("jdbc:mysql://localhost/Miramar","testuser","Pa$$word");
        System.out.println("Database connected");
        Statement statement = connection.createStatement();
         ResultSet resultSet = statement.executeQuery
                ("select * from Student;");
       while (resultSet.next())
            System.out.println(resultSet.getString(1) + "\t" +
                    resultSet.getString(2) + "\t" + resultSet.getString(3) + "\t" +
                    resultSet.getString(4) + "\t" + resultSet.getString(5)+"\t" +
                    resultSet.getString(6) + "\t" + resultSet.getString(7) + "\t" +
                    resultSet.getString(8) + "\t" + resultSet.getString(9));


        int rowUpdate = statement.executeUpdate
                ("update Student set zipCode = '92126'" +
                        "where ssn = '111222333';");
        System.out.println("Rows updated: " + rowUpdate);
        ResultSet resultSet2 = statement.executeQuery
                ("select * from Student;");
        while (resultSet2.next())
            System.out.println(resultSet2.getString(1) + "\t" +
                    resultSet2.getString(2) + "\t" + resultSet2.getString(3) + "\t" +
                    resultSet2.getString(4) + "\t" + resultSet2.getString(5)+"\t" +
                    resultSet2.getString(6) + "\t" + resultSet2.getString(7) + "\t" +
                    resultSet2.getString(8) + "\t" + resultSet2.getString(9));

        connection.close();
    }
}
```
## Results
<img width="1016" height="291" alt="Screenshot 2026-05-17 203644" src="https://github.com/user-attachments/assets/a989856e-03e3-46dc-9f93-3885ba3ab11c" />
