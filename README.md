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
- **Subtitle Storage**: Stores extracted subtitles in **AWS DynamoDB**.
- **Keyword Search**: Allows users to search for keywords within the subtitles and returns corresponding timestamps.
- **Scalability**: Utilizes Celery for handling multiple video processing tasks concurrently.

## Installation

1. **Clone the Repository**:
   ```sh
   git clone https://github.com/adamofarch/video_parser.git
   cd video_parser

2. **Create and Activate a Virtual Environment**:
   ```sh
   python -m venv venv
   source venv/bin/activate

3. **Install Dependencies**:
   ```sh
   pip install -r requirements.txt

4. **Install ccextractor binary**:
   - Note: It is highly recommended build ccextractor from source, You can Follow the **[Compilation Instructions](https://github.com/CCExtractor/ccextractor/blob/master/docs/COMPILATION.MD)**
   - Note for Arch Users: You can also install ccextractor from AUR using your favourite AUR helper
   Follow the Installation guide on **[CCExtractor/ccextractor](https://github.com/CCExtractor/ccextractor)** to install on your operating system.

5. **Set Up Environment Variables**:
   - Create a `.env` file in the project root with the following variables:
     ```txt
     AWS_ACCESS_KEY_ID=your_aws_access_key
     AWS_SECRET_ACCESS_KEY=your_aws_secret_key
     AWS_STORAGE_BUCKET_NAME=your_s3_bucket_name
     AWS_S3_REGION_NAME=your_s3_region

6. **Run Migrations**:
   ```sh
   python manage.py migrate

7. **Start the Development Server**:
   ```sh
   python manage.py runserver

8. **Start Celery Worker**:
   ```sh
   celery -A video_parser worker -l INFO

## Usage

   1. **Upload a Video**:
      - Navigate to the home page and upload a video file.
      - The video will be processed asynchronously and stored in a configured **S3 BUCKET**, and subtitles will be extracted and stored in **DynamoDB**.

   2. **Search Subtitles**:
      - Enter a keyword in the search form to find the corresponding timestamps in the video where the keyword appears in the subtitles.

## Backend Capabilities

   - **Asynchronous Processing:** Leveraging Celery, the application can handle multiple video uploads and subtitle extraction tasks concurrently, ensuring a responsive user experience.
   - **Scalable Storage:** Using **AWS S3** for video storage and **AWS DynamoDB** for subtitle storage ensures that the application can scale to handle large volumes of data efficiently.
   - **Efficient Searching:** Storing subtitles in DynamoDB allows for fast keyword searches, providing users with quick and accurate results.

## Contributing 

Feel free to open issues or submit pull requests for improvements or bug fixes.

## License

This project is licensed under the MIT License.
