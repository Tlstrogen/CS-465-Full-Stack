**Compare and contrast the types of frontend development you used in your full stack project, including Express HTML, JavaScript, and the single-page application (SPA).**
In the Travlr Getaways project, I used two main types of frontend development: an Express website and an Angular single-page application. Both displayed information to users, but they worked differently.

The Express website was the customer-facing side of the project. It used HTML and Handlebars templates to create pages for travel, meals, rooms, news, and other information. When a customer selected a different page, the browser asked the Express server to build that page. The server combined the template with the correct information and sent the completed HTML back to the browser. In simple terms, the server built a new page each time the customer moved around the website.

JavaScript made the website work behind the scenes. It controlled the routes, retrieved trip information through the API, and sent that information to the correct page. For example, when a customer opened the travel page, JavaScript requested the available trips and gave them to the Handlebars template. The template then placed each trip’s name, image, price, and description on the page.

The Angular single-page application, or SPA, was used for the administrative side of the project. It worked differently because the browser loaded the main application only once. When an administrator moved between the trip list, add-trip form, and edit-trip form, Angular replaced only the part of the screen that needed to change. It did not request an entirely new webpage each time.

Even though the two frontends worked differently, they shared the same API and MongoDB database. Express presented the information to customers, while Angular gave administrators an interactive way to manage it. Together, they showed how one full-stack application can provide different experiences for different types of users.



**Why did the backend use a NoSQL MongoDB database?**

The backend used MongoDB because it is a document-based database. Instead of storing information across rows and columns in several tables, MongoDB stores each trip as a single document. A trip document can contain its code, name, resort, length, start date, price, image, and description in one place.

This structure provides flexibility. If the application later needs to store something new, such as a list of activities or available room types, that information can be added without rebuilding an entire set of database tables. MongoDB can handle documents with slightly different information, which makes it easier for the application to grow and change.

MongoDB also works naturally with JavaScript because its documents resemble JavaScript objects. The trip data could move from MongoDB to the API and then to the Express or Angular frontend without being completely reorganized at every step. Mongoose still provided a schema so the application could check that important fields were stored correctly.

MongoDB worked well because each trip could be treated like one complete information card. The application could retrieve that card, send it through the API, and display it to the user. This made the database flexible while keeping the trip data easy to understand and manage.


**How is JSON different from Javascript and how does JSON tie together the frontend and backend development pieces?**

JavaScript is a programming language that performs actions and controls application logic, while JSON is a text format used to organize and exchange data. JSON ties the frontend and backend together by allowing the backend API to send trip information in a format that the Angular or Express frontend can easily read and display.



**Provide instances in the full stack process when you refactored code to improve functionality and efficiencies, and name the benefits that come from reusable user interface (UI) components.**

During the Travlr Getaways project, I refactored the original static HTML pages into Handlebars templates. Instead of copying the same navigation bar and footer into the home, travel, meals, rooms, and contact pages, I moved them into reusable header and footer partials. I also changed the travel page from reading hardcoded trip information to requesting current trip data from the /api/trips endpoint. This allowed the Express controller to retrieve trip records from MongoDB and pass them to travel.hbs, so the page could automatically display every available trip.

I also created reusable components and services in the Angular administrative application. The TripCardComponent displayed each trip in the TripListingComponent, which meant I did not need to rewrite the card layout for every trip. I placed API calls such as getTrips(), addTrip(), getTrip(), and updateTrip() inside the TripDataService so the add, edit, and listing components could share the same data-access code. These reusable parts reduced duplicate code, kept the interface consistent, made errors easier to fix, and allowed one change to improve every part of the application that used them.

Methods for request and retrieval necessitate various types of API testing of endpoints, in addition to the difficulties of testing with added layers of security. Explain your understanding of methods, endpoints, and security in a full stack application.

In the Travlr Getaways project, I used Postman to test the methods and endpoints of the REST API. A method describes the action being requested, while an endpoint identifies where the request should go. For example, I tested GET /api/trips to retrieve all trips, GET /api/trips/:tripCode to retrieve one trip, POST /api/trips to create a trip, and PUT /api/trips/:tripCode to update one. Postman allowed me to send each request, provide JSON data when needed, and check the returned status code and response.

Security added another step to API testing. The application used authentication and JSON Web Tokens to prevent unauthorized users from changing trip information. I first tested the registration or login endpoint to receive a token. I could then include that token with protected Postman requests. Testing both valid and missing or invalid tokens helped confirm that authorized administrators could make changes while unauthorized users were rejected.


**How has this course helped you in reaching your professional goals? What skills have you learned, developed, or mastered in this course to help you become a more marketable candidate in your career field?**

This course has helped me reach my professional goals by giving me a stronger understanding of HTML, JavaScript, Express, Angular, and the deployment of a full MEAN-stack application. Before completing this project, I understood many of these technologies separately. Building Travlr Getaways showed me how MongoDB, Express, Angular, and Node.js work together as one application. I gained experience creating user interfaces, building REST API endpoints, connecting an application to a database, and adding authentication with JSON Web Tokens.

These skills make me a more marketable candidate because employers need developers who understand the entire path that data takes through an application. I can now explain how information moves from MongoDB through an API to the frontend, as well as how users can securely create or update that information. The project also strengthened my debugging, testing, Git, and problem-solving skills. Most importantly, I now have a completed full-stack project that demonstrates my ability to build both customer-facing and administrative applications instead of only describing those skills on a résumé.
