# Lab 19 – Authentication and Authorization (CIS 485)

## 🔐 Objective

This lab demonstrates three core authentication strategies and role-based authorization using Node.js and Express:

- Basic HTTP Authentication
- JWT (Token-based) Authentication with Roles
- Session-based Authentication with Cookie Support

---

## 🛠️ Technologies Used

- Node.js
- Express.js
- `basic-auth`
- `jsonwebtoken`
- `express-session`

---

## 📁 Files Included

| File              | Description                                       |
|-------------------|---------------------------------------------------|
| `basicAuth.js`    | Basic authentication with hardcoded credentials  |
| `jwtAuth.js`      | JWT login, token validation, and role protection |
| `sessionAuth.js`  | Session login/logout + role-based access control |

---

## 🚀 Getting Started

### 1. Install Dependencies

```bash
npm install express basic-auth jsonwebtoken express-session
2. Run Servers
File	Command	Port
basicAuth.js	node basicAuth.js	3000
jwtAuth.js	node jwtAuth.js	3001
sessionAuth.js	node sessionAuth.js	3002

🔑 Test Routes with curl
✅ Basic Auth
bash
Copy
Edit
curl.exe -u admin:password123 http://localhost:3000/basic-protected
✅ JWT Auth
Login to get a token

bash
Copy
Edit
curl.exe -X POST http://localhost:3001/login -H "Content-Type: application/json" -d '{"username":"user1","password":"password123"}'
Use token to access protected route

bash
Copy
Edit
curl.exe http://localhost:3001/jwt-protected -H "Authorization: Bearer YOUR_TOKEN_HERE"
Admin-only route

bash
Copy
Edit
curl.exe http://localhost:3001/admin -H "Authorization: Bearer YOUR_TOKEN_HERE"
✅ Session Auth
Login and save session cookie

bash
Copy
Edit
curl.exe -X POST http://localhost:3002/session-login -H "Content-Type: application/json" -d '{"username":"user1","password":"password123"}' -c cookies.txt
Access protected route

bash
Copy
Edit
curl.exe http://localhost:3002/session-protected -b cookies.txt
Admin-only route

bash
Copy
Edit
curl.exe http://localhost:3002/session-admin -b cookies.txt
🧠 Reflection Questions
Q: What are the differences between Basic, JWT, and Session Auth?

Basic Auth: Sends credentials with every request. Easy but insecure.

JWT: Stores user data in a signed token. Scalable and stateless.

Session Auth: Server stores session; user stores only session ID in a cookie. Best for traditional web apps.

Q: When would you use each?

Use Basic Auth for internal tools or testing.

Use JWT for stateless APIs (e.g., mobile apps).

Use Session for full web apps with login/logout flows.

👨‍💻 Author
Sam Lima
CIS 485 – Spring 2025
