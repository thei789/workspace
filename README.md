# Local Network Landing Page

A beautiful, responsive landing page hub for your local network services. Access all your local development tools and web projects from one centralized page.

## 🌐 Features

- **Central Hub**: Single entry point for all local network services
- **Responsive Design**: Works seamlessly on desktop, tablet, and mobile
- **Easy to Extend**: Simple HTML/CSS structure for adding new services
- **Zero Dependencies**: Uses vanilla Node.js HTTP server (no npm packages required)
- **Fast & Lightweight**: Minimal overhead, pure static HTML/CSS

## 🚀 Getting Started

### Prerequisites
- Node.js 14.0.0 or higher installed on your system

### Installation

1. Clone the repository:
```bash
git clone <your-github-url>
cd copilot-network-landing-page-setup
```

2. No dependencies to install - ready to go!

### Running the Server

Start the landing page server on port 8080:

```bash
npm start
```

Or run directly:

```bash
node src/server.js
```

The landing page will be available at:
- **Local**: `http://localhost:8080`
- **Network**: `http://192.168.0.24:8080` (or your machine's IP address)

## 📝 Adding New Services

To add a new service link to the landing page:

1. Open `src/index.html`
2. Find the section where you want to add the link (Network Services, Web Projects, etc.)
3. Add a new service card:

```html
<a href="http://localhost:8081" class="service-card">
    <div class="service-icon">🎯</div>
    <h3>My New Service</h3>
    <p>Description of what this service does</p>
    <span class="port-badge">:8081</span>
</a>
```

4. Save the file - changes are live immediately!

For placeholder/coming-soon services, use:
```html
<div class="service-card placeholder">
    <!-- content -->
</div>
```

## 📂 Project Structure

```
copilot-network-landing-page-setup/
├── src/
│   ├── server.js          # Node.js HTTP server (runs on port 8080)
│   └── index.html         # Landing page markup
├── public/
│   └── style.css          # Responsive CSS styling
├── package.json           # Project metadata and scripts
└── README.md              # This file
```

## ⚙️ Configuration

### Changing the Port

To run on a different port, edit `src/server.js`:

```javascript
const PORT = 8080;  // Change this value
```

### Network Access

By default, the server listens on `localhost`. To make it accessible from other machines on your network, you can modify:

```javascript
const HOST = '0.0.0.0';  // Listen on all network interfaces
```

Then access it via: `http://<your-machine-ip>:8080`

## 🔗 Available Services

### Currently Active:
- **Theia IDE** (http://localhost:8024) - Web-based code editor

### Coming Soon:
- Add your web projects and services here!

## 🛠️ Development

The server includes:
- Automatic MIME type detection
- Security checks (directory traversal prevention)
- Error handling (404, 500 responses)
- Clean shutdown support

### Testing the Server

```bash
# Terminal 1: Start the server
npm start

# Terminal 2: Test the landing page
curl http://localhost:8080

# Test CSS file
curl http://localhost:8080/public/style.css
```

## 📦 Deployment

The server is designed for local network deployment and runs directly on your machine.

### Auto-start on Boot (Linux/Mac):

Create a systemd service or launchd plist to auto-start the server on system boot.

### Docker (Optional):

To containerize the landing page:

```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY . .
EXPOSE 8080
CMD ["npm", "start"]
```

## 🔐 Security Notes

- The server includes basic security checks (directory traversal prevention)
- For production use on public networks, add authentication and HTTPS
- Only suitable for local network use; not recommended for public internet exposure

## 📄 License

MIT License - Feel free to use and modify for your needs

## 🤝 Contributing

This is a personal network hub project. Feel free to extend it with:
- New service cards
- Enhanced styling
- Admin panel for managing links
- Dark mode toggle
- Search functionality

## 📞 Support

For issues or questions, check:
- GitHub Issues
- Review the source code in `src/`

---

**Network Location**: 192.168.0.24:8080  
**Local Access**: localhost:8080  
**Development**: code-server on port 8024  

Last updated: 2026-06-15
