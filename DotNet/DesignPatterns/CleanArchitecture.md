# Clean/Onion Architecture

Clean Architecture has a following layers
- **Domain**: Contains core business logic. Holds things like Entities, Exceptions, Business Logic behavior interfaces.
- **Application**: Contains actual business logic implementations. Holds things like Queries, Commands, Dto Models, Validators, etc.
- **Infrastructure** Contains interfaces and adaptor implementation for third-party and connecting services. Holds things like Persistance layer that connects with the DB, Authentication API implementation, Other third party services that your business consumes.
- **Presentation**: Contains UI, and display logic, things that the user will see or use.

The main goal of Clean Architecture is that it separates the domain or business logic from surrounding parts, which allows for easy swap of implementation in any given layer.
