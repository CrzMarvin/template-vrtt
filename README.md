# React + TypeScript + Vite + Tailwindcss template

# origin info:
repo: https://github.com/vitejs/vite/tree/main/packages/create-vite/template-react-ts
This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

# 目前流程,(就是从无到有的过程)
1. create repo:
`yarn create vite react-three  --template react-ts`
copy .prettierrc

2. add tailwindcss:
`yarn add -D tailwindcss postcss autoprefixer`
add file: `tailwind.config.js`:
/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}

add file: `postcss.config.cjs`
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
};

add code to `index.css`:
@tailwind base;
@tailwind components;
@tailwind utilities;

3. change some eslint:
`yarn add -D eslint-plugin-react`
change `eslintrc.cjs` to following:
module.exports = {
  root: true,
  env: { browser: true, es2020: true },
  extends: [
    'eslint:recommended',
    // 'plugin:@typescript-eslint/recommended',
    'plugin:@typescript-eslint/recommended-type-checked',
    // 'plugin:@typescript-eslint/strict-type-checked', optional
    'plugin:react-hooks/recommended',
    'plugin:react/recommended',
    'plugin:react/jsx-runtime',
  ],
  parserOptions: {
    ecmaVersion: 'latest',
    sourceType: 'module',
    project: ['./tsconfig.json', './tsconfig.node.json'],
    tsconfigRootDir: __dirname,
  },
  ignorePatterns: ['dist', '.eslintrc.cjs', 'postcss.config.js', 'tailwind.config.js'],
  parser: '@typescript-eslint/parser',
  plugins: ['react-refresh'],
  rules: {
    'react-refresh/only-export-components': [
      'warn',
      { allowConstantExport: true },
    ],
    'no-unused-vars': 'off',
    'no-console': 'warn',
    '@typescript-eslint/no-unused-vars': 'off',
  },
}

done

# TODO: 
- [ ] add alias
- [ ] add .env
