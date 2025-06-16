# Real-Time Chat Application

This is a simple real-time chat application that allows users to send and receive messages within distinct conversation threads. It uses Firebase for real-time database functionality.

## Features

*   **Real-time messaging:** Messages are sent and received instantly within a selected thread.
*   **Threaded Conversations:** Organize discussions into separate threads. Each thread has its own isolated set of messages.
*   **User-friendly interface:** The chat interface is simple and easy to use.
*   **Firebase integration:** Firebase is used for real-time data synchronization for each thread.
*   **Shareable Thread Links:** Easily share a link to a specific chat thread for others to join.
*   **Username Persistence:** Your chosen username is saved locally for convenience.

## Threads

The application now supports threaded conversations, allowing for multiple, separate chat sessions.

*   **Starting a New Thread:**
    *   Click the hamburger menu icon (☰) in the top-right corner.
    *   Select "Start New Thread" from the menu.
    *   The page will reload with a unique URL for your new thread (e.g., `index.html?thread=thread_1678886400000`). This new URL is your unique thread link.
*   **Joining a Thread:**
    *   If you have a thread-specific link, opening it in your browser will directly take you to that thread.
    *   If you open the base `index.html` without a thread ID, you will be prompted to start a new thread.
*   **Message Isolation:** Messages sent within one thread are not visible in other threads, ensuring conversations remain organized and private to that specific thread.
*   **Sharing Threads:**
    *   Once you are in a thread, click the hamburger menu icon (☰).
    *   Select "Share".
    *   The application will provide a shareable link that includes the current `threadId` (e.g., `index.html?apiKey=YOUR_API_KEY&thread=CURRENT_THREAD_ID`).
    *   Anyone with this link can join your specific chat thread.

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
    *   **Important:** The application expects the Firebase API key to be provided either via a URL parameter (`apiKey=YOUR_KEY`) on first load (it will then be saved to local storage) or by manually entering it via the "Firebase Setup" option in the application menu. For local development, you can modify `index.html` to directly include your Firebase config if preferred, but the primary method is via URL parameter or manual entry.
    *   Enable the Firebase Realtime Database (or Firestore, as the app uses Firestore):
        *   In the Firebase console, go to **Build** > **Firestore Database**.
        *   Click **Create Database**.
        *   Choose a location for your database.
        *   Select **Start in test mode** for the security rules (for development purposes, allowing open read/write).
        *   Click **Enable**.
        *   The application uses Firestore paths like `threads/{threadId}/messages/{messageId}`.

3.  **Open `index.html` in your browser:**
    *   Open the `index.html` file in your web browser.
    *   If it's your first time and you haven't hardcoded the Firebase config, append your API key to the URL: `index.html?apiKey=YOUR_FIREBASE_API_KEY`.
    *   The application will then prompt you to start a new thread or you can use a shared thread link.

## Technologies Used

*   **HTML:** For the structure of the web page.
*   **CSS:** For styling the application.
*   **JavaScript:** For the application logic and interactivity.
*   **Firebase (Firestore):** For real-time database and backend services, storing messages per thread.

## How to Use the Chat Application

1.  **Set your Firebase API Key (if first time):**
    *   Use the URL parameter `?apiKey=YOUR_API_KEY` when opening `index.html`.
    *   Alternatively, use the "Firebase Setup" option in the hamburger menu (☰).
2.  **Enter your name:**
    *   Click the hamburger menu (☰) and select "Set/Change Name".
    *   This name will be displayed with your messages and is saved locally.
3.  **Start or Join a Thread:**
    *   To start a new conversation, click the hamburger menu (☰) and select "Start New Thread".
    *   To join an existing conversation, open a shared thread link.
    *   If no thread is active, you'll be prompted to start one.
4.  **Send messages:** Once in a thread, type your message in the input field at the bottom and click "Send" or press Enter.
5.  **View messages:** Messages from users within the current thread will appear in the chat window in real-time.
6.  **Share a Thread:** Use the "Share" option in the menu to get a link to the current thread.

## Data Persistence

*   **localStorage:**
    *   The Firebase API key (once entered) is stored in local storage for convenience.
    *   Your chosen username is stored in local storage.
    *   General chat messages are *not* stored in local storage by default when a thread is active; the application prioritizes Firebase for thread messages. Thread-specific local storage could be a future enhancement for offline caching per thread.
*   **Firebase Firestore:**
    *   Messages are stored in Firestore under a specific thread structure: `threads/{threadId}/messages/{messageId}`.
    *   This ensures that messages are persistent across devices and sessions for each thread and are only loaded for the relevant active thread.
    *   Comments are stored as part of the message object within the respective thread.
    *   Firebase acts as the single source of truth for all thread-specific chat data.
