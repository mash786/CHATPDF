Gemini AI Chatbot with PDF Support
This project is a Streamlit web application that allows users to upload PDF files, extract the content from the PDFs, and interact with Google Gemini AI to get answers to questions based on the extracted PDF content.

Features
PDF File Upload: Upload a PDF file, and the app extracts its text.
PDF Text Preview: Preview the content extracted from the uploaded PDF.
Interactive AI Chatbot: Ask questions based on the PDF, and Google Gemini AI generates responses.
Tools and Technologies
Streamlit: For building the web app interface.
PyMuPDF (fitz): For extracting text from PDF files.
Google Gemini AI API: For generating responses to user questions based on the PDF content.
Setup Instructions
1. Clone the Repository
Clone the repository to your local machine by running the following command:

bash
Copy code
git clone https://github.com/mash786/ChatPDF.git
2. Install Required Dependencies
Navigate to the project folder and install the dependencies using pip:

bash
Copy code
cd ChatPDF
pip install -r requirements.txt
3. Set Up Google Gemini API
Go to the Google Generative AI website and set up an API key.
Open the app.py file and find the following line:
python
Copy code
genai.configure(api_key="YourAPIKEY")
Replace "YourAPIKEY" with your actual API key.
4. Run the Streamlit App
After setting up the API key, you can run the app using the following command:

bash
Copy code
streamlit run app.py
5. Access the App
Once the app is running, open a browser and go to:

arduino
Copy code
http://localhost:8501
How It Works
Upload PDF: On the homepage, click the Upload PDF button to upload a PDF file.
Extract PDF Text: The app will extract text from the uploaded PDF using PyMuPDF (fitz).
Preview PDF Content: The first 1500 characters of the extracted PDF text will be displayed in the PDF Content Preview section.
Ask a Question: Enter a question related to the content of the PDF in the text input field.
Generate AI Response: The app will use the Google Gemini AI API to generate a response based on the PDF content and display it in the AI Response section.
Code Overview
Main Functions
main(): Handles the main app logic such as file upload, text extraction, and user interaction.
extract_pdf_text(): Extracts the text from the uploaded PDF using PyMuPDF.
generate_response(): Interacts with the Google Gemini AI API to generate responses based on the extracted PDF content.
Example Code Snippets
PDF Text Extraction:

python
Copy code
def extract_pdf_text(uploaded_file):
    """Extract text from PDF using PyMuPDF (fitz)."""
    doc = fitz.open(stream=uploaded_file.read(), filetype="pdf")
    pdf_text = ""
    for page_num in range(len(doc)):
        page = doc.load_page(page_num)
        pdf_text += page.get_text("text")
    return pdf_text
Generate Response Using Google Gemini:

python
Copy code
def generate_response(prompt, pdf_text):
    """Generate response based on PDF content using Google Gemini API."""
    context = f"Here is the content extracted from the PDF:\n\n{pdf_text}\n\nUser's Question: {prompt}\nAnswer:"
    model = genai.GenerativeModel("gemini-1.5-flash")
    response = model.generate_content(context)
    return response.text
Future Enhancements
Support for more file formats (e.g., DOCX, TXT).
Improve PDF text extraction accuracy for scanned documents.
Enhance context understanding for more accurate AI responses.
License
