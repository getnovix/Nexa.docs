Nexa — Built by Ibrahim, an 18-Year-Old Sudanese Developer

«Project: Nexa
Developer: Ibrahim
Background: Self-taught developer from Sudan
Started learning programming: Around age 12
Project status: Under active development
Last updated: October 13, 2026»

---

1. What Is Nexa?

Nexa is a software project being developed with the long-term goal of building financial and digital commerce services for users in Sudan and, potentially, other markets in the region.

The broader vision includes a digital wallet, USDT-related functionality, a marketplace, seller accounts, transaction management, and an escrow-style system for eligible transactions.

The project is part of a larger vision under Novix, a brand intended to support multiple software products over time.

However, there is an important distinction between a product vision and a working product.

Not every feature described in this document is implemented, tested, or ready for public use. The implementation status of individual components must be established by examining the actual source code, tests, integrations, and deployment environment.

This README is intended to document the project honestly as it develops, rather than present future plans as completed achievements.

2. About the Developer

Ibrahim is an 18-year-old self-taught developer from Sudan. He began learning programming at approximately 12 years old.

His learning journey has not followed a conventional academic or professional software engineering path. Financial limitations and personal responsibilities have affected his education and the time he can dedicate to programming.

He continues learning while working toward building software products of his own.

Nexa is an important part of that journey. It represents an attempt to turn programming knowledge into a structured software project involving backend development, databases, authentication, financial workflows, and user-facing services.

The project's value should ultimately be evaluated through its implementation, documentation, reliability, and development history—not through the developer's age or personal circumstances.

Being young or self-taught does not automatically make a project impressive or reliable. Equally, those circumstances do not make a developer's work invalid. The code and evidence should speak for themselves.

3. Technical Stack and Learning

The project involves learning and applying several technologies, including:

- Python: Backend programming and application logic.
- FastAPI: Building HTTP APIs and organizing backend routes.
- PostgreSQL: Relational data storage and database-backed application features.
- SQL: Creating, querying, and updating structured data.
- JWT: A token format that can be used in authentication systems.
- Bash: Working with command-line environments and development or server tasks.
- Git and GitHub: Source control and project history, where configured and used.
- Frontend development: Building user interfaces and connecting them to backend APIs.

The presence of a technology in this list describes the project's technical direction or the developer's work with that technology. It does not, by itself, prove that every component is fully integrated or production-ready.

For example, using FastAPI does not automatically make an API secure. Using PostgreSQL does not automatically make financial transactions correct. Using JWT does not guarantee that authentication and authorization are implemented properly.

Each of these areas requires appropriate implementation and testing.

4. What the Backend Is Supposed to Do

A financial application needs more than screens and buttons.

Its backend must define how users are identified, how requests are validated, how data is stored, and how operations are permitted or rejected.

For Nexa, the relevant areas include:

Authentication and user accounts

The application needs a reliable way to register users, authenticate them, and determine which account is making a request.

If JWT-based authentication is used, the implementation must also handle token validation, expiration, signing keys, and authorization checks.

A token should not be treated as proof that a request is permitted to perform every operation.

Database operations

PostgreSQL can store structured information such as user records, account balances, transactions, and marketplace data.

The database schema and application logic must work together to preserve relationships and enforce the required constraints.

Database usage alone is not evidence that all financial invariants are enforced.

Transactions and balances

A wallet must prevent invalid balance changes and handle concurrent operations correctly.

For example, if an account has 100 units and attempts to transfer 80 units twice at nearly the same time, the system must not allow both operations to spend the same funds.

Depending on the design, appropriate transaction boundaries, database constraints, concurrency controls, and idempotency mechanisms may be needed.

The correctness of these controls must be demonstrated by inspecting the implementation and testing relevant failure scenarios.

API organization

FastAPI supports separating application functionality into routers and modules. This can make a growing application easier to understand and maintain.

However, importing a router into the main application only establishes that the application is configured to include it. It does not independently prove that every endpoint in that router works correctly.

The same standard applies to every component of Nexa: implementation claims should match the available evidence.

5. Wallet, USDT, and Financial Features

The long-term Nexa vision includes digital wallet functionality and support for USDT-related services.

Blockchain-related plans have included networks such as TRON and BNB Smart Chain. The exact networks and features available at any particular time must be verified against the current implementation.

Several distinct capabilities should not be confused:

- An internal account balance is not the same as a blockchain wallet.
- Recording a transaction in a database is not the same as settling a blockchain transaction.
- Displaying a deposit address is not the same as securely processing deposits.
- Supporting a token on one network does not establish support for that token on another network.
- A planned integration with a payment provider is not an operational integration.

Before any wallet feature can be considered ready for real financial use, its transaction lifecycle, reconciliation, failure handling, security controls, and operational requirements need to be evaluated.

This documentation does not claim that Nexa has completed those requirements merely because they are part of the product vision.

6. Marketplace and Escrow Vision

Another part of Nexa's intended functionality is a marketplace where users can list products and conduct transactions.

The broader design includes seller accounts, product information, order management, and a mechanism intended to hold funds until the relevant transaction conditions have been satisfied.

This is commonly described as an escrow-style workflow.

A trustworthy implementation requires more than a field that marks an order as pending. It must define who controls the funds, which events permit their release or return, how duplicate requests are handled, and how disputes are resolved.

The actual status of each marketplace and escrow component should be established from the current source code and tests.

Until those controls have been implemented and verified, escrow should be described as a design goal or work in progress rather than a proven financial protection mechanism.

7. Researching Banking Websites and Security

During the learning process, I have been interested in how financial services and banking websites present their products, organize their user experiences, and handle common account-related workflows.

There is an important distinction between researching a publicly accessible website and conducting a security assessment.

Visiting or examining a banking website does not, by itself, demonstrate that its security has been tested. It also does not establish that vulnerabilities have been found, exploited, or responsibly disclosed.

I do not claim to have discovered banking vulnerabilities, bypassed banking security, or conducted authorized penetration testing unless there is specific evidence supporting such a claim.

Any future security testing should be limited to systems for which the necessary authorization has been obtained.

For Nexa itself, security should be treated as an engineering responsibility requiring appropriate testing, access controls, secret management, database protection, and review of financial workflows.

Security claims should be based on verifiable work, not on an association with banking websites or on the complexity of the technologies used.

8. AI Assistance, Open-Source Software, and Original Work

Modern software development involves many resources: official documentation, tutorials, community discussions, open-source libraries, code examples, debugging tools, and AI-assisted development tools.

I do not consider using these resources inherently dishonest. Learning from them is a normal part of software development.

At the same time, the origin of code matters, and claims about authorship should be accurate.

The following distinctions are important:

Learning from documentation means using technical references to understand how a technology works.

Using open-source dependencies means building on existing software according to its applicable license and requirements.

Adapting an example means modifying or integrating code that originated elsewhere. When attribution or license compliance is required, it should be provided.

Using AI assistance may involve asking for explanations, debugging help, implementation suggestions, or code review. Such assistance does not, on its own, establish that the resulting code is original, correct, secure, or entirely written by the developer.

Building a project involves making design decisions, understanding how components fit together, integrating them, testing their behavior, identifying failures, and maintaining the resulting system.

These activities can overlap. Their exact contribution depends on the work performed.

I want Nexa to be judged through its actual source code and development evidence rather than assumptions based solely on its appearance, the technologies it uses, or the fact that AI tools are available.

I also do not claim that every line of code was written without external help unless that claim can be supported.

Where third-party code, libraries, or substantial adapted examples are used, their origin and licensing requirements should be handled appropriately.

The purpose of this section is not to insist that the project must be considered original. It is to make the standard of evaluation clear: inspect the implementation, its dependencies, and its history.

9. A Living Project, Not a Finished Product

Nexa is being developed over time.

Its implementation, architecture, documentation, and feature set may change as the developer learns more and encounters technical limitations.

A feature that is incomplete today may be implemented later. A design that appears reasonable today may need to be revised after testing. A component that works in a development environment may still require substantial work before it can be used reliably in production.

For that reason, the project's status should be evaluated at a particular point in time.

Three-month review

A review approximately three months after this document's publication should examine the changes made during that period.

Useful evidence includes:

- New source code and documented changes.
- Features that have moved from planning to implementation.
- Tests added and the results they produce.
- Bugs discovered and corrected.
- Database and API changes.
- Features that remain incomplete and the reasons they remain incomplete.

The purpose is to record actual progress, including setbacks, rather than guarantee a particular outcome in advance.

Six-month review

A further review approximately six months after publication should evaluate the project's development over the longer period.

It should examine the source history, implementation status, test coverage, architectural changes, and any available deployment or integration evidence.

It should also document features that were postponed, abandoned, or redesigned.

Neither review should assume that the project has succeeded merely because time has passed.

Progress should be demonstrated through changes that can be inspected and explained.

10. Evidence and Verification

This README is a project description, not an independent technical audit.

Different claims require different kinds of evidence.

Claim| Useful evidence
An API endpoint exists| Source code and route definitions
An endpoint behaves correctly| Tests and reproducible results
Authentication is implemented| Authentication code and tests of relevant cases
A database schema exists| Schema definitions and migrations
Transactions handle concurrent requests| Implementation details and concurrency tests
A blockchain integration works| Integration code and verifiable test results
A payment provider is integrated| Provider configuration, integration code, and successful authorized test transactions
A feature is deployed| Deployment information and evidence that the feature is operational
Code was developed over time| Version-control history and dated project records
Third-party software is used| Dependency declarations, licenses, and source references

No single item of evidence necessarily proves every aspect of a claim.

For example, a successful demonstration may establish that one workflow worked under the demonstrated conditions. It does not establish that the system is secure against every attack or reliable under every possible failure.

Likewise, a Git commit history can help document development activity, but it is not conclusive proof of who originally authored every line.

The goal is to make technical claims proportionate to the evidence available.

11. Current Limitations

Nexa should not be described as a fully operational financial platform simply because its long-term design includes financial services.

Unless independently established by the current implementation, the following should not be assumed:

- That all planned features are implemented.
- That all endpoints have been tested.
- That all financial operations are safe under concurrent requests.
- That all security requirements have been satisfied.
- That real deposits, withdrawals, or blockchain transfers are operational.
- That payment-provider integrations have been approved or deployed.
- That escrow guarantees successful dispute resolution.
- That the platform is ready to handle real customer funds.

These are engineering requirements to verify, not accomplishments to infer from a feature list.

If the project later satisfies particular requirements, the documentation should be updated to describe what was implemented and what evidence supports the change.

12. Development Philosophy

The aim is to build Nexa by learning, implementing, testing, documenting, and improving.

The project is not presented as proof that an 18-year-old has already solved every difficult problem in financial software engineering.

Instead, it documents an ongoing attempt to develop those skills through a substantial project.

I expect to make mistakes. I expect to encounter problems that require redesign. I also expect that some parts of the project will take longer than originally planned.

What matters is whether those problems are addressed honestly and whether the software improves through verifiable work.

I would rather document an incomplete feature accurately than describe it as finished when it is not.

I would rather acknowledge uncertainty than make a security claim that I cannot substantiate.

And I would rather have the implementation examined critically than ask people to accept the project based on a personal story.

13. Closing Statement

Nexa is a work in progress built as part of a longer journey in software development.

Its ambitions are substantial, but ambition is not evidence of completion. Its technical stack provides tools for building software, but the tools themselves do not guarantee quality. Its developer's personal circumstances explain part of the journey, but they do not replace technical verification.

The most useful way to evaluate Nexa is to examine the code, understand the architecture, review the dependencies, run the available tests, and compare the documented status with the actual implementation.

As development continues, this README should evolve alongside the project.

The goal is not to claim more than has been achieved. The goal is to build something real, document it honestly, and make its progress verifiable.
