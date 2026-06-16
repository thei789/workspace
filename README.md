# Local Network Landing Page

A beautiful, responsive landing page hub for your local network services. Access all your local development tools and web projects from one centralized page.

## 🌐 Features

- **Central Hub**: Single entry point for all local network services
- **Responsive Design**: Works seamlessly on desktop, tablet, and mobile
- **Easy to Extend**: Simple HTML/CSS structure for adding new services
- **Zero Dependencies**: Uses vanilla Node.js HTTP server (no npm packages required)
- **Fast & Lightweight**: Minimal overhead, pure static HTML/CSS
- **Security**: Built-in directory traversal prevention and proper error handling

## 🚀 Getting Started

### Prerequisites
- Node.js 14.0.0 or higher installed on your system

### Installation

1. Clone the repository:
```bash
git clone https://github.com/thei789/workspace.git
cd workspace
```

2. No npm dependencies to install - ready to go!

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
2. Find the section where you want to add the link (Development Tools, Network Services, Web Projects, etc.)
3. Add a new service card:

```html
<a href="http://your-ip:port">
    🎯
    <h3>My New Service</h3>
    <p>Description of what this service does</p>
    :port
</a>
```

4. Save the file - changes are live immediately!

For placeholder/coming-soon services, use:
```html
<div class="service-card placeholder">
    💻
    <h3>Coming Soon</h3>
    <p>Your service description here</p>
    :xxxx
</div>
```

## 📂 Project Structure

```
workspace/
├── src/
│   ├── server.js          # Node.js HTTP server (runs on port 8080)
│   └── index.html         # Landing page markup
├── public/
│   └── style.css          # Responsive CSS styling
├── package.json           # Project metadata and scripts
├── README.md              # This file
├── ROADMAP.md             # Future improvement ideas and implementation plans
└── .gitignore             # Git ignore rules
```

## ⚙️ Configuration

### Changing the Port

To run on a different port, edit `src/server.js`:

```javascript
const PORT = 8080;  // Change this value
```

### Network Access

The server listens on all network interfaces (`0.0.0.0`), making it accessible from other machines on your network:

```javascript
const HOST = '0.0.0.0';  // Listens on all network interfaces
```

Access it via: `http://<your-ip>:8080`

## 🔗 Currently Active Services

The hub provides quick access to:

### Development Tools
- **Theia IDE** (http://192.168.0.24:8024) - Web-based code editor and development environment

### Network Services
- **Proxmox** (https://192.168.0.2:8006) - Virtualization Management
- **Home Assistant** (http://192.168.0.30:8123) - Smart home automation system
- **TP-Link Router** (http://192.168.0.1) - Network Gateway
- **OpenMediaVault** (http://192.168.0.103:8090) - NAS & Storage Management
- **Portainer** (https://192.168.0.103:9443) - Docker Container Management
- **Pi-hole** (http://192.168.0.103) - Network Ad Blocker
- **SLZB-MR4** (http://192.168.0.19) - Zigbee Bridge

### Web Projects
- Placeholder sections ready for your projects!

### Quick Info Section
- Displays network information and last updated timestamp

## 🛠️ Development

### Testing the Server

```bash
# Terminal 1: Start the server
npm start

# Terminal 2: Test the landing page
curl http://localhost:8080

# Test CSS file
curl http://localhost:8080/public/style.css
```

### Server Features

- Automatic MIME type detection for HTML, CSS, JS, JSON, images
- Security checks (directory traversal prevention)
- Proper error handling (404 Not Found, 500 Internal Server Error)
- Graceful shutdown support

## 🎨 Styling

The application uses a modern color scheme with:
- Primary blue gradient (#2563eb → #1e40af)
- Light background (#f9fafb)
- Responsive grid layout with auto-fit columns
- Smooth hover transitions and animations
- Mobile-first responsive design

### CSS Variables

All colors and sizing are defined via CSS custom properties in `public/style.css`:

```css
:root {
    --primary-color: #2563eb;
    --secondary-color: #1e40af;
    --accent-color: #dbeafe;
    --text-primary: #1f2937;
    --text-secondary: #6b7280;
    --bg-light: #f9fafb;
    --bg-white: #ffffff;
    --border-color: #e5e7eb;
    --shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
    --shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
}
```

## 📦 Deployment

### Docker (Optional)

To containerize the landing page:

```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY . .
EXPOSE 8080
CMD ["npm", "start"]
```

Build and run:
```bash
docker build -t local-network-hub .
docker run -p 8080:8080 local-network-hub
```

### Auto-start on Boot

#### Linux (systemd)

Create `/etc/systemd/system/network-hub.service`:

```ini
[Unit]
Description=Local Network Hub
After=network.target

[Service]
Type=simple
User=pi
WorkingDirectory=/path/to/workspace
ExecStart=/usr/bin/node src/server.js
Restart=on-failure
RestartSec=10

[Install]
WantedBy=multi-user.target
```

Then enable it:
```bash
sudo systemctl enable network-hub
sudo systemctl start network-hub
```

#### macOS (launchd)

Create `~/Library/LaunchAgents/com.local.network-hub.plist`:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>com.local.network-hub</string>
    <key>ProgramArguments</key>
    <array>
        <string>/usr/local/bin/node</string>
        <string>/path/to/workspace/src/server.js</string>
    </array>
    <key>RunAtLoad</key>
    <true/>
</dict>
</plist>
```

## 🔐 Security Notes

- The server includes basic security checks (directory traversal prevention)
- Serves files from the project root directory only
- Proper HTTP status codes and error handling
- For production use on public networks, consider adding:
  - Authentication/Authorization
  - HTTPS/SSL certificates
  - Rate limiting
  - Input validation

## 📋 Roadmap

See [ROADMAP.md](./ROADMAP.md) for comprehensive improvement ideas including:
- Performance & asset optimization (HTTP caching, minification, Gzip)
- Service management & configuration (config-driven registry, health checks)
- User experience enhancements (dark mode, search, favorites, recently accessed)
- Admin & configuration features (admin dashboard, service management)
- Development experience improvements (live reload, linting, testing)
- Security enhancements (HTTPS, authentication)
- Additional project ideas (CLI tool, service discovery, Docker Compose, notifications)

## 🤝 Contributing

This is a personal network hub project. Feel free to extend it with:
- New service cards
- Enhanced styling
- Admin panel for managing links
- Dark mode toggle
- Search functionality
- Service health checks
- And more! (See ROADMAP.md for detailed ideas)

## 📄 License

MIT License - Feel free to use and modify for your needs

## 📞 Support

For issues or questions:
- Check the [ROADMAP.md](./ROADMAP.md) for feature ideas and implementation plans
- Review the source code in `src/` and `public/`
- Check GitHub Issues if available

---

**Network Location**: 192.168.0.24:8080  
**Local Access**: localhost:8080  
**Development Tool**: Theia IDE on port 8024  
**Last Updated**: 2026-06-15
