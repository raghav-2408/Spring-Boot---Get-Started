## @GeneratedValue(strategy = GenerationType.SEQUENCE)
tells the persistence provider to use a database sequence to generate primary key values for the annotated entity field.

<img src = img.png>


# What is Jakarta?
Jakarta = the new name for Java EE

 Oracle → Eclipse Foundation transfer
In 2017–2019:

Oracle donated Java EE to the Eclipse Foundation
Oracle kept the rights to the javax.* package name
Eclipse had to rename everything

 It’s the package that contains all JPA (Java Persistence API) annotations.

 @Entity
@Id
@Column
@GeneratedValue
@Table
etc.


## List<BankAccount> findByUserIdOrderByIdAsc(Long userId);

That line is a Spring Data JPA repository method.
It is not random — Spring automatically interprets the method name and generates the SQL query for you.


Spring Data JPA reads the method name, understands what you want, and automatically creates the query → no need to write SQL.


“Find all BankAccount entries where userId equals the given value,
and sort them by id in ascending order.”

<hr>
