# Real-Time Chat Application

This is a simple real-time chat application that allows users to send and receive messages. It uses Firebase for real-time database functionality and local storage for caching messages.

## Features

*   **Real-time messaging:** Messages are sent and received instantly.
*   **User-friendly interface:** The chat interface is simple and easy to use.
*   **Message caching:** Messages are cached in local storage for offline access.
*   **Firebase integration:** Firebase is used for real-time data synchronization.

## Setup and Running the Application

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/your-username/real-time-chat-app.git
    cd real-time-chat-app
    ```

2.  **Firebase Setup:**
    *   Create a new Firebase project at [https://console.firebase.google.com/](https://console.firebase.google.com/).
    *   In your Firebase project, go to **Project settings** > **General**.
    *   Under "Your apps", click on the web icon (`</>`) to add a new web app.
    *   Register your app and copy the Firebase configuration object.
    *   Create a `firebase-config.js` file in the project's root directory.
    *   Paste the Firebase configuration object into `firebase-config.js`:
        ```javascript
        // firebase-config.js
        const firebaseConfig = {
          apiKey: "YOUR_API_KEY",
          authDomain: "YOUR_AUTH_DOMAIN",
          projectId: "YOUR_PROJECT_ID",
          storageBucket: "YOUR_STORAGE_BUCKET",
          messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
          appId: "YOUR_APP_ID"
        };

        // Initialize Firebase
        firebase.initializeApp(firebaseConfig);
        ```
    *   Enable the Firebase Realtime Database:
        *   In the Firebase console, go to **Build** > **Realtime Database**.
        *   Click **Create Database**.
        *   Choose a location for your database.
        *   Select **Start in test mode** for the security rules (for development purposes).
        *   Click **Enable**.

3.  **Open `index.html` in your browser:**
    *   Open the `index.html` file in your web browser to run the application.

## Technologies Used

*   **HTML:** For the structure of the web page.
*   **CSS:** For styling the application.
*   **JavaScript:** For the application logic and interactivity.
*   **Firebase:** For real-time database and backend services.

## How to Use the Chat Application

1.  **Enter your name:** When you open the application, you'll be prompted to enter your name. This name will be displayed with your messages.
2.  **Send messages:** Type your message in the input field at the bottom and click "Send" or press Enter.
3.  **View messages:** Messages from all users will appear in the chat window in real-time.

## Data Persistence

*   **localStorage:** Messages are saved in the browser's local storage. This allows you to see previous messages even if you close and reopen the browser (as long as the browser's cache is not cleared).
*   **Firebase Realtime Database:** Messages are also stored in Firebase, ensuring that all users see the same chat history and that messages persist across different devices and sessions. Firebase acts as the single source of truth for the chat data.
