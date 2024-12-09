# mudd.one - Multimodal Ultrasound Data Distiller (**mudd suite** phase 1)

## Overview

### **mudd** is a comprehensive suite for processing, analyzing, measuring, diagnostic sugestion and live exam analysis and reporting for veterinary ultrasound imaging multiframe data. 

    **mudd.one** app is the first phase of the complex **mudd suite** focused on ultrasound video data analysis and preparation training datasets for various ML tools. It supports various video formats (ffmpeg compatibile) and DICOM files (single and multiframe) by pydicom implementation, providing automatic and manual cropping, frame extraction, preprocessing, filtering, and masking capabilities using user-prefered segmentation model.

## Features
- Multiple format support (mp4, mov, avi, wmv, DICOM multiframe)
- Automatic ultrasound area detection and cropping using simple binary detection or AI segmentation model of user's choice (start- and endpoints provided)
- Automatic cropping of ultrasound area with depth scale based on segmentation model confidence level (≥0.9 by default)
- Manual cropping with canvas tools upon failed to apply automatic crop
- Video preprocessing (resolution normalization, grayscale conversion)
- Various filtering options (histogram equalization, contrast adjustment, adaptive thresholding, canny and others)
- Manual masking and labeling canvas tool with basic segmentation libraries drawing function or advenced segmentation model of user's choice delivered canvas tool (implementation start- and endpoints provided)
- Customizable export formats tailored to user's ML dataset requirements
- FastAPI Backend and React/Node.js Frontend with basic UI demo provided

## Project Tree Structure
```
mudd.one/
├── client/                     # Frontend Application
│   ├── src/
│   │   ├── components/         # React Components
│   │   │   ├── ui/             # Reusable UI Components
│   │   │   │   ├── Button/     # Custom Button Components
│   │   │   │   ├── Input/      # Form Input Components
│   │   │   │   └── Layout/     # Layout Components
│   │   │   ├── upload/         # Image Upload Components
│   │   │   ├── processing/     # Image Processing Interface
│   │   │   └── visualization/  # Results Visualization
│   │   ├── pages/              # Next.js Pages
│   │   └── styles/             # Global Styles
│   └── public/                 # Static Assets
├── server/                     # Backend Application
│   ├── core/
│   │   ├── sm_integration/     # Segmentation model Integration
│   │   ├── memory_bank/        # Memory & Confidence System
│   │   └── processors/         # Image Processors
│   ├── api/
│   │   ├── routes/             # FastAPI Endpoints
│   │   └── services/           # Business Logic
│   └── ml/
│       ├── models/             # AI Models
│       └── training/           # Training Scripts
├── docs/                       # Documentation and dependencies list
└── installation/               # Platform dependend installation .sh scripts
```

## Installation

1. Clone the repository:
```bash
git clone https://github.com/Szowesgad/mudd.one.git
cd mudd
```

2. Run the installation script:
```bash
chmod +x install.sh
./install.sh
```

3. Configure the environment:
- Copy `.env.example` to `.env`
- Adjust settings according to your environment

## Usage

1. Start the application:
```bash
python run.py
```

2. Open web browser and navigate to:
```
http://localhost:3000
```

3. Processing workflow:
   - Upload video/DICOM file
   - Verify automatic cropping or adjust manually
   - Review cropped video with cineloop scrolling tool
   - Apply filters as needed
   - Create masks 
   - Export processed data

## API Endpoints

### Backend API
- `POST /api/upload` - Upload video file
- `POST /api/process` - Process video
- `POST /api/apply-filter` - Apply filter to frame (noise detection dependend)
- `POST /api/create-mask` - Create mask using segmentation tool (as example)

## Development

### Backend Development
```bash
cd backend
pip install -r requirements.txt
uvicorn app:app --reload
```

### Frontend Development
```bash
cd frontend
npm install
npm run dev
```

## Troubleshooting

### Common Issues

1. SAM2.1 Model Loading
```
Error: Could not load SAM model
Solution: Ensure CUDA or MPS is properly installed and model checkpoint exists
```

2. DICOM Processing
```
Error: Cannot read DICOM file
Solution: Check if pydicom is properly installed and file is not corrupted
```

3. Memory Issues
```
Error: Out of memory
Solution: Reduce batch size or video resolution
```

## Contributing
1. Fork the repository
2. Create feature branch
3. Commit changes
4. Push to branch
5. Create Pull Request

## License
MIT License

## Contact
For support or questions, please contact: mudd.project@hiai.vision#
Multimodal Ultrasound Data Distiller by hiai.vision® (the AMLT.ai brand)
