## JDBC Basics

- **Purpose**: Java Database Connectivity (JDBC) is an API for connecting and executing queries on databases.
- **Core Interfaces**: `DriverManager`, `Connection`, `Statement`, `ResultSet`.
- **Database Independence**: JDBC provides a standard API for different databases.
- **Database Operations**: Supports CRUD (Create, Read, Update, Delete) operations.
- **Example**: `Connection conn = DriverManager.getConnection("jdbc:url", "user", "password");`.

## Getting Started

- **JDBC Driver**: Load the database driver to establish a connection.
- **DriverManager**: Manages database connections.
- **Basic Steps**: Load driver, establish connection, execute SQL, close connection.
- **Driver Loading**: Use `Class.forName("driverName")` or `DriverManager`.
- **Example**: `Class.forName("com.mysql.cj.jdbc.Driver");`.

## Processing SQL Statements with JDBC

- **Statement Execution**: Use `Statement` and `PreparedStatement` for SQL queries.
- **Execute Methods**: `executeQuery`, `executeUpdate`, `execute`.
- **ResultSet**: Process data returned from queries.
- **SQL Injection Prevention**: Use `PreparedStatement` to secure queries.
- **Example**: `Statement stmt = conn.createStatement(); ResultSet rs = stmt.executeQuery("SELECT * FROM table");`.

## Establishing a Connection

- **DriverManager**: Connect to the database using `DriverManager.getConnection`.
- **Connection URL**: Format - `jdbc:<subprotocol>://<host>:<port>/<database>`.
- **Connection Object**: Represents an active connection to the database.
- **Error Handling**: Use `try-catch` for SQL exceptions.
- **Example**: `Connection conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/db", "user", "password");`.

## Connecting with DataSource Objects

- **DataSource Interface**: Provides a connection factory alternative to `DriverManager`.
- **Connection Pooling**: Often used with DataSource for efficient resource use.
- **JNDI Lookup**: DataSources can be bound in a JNDI registry for easy access.
- **Configuration**: Configure database properties in application server.
- **Example**: `DataSource ds = (DataSource) ctx.lookup("jdbc/MyDataSource"); Connection conn = ds.getConnection();`.

## Handling SQLExceptions

- **SQLException Class**: Catches database errors.
- **Error Codes**: Each exception contains an error code and SQL state.
- **Looping Through Exceptions**: Use `getNextException` to iterate through chained exceptions.
- **Logging Errors**: Record exceptions for debugging.
- **Example**: `catch (SQLException ex) { System.out.println("Error: " + ex.getMessage()); }`.

## Setting Up Tables

- **DDL Statements**: Use `CREATE TABLE` with `Statement` to create tables.
- **Execute Update**: `executeUpdate` method for DDL commands.
- **Column Definitions**: Specify column names, types, and constraints.
- **Error Handling**: Handle `SQLException` for table creation issues.
- **Example**: `stmt.executeUpdate("CREATE TABLE students (id INT PRIMARY KEY, name VARCHAR(50));");`.

## Retrieving and Modifying Values from Result Sets

- **ResultSet Navigation**: Use `next`, `previous`, `first`, and `last` for row movement.
- **Get Methods**: Retrieve column values using `getString`, `getInt`, etc.
- **Update Methods**: Use `updateString`, `updateInt` to modify data in `ResultSet`.
- **Commit Changes**: Use `updateRow` to save changes to the database.
- **Example**: `ResultSet rs = stmt.executeQuery("SELECT * FROM students"); rs.next(); String name = rs.getString("name");`.

## Using Prepared Statements

- **PreparedStatement**: Precompiled SQL statements for efficiency and security.
- **Parameter Binding**: Use `setString`, `setInt` to bind parameters in queries.
- **Execute Methods**: `executeQuery`, `executeUpdate`.
- **SQL Injection Prevention**: Secure against injection attacks.
- **Example**: `PreparedStatement pstmt = conn.prepareStatement("SELECT * FROM students WHERE id = ?"); pstmt.setInt(1, 1);`.

## Using Transactions

- **Transaction Control**: Use `commit`, `rollback` for transaction management.
- **Auto-Commit Mode**: Disable auto-commit for transaction grouping.
- **Savepoints**: Set savepoints within a transaction to rollback to specific points.
- **Error Handling**: Rollback on errors to maintain data integrity.
- **Example**: `conn.setAutoCommit(false); conn.commit(); conn.rollback();`.

## Using RowSet Objects

- **RowSet Interface**: Extends `ResultSet`, provides scrollable and updatable capabilities.
- **Types**: `JdbcRowSet`, `CachedRowSet`, `WebRowSet`.
- **Data Disconnected**: Can be used while disconnected from the database.
- **Usage**: Useful in client-side applications for offline data handling.
- **Example**: `RowSet rs = new JdbcRowSetImpl(); rs.setUrl("jdbc:mysql://localhost/db");`.

## Using JdbcRowSet Objects

- **JdbcRowSet**: A connected `RowSet` for real-time data handling.
- **Scrollable and Updatable**: Move cursor in any direction and update data.
- **Auto-Commit**: Changes are automatically committed to the database.
- **Connection Properties**: Set connection details with `setUrl`, `setUsername`.
- **Example**: `JdbcRowSet jrs = new JdbcRowSetImpl(); jrs.setCommand("SELECT * FROM students");`.

## Using CachedRowSet Objects

- **CachedRowSet**: A disconnected, serializable `RowSet`.
- **Data Caching**: Stores data locally for offline processing.
- **Data Synchronization**: Syncs back to the database when reconnected.
- **Pagination**: Suitable for handling large data in chunks.
- **Example**: `CachedRowSet crs = new CachedRowSetImpl(); crs.setCommand("SELECT * FROM students");`.

## Using JoinRowSet Objects

- **JoinRowSet**: Allows joining data from multiple RowSets.
- **Column Matching**: Joins tables based on specified columns.
- **Data Manipulation**: Supports basic CRUD operations on joined data.
- **Offline Joins**: Join data without needing a database connection.
- **Example**: `JoinRowSet jrs = new JoinRowSetImpl(); jrs.addRowSet(rowSet1, "id");`.

## Using FilteredRowSet Objects

- **FilteredRowSet**: A `RowSet` that filters data based on conditions.
- **RowFilter Interface**: Apply custom filters on `RowSet` data.
- **Dynamic Filtering**: Filter criteria can change during runtime.
- **Data Manipulation**: Only rows matching filter criteria are visible.
- **Example**: `FilteredRowSet frs = new FilteredRowSetImpl(); frs.setFilter(new MyFilter());`.

## Using WebRowSet Objects

- **WebRowSet**: A serializable `RowSet` with XML capabilities.
- **Data Sharing**: Can read/write data in XML format for web applications.
- **Interoperability**: Shares data across different systems in XML.
- **Offline Data Manipulation**: Works without a continuous database connection.
- **Example**: `WebRowSet wrs = new WebRowSetImpl(); wrs.writeXml(new FileOutputStream("data.xml"));`.

## Using Advanced Data Types

- **Complex Types**: Supports advanced SQL types like `ARRAY`, `STRUCT`.
- **Retrieval and Insertion**: Methods to handle non-standard data types.
- **Compatibility**: Works with databases supporting custom types.
- **Examples**: `getArray`, `getStruct` for handling arrays and structured data.
- **Example**: `Array arr = rs.getArray("column"); Object[] data = (Object[]) arr.getArray();`.

## Using Large Objects

- **BLOB and CLOB**: Binary Large Object and Character Large Object types.
- **Storage**: Efficiently stores large data like images, text, multimedia.
- **Retrieval Methods**: `getBlob`, `getClob` to retrieve LOBs.
- **Streaming**: Handle LOB data with `InputStream` or `Reader`.
- **Example**: `Blob blob = rs.getBlob("image"); InputStream is = blob.getBinaryStream();`.

## Using SQLXML Objects

- **SQLXML Interface**: Allows XML data handling in SQL.
- **Storing XML**: Insert XML into a database using SQLXML.
- **Retrieving XML**: `getSQLXML` method for reading XML data.
- **Conversion**: Convert XML to `String` or `Reader`.
- **Example**: `SQLXML xml = rs.getSQLXML("xml_column"); String xmlData = xml.getString();`.

## Using Array Objects

- **Array Interface**: Handles SQL arrays from database tables.
- **Retrieving Arrays**: Use `getArray` method from `ResultSet`.
- **Manipulating Arrays**: Convert SQL arrays to Java arrays for processing.
- **Example Usage**: Common in databases supporting array data types.
- **Example**: `Array arr = rs.getArray("array_column"); Object[] javaArray = (Object[]) arr.getArray();`.

## Using DISTINCT Data Type

- **Purpose**: Represents unique data types in SQL.
- **Compatibility**: Works with databases supporting custom distinct types.
- **Usage**: Useful for enforcing unique constraints.
- **Examples**: Retrieve and manage DISTINCT types with `getObject`.
- **Best Practice**: Ensure database support for DISTINCT types.

## Using Structured Objects

- **Structured Types**: Allows storage of complex types like objects.
- **Retrieving Structured Data**: Use `getObject` to retrieve custom structured data.
- **Database Compatibility**: Requires database support for structured types.
- **Example**: Common in applications with nested data structures.
- **Example**: `Struct struct = rs.getStruct("struct_column"); Object[] attributes = struct.getAttributes();`.

## Using Customized Type Mappings

- **Custom Mappings**: Map SQL types to Java objects for complex types.
- **SQLData Interface**: Allows custom data handling for structured types.
- **Mapping Process**: Define mappings in `Connection` for specific types.
- **Example Usage**: Custom types like `Point`, `Circle` in spatial databases.
- **Example**: `conn.setTypeMap(typeMap);`.

## Using Datalink Objects

- **DATALINK Type**: Links SQL fields to external data sources like URLs.
- **Retrieving Data Links**: Use `getURL` to retrieve DATALINK data.
- **Usage**: Useful in applications requiring external data access.
- **Example**: Common in multimedia and web-based applications.
- **Example**: `URL url = rs.getURL("link_column");`.

## Using RowId Objects

- **RowId Interface**: Represents a unique identifier for rows.
- **Primary Key Access**: Efficient access to rows using RowId.
- **Database Dependency**: Supported by databases with RowId implementation.
- **Retrieving RowId**: Use `getRowId` to retrieve row identifiers.
- **Example**: `RowId rowId = rs.getRowId("row_id_column");`.

## Using Stored Procedures

- **CallableStatement**: Interface for executing stored procedures.
- **Syntax**: `{call procedure_name(?, ?...)}` for procedure execution.
- **Input/Output Parameters**: Set with `setInt`, `setString`, retrieve with `getInt`, `getString`.
- **Error Handling**: Catch `SQLException` for stored procedure issues.
- **Example**: `CallableStatement cs = conn.prepareCall("{call getStudents()}");`.

## Using JDBC with GUI API

- **Swing Integration**: Use JDBC with Swing components like `JTable` for data display.
- **Event Handling**: Retrieve and update data in response to GUI events.
- **Data Binding**: Connect data to GUI components for real-time updates.
- **Error Handling**: Display error messages in GUI.
- **Example**: `table.setModel(new DefaultTableModel(data, columnNames));`.
