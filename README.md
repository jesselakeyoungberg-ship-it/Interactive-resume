# Interactive Resume of Jesse S. LakeYoungberg

This is an interactive, single-page resume for Jesse S. LakeYoungberg, a professional in Operations & Product Management. The resume is designed to be a dynamic and engaging showcase of his skills and experience.

## Features

*   **Interactive Resume Views:** Users can filter Jesse's skills and experiences based on different roles like "Product Manager," "Software Manager," etc. This highlights the most relevant qualifications for a specific job.
*   **AI-Powered Cover Letter Assistant:** A standout feature of this resume is the cover letter generator. Users can input a job title and company name, and the application will use the Gemini API to generate a tailored cover letter based on the information in the resume.
*   **Detailed Project Case Studies:** The resume includes expandable sections for notable projects and case studies, providing detailed information about Jesse's accomplishments.
*   **Tabs for Different Sections:** The content is organized into "Professional Resume," "Projects & FAQ," and "About Me" tabs for easy navigation.

## Technologies Used

*   **Frontend:**
    *   HTML5
    *   [Tailwind CSS](https://tailwindcss.com/): For styling the user interface.
    *   JavaScript: For the interactive features like tab navigation, content filtering, and API calls.
*   **Backend (Serverless):**
    *   [Netlify Functions](https://www.netlify.com/products/functions/): The backend logic for generating the cover letter is deployed as a serverless function on Netlify.
*   **AI:**
    *   [Google Gemini API](https://ai.google.dev/): Used to generate the cover letters.

## Setup

To run this project locally, you will need to have a web browser.

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/your-username/interactive-resume.git
    cd interactive-resume
    ```
2.  **Open `index.html` in your browser:**
    You can simply open the `index.html` file in your favorite web browser to see the resume.

### Setting up the Cover Letter Generator

The cover letter generator requires a Google Gemini API key.

1.  **Get a Gemini API key:**
    Visit the [Google AI for Developers](https://ai.google.dev/) website to get your API key.

2.  **Set up Netlify Dev (Optional, for local testing):**
    If you want to test the serverless function locally, you can use the Netlify CLI.
    *   Install the Netlify CLI:
        ```bash
        npm install -g netlify-cli
        ```
    *   Create a `.env` file in the root of the project and add your API key:
        ```
        GEMINI_API_KEY=your_gemini_api_key
        ```
    *   Run the development server:
        ```bash
        netlify dev
        ```
    This will start a local server, and you can access the resume at `http://localhost:8888`.

## Netlify Function: `generate-letter.js`

The `netlify/functions/generate-letter.js` file contains the serverless function that handles the cover letter generation.

*   It receives the `jobTitle`, `companyName`, and `resumeContext` from the frontend.
*   It securely accesses the `GEMINI_API_KEY` from the environment variables.
*   It constructs a prompt for the Gemini API, including the resume context and the user's query.
*   It sends the request to the Gemini API and returns the generated cover letter to the frontend.
*   This serverless approach ensures that the API key is never exposed on the client-side.
