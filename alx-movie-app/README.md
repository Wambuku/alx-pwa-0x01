CineSeek
A modern movie discovery application built with Next.js, TypeScript, and Tailwind CSS.

API Overview
CineSeek uses the MoviesDatabase API to fetch a wide range of movies, including titles, posters, genres, and release years.
Key features of the API include:

Fetching popular, trending, or filtered movie titles.

Searching by title, year, or genre.

Retrieving detailed information for a single movie.

Pagination support for browsing results.

Well-documented endpoints for flexible integration.

Version
API Version: v1 (as per MoviesDatabase API documentation)

Available Endpoints
Endpoint	Description
/titles	Fetches a list of movies (supports filters)
/titles/search/title/{title}	Search for movies by title
/titles/{id}	Get details for a single movie by ID
/titles/utils/genres	List available movie genres

Request and Response Format
Typical Request (example POST to /titles):
json
Copy
Edit
{
  "year": 2023,
  "genre": "Comedy",
  "page": 1
}
Typical Response:
json
Copy
Edit
{
  "results": [
    {
      "id": "tt1234567",
      "titleText": { "text": "Example Movie" },
      "primaryImage": { "url": "https://example.com/poster.jpg" },
      "releaseYear": { "year": 2023 }
    }
  ]
}
Request: Parameters sent as JSON in POST body or as query parameters.

Response: List of movie objects, each with ID, title, poster image, and release year.

Authentication
All requests must include the following headers:

x-rapidapi-host: moviesdatabase.p.rapidapi.com

x-rapidapi-key: YOUR_API_KEY

Your API key is stored in a local .env.local file as MOVIE_API_KEY=YOUR_API_KEY
(Never commit this file to source control.)

Error Handling
Common error codes:

401 Unauthorized: Missing or invalid API key.

429 Too Many Requests: Rate limit exceeded.

404 Not Found: Invalid endpoint or resource.

500 Internal Server Error: Server-side problem.

Handling:

Use try/catch blocks in API routes.

Check response status codes before processing data.

Show user-friendly error messages for common issues (e.g., loading spinner, error alerts).

Usage Limits and Best Practices
Rate Limit: Most free plans allow up to 100 requests/day (check your RapidAPI dashboard).

Best Practices:

Paginate results using the page parameter.

Cache frequently-requested data on the client to reduce API calls.

Never expose your API key on the frontend; always proxy requests through a server-side route (e.g., Next.js API route).

Handle loading and error states gracefully in the UI.