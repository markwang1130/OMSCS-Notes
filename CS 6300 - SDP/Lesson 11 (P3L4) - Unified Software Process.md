# Lesson 11

In this lesson we will try to combine concepts from software architecture, low-level design, and design patterns with concepts from software engineering activities to discuss a unified software process.

## History Of RUP (Rational Unified Process)

In 1997, Rational defined six best practices for modern software engineering:

1. Develop iteratively, focusing on risk
2. Manage requirements
3. Employ a component-based architecture
4. Model software usually
5. Continuously verify quality
6. Control chances

## Key Features Of RUP

### 🧱 RUP (Rational Unified Process) 的核心特性

RUP 是一种面向对象的软件开发过程框架，强调结构化、可控和可重复的开发流程。它有以下几个显著特征：

---

#### 1. **Software process model（软件过程模型）**

- 定义了软件开发各个阶段（如 Inception, Elaboration, Construction, Transition）的顺序与过渡条件。
- 每个阶段都有明确的目标和验收标准。

> 📌 中文解释：RUP 提供清晰的阶段划分和推进标准，比如从需求获取推进到架构设计，需满足一定的成果（如关键用例、初步原型等）。

---

#### 2. **Component-based（基于组件）**

- 强调构建具有明确定义接口的可重用组件。
- 鼓励通过模块化实现系统可维护性和可扩展性。

> 📌 中文解释：RUP 鼓励将系统拆分成一个个“可插拔”的组件（如服务、模块），每个都有明确的功能和接口，方便复用和替换。

---

#### 3. **Tightly related to UML（与 UML 紧密相关）**

- 使用 UML（统一建模语言）表达系统结构、行为和交互。
- UML 图（如用例图、类图、顺序图等）是开发过程中的重要工件。

> 📌 中文解释：RUP 和 UML 是“搭档”，开发过程中大量使用 UML 进行建模，从需求到设计再到实现都可视化呈现。

---

#### 4. **Distinguishing aspects（区别特性）**

RUP 与传统瀑布式开发模型的不同之处主要包括：

- **Use-case driven（用例驱动）**：  
  需求从用户视角出发，围绕用例构建系统功能。

- **Architecture-centric（以架构为中心）**：  
  早期确定和验证系统架构，架构贯穿整个生命周期。

- **Iterative and Incremental（迭代与增量）**：  
  系统开发通过多个迭代周期逐步展开，每次迭代交付可运行子系统。

> 📌 中文解释：
> - “用例驱动”确保开发重点聚焦于用户需求；  
> - “架构为中心”确保早期发现风险；  
> - “迭代增量”允许渐进式构建，及时反馈和调整。

and incremental

## Use Case Driven

RUP is use case driven. A system performs a sequence of actions in response to user input. Use cases capture this interaction and answer the question: _what is the system suppose to do for each user_?

## Architecture Centric

### 🏗 RUP 是 Architecture-Centric（以架构为中心）

RUP 将系统架构视为开发过程的核心支柱，认为系统的“形式（form）”由架构决定，而“功能（function）”由用例（use cases）定义。

换句话说：

> 🧠 **Use cases define what the system does**  
> 🏛 **Architecture defines how the system is organized**

#### 📌 开发流程大致包括：

1. **Creating a rough outline of the system**  
   初步构建系统的整体轮廓，确定主要模块与交互方向。

   > 中文：先粗略规划出系统是由哪些大块功能或子系统组成，例如 UI 层、业务逻辑层、数据访问层等。

2. **Translating key use cases into sub-systems**  
   将关键用例映射为系统中的子系统、模块或组件。

   > 中文：将用户用例转化为系统内部结构，比如一个“注册账户”用例，可能需要用户界面、身份验证服务、数据库接口等子系统支持。

3. **Refining architecture using additional use cases**  
   继续用更多的用例逐步完善和验证架构设计。

   > 中文：通过更多真实场景的用例（如“修改账户信息”、“发送通知”等）不断验证当前架构是否健壮、是否需要重构或扩展。

---

🎯 **总结**：  
这种从用例到架构的演化方式，使得系统架构既满足当前需求，也具备良好的可扩展性和灵活性，是 RUP 的核心优势之一。


## Iterative And Incremental

### 🔄 RUP 是 Iterative and Incremental（迭代式和增量式）

RUP 强调软件开发应通过一系列 **迭代周期（iteration cycles）** 逐步构建系统，每个周期都能产出一个可用的产品版本（可内部评估或对外发布）。

#### 📦 每个项目通常包含多个开发周期，每个周期又包含四个阶段：

---

#### 1. **Inception（构思阶段）**
- 🔍 Focus: Business modeling
- 明确项目商业目标、初步范围、关键用例、风险和成本估算。

> 中文解释：主要搞清楚“我们要做什么、为什么做”，是商业层面的立项和论证。

**Deliverable**
- Vision document with general vision of the core project's requirements, key features, and main constaints
- Initial use-case model
- Initial project glossary
- Initial business case
- Initial proejct paln and risk assessment
- [optional] One or more prototypes

**Acceptance Criteria**
- **Stakeholder concurrence** on scope, definition, and cost/schedule estimates
- **Requirements understanding** as evidenced by the fidelity of the primary use cases
- **Credibility** of the cost/schedule estimates, priorities, risks, and development process
- Depth and breadth of any prototype that was developed  


---

#### 2. **Elaboration（细化阶段）**
- 🧠 Focus: Requirements + Analysis and Design
- 完善系统需求，进行体系结构设计、风险识别和原型验证。

> 中文解释：搞清楚“怎么做”，并构建系统的基本架构，验证核心风险。

**Deliverable**
- Almost complete use-case model
- Supplementary requirements, including non-functional requirements (security, etc)
- Software architecture
- Design model, test cases, executable prototype
- Revised project plan and risk assessment
- Peliminary user manual

**Acceptance Criteria**
- Vision and architecture are **stable**? 
- The prototype shows that the **major risks have been addressed/resolved** 
- The plan **sufficiently detailed/accurate** 
- All stakeholders agree that the **vision can be achieved** with the current plan 
- The actual resource expenditure vs planned **expenditure are acceptable**? 

---

#### 3. **Construction（构建阶段）**
- 🛠 Focus: Implementation + Test + Deployment
- 在稳定架构的基础上开发功能模块，编写代码，执行单元/集成测试，形成初步产品。

> 中文解释：系统进入主开发期，团队协作完成绝大多数功能实现。

**Deliverable**
- All uses cases realized, with traceability information (which design realizes which use case)
- Software product integrated on adequate platforms
- Completed system tests results
- User manual
- Completed set of artifacts: design, code, test cases, etc

**Acceptance Criteria**
- Product **stable, mature** enough to be deployed to users
- The stakeholders **ready for the transition** into the user community
- Actual resources expenditure vs planned **expiditure are acceptable**


---

#### 4. **Transition（交付阶段）**
- 📦 Focus: Testing + Deployment + Training
- 将系统交付给用户，进行验收测试、部署、培训和文档编写。

> 中文解释：把产品“交出去”，确保用户可以顺利使用，处理部署后的反馈与改进。

**Deliverable**
- Completed project
- In-use project
- Learnt lessons
- Plan for next release

**Acceptance Criteria**
- The uses are **statisfied**
- Actual resources expenditure vs planned **expiditure are acceptable**


---

💡 **注意**：
- 每个阶段可以包含 **多个迭代（iterations）**。
- 每次迭代都应有明确目标和可交付物，比如：原型、部分功能、性能测试报告等。
- 这种方式鼓励持续反馈和风险控制。

---

🎯 **总结**：  
相比传统一次性开发完，RUP 的迭代+增量方法能够更灵活应对需求变更，更早发现设计问题，更好保障产品质量和用户满意度。


## Iterations

Within each iteration the following activities may be observed:

1. Identify relevant use cases
2. Create design
3. Implement the design
4. Verify code against use cases
5. Release a product at the end

## Section Quizzes

### UML 1 Quiz

_What is the difference between a use case and a use case model_?

A use case model is a set of use cases.

### UML 2 Quiz

_What are use case diagrams used for_?

- They can be used to prioritize requirements
- They can be used during requirements elicitation
- They can be used for test case design

### Iterative Approach Quiz

_What are the benefits of iterative approaches_?

- Give developers early feedback
- Minimize risk of developing wrong system
- Accommodate evolving requirements
