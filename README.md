## **📌 Step 1 — Create the Two-Page Portfolio Website**

Create a folder named `portfolio-site/`:

```
portfolio-site/
│── index.html
│── about.html
└── styles.css
```

Basic example:

**index.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>About Me</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>About Me</h1>
        <nav>
            <a href="index.html">Home</a>
            <a href="about.html">About</a>
        </nav>
    </header>

    <section class="content">
        <h2>Who Am I?</h2>
        <p>I am a web developer who loves creating beautiful websites.</p>
    </section>

    <footer>
        <p>© 2025 Prathmesh Mali</p>
    </footer>
</body>
</html>

```

**about.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>My Portfolio</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Prathmesh Mali</h1>
        <nav>
            <a href="index.html">Home</a>
            <a href="about.html">About</a>
        </nav>
    </header>

    <section class="hero">
        <h2>Welcome to My Portfolio</h2>
        <p>I am a passionate web developer.</p>
    </section>

    <footer>
        <p>© 2025 Prathmesh Mali</p>
    </footer>
</body>
</html>
```

**styles.css**

```css
body {
    font-family: Arial, sans-serif;
    margin: 0;
    background: #f2f2f2;
}

header {
    background: #333;
    color: #fff;
    padding: 20px;
    text-align: center;
}

nav a {
    margin: 0 15px;
    color: #fff;
    text-decoration: none;
}

.hero {
    padding: 60px;
    text-align: center;
}

.content {
    padding: 40px;
    text-align: center;
}

footer {
    background: #222;
    color: #fff;
    padding: 10px;
    text-align: center;
}
```

---

## **📌 Step 2 — Initialize Git Locally**

Inside project folder:

```bash
git init
git add .
git commit -m "Initial portfolio website"
```

---

## **📌 Step 3 — Push to GitHub**

Create a new empty GitHub repo.

Then:

```bash
git remote add origin https://github.com/<username>/<repo-name>.git
git branch -M main
git push -u origin main
```

---

## **📌 Step 4 — Create Jenkins Pipeline**

### **1. Open Jenkins → New Item → Pipeline**

Name: `portfolio-pipeline`

### **2. Add this Jenkinsfile in your repo root:**

**Jenkinsfile**

```groovy
pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                echo "Cloning Repository..."
                git url: 'https://github.com/prathmeshm1903/Portfolio-website.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                echo "No build needed for static portfolio website"
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying Website..."

                bat '''
                echo Creating deployment directory...

                if not exist "C:\\inetpub\\wwwroot\\PortfolioWebsite" (
                    mkdir "C:\\inetpub\\wwwroot\\PortfolioWebsite"
                )

                echo Copying website files to IIS folder...

                xcopy /Y /E /I * "C:\\inetpub\\wwwroot\\PortfolioWebsite"

                echo Deployment Successful!
                '''
            }
        }
    }
}
```

> Adjust the deployment path based on your Jenkins server setup.

---

## **📌 Step 5 — Configure GitHub Webhook**

### Go to:

`Repo → Settings → Webhooks → Add Webhook`

* **Payload URL:**
  `http://<JENKINS-IP>:8080/github-webhook/`
* **Content-type:** `application/json`
* **Trigger:** `Just the push event`

Now every push triggers Jenkins automatically.

---

## **📌 Step 1 — Create Two-Page Travel Website**

Create:

```
travel-site/
│── index.html
│── packages.html
│── styles.css
└── Dockerfile
```

Example:

**index.html**

```html
<!DOCTYPE html>
<html>
<head>
    <title>Travel Agency</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
<h1>Explore the World</h1>
<a href="packages.html">View Tour Packages</a>
</body>
</html>
```

**packages.html**

```html
<!DOCTYPE html>
<html>
<head>
    <title>Packages</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
<h1>Our Tour Packages</h1>
<p>More content here...</p>
</body>
</html>
```

---

## **📌 Step 2 — Add Dockerfile**

**Dockerfile**

```dockerfile
FROM nginx:latest
COPY . /usr/share/nginx/html
```

---

## **📌 Step 3 — Initialize Git and Push to GitHub**

```bash
git init
git add .
git commit -m "Travel agency website initial commit"
git remote add origin https://github.com/<username>/<repo>.git
git branch -M main
git push -u origin main
```

---

## **📌 Step 4 — Build Docker Image**

Either clone from GitHub or build from your local copy:

```bash
docker build -t travel-website .
```

OR directly using GitHub source:

```bash
docker build -t travel-website https://github.com/<username>/<repo>.git
```

---

## **📌 Step 5 — Run Docker Container**

```bash
docker run -d -p 8081:80 travel-website
```

Open in browser:

```
http://localhost:8081
```

## ⚡ **Step 1 — Install Required Tools**

Install the following:

* **JDK 17 or 21**
* **Apache Maven**
* **VS Code + Java Extensions Pack**

Verify installations:

```bash
java -version
mvn -version
```

---

## ⚡ **Step 2 — Generate Maven Webapp Structure**

Run the following command inside VS Code terminal:

```bash
mvn archetype:generate -DgroupId=com.blogsite -DartifactId=blog-website -DarchetypeArtifactId=maven-archetype-webapp -DinteractiveMode=false
```

This generates the project automatically:

```
blog-website/
│── pom.xml
│── src
│   ├── main
│   │   └── webapp
│   │       ├── index.jsp
│   │       └── WEB-INF/web.xml
```

---

## ⚡ **Step 3 — Replace JSP with Your HTML Pages**

Navigate to:

```
src/main/webapp/
```

Delete:

```
index.jsp
```

Create:

```
index.html
blog.html
styles.css
```

### **index.html**

```html
<!DOCTYPE html>
<html>
<head>
    <title>My Blog</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
<h1>Welcome to My Blog</h1>
<a href="blog.html">Read Blog →</a>
</body>
</html>
```

### **blog.html**

```html
<!DOCTYPE html>
<html>
<head>
    <title>Blog Post</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
<h1>Blog Post</h1>
<p>This is a sample blog post.</p>
</body>
</html>
```

### **styles.css**

```css
body { font-family: Arial; }
h1 { color: #333; }
```

---

## ⚡ **Step 4 — No Java Code, No Dependencies**

You **do not** need any additional dependencies.
Leave the `pom.xml` exactly as generated.

---

## ⚡ **Step 5 — Build the Project with Maven**

Generate the deployable WAR file:

```bash
mvn clean install
```

This creates:

```
target/blog-website.war
```

---

## ⚡ **Step 6 — (Optional) Deploy and Test Using Apache Tomcat**

🔥 If Tomcat is not installed?

Then you MUST download it:

Apache Tomcat official site:
https://tomcat.apache.org/download-10.cgi

Download → Extract → Done
Now you will see the webapps/ folder.

### **Locate Your Tomcat Folder**

Example installation:

```
apache-tomcat-10.1.20/
```

Inside it, find:

```
webapps/
```

### **Copy the WAR File**

```
target/blog-website.war → apache-tomcat-10.x.x/webapps/
```

Tomcat will auto-deploy the application.

### **Start Tomcat**

Windows:

```
startup.bat
```

Linux/macOS:

```
./startup.sh
```

### **Access the Website**

Open in browser:

```
http://localhost:8080/blog-website
```

---

## ⚡ **Step 7 — Push Project to GitHub**

Inside your project folder:

```bash
git init
git add .
git commit -m "Static blog website using Maven webapp archetype"
git branch -M main
git remote add origin https://github.com/<username>/<repo>.git
git push -u origin main
```
