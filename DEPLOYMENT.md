# Deployment Guide (Localhost + Render)

## Local development

### Backend

1. Go to backend folder.
2. Install packages: npm install
3. Ensure backend/.env has values for PORT, MONGO_URI, JWT_SECRET, CORS_ORIGIN
4. Run: npm start

Backend runs at http://localhost:5000

### Frontend

1. Go to frontend folder.
2. Install packages: npm install
3. Ensure frontend/.env has VITE_API_BASE_URL=http://localhost:5000/api
4. Run: npm run dev

Frontend runs at http://localhost:5173

## Deploy to Render from GitHub

### 1) Deploy backend as Web Service

- Root Directory: backend
- Build Command: npm install
- Start Command: npm start
- Add environment variables:
	- PORT=10000
	- MONGO_URI=<your_mongodb_connection_string>
	- JWT_SECRET=<strong_secret>
	- CORS_ORIGIN=https://<your-frontend-service>.onrender.com

After deploy, copy backend URL, for example:
https://your-backend.onrender.com

### 2) Deploy frontend as Static Site

- Root Directory: frontend
- Build Command: npm install ; npm run build
- Publish Directory: dist
- Environment variable:
	- VITE_API_BASE_URL=https://your-backend.onrender.com/api

## Notes

- CORS_ORIGIN supports comma-separated values. Example:
	CORS_ORIGIN=http://localhost:5173,https://your-frontend.onrender.com
- Do not commit backend/.env or frontend/.env.
