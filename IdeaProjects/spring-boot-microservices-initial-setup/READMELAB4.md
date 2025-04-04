1.	Why is it important to create separate databases for each microservice (e.g., product_service, order_service, inventory_service)?
	This reduces coupling between the service's, improving data isolation as well as independent scalability. There 

2.	What role does Flyway play in managing the database schema, and how does it ensure consistency across environments?
	Flyway manages the database schema by keeping track of changes between environments and makes sure that changes are applied consistently across them. From my understanding, this is done by versioned migration scripts.
3.	How does Spring Data JPA simplify working with databases in each of the microservices?
	It lets us define our CRUD operations with minimal effort (it was like 1 line)
4.	In the InventoryService, why did we use the @Transactional(readOnly = true) annotation, and what is its significance?
	The annotation marks the method as read-only (crazy) and I imagine reduces some overhead. More importantly, if we are checking for stock there is no reason the method should have to write/ make changes so it makes it safer.

5.	In a microservices architecture, what are some challenges when ensuring communication between the Product, Order, and Inventory Services?
	We need to have consistency between the services to make sure that none of the services do something that conflicts with the others. Part of handling this challenge is making sure there aren't errors that propagate through them. i.e. One of their databases has information that doesn't agree with other(s). We also have to deal with coupling between services as we could have situations such as the order service trying to check inventory, but what if inventory is down?
6.	What are the advantages of using TestContainers for integration testing with MySQL in this lab?
	They effectively allow us to run our test on production, with the benefit's of not actually touching production or having to mock. Nice thing being as well that these containers exist only during the test. This helped maintain isolation and the confidence of the tests.

I will say that I haven't taken DBD yet and only have knowledge from a conceptual standpoint, I was struggling to get this to work at all (only kinda), I'm probably going to have talked to you by the time you read this.
