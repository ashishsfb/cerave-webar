# Deployment Log

Project: `cerave-webar`  
Repo: `https://github.com/ashishsfb/cerave-webar`  
Live URL: `https://cerave-webar.onrender.com`  
Date: `March 25, 2026`

## Dev To Live Log

### 1. Forked repo to my own GitHub

Action:
- Forked the original repo to my account
- Set my fork as `origin`
- Kept the original repo as `upstream`

Why:
- Deployment should point to a repo I control

### 2. Renamed local project folder

Action:
- Changed the local folder name only

Why:
- Folder name does not affect git history or GitHub remotes

### 3. Created Render account and connected GitHub

Action:
- Signed into Render with GitHub
- Authorized access to my repo

Link:
- `https://dashboard.render.com/`

Why:
- Render needs GitHub access to pull and deploy code

### 4. Created a new Render Web Service

Action:
- Selected repo `ashishsfb/cerave-webar`
- Branch: `master`
- Language: `Node`

Why:
- This creates the live server for the app

### 5. Used these Render settings

Action:
- Root Directory: blank
- Build Command: `npm install --production=false`
- Start Command: `npm start`
- Instance Type: `Free`

Why:
- `--production=false` was needed because the TypeScript build uses `devDependencies`

### 6. Added Render environment variables

Action:
- `MONGO_URL=<atlas connection string>`
- `NODE_ENV=production`

Why:
- `MONGO_URL` connects the app to MongoDB Atlas
- `NODE_ENV=production` makes the app use production server mode

### 7. Got MongoDB Atlas connection string

Action:
- Atlas -> Cluster -> `Connect` -> `Drivers`
- Selected `Node.js`
- Copied the connection string
- Inserted database username and password
- Used database name `cerave`

Format:

```text
mongodb+srv://USERNAME:PASSWORD@cluster0.weuhjrn.mongodb.net/cerave?retryWrites=true&w=majority&appName=Cluster0
```

Links:
- `https://cloud.mongodb.com/`
- `https://www.mongodb.com/docs/atlas/`

### 8. Allowed database access from hosting

Action:
- Atlas `Network Access`
- Allowed external access for deployment

Why:
- Render must be allowed to reach MongoDB

### 9. First deploy failed

Error:
- TypeScript build could not find `@types/express`

Why:
- Render was installing only production dependencies during build

Fix:
- Changed Render Build Command from:

```bash
npm install
```

- To:

```bash
npm install --production=false
```

### 10. Redeployed

Action:
- Redeployed in Render
- Checked logs

### 11. Verified production route

Tested:

```text
https://cerave-webar.onrender.com/product?lang=en&name=hydrating-cleanser&size=8oz
```

## Redo Checklist For Another Project

1. Push project to a GitHub repo you control
2. Create a Render Web Service
3. Connect the GitHub repo
4. Set branch, build command, and start command
5. Add environment variables
6. Get the MongoDB Atlas driver connection string
7. Allow Atlas network access
8. Deploy
9. Check logs
10. Test one real route

## Useful Links

- Render dashboard: `https://dashboard.render.com/`
- Render docs: `https://render.com/docs`
- MongoDB Atlas: `https://cloud.mongodb.com/`
- MongoDB Atlas docs: `https://www.mongodb.com/docs/atlas/`