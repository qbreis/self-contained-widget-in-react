# Self-contained Widget in React

Bundling everything into a single JavaScript file without a separate CSS file can be a valid approach for Self-contained Widget in React.

I install `styled-components`:

```bash
npm install styled-components
```

Import and use styled-components to define the global styles in `src\index.js`:

```js
import React from 'react';
import ReactDOM from 'react-dom/client';
import { createGlobalStyle } from 'styled-components'; // npm install styled-components
import App from './App';
import reportWebVitals from './reportWebVitals';

const GlobalStyle = createGlobalStyle`
  body {
    margin: 0;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen', 'Ubuntu', 'Cantarell', 'Fira Sans', 'Droid Sans', 'Helvetica Neue', sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }

  code {
    font-family: source-code-pro, Menlo, Monaco, Consolas, 'Courier New', monospace;
  }
`;

const root = ReactDOM.createRoot(document.getElementById('rootxxx'));
root.render(
    <React.StrictMode>
        <GlobalStyle />
        <App />
    </React.StrictMode>
);

reportWebVitals();
```

Directly apply styles using the style attribute in `src\App.js`:

```js
function App() {
    const rootStyle = {
        border: '2px rgba(0,0,0,.05) solid',
        position: 'relative',
        width: '300px',
        height: '300px'
    };
    return (
        <div style={rootStyle}>
            rootxxx
        </div>
    );
}

export default App;
```

To remove `manifest.json` and logo files I update `public\index.html`:

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />
        <meta
            name="description"
            content="Web site created using create-react-app"
        />
        <title>React App</title>
    </head>
    <body>
        <noscript>You need to enable JavaScript to run this app.</noscript>
        <div id="rootxxx"></div>
    </body>
</html>
```

To remove leading slash from paths in build I can adjust the `homepage` property in `package.json` to an empty string. This tells `create-react-app` to generate relative paths instead of absolute paths. In `package.json`:

```json
{
  "name": "react-widget-test",
  "version": "0.1.0",
  "private": true,
  "dependencies": {
    "@testing-library/jest-dom": "^5.17.0",
    "@testing-library/react": "^13.4.0",
    "@testing-library/user-event": "^13.5.0",
    "react": "^18.3.1",
    "react-dom": "^18.3.1",
    "react-scripts": "5.0.1",
    "styled-components": "^6.1.12",
    "web-vitals": "^2.1.4"
  },
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  },
  "eslintConfig": {
    "extends": [
      "react-app",
      "react-app/jest"
    ]
  },
  "browserslist": {
    "production": [
      ">0.2%",
      "not dead",
      "not op_mini all"
    ],
    "development": [
      "last 1 chrome version",
      "last 1 firefox version",
      "last 1 safari version"
    ]
  },
  "homepage": "."
}
```

Rebuild the Project

After making this change, rebuild the project:

```bash
npm run build
```

Files updated:

- modified:   README.md
- modified:   package-lock.json 
- modified:   package.json
- deleted:    public/favicon.ico
- modified:   public/index.html
- deleted:    public/logo192.png
- deleted:    public/logo512.png
- deleted:    public/manifest.json
- deleted:    src/App.css
- modified:   src/App.js
- deleted:    src/index.css
- modified:   src/index.js
- deleted:    src/logo.svg