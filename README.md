# Primark Price Calculator

A specialized web application designed for calculating packaging carton prices for Primark. This tool streamlines the cost estimation process by factoring in manufacturing origins, material specifications, and dynamic fee structures.

![PACD Logo](assets/allport-pacd-logo.png)

## Features

### 📦 Carton Configuration
*   **Manufacturer Origin**: Select from verified production regions (e.g., Bangladesh, India, China).
*   **Material Selection**: Choose specific Flute Types (C32, C40, BC40) based on origin capabilities.
*   **Carton Styles**: Toggle between "Standard Footprint" (pre-defined sizes) and "Custom Footprint" (flexible dimensions).

### 💰 Intelligent Pricing Engine
*   **Dynamic Calculations**: Automatically computes Unit Price, Total Area, and Total Price.
*   **Fee Structure**:
    *   **Program Management Fee**: Automatically applied at **8%**.
    *   **Rebates**: Configurable rebate logic for Primark.
    *   **SQM Pricing**: Base price set to **$0.85 per m²** for custom dimensions.
*   **Small Order Logic**: Applies specific marking/printing fees (Screen Print vs. Label) for orders with a **Quantity < 50**.

### 📄 Professional PDF Export
*   **Dedicated Print View**: Generates a clean, branded A4 Quote/Estimate using a separate layout engine (`pdf_export.html`).
*   **Smart Layout**: Automatically organizes specifications, dimensions, and cost breakdowns.
*   **Reliable Generation**: Supports both automated PDF download and robust "Print to PDF" (Ctrl+P) capabilities.

## Usage

1.  **Launch**: Open `index.html` in any modern web browser.
2.  **Configure**: Select your Origin, Flute Type, and Carton Style.
3.  **Input**: Enter dimensions (if custom) and the required Carton Quantity.
4.  **Calculate**: Click **Calculate Price** to see the detailed cost breakdown.
5.  **Export**: Click **Export PDF** to generate a formal quote document.

## Technical Details

*   **Frontend**: Plain HTML, CSS, and JavaScript for maximum portability and speed.
*   **Styling**: Custom CSS variables for consistent branding (Navy Blue & Red), featuring glass-morphism effects.
*   **PDF Generation**: Utilizes `html2pdf.js` with a dedicated print stylesheet for pixel-perfect A4 references.
*   **Icons**: Integrated Lucide icons for a modern UI feel.

## Recent Updates

*   **Calculation Logic**: Updated Print threshold to < 50 units, Fee to 8%, and SQM Base Price to $0.85.
*   **PDF Export**: Completely overhauled export engine to use a cloned, off-screen renderer for consistent results across devices.
*   **UI Polish**: Enhanced button alignment and spacing for a better user experience.
