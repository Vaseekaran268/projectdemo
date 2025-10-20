# ⚖️ eCourts Case Scraper with PDF Capture

A powerful Streamlit application that automates case data scraping from eCourts India website, captures case details, downloads PDFs, and provides comprehensive data management capabilities.

## 🚀 Features

### Core Functionality
- **Automated Case Scraping**: Extract case data from eCourts India website
- **PDF Capture & Merging**: Automatically capture case details as PDFs and merge multiple documents
- **Excel Export**: Download comprehensive case data in Excel format
- **Database Storage**: SQLite database for organized data management
- **In-App PDF Viewer**: View captured PDFs directly in the application

### Advanced Features
- **Dual Data Views**: 
  - **All Cases**: Complete dataset for selected date
  - **Today/Tomorrow Cases**: Priority cases with upcoming hearings
- **Smart Navigation**: Automated View button clicking and back navigation
- **Date Selection**: Flexible date picking directly in browser session
- **CAPTCHA Handling**: Manual CAPTCHA input with refresh capability
- **Multi-Page Scraping**: Automatic pagination handling

### Data Management
- **Case Details Extraction**:
  - Serial Number, CNR Number, Case Type
  - Court Information, Filing & Registration Numbers
  - Next Hearing Dates, Court Names
- **PDF Processing**:
  - Whole page PDF capture
  - Additional PDF downloads from case pages
  - Automatic PDF merging
- **Database Organization**:
  - Separate tables for cases, PDF files, and merged PDFs
  - BLOB storage for PDF files
  - Timestamp tracking

## 📋 Installation Guide

### Prerequisites
- Python 3.8 or higher
- Google Chrome browser
- ChromeDriver matching your Chrome version

### Step 1: Install Dependencies

```bash
pip install streamlit==1.28.0 selenium==4.15.0 beautifulsoup4==4.12.2 pandas==2.0.3 requests==2.31.0 python-dateutil==2.8.2 lxml==4.9.3 openpyxl==3.1.2 pypdf2==3.0.1
Step 2: Install ChromeDriver
Download ChromeDriver from https://chromedriver.chromium.org/

Ensure it matches your Chrome browser version

Add ChromeDriver to your system PATH or place it in the same directory as the script

Step 3: Run the Application
bash
streamlit run app.py
🎯 Usage Guide
1. Scrape Cases
Initialize Browser: Click "Initialize Browser Session" to open eCourts website

Select Date: Choose your desired date directly in the browser

Enter CAPTCHA: Input the CAPTCHA value shown in the image

Start Capture: Begin automatic data capture for all cases

2. View Database
All Cases: View complete dataset with all captured cases

Today/Tomorrow Cases: Filter for priority cases only

Search Functionality: Search by CNR, Serial, or Case Type

Excel Export: Download filtered data as Excel files

3. PDF Viewer
Filter Options: View PDFs for All Cases or Today/Tomorrow Cases only

In-App Viewing: Display PDFs directly in the browser

Download Options: Download individual or merged PDFs

📊 Sample Output
Case Data Table (Excel Export)
Serial	CNR Number	Case Type	Court Info	Filing Number	Registration Number	Court Name	Next Hearing	PDF Status
1	DL010000000000001	Criminal	Court 1 - Judge A	123/2024	456/2024	Delhi High Court	2024-01-15	✅
2	DL010000000000002	Civil	Court 2 - Judge B	124/2024	457/2024	District Court	2024-01-16	✅
3	DL010000000000003	Criminal	Court 1 - Judge A	125/2024	458/2024	Delhi High Court	2024-01-17	✅
PDF Output Structure
text
downloads/
├── serial_1_093045.pdf
├── serial_2_093046.pdf
├── additional_document_1.pdf
├── additional_document_2.pdf
└── merged_case_1_20240115_093047.pdf
Database Schema
text
cases/
├── id (Primary Key)
├── serial_number
├── cnr_number
├── case_type
├── court_info
├── filing_number
├── registration_number
├── court_name
├── next_hearing_date
├── captured_date
├── pdf_path
├── additional_pdfs
└── merged_pdf_path

pdf_files/
├── id (Primary Key)
├── case_id (Foreign Key)
├── filename
├── file_data (BLOB)
├── file_type
└── uploaded_date

merged_pdfs/
├── id (Primary Key)
├── case_id (Foreign Key)
├── filename
├── file_data (BLOB)
└── merged_date
🔧 Configuration
Environment Variables
DOWNLOAD_DIR: Directory for downloaded files (default: ./downloads)

ECOURTS_URL: eCourts website URL

Browser Options
Headless mode for server environments

Custom download directory setup

PDF printing preferences

Timeout and wait configurations

🛠️ Troubleshooting
Common Issues
ChromeDriver Not Found

text
Error: ChromeDriver not found in PATH
Solution: Download ChromeDriver and add to PATH or place in script directory

CAPTCHA Not Loading

text
Error: Captcha image not found
Solution: Refresh CAPTCHA or check network connection

PDF Display Issues

text
Error: PDF doesn't display properly
Solution: Use download option or check browser PDF viewer compatibility

Database Schema Errors

text
Error: duplicate column name
Solution: Use "Update Database Schema" in Settings or reset database

Performance Tips
Use stable internet connection for scraping

Close unnecessary browser tabs during operation

Monitor database size and reset if needed

Use filters to manage large datasets

📁 Project Structure
text
ecourts-scraper/
├── app.py                 # Main application file
├── ecourts_data.db        # SQLite database (auto-generated)
├── downloads/            # Downloaded files directory
│   ├── pdfs/            # Case PDFs
│   ├── merged/          # Merged PDFs
│   └── exports/         # Excel exports
├── requirements.txt      # Python dependencies
└── README.md           # This file
🔒 Data Privacy & Compliance
This tool is for legitimate case management purposes

Respect website terms of service and rate limiting

Store sensitive data securely

Comply with local data protection regulations

🤝 Contributing
Fork the repository

Create a feature branch

Make your changes

Test thoroughly

Submit a pull request

📄 License
This project is for educational and legitimate legal purposes. Users are responsible for complying with eCourts website terms of service and applicable laws.

🆘 Support
For issues and questions:

Check the Troubleshooting section

Verify all dependencies are installed

Ensure ChromeDriver is properly configured

Check application logs for detailed error information

