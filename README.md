# 🔒 PCI DSS Compliance Testing - Scripts Inspector Demo

A comprehensive demo page showcasing all possible script variants for PCI DSS inventory testing and validation of script inspection tools.

## 📋 Overview

This repository contains a comprehensive HTML demo page designed to test PCI Scripts Inspector services and validate their ability to detect, analyze, and inventory various types of scripts commonly found on payment pages. The page demonstrates real-world scenarios that PCI DSS compliance tools need to handle.

## 🎯 Purpose

- **Test PCI Scripts Inspector Services**: Validate script detection capabilities
- **Demonstrate Script Variants**: Showcase all possible script integration patterns
- **Validate Security Headers**: Test CSP, X-Frame-Options, and other security configurations
- **Iframe Testing**: Test nested content and cross-origin script detection
- **Compliance Validation**: Ensure tools can handle PCI DSS requirements

## 🚀 Features

### **Script Variants Covered**
- **Inline Scripts** (7): Analytics, payment validation, CSRF tokens, dynamic loading
- **External Scripts** (10): CDN libraries, payment processors, analytics tools
- **ES6 Module Scripts** (1): Modern JavaScript module imports
- **Iframe Scripts** (6): Nested content with embedded scripts
- **Cross-Origin Iframe**: Live Google.com website for real-world testing

### **Security Headers & CSP**
- Content Security Policy with script-src restrictions
- X-Frame-Options, X-Content-Type-Options
- Referrer Policy, Permissions Policy
- Frame-src allowance for iframe testing

### **Script Attributes**
- **Security**: `integrity`, `crossorigin`, `referrerpolicy`
- **Loading**: `async`, `defer`, `type="module"`
- **Custom**: `data-*` attributes for configuration

### **Integration Types**
- **Inline**: Direct HTML embedding
- **External**: CDN and third-party sources
- **Dynamic**: JavaScript-generated script tags
- **Module**: ES6 import statements
- **Iframe**: Nested content and cross-origin

## 📊 Script Inventory

| Category | Count | Description |
|----------|-------|-------------|
| **Main Page Scripts** | 18 | Inline + External + Module scripts |
| **Embedded Iframe** | 6 | Data URL with base64 HTML content |
| **Cross-Origin Iframe** | Variable | Live Google.com website |
| **Total Detectable** | 24+ | All accessible scripts combined |

### **Script Breakdown**
- **Inline Scripts**: 7 (analytics, validation, tokens, dynamic loading)
- **External Scripts**: 16 (CDNs, third-party services, custom domains)
- **With Integrity**: 4 (SRI hash verification)
- **Without Integrity**: 20 (no SRI hash)
- **ES6 Modules**: 1 (Vue.js import)

## 🧪 Testing Instructions

### **For PCI Scripts Inspector Testing**

1. **Deploy the page** to GitHub Pages or local server
2. **Run your inspector** on the page URL
3. **Verify script detection** - should find all 24+ scripts
4. **Check integration types** - inline vs external vs iframe
5. **Validate security headers** - CSP, X-Frame-Options, etc.
6. **Test integrity hashes** - some scripts have SRI, others don't
7. **Verify attributes** - crossorigin, async, defer, etc.
8. **Check dynamic loading** - scripts loaded via JavaScript
9. **Test iframe handling** - nested script detection within iframes

### **Expected Results**

- **InspectionJob Status**: Should complete successfully
- **Script Count**: 24+ total scripts detected
- **Security Headers**: All major security headers present
- **Report Generation**: Should create detailed report with script analysis
- **Iframe Detection**: Should detect scripts within iframe content

## 🛠️ Technical Details

### **Security Headers**
```html
<meta http-equiv="Content-Security-Policy" 
      content="default-src 'self'; script-src 'self' 'unsafe-inline' https://cdn.example.com https://js.stripe.com; style-src 'self' 'unsafe-inline'; frame-src 'self' https://www.google.com;">
<meta http-equiv="X-Frame-Options" content="DENY">
<meta http-equiv="X-Content-Type-Options" content="nosniff">
<meta http-equiv="Referrer-Policy" content="strict-origin-when-cross-origin">
```

### **Script Examples**

#### Inline Script
```html
<script>
  // Basic analytics tracking
  console.log('Page loaded:', window.location.href);
  const pageLoadTime = Date.now();
  localStorage.setItem('lastVisit', pageLoadTime);
</script>
```

#### External Script with Integrity
```html
<script src="https://js.stripe.com/v3/" 
        integrity="sha384-abc123def456ghi789jkl012mno345pqr678stu901vwx234yz567abc890def123" 
        crossorigin="anonymous">
</script>
```

#### ES6 Module Script
```html
<script type="module">
  import { createApp } from 'https://unpkg.com/vue@3/dist/vue.esm-browser.js';
  const app = createApp({ data() { return { message: 'Vue.js loaded!' }; } });
  app.mount('#vue-app');
</script>
```

## 🌐 Live Demo

**GitHub Pages**: [https://dtelega.github.io/pci-dss-complience-testing/](https://dtelega.github.io/pci-dss-complience-testing/)

## 📁 Repository Structure

```
pci-dss-complience-testing/
├── README.md                 # This file
├── index.html               # Main demo page (rename from pci-scripts-demo.html)
└── .github/                 # GitHub configuration (if needed)
```

## 🔧 Setup & Deployment

### **Local Testing**
1. Clone the repository
2. Open `index.html` in a web browser
3. Run your PCI Scripts Inspector locally

### **GitHub Pages Deployment**
1. Upload `index.html` to the main branch
2. Enable GitHub Pages in repository settings
3. Select "Deploy from a branch" → "main" → "/ (root)"
4. Access via the provided GitHub Pages URL

### **Custom Domain (Optional)**
- Configure custom domain in repository settings
- Update DNS records as needed

## 📚 PCI DSS Context

This demo page is designed to help validate tools that support PCI DSS Requirement 6.1:

> **Requirement 6.1**: Establish a process to identify security vulnerabilities, using reputable outside sources for security vulnerability information, and assign a risk ranking (for example, as "high," "medium," or "low") to newly discovered security vulnerabilities.

### **Relevant PCI DSS Controls**
- **6.1.1**: Keep current with appropriate security patches
- **6.1.2**: Install critical security patches within one month of release
- **6.1.3**: Establish a process to identify and assign a risk ranking to newly discovered security vulnerabilities

## 🤝 Contributing

This is a demo/testing repository. If you find issues or want to add more script variants:

1. Fork the repository
2. Create a feature branch
3. Add your improvements
4. Submit a pull request

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🔗 Related Resources

- [PCI DSS Requirements and Security Assessment Procedures](https://www.pcisecuritystandards.org/document_library)
- [Content Security Policy Level 3](https://www.w3.org/TR/CSP3/)
- [Subresource Integrity](https://www.w3.org/TR/SRI/)

## 📞 Support

For questions about this demo page or PCI DSS compliance:
- **Repository Issues**: [GitHub Issues](https://github.com/dtelega/pci-dss-complience-testing/issues)

---

**🔒 Created for PCI DSS compliance testing and validation purposes**

*This demo page helps ensure your PCI Scripts Inspector can handle all the script variants commonly found in production payment environments.*
