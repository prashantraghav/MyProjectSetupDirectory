# ✨ VS Code Setup to Format TypeScript and React on Save

This guide helps you configure **VS Code** to automatically format **TypeScript** (`.ts`, `.tsx`) and **React** (`.js`, `.jsx`) files using **Prettier** when saving a file.

---

## ✅ 1. Install Required Extensions

Install the following extensions in VS Code:

- [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- (Optional) [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) – for linting + auto-fixes

---

## ✅ 2. Configure VS Code Settings

Open `settings.json` via:

- `Ctrl + Shift + P` → **Preferences: Open Settings (JSON)**  
  or  
- File → Preferences → Settings → Top-right `{}` icon

Add the following:

```json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",

  "[typescript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[typescriptreact]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[javascriptreact]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  }
}
```

---

## ✅ 3. Add Prettier Configuration (Optional but Recommended)

Create a `.prettierrc` file in the root of your project:

```json
{
  "semi": true,
  "singleQuote": true,
  "trailingComma": "all",
  "printWidth": 100,
  "tabWidth": 2
}
```

Also create a `.prettierignore` file to exclude files/folders from formatting:

```
node_modules
build
dist
coverage
```

---

## ✅ 4. Install Prettier Locally (Optional for CI & Teams)

To ensure consistent formatting across all environments, install Prettier locally:

```bash
npm install --save-dev prettier
```

Then you can manually format all project files using:

```bash
npx prettier --write .
```

---

## ✅ 5. (Optional) Enable ESLint Auto Fixes on Save

If you are using ESLint in your project, enable auto-fixes on save by adding this to `settings.json`:

```json
{
  "editor.codeActionsOnSave": {
    "source.fixAll": true
  }
}
```

This will apply ESLint and Prettier fixes automatically when saving.

---

## ✅ Done!

Now whenever you save a `.ts`, `.tsx`, `.js`, or `.jsx` file, VS Code will auto-format the code using Prettier.

> 💡 **Pro Tip:** You can enforce formatting using Git hooks with tools like `husky` and `lint-staged` for team projects.