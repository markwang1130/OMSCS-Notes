# Lesson 8

In this lesson we will cover the Unified Software Process starting with _software architecture_ where the goal is to lay the foundation on which to build successful and long lasting software systems.

## Interview With Nenad Medvidovic

_Why is software architecture important?_

Architectural design decisions are really the principal design decisions in a software system because it could have long-term implications if not made correctly. Architectural erosion happens when software grows over time while the architecture of a software system is ignored or poorly designed to begin with.

## What Is Software Architecture

What is **SWA (software architecture)**? Depends on the source but generally software architecture could be thought of as:

- Perry and Wolf: Composed of elements (the what), form (the how), and rationale (the why)
- Shaw and Garland:
  - A level of design that involves description of elements from which systems are built
  - Interactions among those elements
  - Patterns that guide their composition
  - Constraints on these patterns

## General Definition Of SWA

A general definition of SWA: _a set of principal design decisions about the system._ The blueprint of a software system includes:

- Structural properties
- Behavioral properties
- Non-functional properties
- Interactions

There is also a temporal aspect of SWA since it should change over the lifetime of a software system.

## Prescriptive Vs. Descriptive Architecture

- A **prescriptive architecture** captures the design decisions made prior to the system's construction (as-conceived SWA). 
- A **descriptive architecture** describes how the system has actually been built (as-implemented SWA).

## Architectural Evolution

When a system evolves, ideally its prescriptive architecture should be modified first. However, in practice this almost never happens.

## Architectural Degradation

Over time, two types of architectural degradation occurs for software systems with poor SWA:

1. **Architectural drift**: introduction of architectural design decisions orthogonal to a system's prescriptive architecture
2. **Architectural erosion**: introduction of architecture design decisions that violate a system's prescriptive architecture.

| 概念                            | 定义         | 状态   | 问题程度 |
| ----------------------------- | ---------- | ---- | ---- |
| **Prescriptive Architecture** | 应该实现的架构设计  | 理想状态 | -    |
| **Descriptive Architecture**  | 实际代码的架构    | 实际状态 | -    |
| **Architectural Drift**       | 轻微偏离但不违反原则 | 偏离   | 可接受  |
| **Architecture Erosion**      | 严重偏离且违反原则  | 偏离   | 严重问题 |


## Architectural Recovery

_What happens when an architecture drifts or erodes?_

We have to take a path leading to **architectural recovery** which typically means to determine SWA from implementation and fix it. Developers should not simply _tweak_ code to recover their SWA.

## Architectural Elements

A SWA typically is not a monolith composition and interplay of different elements. SWA includes:

1. Processing elements
2. Data elements
3. Interaction elements

- **Components** = Processing elements + Data elements
- **Connectors** = Interaction elements
- **Configuration** = Components + Connectors

## Components - Connectors - Configurations

> A **component** is an architectural entity that:
> - Encapsulates a subset of the system's functionality and/or data
> - Restricts access to that subset via an explicitly defined interface   
>
> A **connector** is an architectural entity affecting and regulating interaction.  
> A **configuration** is an association between components and connectors of a SWA.

---

#### 🔹 Component
A **component** represents a **modular unit of computation or data storage**. It is responsible for implementing a specific part of the system’s functionality.

- It encapsulates behavior and/or data.
- It exposes an **interface** to define how other components or systems can interact with it.
- Components are **reusable**, **replaceable**, and **independent**, making them building blocks in architecture.

> 🔁 类比：组件就像一个黑盒模块，有输入输出接口，内部封装了具体实现。

---

#### 🔹 Connector

A **connector** represents the **interaction mechanism** between components.

- It **regulates** communication, coordination, and cooperation among components.
- Connectors can be:
  - **Procedure calls**
  - **Data streams**
  - **Shared databases**
  - **Message passing**
  - **Middleware (e.g., REST API, RPC, pub/sub systems)**

> 🔁 类比：连接器就像电缆、管道或协议，用于连接和通信，决定了信息如何在组件间流动。

---

#### 🔹 Configuration

A **configuration** is the **structure or topology** that results from **composing components and connectors**.

- It defines how the system’s elements are **assembled** and how they **interact**.
- It often uses a **graph** where:
  - **Nodes** = components
  - **Edges** = connectors

> 🔁 类比：配置是整个电路图或装配图，决定了各个模块如何连接成一个整体系统。

## Architectural Styles

An **architectural style** is a named collection of architectural design decisions applicable in a given context. Alternatively from Shaw and Garland, an architectural style:

> ...defines a family of systems in terms of a pattern of structural organization, a vocabulary of components and connectors, with constraints on how the can be combined.

## Types Of Architectural Styles

There are many types of architectural styles in SWA:

1. Pipes and filters (e.g. UNIX)
2. Event-driven (e.g. GUI)
3. Publish-subscribe (e.g. Twitter)
4. Client-server (e.g. Email)
5. P2P (Peer-to-peer)
6. REST (Representational State Transfer)

### 🌉 Common Architectural Styles in Software Architecture

Architectural styles define templates for organizing software systems. Key styles include:

---

#### 🔸 Pipes and Filters
- Filters: independent components processing data.
- Pipes: connectors that stream data between filters.
- Example: `cat file.txt | grep error | sort` (UNIX).
- 🔁 类比：流水线式加工。

---

#### 🔸 Event-Driven (Implicit Invocation)
- Components respond to events asynchronously.
- Loose coupling; components are unaware of each other.
- Used in GUI, game engines, IoT.
- 🔁 类比：广播事件通知。

---

#### 🔸 Publish-Subscribe
- Publishers send messages to a broker.
- Subscribers receive messages based on topics.
- Enables many-to-many communication.
- Used in systems like Twitter, Kafka.
- 🔁 类比：报刊订阅。

---

#### 🔸 Client-Server
- Server offers services; client consumes them.
- Centralized control, common in web systems.
- Example: Email, database access.
- 🔁 类比：餐厅顾客和厨房。

---

#### 🔸 Peer-to-Peer (P2P)
- Each node acts as both client and server.
- Used for file sharing and blockchain.
- Promotes resilience and decentralization.
- 🔁 类比：邻里借书互助系统。

---

#### 🔸 REST (Representational State Transfer)
- Stateless client-server communication over HTTP.
- Uses HTTP verbs: GET, POST, PUT, DELETE.
- Example: `GET /users/123`
- 🔁 类比：菜单点单系统。


## P2P Architectures

**P2P architectures** advocate decentralized resource sharing and discovery. E.g., Skype utilizing super nodes to support a decentralized architecture but still allowing users to communicate P2P.

## Takeaway Message

Several takeaways from this lesson:

1. A great SWA is a ticket to success
2. A great SWA reflects deep understanding of the problem domain
3. A great SWA normally combines aspects of several simpler architectures

## Section Quizzes

### Architectural Recovery Quiz

_Which of the following sentences is true_?

- Architectural drift results in unnecessarily complex architectures

### Architectural Design Quiz

_What are ideal characteristics of an architectural design_?

- Scalability
- Low coupling

### Architectural Styles Quiz

_Mark which architectural style(s) (given) characterizes the following systems_:

1. _Android OS_: event-driven, publish-subscribe
2. _Skype_: client-server, peer-to-peer
3. _World-wide Web_: client-server, REST
4. _DropBox_: client-server
