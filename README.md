# java-cqrs-sample

## When to use it

Like any pattern, CQRS is useful in some places, but not in others. Many systems do fit a CRUD mental model, and so should be done in that style.

The other main benefit is in handling high performance applications. CQRS allows you to separate the load from reads and writes allowing you to scale each independently. If your application sees a big disparity between reads and writes this is very handy. Even without that, you can apply different optimization strategies to the two sides. An example of this is using different database access techniques for read and update.

CQRS fits well with event-based programming models. It's common to see CQRS system split into separate services communicating with Event Collaboration. This allows these services to easily take advantage of Event Sourcing.

Benefits of CQRS include:

* Independent scaling. CQRS allows the read and write workloads to scale independently, and may result in fewer lock contentions.
  * Project Perspective: For the new feeds system it's really clear that we need to take care about the different load demand involving write x reads. 
* Optimized data schemas. The read side can use a schema that is optimized for queries, while the write side uses a schema that is optimized for updates.
  * Project Perspective: Based on future demands, it will provide us a long term solution for different kind of demands.
* Security. 
  * Project Perspective: It’s easier to ensure that only the right domain entities are performing writes on the data. As we need to deal with different kind of clients, it can bring more reliability for our query model.
* Separation of concerns.
  * Project Perspective: Segregating the read and write sides can result in models that are more maintainable and flexible. Most of the complex business logic goes into the write model. The read model can be relatively simple.
* Simpler queries. 
  * Project Perspective: By storing a materialized view in the read database, the application can avoid complex joins when querying. It simplify our database management and versioning. 
* Technology isolation between modules
  * Project Perspective: We can clearly separate the tech stack scope installing exactly the dependencies that each module needs separately. 


It's not mandatory to implement BOTH (commands & queries), the pattern provides
exactly the benefit to isolate the implementation.
