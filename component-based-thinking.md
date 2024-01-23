### Component-Based Thinking

- Components are physical manifestations of modules
    - Modules are physically packaged in different ways 
    - Examples:
        - *jar* for Java
        - *dll* for .Net
        - *gem* for Ruby

- Components offer a language-specific mechanism to group artifacts together, they are often nested to create stratification
- __Wrapper__:
    - The simplest of the components, it wraps code at a higher level of modularity than classes
    - The simplest wrapper is a library. It tends to run in the same memory address as the calling code and communicates via the language function call mechanism
    - Usually compile-time dependencies
- __Subsystems or Layers__:
    - Components appear as deployable subsystems or layers of an event processor
    - A __service__ runs in it's own address space and communicates via low level protocols such as TCP/IP or via higher-level formats such as REST or message queues
    - Services form standalone, deployable units of architecture often called microservices
- In Microservices simplicity is an important architecural principal. A system may consist of enough code to warrant components or be simple enough to contain a small bit of code
- Software architects together with business analysts, subject matter experts, developers and QA engineers, operations, enterprise architects create the initial design for a software system based on software architecture characteristics and business requirements
- Architecture is independent from the software development process
    - The exception to this rule entails the engineering practices pioneered in the Agile software development process, particularly in the areas of deployment and automating governance
- Components are the lowest level of the software system an architect interacts with, with the exception of code quality metrics of the components
- Components consist of the classes whose design falls under the perview of tech leads and developers
- The architects duty is to identify components of the software system on the prohect

