# OnionArchitecture

The Onion architecture is also commonly known as the “Clean architecture” or “Ports and adapters”.

The Onion architecture is a form of layered architecture, and we can visualize these layers as concentric circles. Hence the name Onion Architecture. The Onion architecture was first introduced by Jeffrey Palermo, to overcome the issues of the traditional N-layered architecture approach.

There are multiple ways that we can split the onion, but we are going to choose the following approach, where we are going to split the architecture into 4 layers:
Domain and Application Layer will be at the center of the design. We can refer to these layers as the Core Layers. These layers will not depend on any other layers.
 - Domain Layer: Domain Layer usually contains enterprise logic and entities. Application Layer would have Interfaces and types. The main difference is that The Domain Layer will have the types that are common to the entire enterprise, hence can be shared across other solutions as well.
 - Application Layer: As mentioned earlier, the Core Layers will never depend on any other layer. Therefore what we do is that we create interfaces in the Application Layer and these interfaces get implemented in the external layers. This is also known as DIP or Dependency Inversion Principle.
 - Infrastructure Layer: The infrastructure layer is a bit more tricky. It is where you would want to add your Infrastructure. Infrastructure can be anything. Maybe an Entity Framework Core Layer for Accessing the DB, a Layer specifically made to generate JWT Tokens for Authentication or even a Hangfire Layer.
 - Presentation Layer: The presentation layer is where you would Ideally want to put the Project that the User can Access. This can be a WebApi, Mvc Project, etc.

Conceptually, we can consider that the Infrastructure and Presentation layers are on the same level of the hierarchy.

All of the layers interact with each other strictly through the interfaces defined in the layers below. The flow of dependencies is towards the core of the Onion.

Using dependency inversion throughout the project, depending on abstractions (interfaces) and not the implementations, allows us to switch out the implementation at runtime transparently. We are depending on abstractions at compile-time, which gives us strict contracts to work with, and we are being provided with the implementation at runtime.

Testability is very high with the Onion architecture because everything depends on abstractions. The abstractions can be easily mocked with a mocking library such as Moq.

We can write business logic without concern about any of the implementation details. If we need anything from an external system or service, we can just create an interface for it and consume it. We do not have to worry about how it will be implemented. The higher layers of the Onion will take care of implementing that interface transparently.

