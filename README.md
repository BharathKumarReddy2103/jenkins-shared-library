# Jenkins Shared Library

A **Jenkins Shared Library** is a powerful way to keep your Jenkins pipeline code DRY, modular, and reusable across multiple repositories and Jenkinsfiles. This repository provides a set of custom Groovy scripts, steps, and utilities designed for use as a Jenkins shared library to standardize and streamline CI/CD pipelines.

---

## 📦 Repository Structure

```
.
├── vars/               # Custom pipeline steps (global variables)
│   └── <yourSteps>.groovy
├── src/                # Groovy classes for advanced logic
│   └── <yourPackages>
├── resources/          # Non-Groovy resources (templates, scripts, etc.)
│   └── <yourTemplates>
├── README.md           # Project documentation
└── ...                 # Other standard files
```

- **vars/**: Contains global pipeline steps, accessible directly in Jenkinsfiles (e.g., `myStep { ... }`).
- **src/**: For custom Groovy classes used by your steps.
- **resources/**: Additional files needed by your logic (e.g., email templates, shell scripts).

---

## 🚀 How to Use

### 1. Reference the Library in Your Jenkinsfile

Add the shared library to your Jenkins pipeline using either the **implicit** or **explicit** loading:

#### Implicit (recommended):
Define in Jenkins > Manage Jenkins > Global Pipeline Libraries.

#### Explicit (in Jenkinsfile):
```groovy
@Library('jenkins-shared-library') _
```

### 2. Use Shared Steps in Your Jenkinsfile

Once loaded, you can call any custom steps or classes defined in this library:

```groovy
pipeline {
    agent any
    stages {
        stage('Example') {
            steps {
                myCustomStep(param1: 'value')
                // or:
                script {
                    helperFunction()
                }
            }
        }
    }
}
```

---

## 🛠️ Key Features

- **Reusable pipeline steps:** Standardize common build, test, deploy, and notification logic.
- **Modular Groovy classes:** Encapsulate complex logic and keep pipelines clean.
- **Resource sharing:** Maintain scripts, templates, and configs centrally.
- **Faster onboarding:** Reduce boilerplate for new projects and teams.

---

## ➕ Adding New Steps

1. **Create a new file in the `vars/` directory** (e.g., `vars/myStep.groovy`).
2. **Implement your logic** as a Groovy script.
3. **Document usage** in the script header for discoverability.

---

## 📝 Example: Simple Custom Step

**`vars/helloWorld.groovy`**
```groovy
def call(String name = 'World') {
    echo "Hello, ${name}!"
}
```

**Usage in Jenkinsfile:**
```groovy
helloWorld('Jenkins')
```

---

## 🤝 Contributing

1. Fork the repository & create your feature branch.
2. Add or update steps, classes, or resources.
3. Submit a pull request with clear explanations and usage examples.

---

## 📝 License

This project is licensed under the [MIT License](LICENSE).

---

> **Tip:** Keep your shared library well-documented and modular to maximize its value across Jenkins pipelines.
