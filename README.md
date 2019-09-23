# React + Redux + Firebase

This project was created with 
* [React App](https://github.com/facebook/create-react-app)
* [Redux](https://redux.js.org/)
* [Google Firebase](https://firebase.google.com)
  * Authentication
  * Firestore (Database)
  * Functions
  * Hosting

## Configurations
1. Set Firebase App config in file ```./src/configs/fbConfig.js```
2. Set Google Project Id in file ```./.firebaserc```
3. Set Firestore Rules like bellow:
```
rules_version = '2';
service cloud.firestore {
	match /databases/{database}/documents {
  	// match documents in the notifications collections
  	match /notifications/{notificationId} {
      allow read: if request.auth.uid != null;
    }
  
  	// match documents in the projects collections
  	match /projects/{projectId} {
      allow read, write: if request.auth.uid != null;
    }
  
  	// match logged in user doc in user collections
    match /users/{userId} {
      allow create: if true;
      allow read: if request.auth.uid != null;
      allow write: if request.auth.uid == userId
    }
  }
}
```

### Dependencies
```npm install```

### Run
```npm start```

### Build
```npm run build```

### Firebase Deploy
```firebase deploy```