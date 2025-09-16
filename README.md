# Travel Log Genius

A travel data collection software application designed to capture trip-related information from users to support transportation planning and research by NATPAC (National Transportation Planning and Research Centre).

## Problem Statement

Manual surveys for transportation data collection are time-consuming and cover only a small percentage of the population, leading to inaccurate planning. This project creates a mobile-friendly app to digitally capture trip details such as trip number, origin, destination, mode of transport, timing, and details of accompanying travelers. User consent is required before data collection. The data is anonymized and stored on a server/database accessible by NATPAC scientists.

## Features

- User authentication and secure signup/login using Supabase Auth
- Explicit user consent before data collection
- Records trip details:
  - Trip number (optional)
  - Origin (auto-detected via geolocation or user input)
  - Destination
  - Mode of transport (selectable)
  - Start and end time (auto-filled or manual)
  - Number and details of accompanying travelers (optional)
- Stores data in a Supabase Postgres database
- Analytics dashboard for researchers to view aggregated trip data
- Responsive and accessible UI built with React, Tailwind CSS, and shadcn/ui components
- Toast notifications for user feedback
- Progressive Web App (PWA) support for offline use and installation

## Tech Stack

- Frontend: React with TypeScript, Vite, Tailwind CSS, shadcn/ui, lucide-react (icons)
- Backend: Supabase (Auth, Postgres database, API)
- State Management: React hooks and context
- Routing: react-router-dom
- Hosting: Supports static hosting and PWA features
- Notifications: Custom toast system for UX

## Installation and Setup

1. Clone the repository:
git clone <repository-url>
cd <repository-folder>


2. Install dependencies:
npm install


3. Configure Supabase:
- Create a Supabase project at https://supabase.com/
- Set up the database tables `profiles` and `trips` as per schema
- Note your Supabase URL and Anon Key
- Update `src/lib/supabase.ts` with your Supabase credentials

4. Run the development server:
npm run dev

5. Open [http://localhost:8080](http://localhost:8080) to view the app.

## Database Schema

- **profiles**
- `id`: UUID (primary key, user id from Auth)
- `consent`: boolean (user consent status)
- `updated_at`: timestamp

- **trips**
- `id`: UUID (primary key)
- `user_id`: UUID (foreign key to profiles.id)
- `trip_number`: string (optional)
- `origin`: text (coordinates or location)
- `destination`: text
- `mode`: text (mode of transport)
- `start_time`: timestamp (optional)
- `end_time`: timestamp (optional)
- `companions`: jsonb or text (details of accompanying travelers)
- `created_at`: timestamp

## Usage

- Sign up or log in to the app
- Provide consent to allow data collection
- Record trip details on the trip form; origin can be auto-detected using device geolocation
- Save the trip data, which is stored securely and linked to the user
- Researchers can access aggregated data via the scientist dashboard for planning and analysis

## Contributing

Contributions are welcome! Please open issues or pull requests to improve features, fix bugs, or enhance documentation.

## License

This project is licensed under the MIT License.

## Contact

For questions or feedback, contact the development team at gurnaazgill01@gmail.com

---

*Developed as part of Smart India Hackathon 2025 - NATPAC Travel Data Collection project.*
