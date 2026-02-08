# Payment House - Glossary

Domain terminology and definitions for the project.

**Last Updated:** 2026-02-08

---

| Term | Definition | Context |
|------|------------|---------|
| MEPS+ | MAS Electronic Payment System Plus | Singapore's RTGS system |
| FAST | Fast And Secure Transfers | Singapore's real-time retail payment system |
| CHATS | Clearing House Automated Transfer System | Hong Kong's RTGS system |
| FPS | Faster Payments Service | UK's real-time retail payment system |
| CHAPS | Clearing House Automated Payment System | UK's high-value RTGS system |
| NEFT | National Electronic Funds Transfer | India's deferred net settlement system |
| RTGS | Real-Time Gross Settlement | India's high-value payment system (RBI) |
| UPI | Unified Payments Interface | India's real-time retail payment system (NPCI) |
| IMPS | Immediate Payment Service | India's instant interbank transfer (NPCI) |
| SWIFT gpi | SWIFT Global Payments Innovation | Cross-border payments with tracking |
| ISO 20022 | International standard for financial messaging | XML-based message format |
| pacs.008 | FI to FI Customer Credit Transfer | ISO 20022 payment message |
| pacs.002 | Payment Status Report | ISO 20022 status message |
| pain.001 | Customer Credit Transfer Initiation | ISO 20022 initiation message |
| MT103 | SWIFT Single Customer Credit Transfer | Legacy SWIFT format |
| DLQ | Dead Letter Queue | Destination for unprocessable messages |
| CDC | Change Data Capture | Real-time database change streaming (Debezium) |
| Saga Pattern | Distributed transaction management | Compensating actions for multi-service transactions |
| Circuit Breaker | Resilience pattern | Prevents cascading failures by failing fast |
| ACL | Anti-Corruption Layer | Translates between domain model and external systems |
| DDD | Domain-Driven Design | Architecture approach using bounded contexts |
| Nostro/Vostro | "Our account at their bank" / "Their account at our bank" | Correspondent banking accounts |
| Outbox Pattern | Transactional event publishing | Business state + event in single DB transaction |
| OFAC | Office of Foreign Assets Control | US sanctions list |
| AML | Anti-Money Laundering | Transaction monitoring for suspicious activity |
| PEP | Politically Exposed Persons | High-risk individual screening |
| MAS | Monetary Authority of Singapore | Singapore financial regulator |
| HKMA | Hong Kong Monetary Authority | Hong Kong financial regulator |
| RBI | Reserve Bank of India | India's central bank and regulator |
| FCA | Financial Conduct Authority | UK financial regulator |
| STR | Suspicious Transaction Report | Regulatory filing for suspicious activity |

---

*Add terms as they emerge during design and development.*
