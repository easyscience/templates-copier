# Copier Templates

This repository provides a structured approach to creating new repositories under the **EasyScience** organization using predefined templates. It ensures consistency and accelerates project setup.

## 🚀 Step 1: Create a New Repository Using Templates

First, decide which template you need. This repository provides four templates:

- **`project`** – A template for a **project hub repository**.
- **`project-lib`** – A template for a **Python library repository**.
- **`project-app`** – A template for a **Qt QML desktop application repository**.
- **`common`** – A set of **shared files** used across multiple projects.

The `templates-copier` repository has the following structure:
```
templates-copier/
│── copier.yaml  # Root copier config
│── templates/
│   ├── common/  # A set of shared files used across multiple projects
│   │   ├── .gitignore
│   │   ├── {{_copier_conf.answers_file}}.jinja
│── projects/
│   ├── project/  # A template for a project hub repository
│   ├── project-app/  # A template for a Qt QML desktop application repository
│   ├── project-lib/  # A template for a Python library repository
│   │   ├── {{_copier_conf.answers_file}}.jinja
│   │   ├── README.md.jinja
```

### 1.1. Create a Repository on GitHub
To create a new repository, follow these steps:

- Navigate to **GitHub** and select **"Create New Repository"**.
- Repository template: No template (as we will use Copier templates instead of GitHub templates).
- Enter the repository name, for example, `superduper-lib`.
- Add a description based on the [EasyScience organization profile](https://github.com/easyscience/.github/blob/master/profile/README.md). If a suitable description isn't available, consider adding one to the organization profile first.
- Set the repository visibility to **Public**.
- Ensure **not to initialize** the repository with a README, `.gitignore`, or license file, as these will be handled by Copier.
- Click **"Create repository"** to finalize the process.


### 1.2. Set Up Access to GitHub
This step is required **only if you have not set up GitHub access before**. 
Access to GitHub can be done using Personal Access Tokens (PATs):

- 🔹 Step 1: Generate a Personal Access Token (PAT)
	-	Go to GitHub → Settings → Developer Settings → Personal Access Tokens
- 👉 GitHub PAT Settings
	-	Click “Generate new token”.
	-	Select:
	- •	✅ repo → Full control of repositories.
	- •	✅ workflow → Access GitHub Actions (optional).
	-	Click “Generate token” and copy it.

Now, you can use PAT to interact with GitHub via:
- The **terminal** (recommended for advanced users).
- A **GUI client** like **GitKraken** (for an intuitive interface).

### 1.3. Clone the Repository

Once access to GitHub is set up, **clone the repository to your local machine**.

In the terminal-based approach, this can be done with:
```bash
git clone https://github.com/easyscience/superduper-lib.git
```

Alternatively, you can use a GUI client like GitKraken for a visual interface to manage the repository.

### 1.4. Generate the Project Structure Using Copier
[Copier](https://copier.readthedocs.io/en/stable/) is used to generate project files from predefined templates.

#### 🛠 Install Copier
If you haven’t installed Copier, do so with:
```bash
pip install copier
```

#### 📂 Create the Initial Repository Structure
To initialize the repository, run the following command:
```bash
copier copy gh:easyscience/templates-copier superduper-lib
```
**This command will prompt you for:**  
✔️ The type of template (`project`, `project-lib`, `project-app`, `common`)  
✔️ The name of the project (`superduper-lib`), etc.

Since the repository requires both **project-specific** and **common** templates, **execute the command twice**:

1. Run Copier for the project template:
   ```bash
   copier copy gh:easyscience/templates-copier superduper-lib
   ```
   Select the **`project-lib`** template.

2. Run Copier for common files:
   ```bash
   copier copy gh:easyscience/templates-copier superduper-lib
   ```
   Select the **`common`** template.

#### 📁 Where Are Answers Stored?
The answers provided during setup are stored in:
- **Project-specific answers** → `superduper-lib/.copier-answers_project-lib.yml`
- **Common template answers** → `superduper-lib/.copier-answers_common.yml`

### 1.5. Push Changes to the Repository
After generating the project structure, **push the changes** to GitHub. You can do this via:
- The **terminal**:
  Use your username for 'https://github.com' along with the personal access token (PAT) as the password.
  ```bash
  cd superduper-lib
  git add -A
  git commit -m "Initial project setup using Copier templates"
  git push origin master
  ```
- A **GUI client** like GitKraken.

## ⚙️ Step 2: Perform Manual Repository Configuration
Some repository settings might need manual adjustment:
- **Set up CI/CD workflows** (if applicable).
- **Add repository secrets** (e.g., API keys, deployment keys).
- **Configure repository settings** (branch protection, access control).

## 🔄 Step 3: Keep Your Repository Updated with Template Changes
When the templates in **templates-copier** are updated, apply those updates to your project.

### 📌 To update the repository with the template changes:

Go to the project directory:
```bash
cd superduper-lib
```

Step 1: Update the Common Template
```bash
copier update --answers-file=.copier-answers_common.yml
```

Step 2: Update the Project-Specific Template
```bash
copier update --answers-file=.copier-answers_project-lib.yml
```

Push changes to the repository.


- If conflicts arise, Copier will prompt you to review them.

## 🎯 Summary
| **Step** | **Description** |
|---------|----------------|
| **Step 1** | Create a repository and initialize it using Copier templates. |
| **Step 2** | Perform manual configuration for repository settings. |
| **Step 3** | Keep the repository updated with the latest template changes using `copier update`. |






# Copier Templates

This repository provides a structured approach to creating new repositories under the **EasyScience** organization by using predefined templates. It ensures consistency and accelerates project setup.

## 🚀 Step 1: Create a New Repository Using Templates

First, decide which template you need. This repository provides four templates:

- **`project`** – A template for a **project hub repository**.
- **`project-lib`** – A template for a **Python library repository**.
- **`project-app`** – A template for a **Qt QML desktop application repository**.
- **`common`** – A set of **shared files** used across multiple projects.

So the `templates-copier` repository has the following structure:
```
templates-copier/
│── copier.yaml  # Root copier config
│── templates/
│   ├── common/  # A set of **shared files** used across multiple projects
│   │   ├── .gitignore
│   │   ├── {{_copier_conf.answers_file}}.jinja
│── projects/
│   ├── project/  # A template for a **project hub repository**
│   ├── project-app/  # A template for a **Qt QML desktop application repository**
│   ├── project-lib/  # A template for a **Python library repository**
│   │   ├── {{_copier_conf.answers_file}}.jinja
│   │   ├── README.md.jinja
``` 

### 1.1. Create a Repository on GitHub
To create a new repository, follow these steps:

1. Go to **GitHub → Create New Repository**.
2. Enter the repository name, e.g., `superduper-lib`.
3. Add description, based on the github easyscience organization profile 
(https://github.com/easyscience/.github/blob/master/profile/README.md). If the description is not available, add it there 
first.
4. Select Public as the repository visibility.
3. **Do not initialize** the repository with a README, `.gitignore` or license files (Copier will handle this).
4. Click **"Create repository"**.

### 1.2. Set Up Access to GitHub
This step is required **only if you have not set up GitHub access before**. 
Access to GitHub can be done using Personal Access Tokens (PATs):

🔹 Step 1: Generate a Personal Access Token (PAT)
	1.	Go to GitHub → Settings → Developer Settings → Personal Access Tokens
👉 GitHub PAT Settings
	2.	Click “Generate new token”.
	3.	Select:
	•	✅ repo → Full control of repositories.
	•	✅ workflow → Access GitHub Actions (optional).
	4.	Click “Generate token” and copy it.

Now, you can use PAT to interact with GitHub via:
- The **terminal** (recommended for advanced users).
- A **GUI client** like **GitKraken** (for an intuitive interface).

### 1.2. Clone the Repository

Once access to GitHub is set up, **clone the repository to your local machine**.

In the terminal-based approach, this can be done with:
```bash
git clone https://github.com/easyscience/superduper-lib.git
```

Alternatively, you can use a GUI client like GitKraken for a visual interface to manage the repository.

---

### 1.3. Generate the Project Structure Using Copier
[Copier](https://copier.readthedocs.io/en/stable/) is used to generate project files from predefined templates.

#### 🛠 Install Copier
If you haven’t installed Copier, do so with:
```bash
pip install copier
```

#### 📂 Create the Initial Repository Structure
To initialize the repository, run the following command:
```bash
copier copy gh:easyscience/templates-copier superduper-lib
```
**This command will prompt you for:**  
✔️ The type of template (`project`, `project-lib`, `project-app`, `common`)  
✔️ The name of the project (`superduper-lib`), etc.

Since the repository requires both **project-specific** and **common** templates, **execute the command twice**:

1. Run Copier for the project template:
   ```bash
   copier copy gh:easyscience/templates-copier superduper-lib
   ```
   Select the **`project-lib`** template.

2. Run Copier for common files:
   ```bash
   copier copy gh:easyscience/templates-copier superduper-lib
   ```
   Select the **`common`** template.

#### 📁 Where Are Answers Stored?
The answers provided during setup are stored in:
- **Project-specific answers** → `superduper-lib/.copier-answers_project-lib.yml`
- **Common template answers** → `superduper-lib/.copier-answers_common.yml`

---

### 1.4. Push Changes to the Repository
After generating the project structure, **push the changes** to GitHub. You can do this via:
- The **terminal**:
  ```bash
  git add -A
  git commit -m "Initial project setup using Copier templates"
  git push origin master
  ```
- A **GUI client** like GitKraken.

---

## ⚙️ Step 2: Perform Manual Repository Configuration
Some repository settings might need manual adjustment:
- **Set up CI/CD workflows** (if applicable).
- **Add repository secrets** (e.g., API keys, deployment keys).
- **Configure repository settings** (branch protection, access control).

---

## 🔄 Step 3: Keep Your Repository Updated with Template Changes
When the templates in **templates-copier** are updated, apply those updates to your project.

### 📌 To update the repository with new template changes:
```bash
cd superduper-lib
copier update
```
- This updates files **while preserving your custom modifications**.
- If conflicts arise, Copier will prompt you to review them.

---

## 🎯 Summary
| **Step** | **Description** |
|---------|----------------|
| **Step 1** | Create a repository and initialize it using Copier templates. |
| **Step 2** | Perform manual configuration for repository settings. |
| **Step 3** | Keep the repository updated with the latest template changes using `copier update`. |
