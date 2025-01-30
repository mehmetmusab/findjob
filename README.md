# Job Search Web Application

A comprehensive job search platform built with Laravel, featuring location-based job listings, multilingual support, and Google authentication.

## 🚀 Features

- Location-based job search with autocomplete
- Multilingual support (EN/TR)
- Advanced filtering system
- Google Authentication
- Responsive design
- User profile management with photo upload

## 🏗 Technical Architecture

### Framework & Technologies
- Laravel (MVC Architecture)
- MySQL Database
- JavaScript for autocomplete and location detection
- Google OAuth for authentication

### Design Patterns & Architecture
- MVC (Model-View-Controller) pattern
- Repository pattern for data access
- Service layer for business logic
- Factory pattern for object creation
- Observer pattern for event handling

## 💾 Data Model

### Core Entities:

#### Users
```sql
users
- id (PK)
- email
- password (hashed)
- name
- photo_url
- country_id (FK)
- city_id (FK)
- google_id
- created_at
- updated_at
```

#### Jobs
```sql
jobs
- id (PK)
- title
- description
- company_id (FK)
- location_id (FK)
- working_preference
- status
- applications_count
- created_at
- updated_at
```

#### Locations
```sql
locations
- id (PK)
- country
- city
- town
```

#### Applications
```sql
applications
- id (PK)
- user_id (FK)
- job_id (FK)
- status
- created_at
```

## 🔍 Key Implementation Details

### Location Detection
- Browser's Geolocation API for user location
- Fallback to IP-based location detection
- Location data stored in user session

### Search & Autocomplete
- Implemented using Laravel Scout
- Real-time city and position suggestions
- Elasticsearch for efficient searching

### Authentication
- Laravel Sanctum for API authentication
- Google OAuth integration
- Custom middleware for route protection

### Multilingual Support
- Laravel's localization feature
- Language files for EN and TR
- Session-based language switching

## 🚧 Challenges & Solutions

### Challenge 1: Location-based Search Performance
- **Problem**: Slow performance with large dataset
- **Solution**: Implemented database indexing and caching
- **Result**: 80% improvement in search response time

### Challenge 2: Real-time Autocomplete
- **Problem**: High server load with many concurrent users
- **Solution**: Implemented debouncing and client-side caching
- **Result**: Reduced server requests by 60%

### Challenge 3: Google OAuth Integration
- **Problem**: Session management with OAuth
- **Solution**: Implemented stateless authentication
- **Result**: Seamless OAuth flow with proper error handling

## 🚀 Getting Started

### Prerequisites
- PHP >= 8.1
- MySQL >= 8.0
- Composer
- Node.js & NPM

### Installation
```bash
# Clone the repository
git clone [repository-url]

# Install PHP dependencies
composer install

# Install NPM packages
npm install

# Copy environment file
cp .env.example .env

# Generate application key
php artisan key:generate

# Run migrations
php artisan migrate

# Start the server
php artisan serve
```

## 🔐 Environment Variables
```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=jobsearch
DB_USERNAME=root
DB_PASSWORD=

GOOGLE_CLIENT_ID=your-client-id
GOOGLE_CLIENT_SECRET=your-client-secret
GOOGLE_REDIRECT_URI=your-redirect-uri
```

## 📝 Testing
```bash
# Run unit tests
php artisan test

# Run specific test suite
php artisan test --testsuite=Feature
```

## 🔄 Future Improvements

1. Implement job recommendation system using AI
2. Add email notifications for job applications
3. Integrate more OAuth providers
4. Add advanced analytics dashboard
5. Implement real-time chat with employers

## 📜 License

This project is licensed under the MIT License - see the LICENSE.md file for details
