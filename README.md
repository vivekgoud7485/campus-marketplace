# Campus Marketplace — Full Stack Java

A campus-focused peer-to-peer marketplace starter based on the supplied abstract. Students can browse, search, filter, and list used items. The project uses React + Vite, Java 17 + Spring Boot, Spring Data JPA, and MySQL.

## Features included
- Responsive product catalog with search and category filtering
- Create product listings (title, description, price, category, condition, seller/contact)
- REST API for listing, searching, adding, viewing, and deleting products
- MySQL persistence through Spring Data JPA
- Demo sample listings in the frontend if the API is not running

## Project structure
- `frontend/` — React UI
- `backend/` — Spring Boot REST API
- `database/schema.sql` — optional MySQL schema notes

## Run locally
### 1. Database
Create a MySQL database and user, for example:
```sql
CREATE DATABASE campus_marketplace;
CREATE USER 'campus_user'@'localhost' IDENTIFIED BY 'change_me';
GRANT ALL PRIVILEGES ON campus_marketplace.* TO 'campus_user'@'localhost';
```
Set environment variables before running backend:
- `DB_URL=jdbc:mysql://localhost:3306/campus_marketplace`
- `DB_USERNAME=campus_user`
- `DB_PASSWORD=change_me`

### 2. Backend
Requirements: Java 17+, Maven 3.9+, MySQL 8+.
```bash
cd backend
mvn spring-boot:run
```
API runs at `http://localhost:8080/api/products`.

### 3. Frontend
Requirements: Node.js 20+.
```bash
cd frontend
npm install
npm run dev
```
Open the Vite URL printed in the terminal. Optional `VITE_API_URL` can point to the backend API base, e.g. `http://localhost:8080/api`.

## API endpoints
- `GET /api/products` — list all products; optional `q` and `category` query parameters
- `GET /api/products/{id}` — product details
- `POST /api/products` — create listing (JSON body)
- `DELETE /api/products/{id}` — delete listing
- `GET /api/health` — health check

Example POST body:
```json
{
  "title": "Engineering Mathematics Textbook",
  "description": "Good condition, one semester used.",
  "price": 350,
  "category": "Books",
  "itemCondition": "Good",
  "sellerName": "A Student",
  "sellerContact": "student@example.edu",
  "imageUrl": ""
}
```

## GitHub links (create these repositories under your own account)
- Frontend: `https://github.com/YOUR_USERNAME/campus-marketplace-frontend`
- Backend: `https://github.com/YOUR_USERNAME/campus-marketplace-backend`

These are suggested URLs, not repositories created or verified by this package. To publish, create each repository on GitHub and push the corresponding folder contents.

## Deployment guide
- Frontend: deploy `frontend/` to Vercel or Netlify; set `VITE_API_URL` to the deployed backend API base (for example `https://YOUR-BACKEND-DOMAIN/api`).
- Backend: deploy `backend/` to Render, Railway, or another Java host; set `DB_URL`, `DB_USERNAME`, and `DB_PASSWORD` to a hosted MySQL database. The app reads `PORT` if supplied by the host.
- Database: use a managed MySQL provider and allow the backend host to connect.
- After deployment, use the actual deployed frontend URL as your final project link. No live deployment is created by this source bundle.

## Important production work
This is a working starter, not a production-secure marketplace. Before real use, add Spring Security authentication/authorization, password handling, ownership checks for edits/deletes, validation, image storage, moderation, pagination, and tests. Ratings/reviews, messaging, and transaction workflows are described in the abstract but are not implemented in this starter yet. Do not collect sensitive information or use real transactions until these protections are added.
