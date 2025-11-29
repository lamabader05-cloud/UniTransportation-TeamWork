# Test Plan – UniTransportation App

## 1. Objective
To verify the functional and UI performance of the app built using FlutterFlow and Firebase.

## 2. Testing Scope
- Authentication Flow
- Ride Search & Filter
- Ride Details Screen
- Seat Selection
- Booking Confirmation
- Driver Create Ride Form
- Navigation & UI Responsiveness

## 3. Functional Test Cases
### TC01 – User Login
**Input:** valid email + valid password  
**Expected:** Redirect to Home page.

### TC02 – Ride Search
**Input:** "Imam University" → "Al Malaz"  
**Expected:** List of rides displayed.

### TC03 – Booking Ride
**Input:** Select ride + seat = 1  
**Expected:** Booking saved in Firestore.

## 4. UI/UX Testing
- Check layout on iPhone/Android
- Button tap responses
- Colors + typography consistency
- Error messages visibility
