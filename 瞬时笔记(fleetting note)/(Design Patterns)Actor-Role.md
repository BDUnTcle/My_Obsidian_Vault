---
create date: 2024-03-26
tags:
  - review
  - CS
  - CS/DesignPattern
  - 程序员
modification date: 2024-03-26T19:43:00
type: LearningNote
sr-due: 2024-03-29
sr-interval: 3
sr-ease: 250
---

# Background & Materials
---
# Real Problem
A database keeps track of all of the people a company interacts with. This includes **employees**, **suppliers**, and **customers**. But some people might be employees and customers. Some might be employees, customers, and suppliers. <mark style="background: #FFB8EBA6;">This can lead to information redundancy</mark>. For example, a person's address might be included with is employee, customer, and supplier record. If this person moves, we have to remember to update his address in all three places or the database becomes inconsistent.
# Solution
Decouples actors (persons or organizations) from the many roles they may play (customer, employee, supplier, etc.)
![[Pasted image 20240326194716.png|600]]
- Actors: encapsulate **personal information** such as name, address, and phone number.
- A role: encapsulates **role-specific information** such as an employee's salary, a customer's shopping cart, or a supplier's invoices.

---
# Flash Cards
