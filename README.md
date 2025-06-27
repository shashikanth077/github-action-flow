🚀 GitHub Actions CI/CD for React App
This project uses GitHub Actions for Continuous Integration and Deployment (CI/CD).
On every push to the main branch, it:

Installs dependencies

Runs unit tests

Builds the React app

Deploys the build to GitHub Pages

📁 Workflow File
The GitHub Actions workflow is defined in:
.github/workflows/deploy.yml

📄 Sample Workflow

name: React CI/CD
on:
  push:
    branches:
      - main
jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - uses: actions/setup-node@v3
        with:
          node-version: 18

      - run: npm install
      - run: npm test -- --watchAll=false
      - run: npm run build

      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v4
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./build
          
🌐 GitHub Pages Deployment
To deploy successfully:

Add homepage in package.json:
"homepage": "https://<your-username>.github.io/<repo-name>"

Enable Pages:

Go to Settings > Pages

Select branch: gh-pages

Select folder: / (root)

Enable GitHub Actions write access:

Go to Settings > Actions > General

Under Workflow permissions, choose: Read and write permissions

✅ Result
After pushing to main, your app will be built and automatically deployed to:
https://<your-username>.github.io/<repo-name>
