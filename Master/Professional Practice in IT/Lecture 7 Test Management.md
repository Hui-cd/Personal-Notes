## Software Testing 软件测试

### Overview 概述
Software testing is a **systematic process 系统过程** used to:
- **Verify 验证**: Confirm software meets specified requirements (verification).
- **Validate 验证**: Ensure software satisfies user needs (validation).
- **Identify 识别**: Detect defects, bugs, or issues.
- **Assure 保证**: Maintain quality and mitigate risks.
- **Evaluate 评估**: Check performance, security, and usability.

### Testing Phases 测试阶段

#### Requirements Phase 需求阶段
- **Requirements Review 需求审查**: Validate the clarity, completeness, and achievability of software requirements.

#### Planning Phase 计划阶段
- **Test Planning 测试计划**: Develop detailed test plans outlining strategies, objectives, resources, and schedules.

#### Design Phase 设计阶段
- **Test Design 测试设计**: Create test cases and scenarios based on software design and requirements.

#### Development Phase 开发阶段
- **Unit Testing 单元测试**: Developers test individual code units (e.g., functions, modules).

#### Integration Phase 集成阶段
- **Integration Testing 集成测试**: Focus on interactions between integrated components or modules.

#### System Phase 系统阶段
- **System Testing 系统测试**: Test the entire system to ensure it functions correctly as a whole.

#### Acceptance Phase 验收阶段
- **User Acceptance Testing (UAT) 用户验收测试**: End-users verify the software meets their needs and expectations.

#### Release Phase 发布阶段
- **Deployment Testing 部署测试**: Ensure smooth software deployment in the production environment.

#### Maintenance Phase 维护阶段
- **Regression Testing 回归测试**: Re-run tests to verify new changes do not introduce new defects.

### Testing During Development 开发中的测试

- **Component Test 组件测试**: Uses white-box testing to ensure each component functions correctly.
- **Integration Test 集成测试**: Tests interaction between related components, focusing on interfaces.
- **System Test 系统测试**: Verifies that user requirements are met, focusing on typical business processes and workflows.

### Top-Down vs Bottom-Up 自顶向下 vs 自底向上

| Aspect 方面           | Top-Down Integration Testing 自顶向下集成测试  | Bottom-Up Integration Testing 自底向上集成测试  |
| --------------------- | ------------------------------------------ | -------------------------------------------- |
| Testing Direction 测试方向 | Starts from higher-level modules and goes downward 开始于高级模块并向下测试 | Starts from lower-level modules and goes upward 从低级模块开始并向上测试 |
| Initial Components 初始组件 | Real higher-level components; stubs or drivers for lower-level components 真实高级组件；低级组件的桩或驱动 | Real lower-level components; stubs or drivers for higher-level components 真实低级组件；高级组件的桩或驱动 |
| Dependencies 依赖 | May require stubs or drivers for lower-level components 可能需要低级组件的桩或驱动 | May require stubs or drivers for higher-level components 可能需要高级组件的桩或驱动 |
| Advantages 优点 | Early validation of system functionality; supports high-level design 早期验证系统功能；支持高级设计 | Early detection of critical component issues; supports parallel development 早期检测关键组件问题；支持并行开发 |
| Drawbacks 缺点 | Dependencies on incomplete lower-level components; delayed system testing 依赖不完整的低级组件；延迟系统测试 | May require extensive use of stubs and drivers; complex coordination 可能需要广泛使用桩和驱动；复杂的协调 |

### Functional vs Non-functional Requirements 功能性与非功能性需求

| Aspect 方面             | Functional Requirements 功能性需求 | Non-Functional Requirements 非功能性需求 |
| ----------------------- | ---------------------------------- | ---------------------------------------- |
| Definition 定义         | Specify what the system should do and its features 指定系统应做什么及其功能 | Specify how the system should perform and its qualities 指定系统应如何表现及其质量 |
| Focus 焦点              | Features, actions, behaviors 特征、行动、行为 | Performance, security, usability, scalability, etc. 性能、安全、可用性、可扩展性等 |
| Example 示例            | User login, shopping cart functionality 用户登录、购物车功能 | Response time, encryption, user interface, concurrency 响应时间、加密、用户界面、并发 |
| What they address 它们解决的问题 | Core system functionality 核心系统功能 | System performance, user experience, technical aspects 系统性能、用户体验、技术方面 |
| User expectation 用户期望 | Defines the visible and usable functionality 定义可见和可用的功能 | Defines the system's quality attributes and constraints 定义系统的质量属性和约束 |
| Development impact 开发影响 | Guides feature design and development 指导功能设计和开发 | Guides technical implementation and system design 指导技术实现和系统设计 |
| Testing approach 测试方法 | Form the basis for functional testing 为功能测试提供基础 | Form the basis for non-functional testing 为非功能测试提供基础 |
| Importance in design 设计中的重要性 | Specifies features and use cases 指定功能和用例 | Specifies performance goals, constraints, and limits 指定性能目标、约束和限制 |

### Testing During Deployment 部署期间的测试

- **Performance Test 性能测试**: Test system performance under maximum expected load.
- **Soak Test and Stress Test 浸泡测试和压力测试**: Verify system stability over an extended period and under over-load conditions.
- **Acceptance Test 验收测试**: Compare system functionality against user requirements; typically carried out by clients under supervision.

### Load Test 负载测试
Modelling the expected usage of a software program by simulating multiple users accessing the program concurrently. 通过模拟多个用户同时访问程序来模拟软件程序的预期使用。

#### Importance 重要性
- Critical for multi-user systems, often using client/server models like web servers. 对于多用户系统至关重要，这些系统通常使用客户端/服务器模型，如Web服务器。

#### Examples 示例
- A word processor or graphics editor tested on an extremely large document. 文字处理器或图形编辑器在极大的文档上进行测试。
- A financial package required to generate a report based on many years of data. 一个需要基于多年数据生成报告的财务软件包。
- A spreadsheet tested with maximum columns and rows. 用最大列和行测试的电子表格。

### Soak Testing 浸泡测试
Testing with a significant load extended over a significant period of time to discover how the system behaves under sustained use. 在相当长的时间内进行大量负载测试，以发现系统在持续使用下的表现。

#### Examples 示例
- A system may operate normally for 1 hour but fail when tested for 3 hours. 系统可能正常运行1小时，但在测试3小时时失败。
- Can expose issues like memory leaks or stack overflows. 可以暴露内存泄漏或栈溢出等问题。
- Problems such as rounding, accumulation, or compounding errors that cause unexpected behavior or failures after prolonged operation. 经长时间运行后引起意外行为或故障的问题，如四舍五入、累积或复合错误。

### Stress Testing 压力测试
Subjecting a system to unreasonable loads while denying necessary resources (RAM, disk, CPUs, etc.) to process that load. 在拒绝处理该负载所需的资源（RAM、磁盘、CPU等）的情况下，对系统进行不合理的负载测试。

#### Examples 示例
- Stress the system to its breaking point to determine if failures are harmful. 将系统压力至断点，以确定故障是否有害。
- Focus on robustness, availability, and error handling under loads heavier than typically expected. 重点关注在通常预期之上的重负载下的健壮性、可用性和错误处理。
- Important for mission-critical software (medical, space, defense) where system failure is not an option. 对于系统故障不是选项的关键任务软件（医疗、太空、防御）至关重要。

### Load vs. Stress vs. Soak 负载测试 vs. 压力测试 vs. 浸泡测试
| Test Type 测试类型 | Purpose 目的 | Test Scenario 测试场景 | Example Question 示例问题 |
| ------------------ | ------------- | ---------------------- | -------------------------- |
| Load Test 负载测试 | Assess performance under expected conditions. 在预期条件下评估性能。 | Simulate multiple users or transactions within normal ranges. 在正常范围内模拟多个用户或交易。 | Can the system handle 1000 users concurrently? 系统能同时处理1000个用户吗？ |
| Soak Test 浸泡测试 | Evaluate stability over time. 评估随时间的稳定性。 | Sustain a significant load for an extended period. 在延长期间维持重大负载。 | How does the system perform after 72 hours of continuous use? 系统连续使用72小时后的表现如何？ |
| Stress Test 压力测试 | Identify limits and recovery behavior. 确定极限和恢复行为。 | Push the system beyond normal operational capacity. 将系统推向超出正常运营能力的极限。 | What happens when the system receives 10 times the normal traffic? 系统接收到正常流量10倍时会发生什么？ |

### Challenges in Managing Testing 管理测试的挑战
Balancing quality assurance with time constraints is a primary challenge in testing management within software development. This involves dealing with changing requirements, scope expansion, and limited resources. Maintaining effective communication and collaboration across teams is essential, as well as managing regression testing, test automation, and realistic test data. Adopting best practices and ensuring early testing involvement are crucial for achieving a balance between speed and quality.

### Knowing When Testing is Sufficient 确定何时测试足够
Determining when to conclude testing involves several criteria:
- **Code Coverage 代码覆盖率**: Achieving desired coverage levels.
- **Bug Discovery Rate 错误发现率**: A decline in the rate suggests diminishing returns from continued testing.
- **Open Bugs 开放错误**: Addressing all high-severity bugs.
- **Testing Cycles 测试周期**: Completing planned testing phases like beta or alpha.
These metrics help ensure the software's stability, functionality, and quality, contextualized within project goals and timelines.
