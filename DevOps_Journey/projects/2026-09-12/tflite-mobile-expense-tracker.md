# TensorFlow Lite Mobile Expense Tracker

## Overview
Develop an Android app that uses on-device ML to categorize expenses from photos of receipts and bank statements.

## Architecture
- Mobile app: Kotlin with ML Kit
- Image processing: Tesseract OCR for text extraction
- Classification: Custom TensorFlow Lite model for expense categories
- Storage: Room database for transaction history
- Sync: Optional cloud backup via Firebase

## Workflow
1. User photographs receipt or statement
2. App extracts text using OCR
3. ML model classifies line items into categories
4. User reviews and confirms categorized transactions
5. App updates budget dashboard with insights

## Tools
- Kotlin, TensorFlow Lite, ML Kit, Room, Firebase

## Learning Goals
- Mobile ML deployment
- OCR and text extraction
- Image classification with TF Lite
- On-device data processing

## Build Milestones
1. Basic Android app structure
2. Camera and OCR integration
3. TF Lite model training and deployment
4. Expense categorization logic
5. Dashboard and statistics
