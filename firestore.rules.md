rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{document} {
      allow create: if true;
      allow read: if true;
      allow write: if true;
      allow delete: if request.auth.uid == document;
    }

    match /rides/{document} {
      allow create: if true;
      allow read: if true;
      allow write: if true;
      allow delete: if false;
    }

    match /RoutePrice/{document} {
      allow create: if true;
      allow read: if true;
      allow write: if true;
      allow delete: if false;
    }

    match /notifications/{document} {
      allow create: if true;
      allow read: if true;
      allow write: if true;
      allow delete: if false;
    }

    match /tripe/{document} {
      allow create: if true;
      allow read: if true;
      allow write: if true;
      allow delete: if false;
    }

    match /driver/{document} {
      allow create: if true;
      allow read: if true;
      allow write: if true;
      allow delete: if false;
    }
  }
}
