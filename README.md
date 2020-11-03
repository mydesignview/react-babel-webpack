# React JS project workflow setup using webpack from scratch.

### step 1 : npm init

    package name: (react-babel-webpack)
    version: (1.0.0)
    description: React project setup using webpack
    entry point: (index.js) src/index.js
    test command:
    git repository: (https://github.com/mydesignview/react-babel-webpack.git)
    keywords: reactjs, webpack, babel
    author: santhaname
    license: (ISC)

### Step 2 : Setting up eslint

    eslint extension for the editors
    .eslintrc file creation with the test rule
        {
            "rules": {
                "semi": ["error", "always"],
                "quotes": ["error", "single"]
            }
        }
    above setup is goodenough for the simple JS project, but in our case we are about to create a reactJS with babel so we need add few more things to ensure the eslint has been configured to understand the project need.

    core dependency 'npm install eslint --save-dev' this will install the key eslint package.

    after installing the core dependency, we can define the eslint configuration in two different ways one from the scratch by defining all the required plugin's and configuration, else use the exisisting well established configuration from companies like airbnb, google etc.,

    In this I am taking the second route to define the eslint configuration. I am about to use the airbnb config.

    Install the airbnb esling config package, before installing run the command 'npm info "eslint-config-airbnb@latest" peerDependencies' will output the following object.

    {
    eslint: '^5.16.0 || ^6.8.0 || ^7.2.0',
        'eslint-plugin-import': '^2.21.2',
        'eslint-plugin-jsx-a11y': '^6.3.0',
        'eslint-plugin-react': '^7.20.0',
        'eslint-plugin-react-hooks': '^4 || ^3 || ^2.3.0 || ^1.7.0'
    }
    
    This are all the peer dependencies which got installed as part of the configuration. 'npx install-peerdeps --dev eslint-config-airbnb' this command will add you the respective packages as part of the dev dependencies.

    After installing those peer dependencies it need to be defined as part of the configuration file.

    "extends": ["airbnb"], at the root level and the rules to pick the right files.

    "rules": {
      "react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"] }],
    }

    Finally need to add the babel-loader as part of the eslint parser so that all the babel code will be linted properly.

    Using this command you can install the "npm install babel-eslint --save-dev" after the installation add the below to the eslint file.

    "parser": "babel-eslint",

    Finally the .eslintrc file will look like below

    {
    "parser": "babel-eslint",
    "extends": ["airbnb"],
    "env": {
      "browser": true,
      "node": true,
      "jest": true,
      "commonjs": true
    },
    "rules": {
      "react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"] }],
      "linebreak-style": ["error", "windows"]
    }
}
