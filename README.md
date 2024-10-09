#!/bin/bash

# Exit the script if any command fails
set -e

# Step 1: Clone the repository
echo "Cloning the repository..."
git clone https://github.com/mash786/ChatPDF.git

# Navigate to the project directory
cd ChatPDF

# Step 2: Install required dependencies
echo "Installing dependencies..."
pip install -r requirements.txt

# Step 3: Set up Google Gemini API
echo "Please ensure you have your Google Gemini API key."
echo "You need to replace 'YourAPIKEY' in 'app.py' with your actual API key."
echo "Find the line where the API key is configured:"
echo "  genai.configure(api_key='YourAPIKEY')"
echo "Make sure to update it with your key before proceeding."

# Step 4: Run the Streamlit app
echo "Running the Streamlit app..."
streamlit run app.py

# Step 5: Output instructions
echo "The app is now running on http://localhost:8501"
echo "Open this URL in your web browser to access the app."

