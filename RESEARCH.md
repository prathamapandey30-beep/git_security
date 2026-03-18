# Security Investigation: Committed Secrets & Repository Types

## 1. Risks of Committed Secrets
- **Unauthorized System Access**: Cloud infra, databases, etc.
- **Privilege Escalation**: Simple keys gaining admin access.
- **Data Breaches**: Mass exfiltration of user data.
- **Financial Loss**: Large bills from stolen API keys.
- **Supply Chain Attacks**: Compromising all users of a library.

## 2. Public vs. Private Repositories
- **Public**: Visible to everyone. High risk of bot scanning.
- **Private**: Visibility limited. Lower risk but vulnerable to insider threats or hacks.

## 3. Summary of Risks
| Risk Factor | Public Repo | Private Repo |
| :--- | :--- | :--- |
| **Secret Exposure** | Immediate and global. | Internal exposure. |
| **Intellectual Property** | Fully exposed. | Protected. |
| **Collaboration** | Unlimited. | Restricted access. |
