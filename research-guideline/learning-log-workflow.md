# **Learning Log Workflow & Template**

## **Overview**

This document outlines a **lightweight learning log workflow** to improve
documentation and knowledge-sharing within the team. By consistently capturing
key insights, challenges, and resolutions, we can build a **centralized
knowledge base** that supports continuous learning and efficiency.

---

## **1. Learning Log Workflow**

### **1.1. Logging Process**

1. **Create a new log entry** whenever you start a learning session,
   troubleshooting task, or research activity.
2. **Use the Learning Log Template** (see below) to capture key points.
3. **Store logs in a Git repository** for version control and easy reference.
4. **Tag and organize logs** for searchability.
5. **Review logs weekly or bi-weekly** to extract high-value insights for
   structured documentation.

---

### **1.2. Repository Structure**

To maintain a well-organized system, logs should follow this structure:

```
/learning-logs
  ├── logs/
  │   ├── YYYY-MM-DD-task-title.md  # Individual learning logs
  ├── knowledge/
  │   ├── troubleshooting-guide.md  # Knowledge contributions
  ├── templates/
  │   ├── learning-log-template.md  # Reusable template
```

- **`logs/`** → Stores individual learning logs.
- **`knowledge/`** → Stores structured knowledge contributions (e.g.,
  troubleshooting guides, best practices).
- **`templates/`** → Holds reusable templates.

---

### **1.3. Logging & Review Schedule**

| **Action**              | **Frequency**            | **Purpose**                                             |
| ----------------------- | ------------------------ | ------------------------------------------------------- |
| Write a learning log    | As needed (daily/weekly) | Capture key insights, issues, and solutions             |
| Tag and commit logs     | After completion         | Ensure easy searchability and version control           |
| Weekly review           | End of each week         | Identify valuable insights for structured documentation |
| Bi-weekly retrospective | Every 2 weeks            | Improve the documentation process                       |

---

## **2. Learning Log Template**

> **Use this template for all learning logs.**\
> Store logs in `logs/YYYY-MM-DD-task-title.md` following the naming convention.

```markdown
# Learning Log: [Task Name]

- **Date & Time:** YYYY-MM-DD | HH:MM - HH:MM
- **Task / Topic:** [Brief description]

## Key Learnings

- [Bullet point insights]

## Challenges & Resolutions

- **Issue:** [Brief description]
  - **Solution:** [How it was resolved]

## Next Steps / Action Items

- [Follow-up actions]
```

📂 **Example Filename:** `logs/2025-02-24-git-documentation.md`

---

## **3. Automating the Workflow**

### **3.1. Automating Git Commits for Logs**

Use a **GitHub Action** to automatically commit and push logs to the repository.

1. **Create the following workflow** in `.github/workflows/auto-commit.yml`:

```yaml
name: Auto Commit Logs
on:
  schedule:
    - cron: "0 18 * * *" # Runs daily at 18:00 UTC
jobs:
  commit-logs:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      - name: Commit changes
        run: |
          git config --global user.email "bot@example.com"
          git config --global user.name "AutoCommit Bot"
          git add logs/*.md
          git commit -m "Auto-commit learning logs [$(date)]" || echo "No changes to commit"
          git push origin main
```

2. **This automation ensures that logs are committed daily**.

---

## **4. Best Practices for Team Adoption**

- **Keep logs concise** – focus on insights, challenges, and solutions.
- **Use consistent filenames** for easy retrieval.
- **Tag logs** using YAML front matter for better searchability.
- **Encourage weekly team reviews** to extract structured documentation.
