# Firebase Structure & Configuration

## 🔥 Authentication
- Email/Password
- Student ID validation
- User roles: Rider / Driver / Admin

## 🔥 Firestore Collections
### users
| Field | Type | Description |
|-------|--------|--------------|
| uid | String | Firebase Auth UID |
| role | String | rider/driver |
| name | String | Full name |
| phone | String | User phone number |

### rides
| Field | Type |
|-------|--------|
| driver_id | String |
| from | String |
| to | String |
| price | Number |
| seats | Number |
| date | Timestamp |

### bookings
| Field | Type |
|-------|--------|
| ride_id | String |
| user_id | String |
| status | String |

## 🔥 Firestore Rules
```firebase
allow read, write: if request.auth != null;
