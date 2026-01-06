# Shield360 Research

A comprehensive cloud-based endpoint security dashboard powered by Firebase Firestore. Shield360 Research provides real-time visibility into endpoint security postures, hardware inventory, network configurations, and vulnerability scanning capabilities using the National Vulnerability Database (NVD).

## Features

### 🖥️ Endpoints Dashboard
- **Real-time Endpoint Monitoring**: View all registered endpoints with detailed system information
- **Security Posture Overview**: At-a-glance firewall status and antivirus detection
- **Search & Filtering**: Filter endpoints by hostname, IP address, OS, user, and firewall status
- **Sorting Options**: Sort by name or date (ascending/descending)
- **Statistics Bar**: Quick counts for total endpoints, active firewalls, antivirus installations, and applications

### 📋 Endpoint Details
- **System Identity**: Hostname, FQDN, manufacturer, model, and device identifiers
- **Operating System**: OS name, version, last boot time, and timezone
- **Security Posture**: Firewall status and antivirus software inventory with status indicators
- **Network Information**: Public IP, network interfaces with IPv4, subnet, MAC addresses, and DHCP status
- **Hardware Inventory**: CPU details, RAM capacity, storage devices with partitions, and peripherals (keyboards, mice, printers)
- **User Context**: Current user, privilege groups, and process elevation status
- **Installed Applications**: Complete list of installed software with version information

### 🔒 Vulnerability Scanner
- **NVD Integration**: Scan installed applications against the National Vulnerability Database (NVD)
- **CVSS Scoring**: View vulnerability severity with CVSS scores (Critical, High, Medium, Low)
- **Detailed CVE Information**: Access descriptions, published dates, and direct links to NVD entries
- **Export Reports**: Generate text reports of vulnerability scan results
- **Severity Filtering**: Filter results by severity level

## Tech Stack

- **Frontend**: HTML5, CSS3 (Tailwind CSS), Vanilla JavaScript
- **Backend**: Firebase Cloud Firestore (NoSQL database)
- **APIs**: National Vulnerability Database (NVD) API v2.0
- **Deployment**: GitHub Pages with GitHub Actions CI/CD

## Project Structure

```
Shield360-Research/
├── index.html                 # Main endpoints dashboard
├── endpoint.html              # Individual endpoint details view
├── vulnerability-scanner.html # Vulnerability scanning interface
├── .github/
│   └── workflows/
│       └── static.yml         # GitHub Pages deployment workflow
└── README.md                  # Project documentation
```

## Getting Started

### Prerequisites
- A modern web browser (Chrome, Firefox, Safari, Edge)
- Internet connection for Firebase and NVD API access

### Local Development

1. Clone the repository:
   ```bash
   git clone https://github.com/unknownerror0519/shield360.git
   cd Shield360-Research
   ```

2. Open `index.html` in your web browser, or serve locally using any static file server:
   ```bash
   # Using Python 3
   python -m http.server 8000
   
   # Using Node.js (npx serve)
   npx serve .
   ```

3. Navigate to `http://localhost:8000` in your browser

### Deployment

The project automatically deploys to GitHub Pages on pushes to the `main` branch via GitHub Actions.

## Usage

### Dashboard Navigation

1. **View All Endpoints**: The main dashboard (`index.html`) displays all registered endpoints as cards
2. **Search Endpoints**: Use the search bar to filter by hostname, IP, OS, or user
3. **Filter by Status**: Use the dropdown to filter by firewall status (Active/Inactive)
4. **View Details**: Click on any endpoint card to view detailed information

### Vulnerability Scanning

1. Navigate to an endpoint's detail page
2. Click "Scan for Vulnerabilities" or "Launch Vulnerability Scanner"
3. Wait for the scan to complete (NVD API rate limits apply - 6 seconds between requests)
4. Review the results, filtered by severity
5. Export a text report if needed

## Firebase Configuration

The application connects to Firebase Firestore using the following collection:

- **Collection**: `endpoints`
- **Document Structure**: Each document represents an endpoint with the following main fields:
  - `hostname` - Device hostname
  - `agent_id` - Unique agent identifier
  - `os_info` - Operating system details
  - `identity` - Device identity information
  - `security_posture` - Firewall and antivirus status
  - `network` - Network configuration and interfaces
  - `hardware` - CPU, RAM, storage, and peripheral information
  - `user_context` - Current user and privileges
  - `applications` - List of installed applications
  - `scan_time` - Last scan timestamp

## API Rate Limits

The NVD API has the following rate limits:
- **Without API Key**: Approximately 6 seconds between requests (implemented in the scanner)
- **With API Key**: Higher rate limits available (not currently configured)

## Security Considerations

- Firebase security rules should be configured to restrict access
- No sensitive credentials are stored client-side beyond Firebase configuration
- XSS protection is implemented via HTML escaping functions
- The application runs entirely client-side with no server-side processing

## Browser Compatibility

- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is proprietary software. All rights reserved.

## Support

For support and inquiries, please open an issue in the GitHub repository.

---

© 2026 Shield360 Research | Powered by Firebase
