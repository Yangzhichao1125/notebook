We also ran into some problems related to high concurrency. For example, I was in charge of developing the attendance module. In this module, we faced a major challenge because there were numerous companies and a large number of employees. In almost all the companies, employees are required to clock in before 9:00 a.m. So, during the half - hour period from 8:30 to 9:00 a.m., our service receives a huge number of requests. We tackled this high - concurrency issue from several aspects.

### Front - end Optimization

First, we moved CSS, JavaScript files, and pictures to the CDN (Content Delivery Network). When clients visit the page, they can retrieve data from the CDN, which reduces the load on the backend. Additionally, we set it so that the submit button can only be clicked once within 3 seconds. If a client clicks the button multiple times within one second, it would put a great deal of pressure on the backend.

### Back - end Optimization

1. **Load Balancing**: We ensured effective load balancing. Based on the capabilities of different machines, we could dynamically determine how many requests each machine should handle.
2. **Message Queue**: We introduced a message queue to handle a large number of requests. When a request reaches the backend, we send a message to the queue to handle the problem and then send a response back to the client to indicate that the request has been successfully received. We have another interface to handle the attendance processing later.
3. **Redis Cache**: We used Redis as a cache. When querying data, we can directly retrieve it from Redis, which alleviates the pressure on the database.
4. **Database Optimization**: When dealing with high - concurrency scenarios, we made sure to simplify database operations. We avoided using multiple tables and join operations simultaneously, as this would place a heavy burden on the database. Instead, we used a single table for the situation. Moreover, we added appropriate indexes. Proper indexes can make database queries and updates more efficient.

That's how we addressed the high - concurrency problem.