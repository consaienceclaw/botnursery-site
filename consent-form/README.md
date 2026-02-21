# 🏥 AI Consent Form - BotNursery Project

A simple, mobile-friendly web application for collecting patient consent for AI-assisted medical care.

## 📋 Overview

This single-page application allows healthcare providers to collect formal consent from patients/guardians regarding the use of AI assistants in clinical practice. Designed for **Dra. Clarissa Noer's** pediatric practice (featuring "Fadinha Cientista" AI assistant), but fully parametrizable for any doctor or clinic.

## ✨ Features

- ✅ Single-page HTML app (no framework dependencies)
- ✅ Brazilian Portuguese (pt-BR)
- ✅ Mobile-friendly responsive design (Tailwind CSS)
- ✅ LGPD-compliant consent text with legal references
- ✅ Form validation (required/optional fields)
- ✅ CPF auto-formatting
- ✅ localStorage persistence (ready for backend integration)
- ✅ Timestamp confirmation with unique consent ID
- ✅ **Easy customization** via config variables

## 🚀 Quick Start

### Option 1: Open Directly
Simply open `index.html` in any modern web browser. No server required for basic functionality.

### Option 2: Local Server (Recommended)
For testing or demo purposes:

```bash
# Python 3
python3 -m http.server 8000

# Node.js (if you have npx)
npx http-server

# Then open: http://localhost:8000
```

## ⚙️ Configuration

Edit the **CONFIG** object at the top of `index.html` (lines 18-23):

```javascript
const CONFIG = {
    doctorName: "Dra. Clarissa Noer",     // Doctor's name
    clinicName: "Clínica Pediátrica",      // Clinic name
    botName: "Fadinha Cientista",          // AI assistant name
    specialty: "Pediatria"                 // Medical specialty (optional)
};
```

**That's it!** The entire form updates automatically.

## 📊 Data Storage

### Current: localStorage
Consents are saved to browser localStorage as JSON:

```json
[
  {
    "id": "consent_1707774123456_abc123",
    "config": {
      "doctorName": "Dra. Clarissa Noer",
      "clinicName": "Clínica Pediátrica",
      "botName": "Fadinha Cientista"
    },
    "fullName": "Maria Silva",
    "cpf": "123.456.789-00",
    "email": "[email protected]",
    "consentGiven": true,
    "timestamp": "2026-02-12T19:35:23.456Z",
    "timestampBR": "12/02/2026, 16:35:23"
  }
]
```

### Export Data
Open browser console and run:
```javascript
exportConsents()
```
This downloads all consents as a JSON file.

### Future: Backend Integration
The data structure is ready for API integration. Planned backend endpoints:

- `POST /api/consent` - Submit new consent
- `GET /api/consent/:id` - Retrieve specific consent
- `DELETE /api/consent/:id` - Revoke consent (LGPD compliance)

Example `fetch` integration (replace localStorage save):

```javascript
async function saveConsent(data) {
    const response = await fetch('/api/consent', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(data)
    });
    return response.json();
}
```

## 🔒 Legal Compliance

The consent form includes references to:

- **LGPD** (Lei 13.709/2018) - Brazilian data protection law
- **Resolução CFM nº 1.821/2007** - Medical records digitalization standards
- **Código de Ética Médica** - Professional confidentiality

Key consent points covered:
- AI is a support tool, not decision-maker
- Final medical decisions are human-made
- Data security and confidentiality (LGPD)
- Right to revoke consent
- Right to data deletion

## 📱 Mobile Support

- Responsive design works on all screen sizes
- Touch-friendly form controls
- Optimized font sizes for mobile reading
- Smooth scroll animations

## 🎨 Customization

### Colors
Edit Tailwind classes in the HTML:
- Primary: `bg-blue-600` → change to `bg-green-600`, etc.
- Accents: Search and replace color classes

### Legal Text
Edit the consent text in the `<div class="prose">` section (lines 37-85).

### Form Fields
Add/remove fields in the form section (lines 88-145). Update the JavaScript `formData` object accordingly.

## 🧪 Testing

1. Open `index.html` in browser
2. Fill in form with test data:
   - Nome: Test Patient
   - CPF: 123.456.789-00 (auto-formats)
   - Email: [email protected]
3. Check the consent checkbox
4. Click "Confirmar Consentimento"
5. Verify confirmation message appears with timestamp
6. Open browser DevTools → Console
7. Run: `localStorage.getItem('aiConsents')`
8. Verify JSON data is stored

## 📁 File Structure

```
consent-form/
├── index.html          # Complete single-page app
└── README.md          # This file
```

## 🔮 Future Enhancements

- [ ] Backend API integration (Node.js/Python Flask)
- [ ] PDF generation of signed consent
- [ ] Email confirmation to patient
- [ ] Admin dashboard to view all consents
- [ ] Multi-language support (English, Spanish)
- [ ] Digital signature capture
- [ ] QR code for consent retrieval

## 🐛 Troubleshooting

**Form doesn't submit:**
- Check browser console for errors
- Ensure "Nome Completo" is filled (required field)
- Ensure checkbox is checked

**localStorage full:**
- Browser localStorage limit: ~5-10MB
- Export data with `exportConsents()`
- Clear old data: `localStorage.removeItem('aiConsents')`

**CPF not formatting:**
- Only works with numeric input
- Max 11 digits (Brazilian CPF format)

## 📞 Support

For questions or issues:
- BotNursery Project: Contact via OpenClaw workspace
- Technical issues: Check browser console for errors

## 📄 License

Part of the BotNursery project. For internal use by participating doctors/clinics.

---

**Built with ❤️ for ethical AI-assisted healthcare**

*Version 1.0 - February 2026*
