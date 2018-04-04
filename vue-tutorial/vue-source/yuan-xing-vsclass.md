类实现：

    class User {
      constructor(firstName, lastName) {
        this.firstName = firstName
        this.lastName = lastName
      }

      fullName() {
        return `${this.firstName} ${this.lastName}`
      }
    }

    let user = new User('David', 'Chen')
    user.fullName()  // David Chen

原型实现方式：

```
function User(firstName, lastName) {
  this.firstName = firstName
  this.lastName = lastName
}

User.prototype.fullName = function() {
  return '' + this.firstName + this.lastName
}
```



