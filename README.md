

<h1 align="center">🚀 DevOps Reverse Proxy Project</h1>
<p align="center">
  Nginx + Docker Compose + Go + Flask Microservices
</p>

<hr>

<h2>📦 Project Overview</h2>
<p>This project sets up a Docker Compose-based environment with:</p>

<ul>
  <li>🟨 <strong>Service 1 (Go)</strong> — Returns JSON from <code>/ping</code> and <code>/hello</code></li>
  <li>🟦 <strong>Service 2 (Python Flask)</strong> — Returns JSON from <code>/ping</code> and <code>/hello</code></li>
  <li>🧭 <strong>Nginx Reverse Proxy</strong> — Routes traffic to both services on a single port</li>
</ul>

<h3>🖼️ Screenshot</h3>

<!-- Replace the path with your actual image -->
<img src="screenshots/nginx-routing.png" alt="Nginx Proxy Working" width="600"/>

<hr>

<h2>⚙️ Setup Instructions</h2>

<ol>
  <li>Install Docker and Docker Compose</li>
  <li>Clone this repository:</li>

<pre><code>git clone https://github.com/your-username/devops-nginx-proxy.git
cd devops-nginx-proxy
</code></pre>

  <li>Run the entire system with:</li>

<pre><code>docker compose up --build</code></pre>
</ol>

<p>Once running, visit the endpoints in your browser or use <code>curl</code>:</p>

<ul>
  <li><a href="http://localhost:8080/service1/ping" target="_blank">http://localhost:8080/service1/ping</a></li>
  <li><a href="http://localhost:8080/service1/hello" target="_blank">http://localhost:8080/service1/hello</a></li>
  <li><a href="http://localhost:8080/service2/ping" target="_blank">http://localhost:8080/service2/ping</a></li>
  <li><a href="http://localhost:8080/service2/hello" target="_blank">http://localhost:8080/service2/hello</a></li>
</ul>

<hr>

<h2>🔁 How Routing Works</h2>

<p>Nginx is configured to proxy requests based on URL path:</p>

<ul>
  <li><code>/service1/*</code> ➡️ routed to Go app on <code>http://service1:8001</code></li>
  <li><code>/service2/*</code> ➡️ routed to Flask app on <code>http://service2:8002</code></li>
</ul>

<pre><code>location /service1/ {
    proxy_pass http://service1:8001/;
    rewrite ^/service1(/.*)$ $1 break;
}

location /service2/ {
    proxy_pass http://service2:8002/;
    rewrite ^/service2(/.*)$ $1 break;
}
</code></pre>

<hr>

<h2>✨ Bonus Features Implemented</h2>

<ul>
  <li>✅ <strong>Docker Health Checks</strong> for both services</li>
  <li>✅ <strong>Nginx Access Logs</strong> with timestamp and URL</li>
  <li>✅ <strong>Bridge Networking</strong> for container isolation</li>
  <li>✅ <strong>Single-Port Access</strong> through <code>localhost:8080</code></li>
  <li>🧪 (Optional) Test-ready via CURL or browser</li>
</ul>

<hr>

<h2>📁 Folder Structure</h2>

<pre>
.
├── docker-compose.yml
├── nginx/
│   ├── nginx.conf
│   └── Dockerfile
├── service_1/
│   ├── main.go
│   └── Dockerfile
├── service_2/
│   ├── app.py
│   ├── requirements.txt
│   └── Dockerfile
└── README.md
</pre>

<hr>

<h2>🧠 Author & Notes</h2>
<p>
  Developed as part of a DevOps internship assignment.<br>
  Built using Linux-friendly, reproducible Docker containers.<br>
  <strong>Note:</strong> Do not use Flask's built-in server for production.
</p>

<p align="center">
  <strong>Made with 💻, 🐳, and ❤️</strong>
</p>
