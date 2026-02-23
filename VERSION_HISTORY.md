# Version History
**Primark Carton Price Calculator**

---

## Version 2.5
**Date:** February 23, 2026

### Changes

#### 1. PDF Export (pdf_export.html)
- **Cross-Device Consistency Fix**: Resolved issue where exported PDFs looked different on different devices (desktop vs. mobile vs. tablet).
  - **Root Cause**: The clone container and page element used `mm` units (e.g., `width: 210mm`) which browsers convert differently based on device DPI/pixel density — causing layout shifts on high-DPI mobile screens.
  - **Fix**: Switched all sizing in the PDF generation pipeline to **fixed pixel values** (`794px × 1123px` — A4 at 96 DPI) instead of `mm` units.
  - Padding changed from `20mm` to `57px` (pixel equivalent) for deterministic rendering.
  - Off-screen container now positioned via `left: -894px` to avoid any visibility flicker.
  - Image format uses JPEG at 98% quality for optimal file size.

---

## Version 2.4
**Date:** February 8, 2026

### Changes

#### 1. Pricing Update
- **SQM Rate**: Reduced the base SQM price rate from **$0.80** to **$0.75** USD.

---

## Version 2.3
**Date:** February 6, 2026

### Changes

#### 1. Calculation Logic
- **C-Flute Formula Update**: Adjusted the blank sheet calculation for C-Flute (C32/C40):
  - Length Formula: `(length + width) * 2 + 50` (Previously `+ 15`)
  - Width Formula: `(width + height)` (Previously `(width + height) - 10`)
  - **Full Formula**: `Area = ((2*L + 2*W + 50) * (H + W) / 1,000,000) * 1.08`


## Version 2.2
**Date:** February 5, 2026

### Changes

#### 1. User Interface (index.html)
- **Carton Type Options**: 
  - Changed "Custom" to "Custom Carton"
  - Changed "Standard Footprint" to "Standard Carton (Variable Height)"
- **Carton Selection**: Removed "(Variable Height)" from individual carton options (now shown in Carton Type)
- **Small Order Surcharge Text**: Updated message from "Small Order Surcharge: A $20.00 setup fee applies for orders under 50 cartons." to "Below MOQ (>50) packaging supplier will charge $20 per size breakdown."
- **Flute Type**: Changed "C Flute (C40ECT)" to "C Flute (40ECT)"
- **Packaging Suppliers**: Updated supplier list to:
  - Uniglory Packaging Industries Ltd.
  - Reflex Packaging Ltd.
  - Transworld Packaging Ltd.
  - Union Label & Accessories Ltd.
  - Epyllion Ltd.
  - Youngshine Packtrims Ltd.

#### 2. Calculation Logic
- **Unit Price**: Now displays the actual single carton price (`Area per Carton × SQM Price`) instead of showing the SQM price itself.

#### 3. PDF Export (pdf_export.html)
- **Layout**: Moved "Packaging Supplier" to appear below "Factory Name" section
- **Device Consistency**: Added `windowWidth`, `windowHeight`, and `deviceScaleFactor` settings to ensure consistent PDF output across all devices regardless of screen DPI or pixel ratio.

---

## Version 2.1
**Date:** February 5, 2026

### Changes

#### 1. User Interface (index.html)
- **Header**: Removed "Primark Price Calculator" text from the main navigation bar.
- **Labels**: Renamed generic "Code" fields to specific "Supplier Code" and "Factory Code".
- **New Field**: Added "Packaging Supplier Name" dropdown with specific options (Uniglory, Reflex, etc.) in the Supplier Information section.
- **Origin**: Hidden the "Manufacturer Origin" selection (defaulted to Bangladesh).
- **Flute Type**: Moved "Flute Type" to the top of the Specifications section and locked it to "C Flute (C40ECT)".
- **Carton Display**: Updated standard carton dropdown items to show as `Length x Width mm (Variable Height)`.
- **Carton Type**: Enabled "Carton Type" selection by default.

#### 2. Calculation Logic
- **Standard Cartons**: Updated the list of standard carton dimensions with 14 new size pairs.
- **Pricing Formula**: 
  - Set base **SQM Price to $0.80**.
  - **All** cartons (Standard and Custom) are now priced based on the SQM formula (`Area * $0.80`). Fixed unit prices for standard cartons were removed.
- **Surcharges**: 
  - Replaced the previous marking options (Label/Screen Print) with a flat **$20.00 Small Order Surcharge** applied automatically to orders with quantity < 50.
- **Wastage**: Confirmed 8% wastage (1.08x) is applied strictly to the Area calculation.

#### 3. PDF Export (pdf_export.html)
- **Heading**: Added a main heading "Carton Price Calculator for Primark".
- **Fields**: Included "Packaging Supplier" in the Supplier Information section.
- **Layout**: 
  - Added the **Date** below the main heading (right-aligned).
  - Removed the page footer.
  - Renamed "Supplier Price" row to "Packaging Supplier Net Revenue".
- **Data Accuracy**: Fixed "Flute Type" to display the full description (e.g., "C Flute (C40ECT)") rather than the internal code.
- **Dynamic Filenaming**: implemented smart file naming for exports:
  - **Standard**: `stn[Length][Width][Height]_[Quantity].pdf` (e.g., `stn400330300_55.pdf`)
  - **Custom**: `cus[Length][Width][Height]_[Quantity].pdf`
- **Resolution Independence**: Fixed issue where PDF layout shifted based on screen resolution. Export now forces a standard A4 width (794px) to ensure consistent output on all devices.
