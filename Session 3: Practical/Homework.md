## Homework (Assignments)

Please do the tasks in the order specified with a commit per task. Also please follow Test-driven approach (tests before code).

Below are the tasks : 

1. Create a test to see if the user get successfully created in the table.

`Acceptance Criteria`
- User row should be created with factory user.
- Test should have following assertion and must pass it.

```
assertInstanceOf(User::class, $user);
```

2. Create a test to verify the validation error of incorrect email while creating user.

`Acceptance Criteria`
- The user model should have the rule for email column of user
- Also if for input data, the validation fails, it should not save the user and should return the error in an array.
- Test should have following assertion and must pass it.

```
assertArrayHasKey('email', $user);
```
