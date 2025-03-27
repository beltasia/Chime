# Chime - Real-Time Chat Application

![Chime Logo](https://via.placeholder.com/150x50?text=Chime+Logo)

Chime is a real-time chat application built with React and Firebase that allows users to send and receive messages instantly.

## Features

- 🔐 **Google Authentication** - Secure sign-in with Firebase Auth
- 💬 **Real-time Messaging** - Instant message delivery using Firestore
- 📱 **Responsive Design** - Works on desktop and mobile devices
- 🎨 **Customizable UI** - Built with Chakra UI for easy theming
- 🔄 **Online Status** - See who's online in real-time

## Tech Stack

- **Frontend**: React.js
- **Backend**: Firebase
  - Authentication
  - Firestore Database
  - (Optional) Storage for file uploads
- **UI Library**: Chakra UI
- **Icons**: React Icons

## Getting Started

### Prerequisites

- Node.js (v14+)
- Firebase account
- Google Cloud project

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/chime-chat.git
   cd chime-chat
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Set up Firebase:
   - Create a new project in the [Firebase Console](https://console.firebase.google.com/)
   - Enable Authentication (Google sign-in)
   - Enable Firestore Database
   - (Optional) Enable Storage for file uploads

4. Create `.env` file in the root directory:
   ```env
   REACT_APP_FIREBASE_API_KEY=your_api_key
   REACT_APP_AUTH_DOMAIN=your-project.firebaseapp.com
   REACT_APP_PROJECT_ID=your-project-id
   REACT_APP_STORAGE_BUCKET=your-bucket.appspot.com
   REACT_APP_MESSAGING_SENDER_ID=your-sender-id
   REACT_APP_APP_ID=your-app-id
   ```

5. Run the development server:
   ```bash
   npm start
   ```

6. Open [http://localhost:3000](http://localhost:3000) in your browser.

## Firebase Security Rules

### Firestore Rules
```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /messages/{message} {
      allow read: if true;
      allow create: if request.auth != null;
    }
    match /users/{userId} {
      allow read: if true;
      allow write: if request.auth.uid == userId;
    }
  }
}
```

### Storage Rules (if using file uploads)
```javascript
rules_version = '2';
service firebase.storage {
  match /b/{bucket}/o {
    match /{allPaths=**} {
      allow read: if true;
      allow write: if request.auth != null;
    }
  }
}
```

## Project Structure
chime-app/
├── public/
│   ├── index.html
│   └── assets/          # Static files
│
├── src/
│   ├── components/
│   │   ├── Auth/        # Authentication components
│   │   │   ├── Login.jsx
│   │   │   ├── Signup.jsx
│   │   │   └── AuthProvider.jsx
│   │   ├── Chat/        # Chat components
│   │   │   ├── Message.jsx
│   │   │   ├── MessageList.jsx
│   │   │   ├── MessageInput.jsx
│   │   │   ├── ChannelList.jsx
│   │   │   └── UserList.jsx
│   │   └── UI/          # Reusable UI components
│   │       ├── Button.jsx
│   │       ├── Avatar.jsx
│   │       └── Loading.jsx
│   │
│   ├── context/         # React context providers
│   │   ├── AuthContext.jsx
│   │   └── ChatContext.jsx
│   │
│   ├── hooks/           # Custom hooks
│   │   ├── useAuth.js
│   │   └── useChat.js
│   │
│   ├── services/        # Firebase services
│   │   ├── auth.js
│   │   ├── firestore.js
│   │   └── storage.js   # If you need file uploads
│   │
│   ├── pages/           # Main pages
│   │   ├── Home.jsx
│   │   ├── ChatRoom.jsx
│   │   └── Profile.jsx
│   │
│   ├── utils/           # Utility functions
│   │   ├── helpers.js
│   │   └── validators.js
│   │
│   ├── App.jsx          # Main app component
│   ├── index.jsx        # App entry point
│   └── styles/          # CSS modules
│       ├── main.css
│       ├── auth.css
│       └── chat.css
│
├── .env                 # Environment variables
├── firebase.json        # Firebase config
└── firestore.rules      # Security rules

```

## Available Scripts

- `npm start` - Runs the app in development mode
- `npm test` - Launches the test runner
- `npm run build` - Builds the app for production
- `npm run eject` - Ejects from Create React App (advanced)

## Deployment

To deploy your app to Firebase Hosting:

1. Install Firebase CLI:
   ```bash
   npm install -g firebase-tools
   ```

2. Login to Firebase:
   ```bash
   firebase login
   ```

3. Initialize Firebase project:
   ```bash
   firebase init
   ```
   - Select Hosting
   - Choose your Firebase project
   - Set `build` as your public directory
   - Configure as a single-page app (yes)

4. Build and deploy:
   ```bash
   npm run build
   firebase deploy
   ```

Your app will be deployed to `https://your-project-id.web.app`

## Contributing

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

Distributed under the MIT License. See `LICENSE` for more information.

## Contact

Project Link: [https://github.com/yourusername/chime-chat](https://github.com/beltasia/chime-chat)

## Acknowledgments

- [Firebase Documentation](https://firebase.google.com/docs)
- [React Documentation](https://reactjs.org/docs/getting-started.html)
- [Chakra UI Documentation](https://chakra-ui.com/docs/getting-started)

