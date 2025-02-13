# React Native Firebase & API Integration App

## Setup Instructions

### Prerequisites
Ensure you have the following installed:
- Node.js (latest LTS recommended)
- npm or yarn
- Expo CLI (`npm install -g expo-cli`) or React Native CLI
- Firebase account with a new project

### Installation
1. Clone the repository:
   ```bash
   git clone <repository_url>
   cd <project_directory>
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
   or
   ```bash
   yarn install
   ```
3. Setup Firebase configuration (see next section).

### Firebase Configuration
1. Create a Firebase project at [Firebase Console](https://console.firebase.google.com/).
2. Enable **Authentication** → **Sign-in method** → **Email/Password**.
3. Add a new Firebase app and get the configuration details.
4. Create a `.env` file in the root directory and add:
   ```env
   FIREBASE_API_KEY=<your_api_key>
   FIREBASE_AUTH_DOMAIN=<your_auth_domain>
   FIREBASE_PROJECT_ID=<your_project_id>
   FIREBASE_STORAGE_BUCKET=<your_storage_bucket>
   FIREBASE_MESSAGING_SENDER_ID=<your_messaging_sender_id>
   FIREBASE_APP_ID=<your_app_id>
   ```
5. In the project, create a `firebase.js` file and initialize Firebase:
   ```javascript
   import { initializeApp } from "firebase/app";
   import { getAuth } from "firebase/auth";
   import { getFirestore } from "firebase/firestore";
   import { getStorage } from "firebase/storage";
   import Constants from 'expo-constants';
   
   const firebaseConfig = {
       apiKey: Constants.manifest.extra.FIREBASE_API_KEY,
       authDomain: Constants.manifest.extra.FIREBASE_AUTH_DOMAIN,
       projectId: Constants.manifest.extra.FIREBASE_PROJECT_ID,
       storageBucket: Constants.manifest.extra.FIREBASE_STORAGE_BUCKET,
       messagingSenderId: Constants.manifest.extra.FIREBASE_MESSAGING_SENDER_ID,
       appId: Constants.manifest.extra.FIREBASE_APP_ID,
   };
   
   const app = initializeApp(firebaseConfig);
   export const auth = getAuth(app);
   export const db = getFirestore(app);
   export const storage = getStorage(app);
   ```

### Running the App
1. Start the development server:
   ```bash
   npm start
   ```
   or
   ```bash
   yarn start
   ```
2. Use an emulator or physical device to test the app.

## App Structure
```
/src
  ├── components  # Reusable UI components
  ├── screens     # App pages (Login, Register, Listing, Details)
  ├── navigation  # React Navigation setup
  ├── services    # Firebase and API handling
  ├── assets      # Images and other assets
  ├── App.js      # Main entry point
  └── firebase.js # Firebase setup
```

## Features Implemented
### Firebase Authentication
- Email/password-based login & registration
- Error handling for invalid credentials
- Session persistence using AsyncStorage

### API Integration
- Fetch paginated posts from JSONPlaceholder API
- Display title, image, and description
- Implement infinite scrolling
- Detailed view of each post with image, title, and full content

### Navigation
- Stack navigation for screens
- Smooth transitions between pages

### Additional Standout Features
- **Persistent Login:** Users stay logged in after closing the app
- **Multilingual Support:** Language selection using react-intl
- **Pull to Refresh:** Refresh listing page with swipe down

---
This README provides a comprehensive guide to setting up and running the application. 🚀

