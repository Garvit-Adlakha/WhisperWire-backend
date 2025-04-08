# WhisperWire Backend

A real-time messaging application backend built with Node.js, Express, MongoDB, and Socket.IO.

## Overview

WhisperWire is a modern chat application backend that provides real-time messaging functionality, user authentication, friend management, and group chat capabilities. It leverages Socket.IO for real-time communication and MongoDB for data persistence.

## Features

- **Real-time Messaging**: Instant message delivery using Socket.IO
- **User Management**:
  - Registration and authentication
  - Google OAuth integration
  - Profile management
  - Online status tracking
- **Friend System**:
  - Friend requests
  - Friend management
  - Notifications
- **Chat Functionality**:
  - Private messaging
  - Group chats with admin controls
  - Message read receipts
  - Typing indicators
- **Media Support**:
  - File/image uploads
  - Avatar customization
  - Group icons
- **Security**:
  - Password hashing with bcrypt
  - JWT authentication
  - Rate limiting
  - CORS protection

## Tech Stack

- **Runtime**: Node.js
- **Framework**: Express.js
- **Database**: MongoDB with Mongoose ODM
- **Real-time Communication**: Socket.IO
- **Authentication**: JWT, Google Auth Library
- **File Upload**: Multer, Cloudinary
- **Security**: Helmet, HPP, Express Rate Limit
- **Validation**: Express Validator

## API Endpoints

### Authentication

- `POST /api/v1/user/signup` - Register a new user
- `POST /api/v1/user/signin` - Log in a user
- `POST /api/v1/user/google-auth` - Authenticate with Google
- `POST /api/v1/user/signout` - Sign out a user

### User Management

- `GET /api/v1/user/profile` - Get current user profile
- `GET /api/v1/user/profile/:id` - Get specific user profile
- `PUT /api/v1/user/update` - Update user profile
- `GET /api/v1/user/search` - Search for users

### Friend Management

- `PUT /api/v1/user/sendrequest` - Send friend request
- `PUT /api/v1/user/acceptrequest` - Accept friend request
- `GET /api/v1/user/notifications` - Get all notifications
- `GET /api/v1/user/getfriends` - Get user's friends
- `DELETE /api/v1/user/removefriend/:friendId` - Remove a friend

### Chat Management

- `POST /api/v1/chat/new` - Create new group chat
- `GET /api/v1/chat/getChat` - Get all user chats
- `GET /api/v1/chat/getGroup` - Get all user groups
- `GET /api/v1/chat/:id` - Get chat details
- `PUT /api/v1/chat/:id` - Rename a group
- `DELETE /api/v1/chat/:id` - Delete a chat

### Group Management

- `PUT /api/v1/chat/addMembers` - Add members to group
- `PUT /api/v1/chat/removeMembers` - Remove members from group
- `DELETE /api/v1/chat/leave/:id` - Leave a group

### Messaging

- `POST /api/v1/chat/message` - Send message with attachments
- `POST /api/v1/chat/direct-message` - Send direct message
- `GET /api/v1/chat/message/:id` - Get chat messages

### File Upload

- `POST /api/v1/upload` - Upload files

## Socket.IO Events

- `NEW_MESSAGE` - When a new message is sent
- `NEW_MESSAGE_ALERT` - Alert for new message
- `TYPING` - When a user is typing
- `STOP_TYPING` - When a user stops typing
- `USER_STATUS_CHANGE` - When user status changes
- `GET_ONLINE_USERS` - Get online users
- `REFETCH_CHATS` - Trigger client to refresh chats
- `ALERT` - General alert events

## Data Models

### User Model
- Basic information: name, username, email, password (hashed)
- Profile data: avatar, bio
- Status tracking: online status, last active time
- Authentication: Google OAuth support
- Relationships: friends list, pending friend requests
- Timestamps: creation and update dates

### Chat Model
- Chat type: one-to-one or group chats
- Group metadata: name, icon (for group chats)
- Participants: members list, creator, admins (for groups)
- Message tracking: reference to latest message
- Timestamps: creation and update dates

### Message Model
- Contextual data: chat reference, sender information
- Content: text message and file attachments
- Status tracking: read receipts
- Timestamps: creation and update dates

### Request Model
- Participants: sender and recipient
- Classification: request type (friend, group invite)
- Status tracking: pending, accepted, rejected
- Timestamps: creation and update dates

## Installation and Setup

1. Clone the repository
   ```
   git clone https://github.com/yourusername/whisperWire-backend.git
   cd whisperWire-backend
   ```

2. Install dependencies
   ```
   npm install
   ```

3. Create a `.env` file in the root directory with the following variables:
   ```
   NODE_ENV=development
   PORT=5000
   MONGODB_URI=your_mongodb_connection_string
   JWT_SECRET=your_jwt_secret
   JWT_EXPIRE=7d
   BCRYPT_SALT_ROUNDS=10
   GOOGLE_CLIENT_ID=your_google_client_id
   CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name
   CLOUDINARY_API_KEY=your_cloudinary_api_key
   CLOUDINARY_API_SECRET=your_cloudinary_api_secret
   ```

4. Start the development server
   ```
   npm run dev
   ```

5. For production
   ```
   npm start
   ```

## Development

- Run with Nodemon for development: `npm run dev`
- The server will restart automatically when code changes are detected

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

Garvit Adlakha