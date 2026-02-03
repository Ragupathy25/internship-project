
---

## 🔐 Application Flow

1. **User Registration**
   - Data submitted via AJAX
   - User credentials stored securely in MySQL
   - Passwords hashed using `password_hash()`

2. **User Login**
   - AJAX-based authentication
   - Unique token generated on successful login
   - Token stored in:
     - Browser **LocalStorage**
     - Backend **Redis** (with expiry)

3. **Profile Management**
   - Token sent with each request
   - Token validated using Redis
   - Profile data stored in MongoDB

---

## 🔑 Session Handling (Important)

- PHP Sessions are **NOT used**
- Login session is maintained **only using LocalStorage**
- Redis is used for backend token validation

Example:
```js
localStorage.setItem("token", "<generated_token>");
