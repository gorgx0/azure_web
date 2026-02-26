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

```bash
npm install
```

---

## Local Development

Start the Parcel dev server with hot module reloading:

```bash
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

```bash
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

---

### Using a Deployment Token (Recommended for CLI Deployments)

In the Azure Portal:

1. Open your **Static Web App** resource.
2. Go to **Deployment token**.
3. Copy the token value.

Store the token as an environment variable instead of hardcoding it.

#### macOS / Linux

```
export SWA_DEPLOYMENT_TOKEN="your_deployment_token_here"
```

#### Windows (PowerShell)

```
$env:SWA_DEPLOYMENT_TOKEN="your_deployment_token_here"
```

You can now deploy using the npm script:

```
npm run deploy
```

The script uses:

```
swa deploy dist --env production --deployment-token `$SWA_DEPLOYMENT_TOKEN`
```

This keeps the token out of source control and prevents accidental leaks.

---

### Deploy to Preview Environment

Azure Static Web Apps also supports a **preview** environment.

After building the project:

```bash
npm run build
```

Deploy to preview:

```bash
npm run deploy:preview
```

This runs:

```
swa deploy dist --env preview --deployment-token $SWA_DEPLOYMENT_TOKEN
```

Use preview deployments for staging, testing, or validating changes before promoting to production.

---

Manual deploy (without npm script):

```
swa deploy dist --env production --deployment-token $SWA_DEPLOYMENT_TOKEN
```

Ensure the `SWA_DEPLOYMENT_TOKEN` environment variable is set before running the command.

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
