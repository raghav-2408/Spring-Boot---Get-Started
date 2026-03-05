# Create Entity Class

```java
package com.example.BootDemo;

import jakarta.persistence.*;

@Entity
@Table (name = "users")
public class User {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;
    private String email;

    public User() {}

    public Long getId() {
        return id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getEmail() {
        return email;
    }

    public void setEmail(String email) {
        this.email = email;
    }
}
```

# Create Repository

```java
package com.example.BootDemo;

import org.springframework.data.jpa.repository.JpaRepository;
import com.example.BootDemo.User;

public interface UserRepository extends JpaRepository<User, Long> {
    
}
```

# Create Controller

```java
package com.example.BootDemo;

import org.springframework.web.bind.annotation.*;
import java.util.List;
import com.example.BootDemo.User;
import com.example.BootDemo.UserRepository;

@RestController
@RequestMapping("/users")
public class UserController {

    private final UserRepository repo;

    public UserController(UserRepository repo) {
        this.repo = repo;
    }

    @PostMapping
    public User createUser(@RequestBody User user) {
        return repo.save(user);
    }

    @GetMapping
    public List<User> getUsers() {
        return repo.findAll();
    }
}
```
