![[Pasted image 20260309232501.png]]
Primary Key: underlined
Composite Attribute: branches
Multi-valued Attribute: double border
Derived Attribute: dotted line

Relationships: diamond
Partial/Total Participation: single/double line
Relationship Attribute: an attribute about the relationship (branches from relationship)
Relationship Cardinality: # of instances of an entity from a relation that can be associated with the relation (1:1, 1:N, 1:M)

Weak Entity: entity that cannot be uniquely identified by its attributes alone (double border)
Identifying Relationship: A relationship that serves to uniquely identify the weak entity

## Designing ER Diagrams

> [!example] Company Data Storage Requirements
> The company is organized into branches. Each branch has a unique number, a name, and a particular employee who manages it.
> 
> The company makes it’s money by selling to clients. Each client has a name and a unique number to identify it.
> 
> The foundation of the company is it’s employees. Each employee has a name, birthday, sex, salary and a unique number.
> 
> An employee can work for one branch at a time, and each branch will be managed by one of the employees that work there. We’ll also want to keep track of when the current manager started as manager.
> 
> An employee can act as a supervisor for other employees at the branch, an employee may also act as the supervisor for employees at other branches. An employee can have at most one supervisor.
> 
> A branch may handle a number of clients, with each client having a name and a unique number to identify it. A single client may only be handled by one branch at a time.
> 
> Employees can work with clients controlled by their branch to sell them stuff. If nescessary multiple employees can work with the same client. We’ll want to keep track of how many dollars worth of stuff each employee sells to each client they work with.
> 
> Many branches will need to work with suppliers to buy inventory. For each supplier we’ll keep track of their name and the type of product they’re selling the branch. A single supplier may supply products to multiple branches.
> 
![[Pasted image 20260309234117.png]]

## ERD to Schema
#### Step 1: Regular Entity
![[Pasted image 20260309234452.png]]
![[Pasted image 20260309234509.png]]

#### Step 2: Weak Entity
![[Pasted image 20260309234554.png]]
![[Pasted image 20260309234659.png]]

#### Step 3: Binary 1:1 Relationship Types
![[Pasted image 20260309234731.png]]
![[Pasted image 20260309235231.png]]

> [!question] Why favor total participation?
> If we add `branch_id` as a foreign key into employee, non-manager employees will have null values for that attribute. But if we favor total participation (add `mgr_id` into branch), the column will never be null because every branch has a manager (total participation).

#### Step 4: Binary 1:N Relationship Types
![[Pasted image 20260309235403.png]]
![[Pasted image 20260309235800.png]]

> [!question] Why choose 1 side?
> There is no way to do it the other way. For instance, a branch can have many employees, but we can't list every employee's `emp_id` in a single entry.

#### Step 5: Binary N:M Relationship Types
![[Pasted image 20260309235953.png]]
![[Pasted image 20260310000152.png]]

#### Final Schema:
![[Pasted image 20260310000416.png]]
