# React with vite

[toc]

## 1. create react-app

```shell
npm create vite@latest
```

## 2. Install npm  to the project directory

```
cd [DIR-NAME]
npm install
```

## 3. run development engine

```shell
npm run dev
```

## 4. proxy

- /vite.config.js

```javascript
export default defineConfig({
    server: {
    proxy: {
      	"/[url]": {
        target: "http://localhost:[portNumber]",
        secure: false,
      },
    },
  },
  plugins: [react()],
})
```

## 5. Package

### 1. React dom

```shell
npm install react-dom
```

### 2. React Icon

```shell
npm install react-icons
```

### 3. React Markdown

```shell
npm install react-markdown
```









