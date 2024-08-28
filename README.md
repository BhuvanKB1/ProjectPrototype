# Floor Plan Grid System

Welcome to the **Floor Plan Grid System**, a Flask-based prototype designed to overlay a coordinate grid on floor plan images. This tool is perfect for facilities management, office organization, or any use case requiring a visual representation of floor layouts with grid coordinates.

The application allows users to upload floor plan images or PDFs, applies a grid overlay, and provides a downloadable link to the modified floor plan. This functionality streamlines the process of managing and interacting with floor layouts in a more organized manner.

## Features

- Adds a coordinate-labeled grid to floor plan images for precise asset location tracking.
- Displays dynamic thumbnails for assets, color-coded based on warranty status.
- Generates a downloadable summary table of assets associated with floor plans.

## Prerequisites

Ensure the following are installed before starting:

- **Python** version 3.7 or newer
- **MySQL** database

## Installation

Follow these steps to set up the application locally:

1. **Clone the repository:**

   ```bash
   git clone [repository URL]
   cd floor_plan_app
   ```

2. **Set up a virtual environment (optional but recommended):**

   ```bash
   python3 -m venv venv
   source venv/bin/activate  # For Windows: venv\Scripts\activate
   ```

3. **Install the required dependencies:**

   ```bash
   pip install -r requirements.txt
   ```

## Configuration

1. **Update MySQL credentials in `app/config.py`:**

   Modify the `app/config.py` file with your MySQL database details:

   ```python
   class Config:
       # ... other configurations ...
       DB_HOST = 'localhost'
       DB_USER = 'your_mysql_username'
       DB_PASSWORD = 'your_mysql_password'
       DB_NAME = 'your_database_name'
   ```

2. **Create an `uploads` directory:**

   ```bash
   mkdir uploads
   ```

## Running the Application

Once the setup is complete, start the application using:

```bash
python3 run.py
```

The app will run on `http://localhost:5000`.

## Testing the API

Use an API client like **Postman** or **Insomnia** to interact with the application by sending a POST request.

- **Endpoint:** `http://localhost:5000/process_floor_plan`
- **Method:** POST
- **Body Type:** Multipart Form Data
- **Form Fields:**
  - `file` (File): Upload the floor plan image or PDF.
  - `building_name` (Text): Enter the building name.
  - `floor_number` (Text): Specify the floor number.
  - `grid_size` (Text, optional): Define grid size in pixels (default is 20).

**Sample Response:**

```json
{
  "message": "Floor plan processed successfully",
  "user_id": "generated-uuid",
  "building_name": "Building A",
  "floor_number": "1",
  "floorplan_link": "http://localhost:5000/uploads/generated-uuid.png"
}
```

## Accessing the Processed Image

To view or download the modified floor plan, open the `floorplan_link` provided in the response using a web browser.

## Dependencies

Below are the required dependencies for the application:

- **Flask**
- **opencv-python**
- **numpy**
- **pillow**
- **pdf2image**
- **PyMySQL**
- **cryptography**
- **blinker**
- **Flask-Cors**
- **Werkzeug**
- **click**
- **Jinja2**

## Notes

- For security purposes, use a dedicated MySQL user with limited privileges instead of the root user.

## Quick Steps

1. Install dependencies and configure the settings.
2. Launch the Flask application locally.
3. Submit a POST request with the necessary fields.
4. Access the modified floor plan via the provided download URL.

---

Thank you for choosing the **Asset Location Mapping System**!
