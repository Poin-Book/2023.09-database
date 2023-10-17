# JDBC Programming

> 작성자: 최선규

## Connection

[Open]

- `java.sql.Connection` 인터페이스를 구현한 클래스의 인스턴스를 생성한다.
- `java.sql.DriverManager` 클래스의 `getConnection()` 메소드를 이용한다.

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

class ConnectionTest {
    public static void main(String[] args) {
        Connection conn = null;
        try {
            Class.forName("com.mysql.jdbc.Driver");
            String url = "jdbc:mysql://localhost:3306/mysql?serverTimezone=UTC&useSSL=false";
            String user = "root", password = "12345";

            con = DriverManager.getConnection(url, user, password);
            System.out.println("Connected");
        } catch(ClassNotFoundException e){
            system.out.println("ClassNotFoundException: " + e.getMessage());
        } catch (SQLException e) {
            System.out.println("SQLException: " + e.getMessage());
        }
    }
}
```

[Close]

- con.close()를 이용하여 연결을 종료한다.

```java
class ConnectionTest {
    public static void main(String[] arg) {
      // DB connection
      ...

      // DB operation
      ...

      // DB close
      try {
        if (con != null && !con.isClosed()) con.close();
      } catch (SQLException e) {
        System.out.println("SQLException: " + e.getMessage());
      }
    }
}
```

## DB Operation

[Statement]

- `java.sql.Statement` 인터페이스를 구현한 클래스의 인스턴스를 생성한다.
- `java.sql.Connection` 인터페이스의 `createStatement()` 메소드를 이용한다.

```java
// DB update
Statement stmt = null;
try {
    stmt = con.createStatement();
    String update = "update instructor set salary = salary * 1.1 where dept_name=comp. sci'"; int count = stmt.executeUpdate(update);
    System.out.println(count);  
} catch (SQLException e) {
    System.out.println("SQLException: " + e.getMessage());
}
```

[Result of a Query]

- `java.sql.ResultSet` 인터페이스를 구현한 클래스의 인스턴스를 생성한다.
- `java.sql.Statement` 인터페이스의 `executeQuery()` 메소드를 이용한다.

```java
// DB query
Statement stmt = null; 
ResultSet rs = null; 
try {
    stmt = con.createStatement(); 
    String sql = "select name, course_id from instructor natural join teaches"; 
    rs = stmt.executeQuery(sql);

    while (rs.next()) { 
        String name = rs.getString(1); 
        if (rs.wasNull()) name = "null"; 
        String course_id = rs.getString(2); 
        if (rs.wasNull()) course_id = "null"; System.out.println(name + "\t" + course_id);
    }
} catch (SQLException e) { 
    System.out.println("SQLException: " + e.getMessage());
} 
```

[Prepared Statement]

- `java.sql.PreparedStatement` 인터페이스를 구현한 클래스의 인스턴스를 생성한다.
- `java.sql.Connection` 인터페이스의 `prepareStatement()` 메소드를 이용한다.

```java
// DB insert
PreparedStatement pstmt = null; 
try {
    String psql = "insert into instructor value (?, ?, ?, ?)"; 
    pstmt = con.prepareStatement(psql);

    String id = "12345", name = "Neumann", dept_name = "Biology"; 
    int salary = 98000; 
    pstmt.setString(1, id); 
    pstmt.setString(2, name); 
    pstmt.setString(3, dept_name); 
    pstmt.setInt(4, salary);

    int count = pstmt.executeUpdate(); 
    System.out.println(count);
} catch (SQLException e) { 
    System.out.println("SQLException: " + e.getMessage());
}
```
