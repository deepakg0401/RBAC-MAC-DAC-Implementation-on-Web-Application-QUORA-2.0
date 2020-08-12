# RBAC, MAC, DAC Implementation on Web Application QUORA 2.0

## Question answering platform.

Implemented RBAC, MAC, DAC on a web application Quora 2.0,as in the web app their were different roles like admin,questioner,answerer etc. Therefore access was given according to the roles to ensure security of information.

## Characteristics and Policies [1]

- within the RBAC framework, a **user** is a person, a **role** is a collection of job functions, and an **operation** represents a particular mode of access to a set of one or more protected RBAC objects; 

- the type of operations and the objects that RBAC controls is dependent on the type of system in which it will be implemented, e.g. within a  transaction management system, operations would take the form of and exhibit all the properties of a transaction;

- roles can have overlapping responsibilities and privileges, i.e. users belonging to different roles may need to perform common operations. RBAC therefore supports the concept of role hierarchies; 

- a **role hierarchy** defines roles that have unique attributes and that may contain other roles, i.e. that one role may implicitly include the operations, constraints, and objects that are associated with another role; 

- **role authorisation** (association of user with a role) can be subject to the following:
    - the user can be given no more privilege than is necessary to perform his/her job **(principle of least privilege)**; 
    - the role in which the user is gaining membership is not mutually exclusive with another role for which the user already possesses membership **(static separation of duty)**; & 
    - the numerical limitation that exists for role membership cannot be exceeded **(cardinality property)**; 
 
- **role activation** involves the mapping of a user to one or possibly many  roles. A user initiates a session during which the user is associated with a subset of roles for which that user has membership. A particular role for a user can be activated if: 
    - the user is authorised for the role being proposed for activation; 
    - the activation of the proposed role is not mutually exclusive with any other active role(s) of the user; 
    - the proposed operation is authorised for the role that is being proposed for activation; & 
    - the operation being proposed is consistent within a mandatory sequence of operations; 

- **role execution** of an operation can take place only if the subject is acting within an active role, i.e. once it is determined that a role is part of the authorised role set for the subject; 

- **dynamic separation of duty** can be provided with RBAC as long as the following rule is satisfied: a subject can become active in a new role  only if the proposed role is not mutually exclusive with any of the roles in which the subject is currently active; 

- **operation authorisation** can only be granted to a subject if the operation is authorised for the subjects proposed active role; 

- **operational separation of duty** requires that for all the operations associated with a particular business function, no single user can be allowed to perform all of these operations. In other words, a role can be associated with an operation of business function only if the role is an authorised role for the subject and the role had not been assigned previously to all of the other operations; 

- **object access authorisation** requires subject access to RBAC objects to be controlled. This ensures enforcement of enterprise policies to RBAC objects. A subject can access an object only if: 
    - the role is part of the subjects current **active role set**; 
    - the role is allowed to perform the operation; & 
    - the operation to access the object is authorised. 

## Implementation

**Database**    Four database tables are created to store role and permission information: the `roles` table stores a role ID and role name, the `permissions` table stores a permission ID and description, the `role_perm` table associates which permissions belong to which roles, and the `user_role` table associates which roles are assigned to which users.

**Model Classes**   `Role` class is to return a role object that is populated with each roles corresponding permissions. `PrivilegedUser` class extends existing User class (reuse existing code logic for managing users) and then add some additional methods specifically working with privileges. `Permission` class is to add and delete permissions. `Database` class to connect with database.

**Password**    Passwords are stored using 128-bit SHA512 algorithm. The algorithm is considered computationally expensive to brute-force password (in the event your database is compromised).

## How to Run Project
- **1.** Install latest django version
- **2.** Install python
- **3.** Setup a virtual environment
- **4.** Install mysql client
- **5.** Inside the quora2.0/quora directory, run the following command:
          - **a.** python manage.py runserver
- **6.** Use the following login credentials or create a new user:
         - **a.** Username- dtushar279@gmail.com
          -**b.** Password- tushar123
- **7.** To view screenshots of the web application:
         - **a.** Open quora2.0/Quora2.0_SS.pdf


