- series of stages that provide a framework for the development and management of an information system
![[Pasted image 20250419154455.png]]
# Stages
1. **Planning and Feasibility Study:**
    - **Goal:** Determine if the project is viable and worth pursuing. Define the problem and scope.
    - **Activities:** Identify the need/opportunity, define high-level goals, conduct initial requirements gathering, perform feasibility studies (technical, economic, operational, schedule - TEOS), estimate resources, assess risks, get project approval.
    - **Deliverable:** Feasibility report, project plan outline, initial scope definition.

2. **Analysis / Requirements Definition:**    
    - **Goal:** Understand and document what the system must do in detail. Define user needs precisely.
    - **Activities:** Gather detailed functional and non-functional requirements from stakeholders (interviews, surveys, observation), analyze existing systems, model business processes, analyze data requirements.
    - **Deliverable:** Software Requirements Specification (SRS) document, use cases, data models. This is often considered the most critical phase.

3. **Design:**    
    - **Goal:** Determine how the system will be built to meet the specified requirements. Create the technical blueprint.
    - **Activities:** Define the overall system architecture, design modules/components, specify interfaces between components, design databases, design user interfaces (UI) and user experience (UX), select technologies (programming languages, platforms). Divided into High-Level Design (architecture) and Low-Level Design (module specifics).
    - **Deliverable:** Design specification documents, architecture diagrams, database schema, UI mockups/prototypes.

4. **Implementation / Development / Coding:**    
    - **Goal:** Build the actual system based on the design specifications.
    - **Activities:** Write the code, create databases, install necessary hardware/software environments, perform unit testing (testing individual code components).
    - **Deliverable:** Working code modules, compiled software, unit test results.

5. **Testing:**    
    - **Goal:** Verify that the developed system meets the requirements defined in the Analysis phase and works correctly according to the Design. Find and fix defects.
    - **Activities:**
        - Integration Testing: Test interfaces between modules.
        - System Testing: Test the entire system as a whole.
        - Performance Testing: Check speed, reliability, load handling.
        - Security Testing: Identify vulnerabilities.
        - User Acceptance Testing (UAT): Users test the system to confirm it meets their needs in a real-world scenario.
    - **Deliverable:** Test plans, test cases, bug reports, test summary report, user acceptance sign-off.

6. **Deployment / Installation:**    
    - **Goal:** Make the system operational for end-users. Put the system into production.
    - **Activities:** Install the software/hardware in the production environment, data migration/conversion from old systems, user training, finalize documentation. Deployment strategies can vary (e.g., direct cutover, parallel adoption, phased rollout).
    - **Deliverable:** Operational system, user documentation, training materials.

7. **Maintenance / Operation:**    
    - **Goal:** Keep the system running smoothly and adapt it to changing needs over its lifespan. This is often the longest phase.
    - **Activities:** Ongoing user support, monitoring system performance, bug fixing (corrective maintenance), adding minor enhancements (adaptive maintenance), improving performance or maintainability (perfective maintenance), system updates, backups, eventual decommissioning.
    - **Deliverable:** Updated documentation, bug fixes, enhancement releases, performance reports.

# Different Models
- **Waterfall Model:** A linear, sequential approach where each phase must be fully completed before the next begins. Simple but rigid, difficult to accommodate changes.

- **V-Model:** An extension of Waterfall that emphasizes testing activities corresponding to each development phase.

- **Iterative Model:** The system is built in repeated cycles (iterations), with each iteration producing a functional subset or improved version of the system. Allows for feedback and refinement.
   
- **Spiral Model:** Risk-driven approach combining iterative development with aspects of Waterfall. Suitable for large, complex, high-risk projects.

- **Agile Models (e.g., Scrum, Kanban, XP):** Focus on flexibility, collaboration, rapid delivery of working software in short cycles (sprints), customer feedback, and adapting to change. Very popular in modern software development.

### models
**1. Waterfall Model**
- **Core Concept:** A linear, sequential "one-way street" approach. Each phase must be fully completed and signed off before the next phase can begin.
- **Process Flow:**
    1. **Requirements:** Gather and document all requirements comprehensively. Freeze requirements.
    2. **Design:** Create the complete system architecture and detailed design based only on the frozen requirements.
    3. **Implementation:** Write the code based only on the finalized design.
    4. **Testing:** Verify the entire implemented system against the original requirements.
    5. **Deployment:** Install the finished product.
    6. **Maintenance:** Address issues found after deployment.
- **Characteristics:**
    - Strictly sequential.
    - Emphasis on thorough documentation at each stage.
    - Clear milestones and deliverables for each phase.
    - Very little room for changing requirements once a phase is complete.
- **Advantages:**
    - Simple to understand, manage, and monitor progress.
    - Disciplined approach with clear stage gates.
    - Good for projects where requirements are extremely stable, well-understood, and unlikely to change.
- **Disadvantages:**
    - **Highly Inflexible:** Extremely difficult and costly to go back and change something in a previous phase.
    - **Late Feedback:** Working software is not produced until late in the cycle, so users don't see anything tangible for a long time.
    - **Risk:** Assumes all requirements can be captured perfectly upfront, which is rarely true for complex projects. If requirements are wrong, the entire project might fail or require massive rework.
    - **Blocks** progress; one phase must finish before the next starts.
- **When to Use:**
    - Small, simple projects.
    - Projects with completely fixed, clear, and stable requirements.
    - Projects where the technology stack is well-understood.
    - (Rarely used for large, complex software projects today due to its rigidity).

**2. V-Model (Verification and Validation Model)**

- **Core Concept:** An extension of the Waterfall model, emphasizing the relationship between each development phase and its corresponding testing phase. It highlights Verification (Are we building the product right?) and Validation (Are we building the right product?).
- **Process Flow:** It forms a V-shape:
    - Left Side (Development - going down):
        1. Requirements Analysis (Produces SRS)
        2. System Design (Produces High-Level Design)
        3. Architectural Design (Produces Low-Level Design/Module Specs)
        4. Module Design/Coding (Produces Code)
    - Right Side (Testing - going up):
        1. Unit Testing (Tests individual code modules, validates Module Design)
        2. Integration Testing (Tests interfaces between modules, validates Architectural Design)
        3. System Testing (Tests the entire system, validates System Design)
        4. User Acceptance Testing (UAT) (Users test against requirements, validates Requirements Analysis)
- **Characteristics:**
    - Still largely sequential like Waterfall.
    - Test planning and design happen early, in parallel with the corresponding development phase.
    - Explicit linking of development deliverables to testing phases.
- **Advantages:**
    - Emphasizes verification and validation throughout the lifecycle.
    - Testing activities start early, improving the chance of finding defects sooner.
    - Clear mapping helps ensure testing covers requirements and design aspects.
- **Disadvantages:**
    - Retains the rigidity of the Waterfall model regarding requirement changes.
    - No early prototypes are produced for user feedback.
    - If issues are found late (e.g., in System Testing), backtracking and fixing can still be expensive.
        
- **When to Use:**
    
    - Projects where high reliability and robustness are crucial (e.g., medical systems, avionics, critical infrastructure).
        
    - Projects where requirements are well-defined and stable.
        
    - When ample resources for rigorous testing are available.
        

**3. Iterative Model**

- **Core Concept:** Start with a subset of requirements, build a small working version (iteration 1), get feedback, refine requirements, and build subsequent versions (iterations 2, 3...) adding more functionality until the complete system is ready.
    
- **Process Flow:**
    
    1. Initial Planning (high-level requirements & architecture).
        
    2. **Iteration 1:** Detailed Planning -> Requirements -> Design -> Implementation -> Test -> Evaluation/Feedback. (Produces a usable, core piece of software).
        
    3. **Iteration 2:** Detailed Planning -> Requirements (refined/new) -> Design -> Implementation -> Test -> Evaluation/Feedback. (Adds more features to Iteration 1's product).
        
    4. ...Repeat until all requirements are met...
        
    5. Final Deployment.
        
- **Characteristics:**
    
    - Produces working software in increments.
        
    - Allows requirements to be refined over time.
        
    - Feedback from one iteration guides the next.
        
    - Focus is on building parts of the system repeatedly.
        
- **Advantages:**
    
    - Working functionality is available much earlier than Waterfall.
        
    - More flexible; easier to incorporate changes and user feedback.
        
    - Easier to manage risk by tackling high-risk features in early iterations.
        
    - Users can provide valuable feedback on usable increments.
        
- **Disadvantages:**
    
    - Total cost and timeline may not be as clear upfront.
        
    - Requires robust architecture design early on to accommodate future additions.
        
    - Integration between iterations needs careful planning.
        
    - Can sometimes lead to feature creep if scope isn't managed.
        
- **When to Use:**
    
    - Large, complex systems that can be broken down into smaller modules/iterations.
        
    - Projects where requirements are not fully defined at the start or are expected to evolve.
        
    - Projects where early user feedback is desired.
        

**4. Spiral Model**

- **Core Concept:** A risk-driven model combining the iterative nature with the systematic control of the Waterfall model. Development proceeds in spirals, with each spiral incorporating risk analysis.
    
- **Process Flow:** Each loop of the spiral typically involves four phases:
    
    1. **Determine Objectives, Alternatives, Constraints:** Understand the goals and limitations for this cycle.
        
    2. **Evaluate Alternatives, Identify and Resolve Risks:** Perform risk analysis, build prototypes to clarify requirements or technical feasibility, choose the best approach. This is the critical risk management step.
        
    3. **Develop and Verify Next-Level Product:** Implement and test the product for the current spiral (this phase often resembles a mini-Waterfall).
        
    4. **Plan Next Phases:** Review the results, plan the next spiral loop. If risks are resolved and the product is ready (based on objectives), proceed to deployment.
        
- **Characteristics:**
    
    - Strong emphasis on risk analysis and mitigation.
        
    - Iterative development with increasing functionality/detail per spiral.
        
    - Uses prototyping extensively to reduce risk.
        
    - Systematic approach within each cycle.
        
- **Advantages:**
    
    - Excellent for managing high-risk projects.
        
    - Allows for flexibility and changes as risks or requirements become clearer.
        
    - Produces prototypes and early versions for user feedback.
        
    - Systematic development and quality control.
        
- **Disadvantages:**
    
    - Complex model, requires significant expertise in risk management.
        
    - Can be expensive due to the overhead of risk analysis in each cycle.
        
    - May be overkill for smaller or low-risk projects.
        
    - Relies heavily on reliable risk assessment.
        
- **When to Use:**
    
    - Large, complex, and high-risk projects.
        
    - Projects where requirements are uncertain or need clarification through prototyping.
        
    - Mission-critical projects where risk avoidance is paramount.
        

**5. Agile Models (e.g., Scrum, Kanban, XP)**

- **Core Concept:** An umbrella term for iterative and incremental methodologies focused on flexibility, collaboration, customer satisfaction, and rapid delivery of working software. Embraces change rather than resisting it. Based on the Agile Manifesto values and principles.
    
- **Process Flow:** Varies by specific methodology (Scrum, Kanban, XP), but generally involves:
    
    - Breaking work into small, manageable units (user stories, features).
        
    - Developing and delivering in short, time-boxed cycles (e.g., Sprints in Scrum, typically 1-4 weeks).
        
    - Close collaboration between developers, testers, and business stakeholders/customers.
        
    - Regular feedback loops and adaptation based on feedback and changing priorities.
        
    - Prioritizing working software.
        
- **Characteristics:**
    
    - Iterative and Incremental.
        
    - Adaptive Planning (plans are expected to change).
        
    - Focus on individuals, collaboration, and communication.
        
    - Self-organizing, cross-functional teams.
        
    - Rapid response to change.
        
    - Customer involvement throughout the process.
        
- **Advantages:**
    
    - Highly flexible and adaptable to changing requirements, even late in development.
        
    - Faster delivery of usable features (Minimum Viable Products - MVPs).
        
    - Improved customer satisfaction due to close collaboration and frequent demos.
        
    - Better visibility and risk management through short cycles.
        
    - Promotes teamwork and continuous improvement.
        
- **Disadvantages:**
    
    - Requires strong commitment and collaboration from the team and customer.
        
    - Less predictable regarding final scope, cost, and timeline at the very beginning.
        
    - Can be challenging for large, distributed teams (though scalable frameworks exist).
        
    - Documentation might be less comprehensive if not actively managed ("working software over comprehensive documentation").
        
    - Requires experienced and disciplined team members.
        
- **When to Use:**
    
    - Projects where requirements are expected to evolve or are complex and uncertain.
        
    - Environments needing rapid delivery and quick adaptation to market changes.
        
    - Projects where close customer collaboration is possible and desired.
        
    - Most common approach for software product development today.