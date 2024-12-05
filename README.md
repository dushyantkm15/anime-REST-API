# anime-REST-API
# Anime Recommendation Backend

## Overview
This is a FastAPI-based backend application for an anime recommendation system, providing user authentication, anime search, and personalized recommendations.

## Features
- User Registration and Authentication
- Anime Search
- Personalized Anime Recommendations
- User Genre Preferences

## Prerequisites
- Python 3.8+
- FastAPI
- SQLModel
- PostgreSQL
- Uvicorn

## Installation

### 1. Clone the Repository
```bash
git clone <your-repository-url>
cd <project-directory>
```

### 2. Create a Virtual Environment
```bash
python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`
```

### 3. Install Dependencies
```bash
pip install fastapi sqlmodel psycopg2-binary uvicorn
```

## Configuration

### Database
- PostgreSQL connection details are configured in `db/config.py`
- Connection string format: 
  ```
  postgresql+psycopg://username:password@host:port/database?sslmode=require
  ```

### Environment Variables
Recommended to use environment variables for sensitive information like database credentials.

## Endpoints

### Authentication Routes (`/auth`)
- **POST** `/register`
  - Registers a new user
  - Request Body: `Register` schema
  - Returns: User registration response

- **POST** `/login`
  - Authenticates user and provides token
  - Request Body: `Register` schema
  - Returns: Authentication token

### Anime Routes (`/anime`)
- **POST** `/search`
  - Search for anime
  - Request Body: `SearchRequest` schema
  - Returns: Anime search results

- **POST** `/recommendations`
  - Get personalized anime recommendations
  - Requires Authentication
  - Returns: List of recommended anime

### User Preference Routes (`/user`)
- **POST** `/preferences`
  - Set user's anime genre preferences
  - Requires Authentication
  - Request Body: `Genres` schema
  - Returns: Preference setting response

## Project Structure
```
.
├── main.py             # Main FastAPI application entry point
├── db/
│   └── config.py       # Database configuration
├── routes/
│   ├── user.py         # User authentication routes
│   ├── anime.py        # Anime-related routes
│   └── pref.py         # User preference routes
├── controllers/
│   ├── user.py         # User authentication logic
│   ├── anime.py        # Anime search and recommendation logic
│   └── pref.py         # User preference management
├── schemas/
│   ├── register.py     # User registration schema
│   ├── query.py        # Search request schema
│   └── pref.py         # User preferences schema
└── utils/
    └── auth.py         # Authentication utilities
```

## Authentication
- Uses token-based authentication
- `auth_wrapper` in `utils/auth.py` handles authentication for protected routes

## Error Handling
- Custom error handling for routes
- Standardized error responses with appropriate HTTP status codes

## Database
- Uses SQLModel for ORM
- PostgreSQL as the database
- Automatic table creation on server start

## Running the Application

### Development Mode
```bash
python main.py
```

### Using Uvicorn
```bash
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

## Deployment Considerations
- Use environment variables for sensitive configurations
- Configure SSL for production
- Consider using a production-grade WSGI server

## Technologies
- FastAPI
- SQLModel
- PostgreSQL
- Uvicorn
- GraphQL (AniList)

## Contributing
1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a new Pull Request


