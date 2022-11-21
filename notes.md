### Fast Refresh with Expo Web

# 1. Add necessary libraries

npm install @pmmmwh/react-refresh-webpack-plugin webpack-hot-middleware react-refresh

# 2. At the moment if this writing (2022. April) there’s some issue with react-error-overlay 6 which needs this fix in package.json

```
"resolutions": {
"react-error-overlay": "6.0.9"
},
```

3. Eject the Webpack config:

```
expo customize:web
```

# 4. In your newly created webpack.config.js:

```
const createExpoWebpackConfigAsync = require('@expo/webpack-config');
const ReactRefreshWebpackPlugin = require("@pmmmwh/react-refresh-webpack-plugin");

module.exports = async function (env, argv) {
  const config = await createExpoWebpackConfigAsync(env, argv);
  // Use the React refresh plugin in development mode
  if (env.mode === "development") {
    config.plugins.push(
      new ReactRefreshWebpackPlugin()
    );
  }
  return config;
};
```
