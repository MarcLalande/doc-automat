# doc-automat

Case study for a private fullstack project that turns messy business PDFs into structured data.

The source code and real documents are not public because the project handles operational files and private business data. This repository is a sanitized overview of the architecture, stack, and engineering work.

## What It Does

- Uploads PDF documents through a web panel
- Preprocesses scanned files with orientation correction and OCR
- Sends documents through an AI extraction pipeline
- Normalizes the result into a fixed JSON structure
- Stores document status, extracted fields, errors, and exports
- Supports a background scanner mode for folders of incoming PDFs

## Why It Was Built

Manual document processing was slow and error-prone, especially when files arrived as scans, rotated pages, or inconsistent document layouts.

The goal was to make a small internal tool that could:

- reduce repetitive manual entry
- keep failed documents visible and debuggable
- work with both uploaded files and watched folders
- produce predictable JSON output for downstream systems

## Stack

**Frontend:** Vue 3, TypeScript, Vite, Tailwind CSS  
**Backend:** Node.js, Fastify, TypeScript  
**Database:** PostgreSQL  
**Processing:** OCR, PDF preprocessing, queue-based extraction  
**Infrastructure:** Docker Compose, environment-based configuration

## Main Features

- Web panel for upload, review, status tracking, and JSON export
- Background scanner that watches folder trees for new or changed PDFs
- Queue-based processing to avoid overloading external services
- Local OCR text stored for verification
- Error states shown to users instead of silently failing
- Configurable runtime behavior through environment variables
- Docker setup for repeatable deployment

## Engineering Notes

The hardest parts were not the UI itself, but the edge cases around real documents:

- scans arriving sideways or upside down
- half-copied files appearing in watched folders
- documents that were not the expected type
- AI responses needing strict normalization
- keeping processing state stable across restarts

The system was built around explicit states, deterministic preprocessing, and simple operational visibility.

## What I Worked On

- Designed the document processing flow from upload/folder input to JSON output
- Built the Vue admin panel and TypeScript backend API
- Added PDF preprocessing, OCR verification, and extraction queueing
- Implemented persistent processing state and visible error handling
- Prepared Docker-based local deployment

## Privacy

This repository intentionally excludes:

- source code
- private prompts
- real schemas
- client documents
- API keys
- internal deployment details

The original implementation is private because it was built for a company workflow and handles sensitive
operational documents.
