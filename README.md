# HGV Check UK — auto-lookup ANPR prototype

The camera scanner OCRs live video and, after the same current-style UK registration is detected in two consecutive scans with OCR confidence >=65%, automatically calls the backend `/api/vehicle/:registration`. User can edit and manually submit a registration. It supports rear/front cameras and torch where hardware allows.

Run with Node.js 20+: `cp .env.example .env`, fill approved credentials, `npm install`, `npm start`. Open `http://localhost:3000`. iPhone camera requires HTTPS deployment and Safari camera permission.

ANPR uses general Tesseract OCR, not specialist plate recognition. It may misread characters and only recognises the current standard UK format AB12CDE. Two matching reads reduce false triggers but do not guarantee correctness. Use a specialist UK-capable ANPR SDK and real-world testing for commercial release.

DVLA and DVSA credentials must remain server-side. Full VTG6A/VTG7A plating-certificate retrieval is not implemented; secure an authorised data source or build a verified document-upload process. Do not present MOT history as the plating certificate.
