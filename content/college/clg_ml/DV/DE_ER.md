ER model stands for an Entity-Relationship model.
It is a high-level data model.
This model is used to define the data elements and relationship for a specified system.
It develops a conceptual design for the database.

why?
- It makes them easy to convert into relations (tables).
- It provide the purpose of real-world modeling of objects which makes them intently useful.
- It require no technical knowledge and no hardware support.
- These diagrams are very easy to understand and easy to create even for a naive user.
- It gives a standard solution for visualizing the data logically.
- They help in planning and organizing database structure, ensuring data consistency and integrity

Tools for Creating
1. Software Tools:
    - MySQL Workbench
    - Lucidchart
    - ER/Studio
2. Online Tools:
    - draw.io
    - Creately

# components
1. Entity
    - Weak
    - Strong
2. Attribute
    - Key
    - Composite
    - Multivalued
    - Derived
3. Relation
    - One to one
    - One to many
    - Many to one
    - Many to many

Entity
----
An entity may be any object, class, person or place.
In the ER diagram, an entity can be represented as rectangles.

- Weak entity
---
It is an entity that depends on another entity .
The weak entity doesn't contain any key attribute of its own.
The weak entity is represented by a double rectangle.

Attribute
---
The attribute is used to describe the property of an entity.
Eclipse is used to represent an attribute.

-  Key attribute
---
The key attribute is used to represent the main characteristics of an entity.
It represents a primary key.
The key attribute is represented by an ellipse with the text underlined.

- Composite Attribute
---
It is an attribute that composed of many other attributes .
The composite attribute is represented by an ellipse, and those ellipses are connected with an ellipse.

- Multivalued Attribute
These are  attribute that can have more than one value.
The double oval is used to represent multivalued attribute.

- Derived Attribute
-----
It is an attribute that can be derived from other attribute.
It can be represented by a dashed ellipse.

Primary Keys and Foreign Keys
---
Primary Key: A unique identifier for each entity instance (e.g., Student ID).
Foreign Key: An attribute that creates a link between two tables (e.g., Course ID in Enrollments table).
Role in ER Diagrams: Ensure data integrity and establish relationships between tables

Relationship
---
A relationship is used to describe the relation between entities.
Diamond or rhombus is used to represent the relationship.

1. One-to-One Relationship
---
When only one instance of an entity is associated with the relationship,

2. One-to-many relationship
---
When only one instance of the entity on the left, and more than one instance of an entity on the right associates with

3. Many-to-one relationship
---
When more than one instance of the entity on the left, and only one instance of an entity on the right associates with the relationship

4. Many-to-many relationship
----
When more than one instance of the entity on the left, and more than one instance of an entity on the right associates with the relationship


# Notation of ER diagram
- Standard Symbols:
    Rectangles for entities, ovals for attributes, diamonds for relationships, lines for linking them.
- Crow’s Foot Notation:
    Uses symbols like crow's feet to represent cardinality and relationships.
- Chen’s Notation:
    Uses rectangles, ovals, and diamonds with labels to depict entities, attributes, and relationships.

# advances

Generalization:
---
Combining similar entities into a single general entity.
Generalization is the process of abstracting common features;
- Examples: Generalization (Employee and Customer -> Person),

Specialization
---
specialization is the process of defining sub-entities.
Dividing a general entity into more specific entities.
- Examples: Specialization (Vehicle -> Car, Truck)


Aggregation:
---
Representing a relationship as an entity to simplify complex relationships.
A higher-level abstraction that encapsulates a relationship set.
Example: Projects composed of tasks, employees, and deadlines.
When to Use Aggregation: To simplify ER diagrams when relationships involve multiple entities.

Composition:
---
Stronger form of aggregation indicating ownership.
A form of aggregation with a strong ownership between entities.
Example: House (whole) and Room (part).
- Differentiating from Aggregation: Composition implies a lifecycle dependency between the part and the whole.

