# WorkTrust — Unified Workforce Management Portal
### Tailored specifically for Colleges (Campus Operations) and Hospitals (Clinical & Support Staff)

**WorkTrust** is a responsive, enterprise-grade workforce management system built with **React**, **Vite**, **JavaScript**, and custom modern **CSS**. It unifies two critical service sectors under one dashboard with seamless sector switching, live calculations, simulated hardware attendance demos, and printable payroll slips.

---

## 🌟 Key Features Overview

### 1. Unified Dashboard & Sector Selector
- **Interactive Sector Switcher in Header:**
  - 🎓 **College Campus Sector:** Campus non-teaching operations.
  - 🏥 **Hospital Healthcare Sector:** 24/7 Clinical & support staff.
  - 🌐 **Multi-Sector Overview:** Combined enterprise view across both divisions.
- **Dynamic Context Theming:** Emerald styling for campus operations, clinical sky-blue for healthcare, deep slate headers (`#0f172a`).
- **Interactive Toast Notifications:** Immediate visual confirmation for all actions (check-ins, shift creation, hazard logging, edits).

---

### 2. 🎓 College Module (Non-Teaching Staff)
- **Staff Managed:** Cleaners & sanitation crew, campus security guards, facilities maintenance (electricians & plumbers), and administrative support clerks (exam cell & admissions).
- **Employee Directory:** Full profile cards and table view with search by name/ID/zone, filtering by department and active status.
- **Form & Validation:** Modal to enroll or edit staff records with field validation (positive basic salary, wage rates, emergency contact).
- **Shift Scheduler:** Morning (06:00 - 14:00), General Day (09:00 - 17:00), Evening (14:00 - 22:00), and Night Security (22:00 - 06:00). Day-by-day roster viewer and custom shift generator.
- **Simulated QR Attendance Demo:** Camera viewfinder animation, green laser scanning beam, simulated badge recognition, and check-in/check-out timestamp logging.
- **Working Hours & Overtime:** Automatically computes regular shift hours and calculates time beyond 8 hours as overtime (paid at **1.5x regular wage**).

---

### 3. 🏥 Hospital Module (Clinical & Support Staff)
- **Staff Managed:** ICU and triage registered nurses, infection control & biomedical waste handlers, emergency security officers, and diagnostic technicians (CT, MRI, Biochem, Biomedical).
- **24/7 Round-the-Clock Rotations:** Day, Evening, and Night Critical shifts with night shift differential allowances (`+$150/mo`).
- **🚨 Missing Check-Out Alerts:** Real-time alert banner detecting staff members whose shift has ended but have no checkout timestamp logged. Includes **"Verify Staff Safety & Force Check-Out"** modal with supervisor verification notes.
- **🩺 Ward Staffing Gap Indicators:** Real-time staffing monitors comparing required nurse-to-patient and support staff quotas against rostered personnel across ICU, ER Trauma Bay, Surgical Suites, Radiology, and Pathology. Features one-click **"Request Backup Cover"** dispatcher.
- **⚠️ Workplace Hazard Reports & Tracking:** Incident logging board for biomedical sharps overflow, chemical spills, frayed electrical cords, and ventilation issues. Workflow status tracking (**Open** ➔ **Under Investigation** ➔ **Remediation in Progress** ➔ **Resolved**).
- **🔒 Privacy Notice:** Operates strictly with fictional demo data. Zero Patient Health Information (PHI) is ingested or stored.

---

### 4. 💰 Shared Payroll Module & Printable Payslips
- **Automated Live Calculation:**
  - **Basic Pay:** Contracted monthly salary.
  - **Allowances:** Standard allowance plus night-shift differential for hospital and security personnel.
  - **Overtime Earnings:** Accurately calculated from attendance logs:
    $$\text{Overtime Earnings} = \text{Overtime Hours} \times (\text{Hourly Rate} \times 1.5)$$
  - **Gross Pay:** $\text{Basic} + \text{Allowances} + \text{Overtime Earnings}$
  - **Statutory Deductions:** Provident Fund (12% of basic), Income Tax / TDS estimate (4%–10%), Medical & Welfare ($45.00), Professional Tax ($20.00).
  - **Net Take-Home Salary:** $\text{Gross Pay} - \text{Total Deductions}$
- **Itemized Calculation Modal:** Transparent breakdown explaining the exact formula and attendance records used.
- **🖨️ Printable Payslips:** Official certified payslip format with institutional headers, employee ID badges, earnings/deductions grid, amount in words, and authorized signature lines. Uses `@media print` CSS so clicking **"Print / Save as PDF"** opens a print dialogue formatted for clean A4 output without navigation or buttons.

---

## 🚀 How to Run Locally

### Prerequisites
Make sure **Node.js** (version 18 or higher) and **npm** are installed on your machine.
- To check:
  ```powershell
  node -v
  npm -v
  ```
- If Node.js is not yet installed on Windows, download and install the LTS version from [https://nodejs.org/](https://nodejs.org/).

### Step 1: Open the Project Directory
Open PowerShell or your terminal in this project folder:
```powershell
cd "c:\Users\madhumitha\OneDrive\Desktop\workplace"
```

### Step 2: Install Dependencies
Install Vite and React dependencies:
```powershell
npm install
```

### Step 3: Start the Vite Local Development Server
```powershell
npm run dev
```

### Step 4: Open in Your Browser
Once the dev server starts, Vite will print a local URL (typically `http://localhost:5173`). Open that URL in your browser:
```
http://localhost:5173
```

---

## 🛠️ Verification & Build Check
To test the production build locally without deploying:
```powershell
npm run build
npm run preview
```

---

## 📁 Project Architecture
```
workplace/
├── index.html                   # HTML entry point with Inter font & mobile viewport
├── package.json                 # Project scripts and dependencies
├── vite.config.js               # Vite React configuration
├── README.md                    # Project documentation & local run guide
├── public/
│   └── favicon.svg              # WorkTrust vector shield brand icon
└── src/
    ├── main.jsx                 # React root renderer
    ├── App.jsx                  # Main application orchestrator & sector routing
    ├── index.css                # Global enterprise styling, animations & @media print rules
    ├── data/
    │   └── initialData.js       # Complete fictional demo data (Colleges, Hospitals, Shifts, Hazards)
    ├── context/
    │   └── AppContext.jsx       # State store with localStorage persistence & toast manager
    ├── utils/
    │   ├── payrollCalculator.js # Accurate overtime, deductions, and gross/net calculations
    │   └── formatters.js        # Currency, dates, and severity badge styling
    └── components/
        ├── layout/
        │   ├── Header.jsx       # Sector Switcher, Alerts badge, QR Demo shortcut
        │   ├── Sidebar.jsx      # Navigation tabs, mobile drawer & privacy disclaimer
        │   └── Toast.jsx        # Notification feedback stack
        ├── common/
        │   ├── StatCard.jsx     # Metrics card with trends
        │   ├── Modal.jsx        # Accessible pop-up dialog
        │   ├── Badge.jsx        # Status and severity pills
        │   └── QrScannerModal.jsx # Simulated camera QR scanner with scanning laser
        ├── college/
        │   ├── CollegeDashboard.jsx   # Non-teaching metrics and campus distribution
        │   ├── StaffDirectory.jsx     # Cleaners, security, maintenance & admin staff
        │   ├── ShiftScheduler.jsx     # Weekly shift roster & custom shift creator
        │   └── AttendanceHistory.jsx  # Daily logs, check-in/out & overtime tracking
        ├── hospital/
        │   ├── HospitalDashboard.jsx    # Clinical workforce KPIs & safety alerts
        │   ├── ClinicalStaffDirectory.jsx # Nurses, infection control & technicians
        │   ├── ShiftRotations.jsx       # 24/7 Day/Night rotation viewer
        │   ├── StaffingGapsWidget.jsx   # Ward quota ratio indicators
        │   ├── MissingCheckoutAlerts.jsx# High-priority staff headcount audit
        │   └── HazardReports.jsx        # Biohazard, spill & equipment incident tracking
        └── payroll/
            ├── PayrollModule.jsx   # Transparent multi-sector payroll matrix
            ├── PayslipModal.jsx    # Step-by-step formula breakdown
            └── PrintablePayslip.jsx# Clean printable slip with A4 formatting
```
#   W o r k T r u s t  
 