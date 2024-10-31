## Java Servlet Technology

- **Definition**: Java Servlets are server-side Java programs that handle HTTP requests and generate dynamic responses.
- **Java EE Component**: Part of Java EE for building web applications.
- **Request-Response Model**: Works within a web server to process client requests.
- **HTTP Support**: Built-in support for handling HTTP protocols.
- **Example**: `@WebServlet("/example") public class ExampleServlet extends HttpServlet { ... }`.

## What Is a Servlet?

- **Purpose**: Servlets extend the server's capabilities by handling client requests and generating responses.
- **Servlet API**: Part of the `javax.servlet` package.
- **Request Processing**: Works within a server to process HTTP requests and return responses.
- **Platform Independence**: Runs on any server that supports Java Servlets.
- **Example**: `public class MyServlet extends HttpServlet { ... }`.

## Servlet Lifecycle

- **Lifecycle Methods**: `init`, `service`, and `destroy`.
- **Initialization**: `init` method for initializing resources.
- **Service**: `service` method to handle requests and generate responses.
- **Destruction**: `destroy` method called before servlet is removed.
- **Example**: `public void init() { ... } public void destroy() { ... }`.

## Handling Servlet Lifecycle Events

- **Listeners**: Classes that listen to servlet lifecycle events.
- **Types of Events**: Context, session, and request lifecycle events.
- **Example Events**: `contextInitialized`, `sessionCreated`, and `requestDestroyed`.
- **Event Handling**: Implements listener interfaces like `ServletContextListener`.
- **Example**: `public class MyContextListener implements ServletContextListener { ... }`.

## Defining the Listener Class

- **Purpose**: Listens for specific events in the servlet lifecycle.
- **Implementation**: Implements interfaces like `ServletContextListener`, `HttpSessionListener`.
- **Annotations**: Annotate with `@WebListener` to define a listener.
- **Example Methods**: `contextInitialized`, `contextDestroyed`.
- **Example**: `@WebListener public class MyListener implements ServletContextListener { ... }`.

## Handling Servlet Errors

- **Error Handling**: Configure custom error pages in `web.xml`.
- **Exception Types**: Handle exceptions and error codes.
- **Error Page Mapping**: Map specific errors to custom pages.
- **Logging**: Log errors for debugging and tracking.
- **Example**: `<error-page><exception-type>java.lang.Exception</exception-type><location>/errorPage.jsp</location></error-page>`.

## Sharing Information

- **Shared Resources**: Use `ServletContext` to share information across servlets.
- **Scope Objects**: Share data with request, session, and application scopes.
- **Attribute Setting**: Use `setAttribute` and `getAttribute` methods.
- **Thread Safety**: Handle concurrent access for shared data.
- **Example**: `getServletContext().setAttribute("sharedData", data);`.

## Using Scope Objects

- **Scope Levels**: Request, session, and application scopes.
- **Request Scope**: Lives for a single request.
- **Session Scope**: Lasts for the user’s session.
- **Application Scope**: Shared across the entire application.
- **Example**: `request.setAttribute("name", "value");`.

## Controlling Concurrent Access to Shared Resources

- **Synchronization**: Use `synchronized` blocks to control access to shared data.
- **Thread Safety**: Prevents concurrent modification issues.
- **Scope Consideration**: Especially important for session and application scope.
- **ServletContext Locking**: Control access to application-wide resources.
- **Example**: `synchronized(getServletContext()) { ... }`.

## Creating and Initializing a Servlet

- **Servlet Declaration**: Extend `HttpServlet` and override lifecycle methods.
- **Initialization Parameters**: Define parameters in `web.xml` or annotations.
- **Context Initialization**: Use `init` to set up resources.
- **Example Annotation**: `@WebServlet("/myServlet")`.
- **Example**: `public void init() { ... }`.

## Writing Service Methods

- **Service Method**: Override `doGet`, `doPost`, `doPut`, etc., to handle requests.
- **HttpServletRequest and HttpServletResponse**: Used to handle client requests and responses.
- **Method Specific**: Each method corresponds to an HTTP method (GET, POST).
- **Example**: `protected void doGet(HttpServletRequest request, HttpServletResponse response) { ... }`.
- **Error Handling**: Include error handling within service methods.

## Getting Information from Requests

- **Request Parameters**: Retrieve with `getParameter`, `getParameterValues`.
- **Headers and Attributes**: Access headers with `getHeader` and attributes with `getAttribute`.
- **Request URI**: Use `getRequestURI` for the request path.
- **Example**: `String param = request.getParameter("paramName");`.
- **Form Data**: Supports reading form data sent from the client.

## Constructing Responses

- **Response Object**: Use `HttpServletResponse` to construct responses.
- **Setting Content Type**: Use `setContentType` to define the response MIME type.
- **Writing Output**: Get `PrintWriter` or `OutputStream` to write response.
- **Setting Status Codes**: Use `setStatus` for HTTP status codes.
- **Example**: `response.setContentType("text/html"); PrintWriter out = response.getWriter();`.

## Filtering Requests and Responses

- **Filters**: Intercept requests and responses to modify or inspect them.
- **Filter Interface**: Implement `Filter` interface with `doFilter` method.
- **Chaining**: Call `chain.doFilter` to pass request/response to the next filter.
- **Configuration**: Define filters in `web.xml` or annotations.
- **Example**: `@WebFilter("/*") public class MyFilter implements Filter { ... }`.

## Programming Filters

- **Purpose**: Perform tasks like authentication, logging, and data compression.
- **Filter Chain**: Multiple filters can be chained together.
- **Filter Lifecycle**: `init`, `doFilter`, `destroy` methods.
- **Example**: `public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain) { ... }`.
- **Annotations**: Use `@WebFilter` for easy configuration.

## Programming Customized Requests and Responses

- **Custom Wrappers**: Extend `HttpServletRequestWrapper` and `HttpServletResponseWrapper`.
- **Modifying Behavior**: Override methods to add custom processing.
- **Use Cases**: Useful for customizing request parameters or response headers.
- **Example**: `public class MyRequestWrapper extends HttpServletRequestWrapper { ... }`.
- **Custom Filter**: Often used in filters for advanced request/response handling.

## Specifying Filter Mappings

- **Mapping Filters**: Define URL patterns or servlets for filter application.
- **Annotations or XML**: Use `@WebFilter` or `web.xml` for configuration.
- **Order of Filters**: Specify order if multiple filters are applied.
- **Example**: `<filter-mapping><filter-name>myFilter</filter-name><url-pattern>/*</url-pattern></filter-mapping>`.
- **Annotation Example**: `@WebFilter("/secured/*")`.

## To Specify Filter Mappings Using NetBeans IDE

- **Step 1**: Open Project and navigate to `web.xml`.
- **Step 2**: Add `<filter>` and `<filter-mapping>` elements for filter configuration.
- **Step 3**: Specify filter name and URL pattern.
- **Step 4**: Save and redeploy application.
- **Example**: Configure filters directly in NetBeans using graphical editor.

## Invoking Other Web Resources

- **RequestDispatcher**: Use to forward or include other resources.
- **Forwarding**: Transfers control to another servlet or JSP.
- **Including Resources**: Insert content from another resource in the response.
- **Methods**: `forward` and `include`.
- **Example**: `RequestDispatcher rd = request.getRequestDispatcher("otherResource"); rd.forward(request, response);`.

## Including Other Resources in the Response

- **Including**: Add content from another resource into the response.
- **RequestDispatcher**: Use `include` method to include content.
- **Dynamic Responses**: Useful for inserting dynamic content.
- **Example**: `RequestDispatcher rd = request.getRequestDispatcher("/header.jsp"); rd.include(request, response);`.

## Transferring Control to Another Web Component

- **Forwarding**: Use `RequestDispatcher` to pass control.
- **Control Flow**: Original servlet relinquishes control to the target component.
- **Example Use**: Forward requests for specific tasks like login verification.
- **Example**: `RequestDispatcher rd = request.getRequestDispatcher("/welcome.jsp"); rd.forward(request, response);`.

## Accessing the Web Context

- **ServletContext**: Access shared application data.
- **Context Parameters**: Retrieve global parameters with `getInitParameter`.
- **Attribute Storage**: Store shared attributes across servlets.
- **Example**: `getServletContext().getInitParameter("paramName");`.
- **Usage**: Useful for application-wide resources.

## Maintaining Client State

- **Session Tracking**: Use sessions to track user state across requests.
- **Techniques**: Cookies, URL rewriting, and HTTPSession.
- **State Management**: Store user-specific data.
- **Example**: `HttpSession session = request.getSession();`.
- **Persistence**: Ensures data availability between user requests.

## Accessing a Session

- **Session Creation**: `getSession` method to retrieve or create a session.
- **Session ID**: Unique identifier for each session.
- **Timeout**: Sessions can expire after inactivity.
- **Example**: `HttpSession session = request.getSession(true);`.
- **Use Case**: Ideal for user login and shopping cart functionality.

## Associating Objects with a Session

- **Storing Attributes**: Use `setAttribute` to associate objects with session.
- **Retrieving Attributes**: Use `getAttribute` to retrieve session data.
- **Session Persistence**: Attributes persist across multiple requests.
- **Example**: `session.setAttribute("username", "John");`.
- **Data Sharing**: Useful for user preferences and shopping cart.

## Session Management

- **Session Timeout**: Define session expiry time in `web.xml` or programmatically.
- **Invalidation**: Use `session.invalidate` to terminate a session.
- **Session ID**: Server assigns a unique ID to each session.
- **Example**: `session.setMaxInactiveInterval(600);`.
- **Best Practice**: Handle session expiration to prevent data leaks.

## To Set the Timeout Period Using NetBeans IDE

- **Step 1**: Open `web.xml` in NetBeans.
- **Step 2**: Locate `<session-config>` and add `<session-timeout>` element.
- **Step 3**: Specify timeout duration in minutes.
- **Example**: `<session-config><session-timeout>30</session-timeout></session-config>`.
- **Result**: Session expires after specified timeout.

## Session Tracking

- **Tracking Methods**: Cookies, URL rewriting, SSL sessions.
- **URL Rewriting**: Append session ID to URLs for session tracking.
- **Fallback Mechanism**: URL rewriting if cookies are disabled.
- **Example**: `response.encodeURL("nextPage.jsp");`.
- **Use Case**: Maintain state even without cookies.

## Finalizing a Servlet

- **Destroy Method**: `destroy` method for cleanup before servlet is unloaded.
- **Resource Release**: Close resources like database connections.
- **Lifecycle End**: Called when server removes the servlet.
- **Example**: `public void destroy() { ... }`.
- **Best Practice**: Ensure all resources are properly closed.

## Tracking Service Requests

- **Request Counting**: Track the number of requests serviced by the servlet.
- **Thread Safety**: Use synchronization for counters.
- **Use Case**: Useful in monitoring traffic or usage metrics.
- **Example**: `private int requestCount = 0; synchronized(this) { requestCount++; }`.
- **Data Collection**: Common for analytics.

## Notifying Methods to Shut Down

- **Shutdown Notifications**: Notify long-running methods when a servlet is unloaded.
- **Interruption Handling**: Interrupt threads or release resources.
- **Usage**: Important for servlets with background processing.
- **Example**: Implement cleanup in `destroy` method.
- **Graceful Shutdown**: Ensures resources are freed.

## Creating Polite Long-Running Methods

- **Interruptible Threads**: Use `Thread.interrupt` for thread management.
- **Monitoring Status**: Check servlet state regularly in long-running tasks.
- **Example Usage**: Long-running processes like data processing tasks.
- **Best Practice**: Make long-running methods responsive to shutdown.
- **Example**: `if (Thread.currentThread().isInterrupted()) return;`.

## The mood Example Application

- **Purpose**: Demonstrates servlet functionality through a sample application.
- **Components**: Includes servlets, JSPs, and listeners.
- **Example Features**: Session management, request handling.
- **Educational Value**: Showcases Java EE features.
- **Best Practice**: Use as a reference for servlet applications.

## Components of the mood Example Application

- **Servlets**: Core logic for handling user interactions.
- **JSPs**: Generate HTML content for user interface.
- **Listeners**: Track and manage session and context events.
- **Filters**: Handle pre-processing of requests and responses.
- **Example**: `MoodServlet`, `MoodFilter`, and `MoodListener`.

## Running the mood Example

- **Deployment**: Deploy on a servlet container like Apache Tomcat.
- **Configuration**: Configure `web.xml` for servlet and listener mapping.
- **Session Management**: Tracks user session across requests.
- **Logging**: Logs user interactions for tracking.
- **Example**: `http://localhost:8080/moodApp`.

## To Run the mood Example Using NetBeans IDE

- **Step 1**: Open the project in NetBeans.
- **Step 2**: Configure project properties if needed.
- **Step 3**: Deploy the application using NetBeans Run option.
- **Step 4**: Access the application via local server URL.
- **Example URL**: `http://localhost:8080/moodApp`.

## To Run the mood Example Using Ant

- **Step 1**: Open a command prompt or terminal.
- **Step 2**: Navigate to the project directory.
- **Step 3**: Run `ant` build file using `ant deploy`.
- **Step 4**: Access the application via configured server URL.
- **Example Command**: `ant deploy`.

## Uploading Files with Java Servlet Technology

- **Purpose**: Allows users to upload files to the server through servlets.
- **Multipart Requests**: Use multipart encoding to handle file data in HTTP requests.
- **Servlet Requirements**: Use `@MultipartConfig` annotation to handle file uploads.
- **Methods**: Access uploaded files with `getPart` and `getParts` methods.
- **Example**: `@MultipartConfig public class FileUploadServlet extends HttpServlet { ... }`.

## The @MultipartConfig Annotation

- **Purpose**: Specifies settings for file upload handling in servlets.
- **Attributes**: `location`, `maxFileSize`, `maxRequestSize`, and `fileSizeThreshold`.
- **File Size Limits**: Control upload limits to avoid oversized files.
- **Location**: Specifies temporary file storage directory.
- **Example**: `@MultipartConfig(location="/tmp", maxFileSize=1048576, maxRequestSize=2097152)`.

## The getParts and getPart Methods

- **getParts Method**: Retrieves all parts of a multipart request as a collection.
- **getPart Method**: Retrieves a specific file part by name.
- **File Handling**: Use `Part.write` to save the file to a specified path.
- **Error Handling**: Catch `IOException` and `ServletException` for file processing.
- **Example**: `Part filePart = request.getPart("file"); filePart.write("uploads/" + fileName);`.

## The fileupload Example Application

- **Purpose**: Demonstrates how to implement file upload in a servlet application.
- **Core Components**: Servlet for handling uploads, JSPs for UI, and utility classes.
- **Multipart Request Handling**: Uses `@MultipartConfig` and `getPart` methods.
- **User Interface**: Provides a simple form to select and upload files.
- **Example**: `FileUploadServlet` handles file saving and feedback to the user.

## Architecture of the fileupload Example Application

- **Components**: Includes servlet, JSP pages, and configuration files.
- **Servlet**: Handles the logic for receiving and saving uploaded files.
- **JSP**: Provides the form for users to select files to upload.
- **Directory Structure**: Organizes files into logical folders (e.g., `/uploads` for storage).
- **Configuration**: Uses `web.xml` for servlet and upload settings.

## Running the fileupload Example

- **Deployment**: Deploy on a servlet container like Apache Tomcat or GlassFish.
- **File Storage**: Configure storage location for uploaded files in `@MultipartConfig`.
- **Accessing the Application**: Open the URL where the application is deployed.
- **Testing**: Upload various files to confirm correct handling.
- **Example URL**: `http://localhost:8080/fileuploadApp`.

## To Build, Package, and Deploy the fileupload Example Using NetBeans IDE

- **Step 1**: Open the fileupload project in NetBeans.
- **Step 2**: Configure project properties for servlet version and context path.
- **Step 3**: Use NetBeans' "Run" option to deploy the application.
- **Step 4**: Access the application on the local server.
- **Example URL**: `http://localhost:8080/fileuploadApp`.

## To Build, Package, and Deploy the fileupload Example Using Ant

- **Step 1**: Open a terminal or command prompt.
- **Step 2**: Navigate to the fileupload project directory.
- **Step 3**: Run `ant` with the target `deploy` or `build` for packaging.
- **Step 4**: Deploy the generated WAR file to a servlet container.
- **Example Command**: `ant deploy`.

## To Run the fileupload Example

- **Step 1**: Deploy the application using NetBeans or Ant.
- **Step 2**: Open a browser and navigate to the application URL.
- **Step 3**: Use the upload form to select and upload a file.
- **Step 4**: Verify that the file is saved in the specified directory.
- **Example**: Access the upload form at `http://localhost:8080/fileuploadApp/upload.jsp`.
