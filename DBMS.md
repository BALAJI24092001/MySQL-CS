# DATABASE MANAGEMENT SYSTEM (DBMS)

A database management system (DBMS) is a collection of programs that enables users to create and maintain a database. The DBMS is a general-purpose software system that facilitates the processes of defining, constructing, manipulating and sharing databases among various users and applications.

_**Contents**_:

1. Overview of DBMS
2. ER Diagram
   1. Entities and Attributes
   2. ER Diagram Symbols
3. Relational Algebra
4. Relational Calculus
   1. Tuple Relational Calculus
   2. Domain Relational Calculus
5. Functional Dependency and Decomposition
   1. Amstrong's Axioms
   2. Lossless Decomposition
6. Normalization and Normal Forms
   1. Anomalies
   2. Types of Anomalies
   3. 1 NF
   4. 2 NF
   5. 3 NF
   6. BCNF
   7. 4 NF
   8. 5 NF
   9. Advantages and Disadvantages

---

_**Data Model:**_ A data model is a collection of concepts that can be used to describe the structure of a database. It provides the necessary means to achieve abstraction.

_**Schema**_: In any data model, it is important to distinguish between the description of the database and the database itself. The description of a database is called the database schema, which is specified during database design and is not expected to change frequently.

## Overview of DBMS

1. _**Requirements Analysis:**_ <br>
   The very first step in designing a database application is to understand what data is to be stored in the database, what applications must be built on top of it, and what operations are most frequent and subject to performance requirements. In other words, we must find out what the users want from the database. This is usually an informal process that involves discussions with user groups, a study of the current operating environment and how it is expected to change, analysis of any available documentation on existing applications that are expected to be replaced or complemented by the database, and so on
2. _**Conceptual Database Design:**_<br>
   The information gathered in the requirements analysis step is used to develop a highlevel description of the data to be stored in the database, along with the constraints that are known to hold over this data. This step is often carried out using the ER model, or a similar high-level data model.
3. _**Logical Database Design:**_<br>
   We must choose a DBMS to implement our database design, and convert the conceptual database design into a database schema in the data model of the chosen DBMS. We will only consider relational DBMSs, and therefore, the task in the logical design step is to convert an ER schema into a relational database schema.
4. _**Schema Refinement:**_<br>
   The fourth step in database design is to analyze the collection of relations in our relational database schema to identify potential problems, and to refine it. In contrast to the requirements analysis and conceptual design steps, which are essentially subjective, schema refinement can be guided by some elegant and powerful theory.
5. _**Physical Database Design:**_<br>
   In this step we must consider typical expected workloads that our database must support and further refine the database design to ensure that it meets the desired performance criteria. This step may simply involve building indexes on some tables and clustering some tables, or it may involve a substantial redesign of parts of the database schema obtained from the earlier design steps.
6. _**Security Design:**_<br>
   In this step, we identify different user groups and different roles played by various users (e.g., the development team for a product, the customer support representatives, the product manager). For each role and user group, we must identify the parts of the database that they must be able to access and the parts of the database that they should not be allowed to access, and take steps to ensure that they can access only the necessary parts.

## ER Diagram

The entity-relationship (ER) data model allows us to describe the data involved in a realworld enterprise in terms of objects and their relationships and is widely used to develop an initial database design. The ER model is important primarily for its role in database design. It provides useful concepts that allow us to move from an informal description of what users want from their database to a more detailed, and precise, description that can be implemented in a DBMS. Within the larger context of the overall design process, the ER model is used in a phase called conceptual database design.

_**Entity:**_ An entity is a “thing” or “object” in the real world that is distinguishable from all other objects. An entity is represented by a set of attributes. An entity set is a set of entities of the same type that share the same properties, or attributes.

_**Relationship:**_ A relationship is an association among several entities. A relationship set is a set of relationships of the same type.

### Attributes

- The basic concept that the ER model represents is an entity, which is a thing or object in the real world with an independent existence.
- An entity may be an object with a physical existence (for example, a particular person, car, house, or employee) or it may be an object with a conceptual existence (for instance, a company, a job, or a university course).
- Each entity has attributes—the particular properties that describe it. For example, an EMPLOYEE entity may be described by the employee’s name, age, address, salary, and job.
- A particular entity will have a value for each of its attributes. The attribute values that describe each entity become a major part of the data stored in the database.

_**Composite attributes:**_

- Composite attributes can be divided into smaller subparts, which represent more basicattributes with independent meanings.
- For example, the Address attribute of the EMPLOYEE entity can be subdivided into Street address, City, State.
- Attributes that are not divisible are called simple or atomic attributes.

_**Single-Valued Attribute:**_

- A single-valued attribute is an attribute that can have only one value for a particular entity within a database.
- In other words, each entity instance possesses a single, unique value for a single-valued attribute.
- For example, the ”Age” attribute of a person is single-valued because each person has a specific, singular age at any given time, and that age doesn’t change while referring to the same person.
- Single-valued attributes are straightforward and do not allow for multiple values or variations.

_**Multivalued Attribute:**_

- A multivalued attribute is an attribute that can have multiple values for a single entity within a database. This means that an entity can have more than one value associated with the same attribute.
- For instance, the ”Colors” attribute for a car is multivalued because a car can have one or more colors. A single-color car has only one value for the ”Colors” attribute, whereas a two-tone car has two values for the same attribute. Similarly, the ”College degrees” attribute for a person is multivalued because different individuals may have varying numbers of college degrees, ranging from zero to multiple degrees.
- Multivalued attributes introduce complexity into the data model, and they can have constraints, such as minimum and maximum values, to limit the number of values allowed for each entity.

  _**Stored Attribute:**_

- A stored attribute is an attribute whose value is directly and explicitly stored in the database. These values are typically entered or updated by users or processes and are maintained as part of the entity’s data.
- Stored attributes are not computed or derived from other attributes or external sources. For example, in the context you provided, ”Birth date” is a stored attribute of a person because it represents an explicit value that is recorded in the database and is not calculated from other attributes or data.

_**Derived Attribute:**_

- A derived attribute is an attribute whose value can be calculated or derived from other attributes or data within the database.
- The value of a derived attribute is not stored explicitly but is computed or derived when needed based on specific rules, algorithms, or formulas.
- In the example you mentioned, ”Age” is a derived attribute of a person because it is calculated by subtracting the person’s ”Birth date” from the current date.
- The ”Age” attribute doesn’t have a directly stored value; instead, it is derived from the stored ”Birth date” attribute and the current date when required.

### ER Diagram Symbols

<center>
   <img src = 'https://erikanacua.wordpress.com/wp-content/uploads/2013/02/image0021.png'>
</center>

### Relational Algebra

Relational algebra refers to a procedural query language that takes relation instances as input and returns relation instances as output. It performs queries with the help of operators. It gives a step by step process to obtain the result of the query.

#### Select Operator ($\sigma$):

Select operator is an unary operator. It can be used to select those tuples of a relation
that satisfy a given condition.
Notation: $\sigma_{\theta}(R)$ <br>

- $\sigma$: Select operator(read as sigma)
- $\theta$: Selection condition
- $R$: Relation name

  Result is a relation with the same scheme as R consisting of the tuples in R that satisfy condition θ

  Syntax: $\sigma_{condition}(relation)$

#### Project Operator $(\prod)$

The projection operator $\prod$ is one of the unary operators in relational algebra (RA) and is used to project columns from a relation. It can select specific columns from a given relation. <br>
_**Note:**_ It gives **distinct** fields only. <br>
_**Syntax:**_ $\prod_{A_1, A_2}(relation)$, this will return attribute A1 and A2 from the relation.

#### Rename Operator $(\rho)$

The RENAME operation is used to rename the output of a relation. Sometimes it is simple and suitable to break a complicated sequence of operations and rename it as a relation with different names. <br>
**Syntax** : $\rho_{X}(R)$, it will rename the relation R to X

#### Set operators

Union $(\cup)$, Intersection $(\cap)$, set difference $(–)$ are called set operators. Result of combining two relations with a set operator is a relation $\implies$ all its elements must be tuples having same structure. Hence scope of set operations is limited to union-compatible relations.

#### Union Compatible Relations

Two relations are union compatible if

1. Both have same number of columns
2. Names of attributes are same
3. Corresponding fields have same type
4. Attributes with the same name in both relations have same domain and datatype.

### Relational Calculus

Relational calculus is an alternative to relational algebra. In contrast to algebra, which is procedural, calculus is nonprocedural, or declarative, in that it allows us to describe the set of answers without being explicit about how they should be computed. The variant of the calculus that we present in detail is called the tuple relational calculus (TRC). Variables in TRC take on tuples as values. In another variant, called the domain relational calculus (DRC), the variables range over field values.

#### Tuple Relational Calculus

TRC is a nonprocedural query language, where each query is of the form

$$
\{t | P(t)\}
$$

where t = resulting tuples, <br>

$P(t) =$ known as predicate and these are the conditions that are used to fetch t. <br>
$P(t)$ may have various conditions logically combined with OR $(\lor)$, AND $(\land)$, NOT $(\neg)$

It also uses quantifiers:<br>
$\exists \in  r(Q(t)) =$ "there exists" a tuple in t in relation r such that predicate $Q(t)$ is true. <br>
$\forall t \in r(Q(t)) = Q(t)$ is true "for all" tuples in relation r. <br>

$\{ P | \exists S \in Students(S.CGPA > 8 \land P.name = S.name \land P.age = S.age)\}$
: returns the name and age of students with a CGPA above 8.

#### Domain Relational Calculus

$\{<x_1, x_2, ..., x_n> | P(x_1, x_2, ..., x_n)\}$

- $x_1, x_2, ..., x_n$ represent domain variables
- ## P represents a formula similar to that of the predicate calculus

  | Name    | Age | Marks | Subject |
  | ------- | --- | ----- | ------- |
  | David   | 23  | 78    | Maths   |
  | Mathew  | 29  | 54    | English |
  | Anand   | 29  | 89    | JAVA    |
  | Mitchel | 21  | 56    | Maths   |
  | Shaun   | 26  | 92    | Maths   |

  Relation Students <br>
  $\{< a, b> \exists a, b, c, d(< a, b, c, d> \in students \land c > 75)\}$ <br>
  returns the name and age of students having marks above 75.

  <u>Note</u> You have to mention the domain variables in the same order as given in the table.
