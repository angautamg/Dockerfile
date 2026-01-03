<h1 align="center">🐳 Docker Setup Guide</h1>

<p align="center">
  A simple explanation of <b>Dockerfile</b> and <b>Docker Compose</b> for beginners and developers.
</p>

<hr/>

<h2>📦 What is Docker?</h2>
<p>
Docker is a platform that allows you to <b>package your application along with its dependencies</b>
into a single unit called a <b>container</b>.
This ensures the application runs the same way in every environment.
</p>

<hr/>

<h2>📄 What is a Dockerfile?</h2>

<p>
A <b>Dockerfile</b> is a text file that contains instructions to build a Docker image.
It defines:
</p>

<ul>
  <li>Which base image to use</li>
  <li>How to copy project files</li>
  <li>How to install dependencies</li>
  <li>How to start the application</li>
</ul>

<h3>🧩 Example Dockerfile</h3>

<pre>
<code>
FROM node:18-alpine

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm", "start"]
</code>
</pre>

<h4>🔍 Explanation</h4>
<ul>
  <li><b>FROM</b> – Uses Node.js 18 lightweight image</li>
  <li><b>WORKDIR</b> – Sets working directory inside container</li>
  <li><b>COPY</b> – Copies project files into container</li>
  <li><b>RUN</b> – Installs dependencies</li>
  <li><b>EXPOSE</b> – Opens application port</li>
  <li><b>CMD</b> – Starts the application</li>
</ul>

<hr/>

<h2>🔗 What is Docker Compose?</h2>

<p>
<b>Docker Compose</b> is a tool used to <b>run and manage multiple containers together</b>.
Instead of running multiple Docker commands, everything is defined in a single file:
<b><code>docker-compose.yml</code></b>
</p>

<p>
It is commonly used when your app depends on:
</p>

<ul>
  <li>Backend + Database</li>
  <li>Frontend + Backend</li>
  <li>Microservices</li>
</ul>

<h3>🧩 Example docker-compose.yml</h3>

<pre>
<code>
version: "3.9"

services:
  app:
    build: .
    ports:
      - "3000:3000"
    volumes:
      - .:/app
    environment:
      - NODE_ENV=development
</code>
</pre>

<h4>🔍 Explanation</h4>
<ul>
  <li><b>services</b> – Defines containers</li>
  <li><b>build</b> – Builds image using Dockerfile</li>
  <li><b>ports</b> – Maps local port to container port</li>
  <li><b>volumes</b> – Syncs local files with container</li>
  <li><b>environment</b> – Sets environment variables</li>
</ul>

<hr/>

<h2>⚙️ How to Run the Project</h2>

<pre>
<code>
docker-compose up --build
</code>
</pre>

<p>
This command will:
</p>

<ul>
  <li>Build the Docker image</li>
  <li>Create containers</li>
  <li>Start the application</li>
</ul>

<hr/>

<h2>🎯 Key Difference</h2>

<table border="1" cellpadding="8">
  <tr>
    <th>Dockerfile</th>
    <th>Docker Compose</th>
  </tr>
  <tr>
    <td>Defines how to build an image</td>
    <td>Defines how to run containers</td>
  </tr>
  <tr>
    <td>Used for single container</td>
    <td>Used for multiple containers</td>
  </tr>
  <tr>
    <td>Low-level instructions</td>
    <td>High-level orchestration</td>
  </tr>
</table>

<hr/>

<h2>✨ Summary</h2>

<ul>
  <li>✔ Dockerfile → <b>How to build</b> the app</li>
  <li>✔ Docker Compose → <b>How to run</b> the app</li>
  <li>✔ Together → <b>Easy development & deployment</b></li>
</ul>

<p align="center">
  🚀 Happy Dockering!
</p>
