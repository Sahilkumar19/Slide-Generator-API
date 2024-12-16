# Slide Generator API

This application provides an API to generate, configure, and download presentations dynamically. It uses Flask for the API server and Python's `pptx` library to create PowerPoint presentations. I have added some sample presentation generated uing the api which are in the presentatins folder inside the main directory(SlideGeneratorAPI).

## Features

- Create presentations with a configurable number of slides and layouts.
- Configure and update presentations after creation.
- Download generated presentations.
- Built-in rate-limiting for API requests.

## Testing

- I have tested all endpoints of the APIs using the postman.

## Loom Video Link

- https://www.loom.com/share/06fa628fac7a46caa3ce9f30d910d0b7?sid=a9dedd10-2824-4407-b41d-dec70f6ee562

## Setup Instructions

1. Clone the repository:

   ```bash
   git clone https://github.com/Sahilkumar19/Slide-Generator-API.git
   cd Slide-Generator-API
   ```

2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Set up an environment variable for the Gemini API key (optional):

   ```bash
   export GEMINI_API_KEY="your-api-key"
   ```

   Or replace the `GEMINI_API_KEY` variable in the code directly.

4. Run the application:

   ```bash
   python app.py
   ```

5. Use a REST client (e.g., Postman) to interact with the API.

## API Documentation

### 1. Create a Presentation

**POST /api/v1/presentations**

#### Request Body

```json
{
  "topic": "<topic-name>",
  "config": {
    "num_slides": 10,
    "layout": "bullet_points",
    "theme": { "background_color": "#FFFFFF" }
  }
}
```

#### Response

```json
{
  "id": "<presentation-id>",
  "message": "Presentation created successfully"
}
```

### 2. Get Presentation Metadata

**GET /api/v1/presentations/<presentation_id>**

#### Response

```json
{
  "id": "<presentation-id>",
  "topic": "<topic-name>",
  "config": { "num_slides": 10 },
  "created_at": "<timestamp>",
  "file_path": "<path-to-file>"
}
```

### 3. Download Presentation

**GET /api/v1/presentations/<presentation_id>/download**

Downloads the generated presentation as a `.pptx` file.

### 4. Configure a Presentation

**POST /api/v1/presentations/<presentation_id>/configure**

#### Request Body

```json
{
  "num_slides": 5,
  "layout": "two_column"
}
```

#### Response

```json
{
  "message": "Presentation configuration updated successfully"
}
```
