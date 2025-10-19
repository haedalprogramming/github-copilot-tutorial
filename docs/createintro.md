# Create a Personal Introduction Page Using GitHub Copilot CLI

This guide will walk you through the process of creating a personal introduction page using GitHub Copilot CLI. By following these steps, you will be able to leverage the power of GitHub Copilot to generate the necessary HTML and CSS for your page.

## Step 1: Set Up Your Environment

Before you begin, ensure you have the following prerequisites:

- A GitHub account
- Git and Node.js installed on your machine
- GitHub CLI installed

## Step 2: Create a New Repository

1. Open your terminal and create a new directory for your project:

   ```bash
   mkdir intro && cd intro
   ```

2. Create a new GitHub repository:

   ```bash
   gh repo create intro --public --source=. --remote=origin --push
   ```

3. Initialize a new Git repository:

   ```bash
   git init -b main
   ```

## Step 3: Generate Your Introduction Page

Use GitHub Copilot CLI to generate the HTML and CSS for your personal introduction page. You can do this by providing a natural language prompt.

### Example Prompt

Run the following command to generate a simple introduction page:

```bash
gh copilot suggest -t code "A simple, responsive personal intro page (Korean), with a hero section (name, role), about, skills badges, contact links (email, GitHub). Use semantic HTML5 and a minimal CSS in one file."
```

### Save the Output

Once you receive the generated code, save it to a file named `index.html` in your project directory.

## Step 4: Customize Your Page

Edit the `index.html` file to personalize the content. Update the following sections:

- Your name
- Your role
- A brief introduction about yourself
- Your skills
- Contact information

## Step 5: Add Assets

Include any images you want to use, such as an avatar or Open Graph image, in the `assets` directory. You can use the following commands to download images:

```bash
gh copilot suggest -t shell "download a CC0 avatar image to ./assets/avatar.jpg"
```

## Step 6: Set Up GitHub Actions for Deployment

To automatically deploy your introduction page to GitHub Pages, set up GitHub Actions:

1. Create a workflow file at `.github/workflows/pages.yml` with the following content:

   ```yaml
   name: Deploy to GitHub Pages

   on:
     push:
       branches: [ "main" ]
     workflow_dispatch:

   permissions:
     contents: read
     pages: write
     id-token: write

   concurrency:
     group: "pages"
     cancel-in-progress: true

   jobs:
     deploy:
       runs-on: ubuntu-latest
       steps:
         - name: Checkout
           uses: actions/checkout@v4

         - name: Upload artifact
           uses: actions/upload-pages-artifact@v3
           with:
             path: '.'

         - name: Deploy to GitHub Pages
           uses: actions/deploy-pages@v4
   ```

## Step 7: Commit and Push Your Changes

After making all the necessary changes, commit your work and push it to GitHub:

```bash
git add .
git commit -m "feat: my intro page"
git push -u origin main
```

## Step 8: Access Your Page

Once the GitHub Actions workflow completes successfully, your introduction page will be available at:

```
https://<username>.github.io/intro/
```

## Conclusion

Congratulations! You have successfully created a personal introduction page using GitHub Copilot CLI. Feel free to explore additional features and customize your page further.