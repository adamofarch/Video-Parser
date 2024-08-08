## Overview

This project is a Django-based web application that allows users to upload videos, extract subtitles from the videos using `ccextractor` binary, and perform keyword searches within the extracted subtitles. The application leverages Celery for asynchronous task processing and AWS DynamoDB for storing and querying subtitles.

## Technologies Used

- **Django**: Web framework for building the application.
- **Celery**: Asynchronous task queue for processing video files and subtitle extraction.
- **ccextractor**: Tool for extracting subtitles from video files.
- **AWS S3**: Cloud storage for storing uploaded videos.
- **AWS DynamoDB**: NoSQL database for storing extracted subtitles and enabling fast keyword searches.
- **Django Environ**: Library for managing environment variables.

## Features

- **Video Upload**: Users can upload video files through the web interface.
- **Subtitle Extraction**: Extracts subtitles from uploaded videos asynchronously using Celery and `ccextractor`.
- **Subtitle Storage**: Stores extracted subtitles in AWS DynamoDB.
- **Keyword Search**: Allows users to search for keywords within the subtitles and returns corresponding timestamps.
- **Scalability**: Utilizes Celery for handling multiple video processing tasks concurrently.

## Installation

1. **Clone the Repository**:
   ```sh
   git clone https://github.com/adamofarch/video_parser.git
   cd video_parser

2. 
