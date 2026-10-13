Nexa — Built by Ibrahim, an 18-Year-Old Sudanese Developer

«A long-term vision for digital finance and e-commerce in Sudan.

Built by a self-taught developer who began learning programming at approximately 12 years old.

Parent brand: Novix
Project: Nexa
Project status: Ongoing development
Documentation date: October 13, 2026»

---

1. Introduction

Nexa is a software project focused on the intersection of digital finance, peer-to-peer transactions, and e-commerce.

Its long-term goal is to develop an integrated platform through which users can manage digital balances, exchange value, purchase products, operate online stores, and access related digital services.

The project is being developed with the Sudanese market in mind, where practical digital commerce solutions could help address challenges involving payments, access to online services, and interactions between buyers and sellers.

The ambition is substantial: to build a major e-commerce ecosystem in Sudan and, over time, explore opportunities in other markets in the region.

However, Nexa is an ongoing engineering project. Its long-term vision must not be confused with the features currently implemented, independently verified, or ready for production.

This README documents the product's intended direction, its technical principles, and the reasoning behind its design. Specific implementation claims should be evaluated against the relevant source code, tests, integrations, and deployment evidence.

2. About the Developer

Ibrahim is an 18-year-old self-taught developer from Sudan who began learning programming at approximately 12 years old.

His journey has taken place alongside financial limitations, work responsibilities, and the practical difficulties of learning software engineering without following a conventional academic path.

He is building Nexa as an opportunity to apply what he learns to a substantial software system rather than limiting his work to isolated exercises.

His interests include Python development, backend engineering, databases, API design, financial workflows, application architecture, and the challenges of building reliable digital services.

Nexa is not presented as proof that its developer has mastered every aspect of software engineering. It is a long-term project through which he is developing his skills while attempting to solve practical problems.

The objective is to turn learning into working software, improve that software over time, and document the process honestly.

3. The Problem Nexa Wants to Address

Digital commerce depends on more than the existence of an online storefront.

A buyer and a seller may need a way to discover each other, agree on a price, arrange payment, confirm fulfillment, and resolve a disagreement if something goes wrong.

In addition, users may encounter separate systems for payments, product listings, digital services, and account management.

Nexa explores whether some of these activities can be brought together in a coherent platform.

The underlying questions include:

- How can buyers and sellers interact through a structured digital marketplace?
- How can users access practical payment and transaction workflows?
- How can a marketplace handle orders and disputes without relying entirely on informal communication?
- How can a seller manage products, availability, and orders?
- How can digital products be delivered after a successful purchase?
- How can transaction records and account balances remain consistent?
- How can the platform communicate clearly with users when something fails?

These are product and engineering problems, not problems that can be solved merely by creating an attractive interface.

The aim is to develop software that addresses them through defined workflows, appropriate safeguards, and continuous improvement.

4. Nexa and Novix

Novix is the broader brand and long-term product vision.

Nexa is one product within that ecosystem.

The broader Novix vision has included additional products and services such as:

- Novix AI.
- Novix Chat.
- Novix Trade.
- Novix Cloud.
- Nexa Developer.

These names describe the wider product direction. They should not automatically be interpreted as evidence that every proposed product has been launched or is commercially available.

Nexa itself is intended to bring together financial and commerce-related capabilities that would otherwise be distributed across separate services.

The distinction is straightforward:

Novix represents the broader ecosystem. Nexa is the product being developed around digital finance and commerce.

5. Nexa's Product Architecture

The long-term Nexa vision can be understood as a set of related components.

5.1 Digital wallet

The wallet is intended to provide users with account and balance functionality.

Depending on the implemented version, this may include internal balances, transaction history, deposits, withdrawals, and transfers.

A wallet interface must be supported by backend logic that validates requests and protects the integrity of account records.

A balance displayed on the screen is not sufficient evidence that the underlying financial workflow is correct. The database operations, transaction rules, and relevant failure cases must also be examined.

5.2 USDT and blockchain integration

Nexa's broader technical direction includes USDT-related functionality and blockchain networks such as TRON and BNB Smart Chain. Polygon has also been considered in the development roadmap.

Blockchain integration introduces requirements that differ from ordinary database-backed transfers.

These include transaction confirmation, network-specific addresses, transaction identifiers, deposit monitoring, withdrawal processing, network fees, reconciliation, and the handling of failed or delayed transactions.

Support for one network does not imply support for every network.

Similarly, storing an internal transaction record does not establish that a blockchain transfer has been broadcast, confirmed, or settled.

The supported networks and operational status of each blockchain feature must be verified against the current implementation.

5.3 Internal balances and transaction records

An application may maintain internal account balances for transactions that take place within its own system.

Those balances must be handled consistently.

A sound design should define how balances change, how transaction records are created, how failed operations are reversed, and how duplicate requests are prevented from causing duplicate financial effects.

For financial operations, the implementation must also account for concurrent requests and other failure conditions.

PostgreSQL transactions, appropriate constraints, concurrency controls, and idempotency mechanisms may form part of that design.

The precise implementation should be assessed from the actual code and tests.

5.4 Transaction history and notifications

Users need to understand what happened to their transactions.

Transaction history can help communicate the amount, direction, status, and time of an operation.

Notifications can communicate relevant events, such as a transaction changing status or an order requiring attention.

These features should reflect the actual backend state rather than rely exclusively on frontend assumptions.

Where real-time updates are implemented, the system should also account for reconnection, authentication, and consistency between the latest server state and the displayed information.

6. Peer-to-Peer Trading: Why P2P Matters

Peer-to-peer trading, commonly called P2P, is an important part of Nexa's broader vision.

P2P allows users to interact with other users to exchange value according to defined platform rules.

Depending on the supported markets and services, the model may involve buyers and sellers agreeing on an exchange, such as exchanging a digital asset for an accepted local payment method.

The platform's role is to provide the infrastructure through which eligible participants can discover offers, communicate, follow transaction rules, and access available dispute-handling processes.

The exact currencies, payment methods, eligibility requirements, and supported transaction types depend on the operational model and applicable legal requirements.

Why build P2P into Nexa?

A P2P system can address several practical needs.

Price discovery: Users can compare available offers instead of relying on a single displayed exchange price.

Participant choice: Buyers and sellers can evaluate the offers available to them.

Structured transactions: Orders can follow a defined sequence rather than depend entirely on informal messages.

Transaction records: The platform can record the stages of an order and the actions taken by the participants.

Dispute handling: A defined process can provide a way to report problems and review available transaction evidence.

Marketplace integration: P2P can complement other platform services where the business model and legal requirements permit it.

These benefits depend on implementation quality. A P2P interface alone does not establish that a transaction is safe or that either participant will fulfill an agreement.

How a P2P transaction may work

A proposed P2P workflow could follow these stages:

1. A seller publishes an offer with its price, limits, and permitted payment methods.
2. A buyer selects an offer and creates an order.
3. The system validates the order against the offer's rules and availability.
4. Where an authorized escrow mechanism is available, the relevant digital assets may be reserved or held under predefined conditions.
5. The buyer and seller follow the agreed payment process.
6. The system receives and evaluates the required confirmation or evidence.
7. The transaction is completed according to the applicable rules, or it enters a dispute or cancellation workflow.
8. The transaction outcome is recorded for future reference.

Not every P2P model requires the same sequence. The final workflow must reflect the actual custody arrangement, payment methods, applicable law, and implemented controls.

A critical design question is whether Nexa merely coordinates transactions or also controls assets during part of the transaction. That distinction affects both the architecture and the platform's legal obligations.

P2P is not a guarantee of safety

A marketplace can reduce ambiguity by defining transaction rules, preserving records, and providing structured dispute handling.

It cannot eliminate every form of fraud, payment reversal, identity misuse, or participant misconduct.

The platform must define its responsibilities and communicate its limitations clearly.

7. Why Nexa Is Designed as an Intermediary Platform

A central product-design question is the role Nexa should play in transactions between users.

The intended model is to provide a digital platform that connects participants and coordinates supported workflows, rather than simply presenting itself as the direct buyer or seller of every item exchanged.

For example, a marketplace may connect an independent seller with a buyer, provide order-management tools, record the transaction, and offer a defined process for handling disputes.

A P2P service may similarly provide an environment in which eligible users discover offers and follow structured transaction procedures.

This model is intended to make interactions more organized and traceable.

It also helps clarify which responsibilities belong to the buyer, which belong to the seller, and which belong to the platform.

However, being an intermediary does not automatically remove legal or regulatory obligations.

Depending on the jurisdiction, business model, assets involved, and degree of control over funds, a platform may still be subject to requirements concerning payments, custody, money transmission, consumer protection, identity verification, financial crime prevention, data protection, or other regulated activities.

The relevant requirements must be assessed before launching affected services.

The architecture should therefore be designed around the actual business model and the obligations that apply to it—not around an assumption that calling a service an intermediary creates a legal exemption.

The intended objective is to build a useful platform with clearly defined responsibilities, appropriate authorization, and transparent operating rules.

8. Escrow and Transaction Protection

The Nexa vision includes an escrow-style mechanism for eligible marketplace or P2P transactions.

In a typical escrow workflow, the relevant funds or assets are held or restricted under predefined conditions while the parties complete their obligations.

For example, a buyer may place an order for a product. Instead of immediately making the proceeds available to the seller, the system may reserve the relevant amount until the required fulfillment condition is satisfied.

The intended purpose is to reduce certain risks associated with transactions between parties who do not necessarily know or trust each other.

A proper implementation must define:

- Which assets are held and by whom.
- Whether the platform has custody or uses an authorized third-party arrangement.
- When a transaction can be funded.
- Which conditions permit release.
- How cancellation and refunds work.
- What happens when a participant stops responding.
- How disputes are initiated and reviewed.
- How duplicate requests and conflicting state changes are prevented.
- How all changes are recorded and reconciled.

Escrow is not simply a database field or an order status.

If the underlying assets are not actually held or restricted according to the stated rules, the system must not imply that they are protected by escrow.

The mechanism must also comply with the legal requirements applicable to the actual custody and transaction model.

9. Marketplace and Seller Stores

Nexa is intended to include a marketplace where users can discover products and interact with sellers.

The broader product design includes individual seller storefronts and product-management functionality.

Depending on the implemented version, seller tools may include:

- Store profiles and descriptions.
- Product names, images, and descriptions.
- Product pricing and available quantities.
- Inventory management.
- Order tracking.
- Delivery options.
- Seller information and relevant verification status.
- Transaction and fulfillment history.

A marketplace requires more than a product catalog.

The system must define how inventory is reserved, how orders change state, how duplicate orders are handled, and how cancellations or refunds affect both the order and its associated financial records.

It must also communicate the respective responsibilities of buyers, sellers, and the platform.

The long-term objective is to make it easier for sellers to participate in digital commerce without requiring each seller to build an independent online store and transaction system from scratch.

The current availability of individual store features should be established from the implementation.

10. Orders, Delivery, and Disputes

The marketplace vision includes structured order management.

An order may pass through stages such as creation, payment processing, fulfillment, delivery confirmation, completion, cancellation, or dispute review.

The exact states and permitted transitions must be defined in the backend.

For physical products, fulfillment may involve delivery arrangements and confirmation that the relevant product has been received.

For digital products, fulfillment may involve authorizing access to a download or delivering a digital item after a successful payment.

These workflows have different failure conditions and should not automatically share identical business rules.

Dispute handling

A dispute mechanism is intended to provide a structured process for situations in which a buyer and seller disagree about a transaction.

Depending on the final design, the process may involve:

1. Opening a dispute.
2. Recording the reason and relevant evidence.
3. Temporarily restricting certain transaction actions where legally and technically appropriate.
4. Reviewing the information available.
5. Applying the outcome permitted by the platform's rules.
6. Recording the decision and the resulting transaction state.

A dispute interface does not by itself establish fair or reliable dispute resolution. The platform needs defined procedures, appropriate permissions, evidence handling, and a process for reviewing decisions.

11. Digital Products and Services

The broader Nexa marketplace vision includes digital products, potentially including downloadable books and other digital goods.

Digital commerce introduces different requirements from the sale of physical products.

The platform may need to manage product availability, purchase authorization, download permissions, and the relationship between a successful transaction and access to the purchased item.

A download should not be authorized merely because a client claims to have paid. The server must validate the relevant transaction state and enforce access rules.

The product vision has also included keeping some digital book prices accessible, with a proposed price ceiling of approximately US$0.50 for the relevant category.

That figure is a product-design proposal, not a claim that every digital book currently follows that pricing rule.

The actual pricing policy and availability of digital products must be verified against the current implementation and commercial terms.

12. Currency Conversion and Pricing

Nexa's broader design includes exchange-rate functionality for displaying or calculating prices across supported currencies.

For example, a marketplace may need to convert a product's reference price into a locally displayed price.

A robust implementation must define:

- The source of the exchange rate.
- Who is permitted to change it.
- When a rate becomes effective.
- How prices are rounded.
- Whether a displayed price is indicative or binding.
- How existing orders are treated when rates change.
- How fees and margins are disclosed.
- How calculations are reproduced for auditing.

If administrators can control an exchange-rate parameter, changes should be authorized and recorded appropriately.

A displayed conversion is not necessarily a completed currency exchange. Actual exchange services may involve additional liquidity, settlement, operational, and regulatory requirements.

13. Deposits, Withdrawals, and External Providers

Nexa's broader financial-service vision includes possible integrations with payment providers and blockchain-related services.

An external provider may supply some of the infrastructure needed to accept payments, process withdrawals, or support other financial operations.

The exact responsibilities depend on the provider's API, contractual arrangement, permissions, and supported markets.

A provider integration is not complete merely because the application can send an HTTP request.

The implementation must address authentication, request validation, error handling, transaction status, duplicate callbacks, reconciliation, and the possibility that a request times out even though the provider has processed it.

Real-money services may also require provider approval, commercial agreements, licensing arrangements, or other authorization.

The current status of each integration must be verified independently.

14. Virtual Cards and Additional Financial Services

The longer-term product vision has included exploring virtual-card functionality through an appropriate external issuer or financial-services partner.

Such a feature would depend on the availability of a suitable provider, supported countries, identity and eligibility requirements, commercial terms, and applicable regulation.

Nexa should not be described as issuing its own Visa cards unless the actual operating arrangement supports that statement.

If card functionality is offered through a partner, the relationship and respective responsibilities should be described accurately.

The same principle applies to other financial services: the interface, provider integration, and legal authority to offer a service are separate requirements.

15. Customer Support and AI-Assisted Features

Nexa's product vision includes customer-support functionality.

This may involve a support conversation interface, structured support requests, user messages, and an administrative process for handling unresolved issues.

AI-assisted customer support has also been considered as a way to help users understand features, navigate common workflows, and receive explanations.

Such a system should communicate its limitations and avoid claiming that it can independently authorize financial transactions, reverse payments, or make binding dispute decisions unless those actions are explicitly supported and appropriately controlled.

AI should complement the platform's defined workflows rather than replace authorization checks or reliable transaction processing.

The existence and scope of any operational AI support feature must be verified against the current implementation.

16. Accounts, Devices, and Active Sessions

The broader application design includes account-management and session-management considerations.

A user may need to review active sessions or devices and, where supported, revoke access to a session that is no longer trusted.

These capabilities can help users understand where their account is active and manage access.

However, a session-management interface must be connected to actual server-side session or token controls.

Displaying a device list is not enough if the corresponding sessions cannot be reliably invalidated.

The implementation should define how authentication state is tracked, how revocation works, and how sensitive account changes are protected.

17. Administration and Operational Controls

A platform supporting multiple users, stores, and transaction types requires operational tools.

The Nexa vision includes an administrative interface for reviewing relevant users, transactions, marketplace activity, support requests, and disputes.

Depending on the implemented version, administrative capabilities may also include reviewing deposits or withdrawals, managing product availability, and changing permitted platform settings.

Administrative access should be protected through appropriate authentication, authorization, and audit logging.

Sensitive actions should have defined permissions, and changes affecting financial records should be traceable.

An administrative interface should not be treated as proof that operational controls are complete. The underlying permissions, transaction rules, and audit mechanisms must be evaluated separately.

18. Nexa Developer and the Broader Novix Ecosystem

The broader Novix vision has included developer-oriented services under the Nexa Developer concept.

The proposed direction includes tools that could help developers deploy applications and work with services such as databases, hosting, and SSL configuration.

This is a separate product direction from the core Nexa wallet and marketplace.

Building a developer platform would introduce additional engineering responsibilities, including resource isolation, access control, deployment reliability, usage limits, monitoring, and security.

It should therefore be treated as a separate workstream rather than assumed to be part of the current operational Nexa application.

19. Technical Stack

Technologies associated with the project's development include:

- Python.
- FastAPI.
- PostgreSQL.
- SQL.
- Bash.
- JWT-based authentication where implemented.
- Frontend technologies used by the current application.
- External APIs and blockchain infrastructure where integrated.

The exact stack can change as the project evolves.

Technology selection is only one part of engineering quality.

For example, FastAPI does not automatically provide secure authorization. PostgreSQL does not automatically prevent every business-logic error. JWT does not automatically guarantee safe session management.

The quality of the resulting system depends on how the components are implemented, integrated, tested, and maintained.

20. Code Authorship and AI-Assisted Reasoning

Ibrahim states that he writes 100% of Nexa's application code himself.

He does not use AI as a code generator for Nexa, and he does not describe the project as a collection of code copied from AI responses or assembled from open-source repositories.

His use of AI is primarily analytical.

He may share his own project files and ask an AI model to reason through hypothetical situations, such as:

- What might happen if two requests update the same balance concurrently?
- What happens if a transaction fails halfway through a workflow?
- How might one component affect another?
- What could happen if an external service responds slowly or becomes unavailable?
- Which failure cases might be overlooked in a particular design?
- Why would a specific result occur under a given set of assumptions?

The model provides possible outcomes and explanations. Ibrahim then uses that analysis to inform his own reasoning and development work.

The motivation is to explore more scenarios than he could comfortably enumerate mentally on his own, especially in a system involving multiple interacting components.

This is a form of analytical assistance, not a claim that AI can replace testing or prove that a design is correct.

AI-generated analysis can be incomplete or wrong. Its suggestions must be evaluated rather than accepted automatically.

Ibrahim's stated distinction is that he writes the code himself while using AI to help examine possible behaviors and consequences.

The project should therefore be evaluated through its source code, architecture, tests, and development evidence, rather than assuming that AI use necessarily means AI-generated code.

This statement describes the developer's account of his own workflow. It is not an independent authorship audit.

21. Open-Source Dependencies and Technical References

Software development frequently relies on established libraries, protocols, and technical documentation.

Using a dependency is different from claiming authorship of that dependency.

Nexa's dependencies should be identifiable through its dependency declarations and relevant licensing information.

Where external code is incorporated or adapted, applicable license and attribution requirements should be respected.

The developer's position is that he writes the project's application code himself and uses AI for analytical reasoning rather than copying generated implementations.

That claim should be understood alongside the project's actual dependencies and available development history.

No project should need to hide its dependencies or exaggerate its originality to demonstrate that meaningful engineering work has taken place.

22. Security and Reliability

Security is particularly important when software manages accounts, balances, payments, or transactions.

Nexa's intended engineering responsibilities include appropriate controls for authentication, authorization, input validation, database consistency, secret management, and error handling.

Depending on the supported features, additional controls may be needed for blockchain transactions, payment-provider callbacks, session revocation, administrative operations, and dispute workflows.

Security should be assessed through the actual implementation and suitable testing.

A successful demonstration does not prove that a system is secure against every attack. Likewise, the use of a particular framework does not establish that its configuration is secure.

Any security assessment should be conducted within an authorized scope.

Claims about security audits, penetration testing, certifications, or regulatory approval should only be made when supported by appropriate evidence.

23. Project Status and Honest Reporting

Nexa is a developing project, and its features may have different levels of maturity.

For clarity, project documentation should distinguish among:

Planned: The feature is part of the product direction but has not necessarily been implemented.

In development: Work is actively taking place, but the feature may be incomplete.

Implemented: Relevant code exists, although its correctness and completeness still need to be established.

Tested: Specific behavior has been tested under documented conditions.

Operational: The feature is deployed and functioning in its intended environment.

Production-ready: The feature has met the relevant engineering, operational, security, and compliance requirements for its intended use.

These categories are not interchangeable.

A feature should be described according to the evidence available at the time of publication.

The same principle applies to integrations, user numbers, commercial partnerships, security claims, and deployment status.

24. Three-Month and Six-Month Reviews

This documentation is intended to provide a point of reference for future development.

A review approximately three months after October 13, 2026, can examine changes made by approximately January 13, 2027.

A review approximately six months after that date of publication can examine progress by approximately April 13, 2027.

These are review points, not promises that specific features will be completed by those dates.

Useful evidence includes:

- Changes in source code and version history.
- New endpoints and database operations.
- Improvements to transaction handling.
- Features that have moved from planning to implementation.
- Tests and their results.
- External integrations that have become operational.
- Known limitations and unresolved technical problems.
- Decisions to redesign or abandon earlier ideas.

The purpose is to compare the project's actual evolution with its documented direction.

Progress should include both achievements and lessons learned.

25. Why Build Something This Ambitious?

Nexa is a substantial undertaking because its intended components interact with one another.

A marketplace needs order management. Order management interacts with payments. Payment workflows depend on consistent transaction records. Escrow introduces conditional release rules. P2P introduces interactions between participants. External providers introduce additional failure modes and dependencies.

These systems cannot be treated as entirely independent features.

Building them together requires careful design, testing, and a willingness to revise assumptions when the implementation exposes problems.

Ibrahim's motivation is to use programming to develop useful services and eventually contribute to a much larger digital commerce ecosystem in Sudan.

The ambition is not evidence that the project has already reached that destination.

It explains why he is willing to undertake the work required to explore it.

The project will be judged by what it becomes, how well it works, and whether its claims remain consistent with the available evidence.

26. Final Statement

Nexa is an ongoing attempt to build an integrated digital finance and e-commerce platform with a long-term focus on Sudan.

It brings together several challenging areas of software engineering: backend development, databases, account and transaction management, marketplace workflows, P2P interactions, and potential external financial integrations.

The developer's ambition is large, but the documentation does not treat future plans as completed achievements.

His stated development approach is to write the code himself and use AI as a reasoning tool for exploring hypothetical scenarios and understanding possible system behavior.

The project should be evaluated through its implementation, tests, dependencies, and documented progress.

The goal is not to claim that every problem has already been solved.

The goal is to build useful software, learn from the process, document the work honestly, and demonstrate progress over time.
