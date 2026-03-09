## Entity -> Contains Database fields
## Repository -> Handles database operations
## Service -> Business Logic
## Controller -> Rest APIs
## Resources -> Database config and PostgreSQL connection
## @Autowired -> Automatically injects the required dependency (say creating an instance)


@Service

Marks this class as a Spring Bean with the service stereotype.
Spring will detect it during component scanning and manage its lifecycle (create one instance by default—singleton).
Conceptually, a service contains business logic (e.g., validations, rules, orchestration).

@Autowired private UserRepository userRepository;

Dependency Injection (DI): Spring injects an instance of UserRepository into this field.
UserRepository is a Spring Data JPA repository (extends JpaRepository<User, Long>), so Spring creates its implementation at runtime.
Field injection works, but the recommended approach is constructor injection (more testable, safer, and works well with final fields).



 Why do we use @RequestBody User user in the controller?
Because the client (frontend / Postman / mobile app) sends JSON data in the HTTP request body, like this:
```json
{
  "name": "Raghav",
  "email": "raghav@example.com",
  "password": "1234",
  "role": "F",
  "phone": 9988776655,
  "address": "Navi Mumbai"
}
```
Spring needs a way to convert that JSON into a Java object.
That’s exactly what @RequestBody does.

✅ What @RequestBody actually does
When you write:
Java@PostMapping("/register")public User registerUser(@RequestBody User user) {    return userRepository.save(user);}Show more lines
```java
@PostMapping("/register")
public User registerUser(@RequestBody User user) {
    return userRepository.save(user);
}
```
Spring performs 3 big operations:
1) It reads the raw JSON from the request body
The request contains JSON — not form parameters, not query params — RAW JSON.
2) It converts JSON → Java object using Jackson
