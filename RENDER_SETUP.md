# LifeLink Backend - Render setup

## Why the previous deployment failed
`better-sqlite3` is a native Node module. The old deployment contained a binary built for
Node ABI 137 (Node 24), while Render was running Node 22 (ABI 127).

This package now:
- pins the deployment to Node 22.x via `package.json` and `.node-version`
- forces `better-sqlite3` to build from source via `.npmrc`
- rebuilds `better-sqlite3` during `npm install` via `postinstall`

## Render settings
Build Command:
```bash
npm install
```

Start Command:
```bash
npm start
```

If Render has an old cached `node_modules`, use **Manual Deploy -> Clear build cache & deploy**
(or the equivalent clear-cache option in Render) once.

## JWT_SECRET
Set `JWT_SECRET` in Render Environment Variables. Do not commit the secret to GitHub.

Example:
`JWT_SECRET=<long-random-secret>`
