# Deployment

Production frontend: https://roam-local.vercel.app
Vercel project: roam-local (prj_PnXI2A0FlHk9mYl54WOKgFeilBAs), direct source deployment; Git auto-deploy is not connected.
Backend: Render MyPoke workspace, roam-local-api (srv-dc1l7jetlv9c73cdfgi0), free plan in Singapore.
Build: npm install --omit=dev
Start: npm start
MongoDB is configured through the backend's MONGODB_URI environment variable. Contact messages and favorites persist in MongoDB. Backend deploys automatically from GitHub main. Vercel routes /api to the backend. The free backend can sleep when idle.
