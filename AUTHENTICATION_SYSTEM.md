# Great India Authentication System

## Overview
This project now includes a comprehensive authentication system that ensures only registered users can access the platform. Users have the option to sign up, sign in, or continue as guests with limited access.

## Features

### 🔐 User Authentication
- **Sign Up**: New users can create accounts with username, email, and password
- **Sign In**: Existing users can log in with email and password
- **Guest Access**: Users can explore the platform without signing up (limited features)
- **JWT Token Authentication**: Secure token-based authentication system
- **Automatic Session Management**: Tokens are stored and managed automatically

### 🎨 User Interface
- **Modern Design**: Beautiful authentication page with Indian heritage color scheme
- **Responsive Design**: Works on all devices
- **Tab-based Interface**: Easy switching between Sign In and Sign Up
- **User Menu**: Authenticated users see their name and dropdown menu
- **Guest Prompt**: Non-authenticated users see sign-in prompt in navigation

### 🛡️ Security Features
- **Password Hashing**: Secure bcrypt password hashing
- **JWT Tokens**: Secure JSON Web Tokens for session management
- **Protected Routes**: Automatic redirection for unauthenticated users
- **Input Validation**: Client and server-side validation

## How It Works

### 1. First Visit
When users first visit any page of the Great India platform:
- If not authenticated and not in guest mode → Redirect to `/auth.html`
- Authentication page shows Sign In/Sign Up options
- Users can choose to register, sign in, or continue as guest

### 2. After Authentication
Once authenticated:
- JWT token is stored in browser localStorage
- User information is stored for display
- Navigation updates to show user name and menu
- Full access to all platform features

### 3. Guest Mode
Guest users can:
- Browse the platform with limited features
- See a "Sign In / Sign Up" prompt in navigation
- Upgrade to full account anytime

## File Structure

### Frontend Files
```
frontend/
├── auth.html              # Authentication page (Sign In/Up)
├── js/
│   ├── auth.js            # Authentication logic
│   └── auth-helper.js     # Authentication helper for all pages
└── [other pages]          # All pages include auth-helper.js
```

### Backend Files
```
backend/
├── routes/
│   └── auth.js            # Authentication API routes
├── middleware/
│   └── auth.js            # JWT middleware for protected routes
└── server.js              # Main server with CORS and auth routes
```

## API Endpoints

### Authentication Routes
- `POST /api/auth/register` - Create new user account
- `POST /api/auth/login` - Sign in existing user
- `GET /api/auth/me` - Get current user info (protected)

### Request/Response Examples

**Register Request:**
```json
{
  "username": "john_doe",
  "email": "john@example.com",
  "password": "securepassword"
}
```

**Login Request:**
```json
{
  "email": "john@example.com",
  "password": "securepassword"
}
```

**Success Response:**
```json
{
  "message": "Login successful",
  "token": "jwt_token_here",
  "user": {
    "id": 1,
    "username": "john_doe",
    "email": "john@example.com"
  }
}
```

## Usage Instructions

### 1. Start the Backend Server
```bash
cd backend
npm start
```
Server runs on port 5001 by default.

### 2. Open the Frontend
Navigate to any page in the frontend directory:
- `index.html` - Will redirect to auth if not authenticated
- `auth.html` - Direct access to authentication page

### 3. Testing Authentication
1. **Sign Up**: Create a new account with username, email, password
2. **Sign In**: Use email and password to log in
3. **Guest Mode**: Click "Continue as Guest" for limited access
4. **Protected Access**: Try accessing other pages to see protection in action

## Technical Implementation

### Client-Side (JavaScript)
- **AuthManager Class**: Handles authentication requests
- **AuthHelper Module**: Provides authentication utilities to all pages
- **Automatic Redirects**: Users redirected based on auth status
- **UI Updates**: Navigation updates dynamically based on user state

### Server-Side (Node.js/Express)
- **JWT Authentication**: Secure token-based authentication
- **Password Hashing**: bcrypt for secure password storage
- **CORS Configuration**: Proper cross-origin request handling
- **Error Handling**: Comprehensive error responses

### Security Considerations
- Passwords are hashed using bcrypt with salt
- JWT tokens include expiration (1 hour default)
- Tokens are validated on protected routes
- Input validation on both client and server
- CORS properly configured for security

## Customization

### Styling
The authentication page uses CSS custom properties for easy theme customization:
```css
:root {
  --heritage-gold: #D4AF37;
  --heritage-deep-red: #8B0000;
  --heritage-orange: #FF6B35;
  /* ... other heritage colors */
}
```

### Authentication Flow
Modify `auth-helper.js` to customize:
- Redirect behavior
- UI updates for different user states
- Additional authentication checks

### API Integration
Extend `auth.js` routes for:
- Password reset functionality
- Email verification
- Social media authentication
- Role-based access control

## Troubleshooting

### Common Issues
1. **CORS Errors**: Ensure backend server is running and CORS is configured
2. **Token Expiration**: Tokens expire after 1 hour, user will need to re-authenticate
3. **Port Conflicts**: Backend runs on port 5001, ensure it's available
4. **LocalStorage**: Clear browser localStorage if experiencing auth issues

### Development Tips
- Use browser DevTools to inspect network requests
- Check console for authentication errors
- Verify JWT tokens at jwt.io for debugging
- Use browser Application tab to view localStorage

## Future Enhancements

Potential improvements:
- Password reset via email
- Email verification for new accounts
- Remember me functionality
- Social media login integration
- User profile management
- Role-based permissions
- Password strength validation
- Two-factor authentication

## Security Notes

- Never store sensitive data in localStorage in production
- Implement HTTPS in production
- Consider refresh token rotation
- Add rate limiting for auth endpoints
- Implement account lockout for failed attempts
- Regular security audits recommended
