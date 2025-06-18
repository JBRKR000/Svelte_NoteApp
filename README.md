# 📝 Notes App

A modern, fast, and secure web app for creating, organizing, and managing notes — inspired by the best, built for productivity.


![2025-06-18_17-41-45 (1)](https://github.com/user-attachments/assets/798dde8f-1ced-4c55-b1f5-1f4787013ca2)



---



## 🚀 Key Features

- ✍️ **Create Notes**  
  Add your thoughts, tasks, or ideas with a clean, intuitive editor.

- 🗂️ **Organize Efficiently**  
  Your notes are safely stored in the cloud — access them anytime, anywhere after logging in.

- 🔐 **Secure Authentication**  
  User sessions managed with secure cookies, stored and validated in the database.

- 💡 **Modern User Interface**  
  Built with responsiveness and interactivity in mind: smooth animations, mobile-friendly layout, and stylish design.

- 🧑‍💼 **User Dashboard**  
  Browse, edit, and delete your notes in a personalized control panel.

- 🛡️ **Advanced Security**  
  Sessions expire securely, with automatic renewal and cleanup of inactive data.

---

## 🏗️ Architecture Overview

| Layer       | Tech Stack                          |
|-------------|-------------------------------------|
| **Frontend** | SvelteKit + TailwindCSS             |
| **Backend**  | Node.js + Drizzle ORM + MySQL       |
| **Auth**     | Custom cookie/session-based system  |
| **Database** | MySQL (users, sessions, notes)      |

---

## 🔄 User Flow

1. **Homepage**  
   Engaging landing page with animations and a "How It Works" section.

2. **Register / Login**  
   Secure signup and login with cookie-based sessions.

3. **Manage Notes**  
   Once logged in, users can create, edit, and browse notes in their personal panel.

4. **Logout**  
   Session is securely ended and cookie removed.

---

## 🧰 Technologies Used

- **🧱 SvelteKit** – Reactive frontend framework for fast SPA/SSR.
- **🎨 TailwindCSS** – Utility-first CSS for rapid and clean styling.
- **📦 Drizzle ORM** – Modern TypeScript ORM for MySQL.
- **🗄️ MySQL** – Structured data storage for scalability and reliability.

---

## 🔮 What's Next?

The application is designed for easy future growth. Planned features include:

- 🏷️ Note tagging and filtering  
- 🔍 Full-text search  
- 🔗 Third-party integrations (e.g. calendars, reminders)

---

> Made with ❤️ using SvelteKit, Drizzle ORM, and TailwindCSS
