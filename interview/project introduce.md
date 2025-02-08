In my previous role as a technical project manager, I led a team of about 10 members in developing a project named "Tencent HR Assistant". First, I'd like to discuss the project's background. At Tencent, the human - resource management platform had been in existence for over a decade, and the features within the company were well - developed. In 2021, the company decided that this system was mature enough to be launched in the market. Given my familiarity with the human - resource platform, I was tasked with developing this project into a SaaS (Software - as - a - Service) platform and taking it to market.

  

The platform's features were reliable, but the major challenge we faced was data isolation for different clients (talents/companies). There were several methods considered for data isolation:

  

The first approach was to add a column in the table. For instance, different clients would have different values in this column. Based on these values, we could identify which data belonged to which client. However, we didn't adopt this method. The reason was that it wasn't secure for data as all companies would be using the same table. Moreover, if all data was stored in the same table, it would grow extremely large, making it difficult to maintain in the long run.

  

The second approach was to use independent databases for isolation. This meant that each client would have its own database. Although this made data isolation straightforward and was relatively easy to develop, it was too costly. Hence, we didn't choose this option either.

  

Ultimately, we used the third approach to solve the data - isolation problem: schema isolation. In this method, within the same database, we could create several schemas. Each client could use a different schema to store their data. This approach ensured data security, prevented the table from becoming overly large, and was less expensive compared to using independent databases.

  

However, the tricky part was figuring out how to effectively isolate the schemas.



We sourced some information from the internet to isolate the schema. Our system caters to numerous talents, and the first problem we had to address was how to expand our database dynamically. 


For example, if a single database could only accommodate around 500 talents, and we needed to increase this capacity, here's the approach we took. 


We utilized a main database to store details of different talents in JDBC (Java Database Connectivity). When a new talent was added, a script would run on our machine. This script would send a message to our system, ensuring that the talent was assigned its own database with details such as an IP address, JDBC - related password, and user information.


This process was initiated in the main space. If the existing database ran out of space to store additional schemas, we would simply create a new database and set up a new schema. We would then transfer the relevant data from the main database to the new database for each talent, enabling them to have their own data storage.


This setup ensured that even if we had a large number of talents or users, all we had to do was add more machines. There was no need to write extra code for this scaling operation. As a result, when we launched our system, within 72 hours, the number of users reached 100,000.