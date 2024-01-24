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

#### Architecture Partitioning

- The first Law of Software Architecture is that everything is a tradeoff
- This includes how components are created
- Coponents represent a general containership mechanism, architects have much leeway in the types of partitioning they use
- Sevel common partitioning styles exist, with different sets of tradeoffs
    - Layered Monolith
        - Modules are layered on top of each other into a single deployable service
        - Layers represent technical capabilities
        - It represents a technical top level partitioning
        - All functionality of a particular type is found in only one layer of the code base, making it easy to import it and use it
        - Examples include MVC
    - Modulare Monolith (Domain Partitioning)
        - Modules are partitioned around domains rather than technical capabilities
        - Is the result of Domain Driven Design
        - The architect identifies domains and workflows independent and decoupled from each other
        - Microservices are based on DDD
        - It uses a top-level partitioning which organizes components by domain rather than technical capabilities
        - Top level components are built around workflows and domains
        - Each component may have subcomponents, including layers, but the top level partitioning focuses on domains
    - Technical Partitioning
        - The top level partitioning of the system revolves around the domains
        - The organizing principle of this architecture is the separation of technical concerns
        - This allows for creating useful levels of system decoupling
        - It enables developers to find certain categories of the code base quickly as that it is organized by capabilities
        - A downside is that most realistic software systems require workflows that cut accross technical capabilities
- Choosing an architectural partioning defines the fundamental architecutral style of the system and the way how the code will be written and partitioned

###### Domain Partitioning Benefits

- Modeled more closely to how the business operates rather than implementation detail
- Easier to use the Inverse Conway Maneuver to build cross functional teams around domains
- Aligns more closely to the modular monilith and microservices architecture styles
- Message flow matches the problem domain
- Easy to migrate data and components to distributed architecture

###### Domain Partitioning Disadvantages

- Customization code appears in multiple places

###### Layered Partitioning Advantages

- Clearly separates customization code
- Aligns more closely to the layered architecture patter

###### Layered Partitioning Disadvantages

- Higher degree of global coupling. Changes to the Common or Local component will likely affect all other components
- Developers have to duplicate domain concepts in both common and local layers
- Higher coupling at the data layer. It is more difficult to untabgle data relationships if later on you want to migrate the architecture to a distributed system

#### Conway's Law

- Organizations which design systems are constrained to produce designs which are copies of the communication structures of these organizations
    - Whan a group of people design a technical artifact, the communication strucuture among the people end up replicated in the design
    - It is common for organizations to partition workers based on technical capabilities
    - Makes sense from an organizational perspective but it hampers collaboration because of the artificial separation of common concerns
- The Inverse Conway Maneuver suggests evolving team and organizational strucutre together to promote the desired architecture

#### Component Identification Flow

- Works best as a iterative refinement process, producing candidates and refinements through feedback

##### Identifying Initial Components

- Top level components are determined based on the type of top-level partitioning is chosen

##### Assign Requirements to Components

- Once initial components are determined, the next step is to align the requirements to those components

##### Analyze Roles and Responsibilities

- Look at the roles and reposnsibilities written in the requirements and ensure that it is in line with the  domain granularity for the component

##### Analyze Architecture Characteristics

- When assigning requirements to components,, we should also look at the architectural characteristics of the components to to see how it impacts component division and granularity 
- Two parts of a system may deal with user input but one part deals with hundreds of concurrent users while another component deals with only a few.

##### Restrucutre Components

- Iterate over components and restructure them as new knowledge comes to light

##### Component Granularity

- Finding the proper granularity for a component is one of the most difficult tasks to do
- Too fine-grained component design leads to too much communication between components 
- Too coarse grained components encourage high internal coupling leading to difficulties to deployability and testability, as well as modularity related negative side effects

###### Component Design

- When architecting a system you must take requirements and determine the coarse grained building blocks that will make up the application

###### Discovering Components

- Create an initial component design based on general knowledge about the system 
- Choose how to decompose it whether by technical or domain partitioning
- The goal is to create an initial design that partitions the problem space into coarse chunks taking into account differing architecture ahracteristics

###### Entity Traps

- A common architecture anti pattern
- This is when you build an architecture as a object-relational mapping
- Use an ORM for this
- You incorrectly identify database relationships as worflows in the applcation
- You are not giving enough though about the actual worflows of your system
- The components are corase grained but offer no information in terms of packaging and structuring of the source code

###### Actor/Actions

- A popular way to map requirements to components
- Originated in the Rational Unified Process
- You identify actors to perform activities and the actions that they can perform
- It allows you to to figure out the typical users of a system and the kinds of things they might do with the system
- The approach is useful when the requirements feature distinct roles and the types of actions those roles can perform
- Works well for monoliths and distributed systems

###### Event storming

- Derives from DDD and share popularity with microservices
- You assume the system will use messages and events to communicate between the variuous components
- You try to determine which events occur in the system based on requirements and identified roles
- You builkd comoponents around those event and message handlers
- Works well with microservices that use events and messages since it allows you to define the messages used in the system

###### Workflow approach

- A more generic approach to event storming
- You are not using DDD or messaging 
- You model the coponents around workflows
- There are no explicit constraints of building a message based system 
- You identify key roles, you determine the worflows these roles engage in, and build the components around those identified activities







