# functional dependency
Functional dependencies are used to mathematically express relations among database entities

# Armstrong’s axioms/properties of functional dependencies:

- Reflexivity: If Y is a subset of X, then X→Y holds by reflexivity rule
    `Example, {roll_no, name} → name is valid.`
- Augmentation: If X → Y is a valid dependency, then XZ → YZ is also valid by the augmentation rule.
    `Example, {roll_no, name} → dept_building is valid, hence {roll_no, name, dept_name} → {dept_building, dept_name} is also valid.`
- Transitivity: If X → Y and Y → Z are both valid dependencies, then X→Z is also valid by the Transitivity rule.
    `Example, roll_no → dept_name & dept_name → dept_building, then roll_no → dept_building is also valid.`

# types of FD
1. Trivial functional dependency
---
In Trivial Functional Dependency, a dependent is always a subset of the determinant.
i.e. If X → Y and Y is the subset of X, then it is called trivial functional dependency

2. Non-Trivial functional dependency
----
In Non-trivial functional dependency, the dependent is strictly not a subset of the determinant.
i.e. If X → Y and Y is not a subset of X, then it is called Non-trivial functional dependency.

3. Multi-valued functional dependency
----
In Multi-valued functional dependency, entities of the dependent set are not dependent on each other.
i.e. If a → {b, c} and there exists no functional dependency between b and c, then it is called a multi-valued functional dependency.

4. Transitive functional dependency
----
In transitive functional dependency, dependent is indirectly dependent on determinant.
i.e. If a → b & b → c, then according to axiom of transitivity, a → c. This is a transitive functional dependency.
