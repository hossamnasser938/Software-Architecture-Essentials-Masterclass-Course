# Architecture styles and patterns

- Architecture patterns

  - Big ball of mud (no architecture)
  - Unitary (all into one physical machine)
  - Client-server (Two-tier)
  - Three-tier

- Architecture styles

  - **Monolothic** => single unit of deployment
  - **Distribued** => distributed deployment units connected remotely

- Monolithic patterns

  - **Layered architecture** => structures the system into a set of hierarchical layers where every layer depends on the one beneath it. In other words it couples every layer with the one beneath it.
    2- Presentation
    1- Business
    0- Data
  - **Hexagonal architecture** => structures the system into 2 major parts:
    - core(application) => contains core business logic or the domain.
    - shell(infrastructure) => contains system input/output dependencies such as UI, DB, etc. Each module of this part is structured as a port and adapter where the port is an abstract definition(interface) of the thing and the adapter is one possible concrete implementation. The port has to be technology-agnostic. This decouples things and makes testing easier. A port is part of the core.
  - **Onion architecture** => is an extension to the hexagonal architecture. It agrees with the sepatration of core and shell but it structures the core into more defined layers. The core can be structured into:
    2- Application services => models bigger processes (should not have logic such as if conditions. should only sequence operations from domain services and domain models)
    1- Domain services => contains logic that might combine a domain model and infrastructure
    0- Domain model => contains business entities and their rules/logic
  - **Clean architecture** => is very similar to the Onion architecture with clearer definitions to the layers. From inner to outer the layers are the following:
    - Entitities => Domain models
    - Use Cases => this is a good thing. Instead of buildig complicated services that contain all logic we separate them into use cases. One more benefit is that the files structure would represent the business which is a an advantage to the readability and ease of understandig of the syetem in the high level.
    - Interface adapters (controllers, presenters, gateways) => converts from domain layer to infrastructure layer and vice versa.
    - Framewroks and drivers => such as db, web framework(express, fastify, ...etc)

- Hexagonal, onion, and clean all are domain-centric architectures where dependency goes from outer to inner or everything can depend on the domain but the domain should not depend on anything.
