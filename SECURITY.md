# Security Policy

This document outlines the security policies for this repository. It is CRITICAL to follow these guidelines to prevent data leaks and unauthorized access.

## 🚫 What NEVER to push

Under no circumstances should the following be committed or pushed to the repository:

### 1. API Keys & Access Tokens
- **Examples**: Google AI API key, AWS Access Key, OpenAI API Key, Stripe Secret Key, Firebase Service Account JSON, GitHub Personal Access Token (PAT).
- **Risk**: These can be used to access paid services on your behalf, potentially costing large sums of money or exposing user data.

### 2. Private Keys and Certificates
- **Examples**: `.ssh/id_rsa`, `.pem`, `.p12`, `.jks` files.
- **Risk**: Allows anyone with the key to impersonate you or gain unauthorized access to servers and encrypted data.

### 3. Database Credentials
- **Examples**: JDBC connection strings containing usernames and passwords, database configuration files with hardcoded credentials.
- **Risk**: Exposes your entire database to third-party access, leading to data theft or destruction.

### 4. Environment Variables
- **Examples**: `.env`, `.env.local`, `config.yaml` with sensitive values.
- **Risk**: These files often contain all the secrets required for the application to run.

---

## 🛠 Best Practices

### Use `.gitignore`
Always maintain a comprehensive `.gitignore` file to ensure sensitive files are never tracked by Git. 
**Recommended entries**:
```bash
# Environment variables
.env
.env.*

# Secrets and keys
*.pem
*.key
secrets/
```

### Environment Variables
For local development, use a template like `.env.example` (containing placeholder values) and keep the actual `.env` file untracked.

#### Why keep .env out of Git?
*   **Prevent Secret Leakage**: If `.env` is pushed, anyone with access to the repo can see all your secrets.
*   **Environment Specificity**: Different environments (development, testing, production) should have different configurations. Committing one set of variables can cause errors when deploying to another environment.
*   **Convenience**: It avoids "merge conflicts" in configuration files since each developer maintains their own local `.env`.

#### Standard Procedure
1. Create a `.env.example` file with placeholder values (e.g., `PORT=3000`, `API_KEY=YOUR_KEY`).
2. Add `.env` to your `.gitignore`.
3. Inform collaborators to copy `.env.example` to `.env` and fill in their own secrets.

### Secret Scanning
Consider using tools like **GitHub Secret Scanning** or **GitLeaks** to detect accidentally committed secrets early.

---

## 🛑 Accidentally Pushed a Secret?
If you have accidentally committed and pushed a secret:
1. **Revoke the secret immediately** (e.g., rotate the API key or change the password).
2. **Remove the secret from Git history** using tools like `git-filter-repo` or BFG Repo-Cleaner.
3. **Notify stakeholders** if any sensitive data was potentially exposed.
