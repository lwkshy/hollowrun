# HollowRun commands

Run all commands from:

```powershell
cd C:\path\to\hollowrun
```

## Install dependencies

```powershell
npm ci
npm run setup
```

## Build the installer and portable executable

```powershell
npm run build
```

Output:

```text
dist-electron\HollowRun <version>.exe
dist-electron\HollowRun Setup <version>.exe
```

## Run the application from source

Build the frontend once, then start Electron:

```powershell
npm run build:frontend
npm start
```

## Verify changes

Run the automated JavaScript tests and frontend lint checks:

```powershell
npm test
npm run lint
```

Compile both native projects without publishing release artifacts:

```powershell
dotnet build HollowRun.Worker\HollowRun.Worker.csproj -c Release
dotnet build HollowRun.Splash\HollowRun.Splash.csproj -c Release
```

## Bump the version

Use one of the synchronized version commands. Each updates the root, backend,
frontend, lockfiles, worker, and splash project versions:

```powershell
npm run version:patch
npm run version:minor
npm run version:major
```

## Optional Sentry source maps

Local builds do not upload source maps by default. For a release build, copy
`frontend\.env.example` to `frontend\.env.local`, set the Sentry organization,
project, and token, then set `SENTRY_UPLOAD_SOURCEMAPS=true`. Never commit the
token or `.env.local` file.
