Functional and non-functional requirements are two fundamental categories used to describe the desired capabilities and characteristics of a software system. They represent different perspectives on what the system should do and how it should perform.  Here's a breakdown based on common software engineering principles and practices:

**Functional Requirements:**

* **Definition:** Describe *what* the system should do; the specific functions and services it provides to users.  These are the core features that deliver value to the user.
* **Focus:** User tasks, system behavior, input/output, calculations, data manipulation, and other specific actions the system performs.
* **Examples:**
    * The system shall allow users to log in with a username and password.
    * The system shall calculate the total price of items in a shopping cart.
    * The system shall generate reports in PDF format.
    * The system shall allow users to search for products by keyword.
* **Characteristics:**
    * Specific and detailed.
    * Testable and verifiable.  You should be able to write test cases to confirm that the functional requirement is met.
    * Prioritized based on user needs.
* **How to Elicit:**  Through user interviews, surveys, use cases, scenarios, and analysis of existing systems.


**Non-Functional Requirements (NFRs):**

* **Definition:** Describe *how* the system should perform; the qualities and constraints that apply to the system as a whole. These are not specific features but rather attributes that affect the user experience and the system's overall operation.
* **Focus:** Performance, security, usability, reliability, maintainability, scalability, portability, and other system-wide characteristics.
* **Examples:**
    * The system shall respond to user requests within 2 seconds.
    * The system shall be accessible to users with disabilities.
    * The system shall be secure against unauthorized access.
    * The system shall be able to handle 1000 concurrent users.
* **Characteristics:**
    * Often expressed as constraints or quality attributes.
    * More difficult to test directly, often requiring specialized testing techniques (e.g., performance testing, security testing).
    * Can be more critical than functional requirements. Failure to meet an NFR can make the entire system unusable.
* **Categories (FURPS+):**  A common way to categorize NFRs is FURPS+:
    * **Functionality (yes, some overlap with functional requirements):**  Features, capabilities, security.
    * **Usability:**  Human factors, aesthetics, consistency, documentation.
    * **Reliability:**  Frequency of failure, recoverability, predictability.
    * **Performance:**  Speed, response time, resource usage, throughput.
    * **Supportability:**  Maintainability, adaptability, serviceability.
    * **(+) Other:**  This can include things like scalability, security, portability, implementation, interface, legal, business rules.
* **How to Elicit:**  By carefully considering user expectations, business goals, technical constraints, and industry standards.



**Key Differences Summarized:**

| Feature         | Functional Requirements                        | Non-Functional Requirements                    |
|-----------------|------------------------------------------------|-------------------------------------------------|
| **What vs. How** | What the system does                           | How the system performs                         |
| **Focus**        | Specific features and services                   | System-wide qualities and constraints            |
| **Examples**     | Login, calculations, reports                      | Performance, security, usability, reliability      |
| **Testability** | Easier to test directly                          | More difficult to test, requires specialized testing |
| **Criticality**  | Important for user value                      | Can be critical for system usability              |


**Relationship and Overlap:**

While distinct, functional and non-functional requirements are related and can sometimes overlap. For example, a security requirement (NFR) might necessitate specific functionalities (e.g., user authentication, access control).  It's important to clearly distinguish between the two categories during requirements elicitation and documentation to ensure all aspects of the system are adequately addressed.
