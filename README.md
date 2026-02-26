# Parcel + Bootstrap Azure App

Simple static web application built with:

- Parcel v2 (bundler)
- Vanilla JavaScript (ES modules)
- Bootstrap 5
- Azure Static Web Apps (deployment target)

---

## Prerequisites

- Node.js 18+ recommended
- npm
- (Optional) Azure CLI
- (Optional) Azure Static Web Apps CLI

---

## Install Dependencies

```
npm install
```

---

## Local Development

Start the Parcel dev server with hot module reloading:

```
npm run start
```

This runs:

```
parcel --no-cache
```

The app will be available at the local URL printed in the terminal.

---

## Production Build

Create an optimized production build:

```
npm run build
```

Output is generated in:

```
dist/
```

Do not edit files inside `dist/` manually.

---

## Run Locally with Azure SWA CLI (Optional)

To simulate Azure Static Web Apps locally:

```
npx swa start dist
```

This serves the built output as Azure would.

---

## Deploy to Azure Static Web Apps

There are two recommended approaches.

### Option 1: Deploy via Azure Portal (Recommended)

1. Push this repository to GitHub.
2. In Azure Portal, create a **Static Web App** resource.
3. Connect your GitHub repository.
4. Configure build settings:

   - App location: `/`
   - Output location: `dist`
   - Build command: `npm run build`

Azure will:
- Install dependencies
- Run the build
- Deploy the `dist/` folder

Subsequent pushes to the selected branch trigger automatic deployments.

---

### Option 2: Deploy via Azure CLI

Install Azure Static Web Apps CLI (if not already installed):

```
npm install -g @azure/static-web-apps-cli
```

Login to Azure:

```
az login
```

Build the project:

```
npm run build
```

Deploy:

```
swa deploy dist --env production
```

You may need a deployment token from the Azure Portal.

---

## Project Structure

```
src/
  index.html   # Entry point
  index.js     # Application JS
  style.css    # Custom styles

dist/          # Production build output
```

---

## Notes

- No test framework is currently configured.
- No linter is configured.
- Uses modern ES syntax and Bootstrap utilities.
- Keep changes inside `src/`; `dist/` is generated.

---

## Recommended Workflow

1. Develop using `npm run start`
2. Build using `npm run build`
3. Commit changes
4. Push to GitHub
5. Let Azure automatically deploy

---

This project is optimized for simple static deployments to Azure Static Web Apps.
