# personal-eslint-setup-react

My eslint/prettier/husky configuration for react projects

## JavaScript

-   Run:

    ```bash
    npm i eslint eslint-config-airbnb eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react prettier eslint-config-prettier eslint-plugin-prettier babel-eslint -D
    ```

    -   With husky ([git hooks](https://github.com/typicode/husky#readme)):

    ```bash
    npm i eslint eslint-config-airbnb eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react prettier eslint-config-prettier eslint-plugin-prettier babel-eslint husky lint-staged -D
    ```

## TypeScript

-   Run:

    ```bash
    npm i eslint eslint-config-airbnb eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react prettier eslint-config-prettier eslint-plugin-prettier @typescript-eslint/parser @typescript-eslint/eslint-plugin -D
    ```

    -   With husky ([git hooks](https://github.com/typicode/husky#readme)):

    ```bash
    npm i eslint eslint-config-airbnb eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react prettier eslint-config-prettier eslint-plugin-prettier @typescript-eslint/parser @typescript-eslint/eslint-plugin husky lint-staged -D
    ```

-   Uncomment the commented rules in the eslint config below when using typescript.
    -   There should only be one parser in use.

### _Note_

-   If using vscode, install [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) and [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

    - Adding `"editor.formatOnSave": true` to your settings should be enough to get eslint working properly, however there have been times in the past that it didn't work.

    - If the above doesn't work add this block to settings:

    ```json
      "editor.formatOnSave": true,
      "editor.defaultFormatter": "esbenp.prettier-vscode",
      "[javascript]": {
          "editor.formatOnSave": false,
          "editor.codeActionsOnSave": {
              "source.fixAll.eslint": true
          }
      }
    ```

    -   If having issues with typescript specifically you may need to add this as well (however it has worked without it in the past):

    ```json
      "eslint.validate": ["typescript", "typescriptreact"]
    ```

### ESLint + Prettier config

-   Create `.eslintrc.json` (needs `.json` to work on windows machines) at project root. It should look like this:

```js
{
    "env": {
        "browser": true,
        "jest": true,
        "node": true
    },
    "extends": [
        "airbnb",
        "prettier",
        "prettier/react"
        // "plugin:@typescript-eslint/recommended",
        // "prettier/@typescript-eslint"
    ],
    "parser": "babel-eslint",
    // "parser": "@typescript-eslint/parser",
    "settings": {
        "import/resolver": {
            "node": {
                "extensions": [
                    ".js",
                    ".jsx",
                    ".ts",
                    ".tsx"
                ]
            }
        }
    },
    "rules": {
        "react/jsx-filename-extension": [
            1,
            {
                "extensions": [
                    ".js",
                    ".jsx",
                    ".tsx"
                ]
            }
        ],
        "prettier/prettier": [
            "warn",
            {
                "arrowParens": "always",
                "bracketSpacing": true,
                "printWidth": 80,
                "singleQuote": false,
                "tabWidth": 4
                "trailingComma": "none",
                "useTabs": false
            }
        ],
        "no-use-before-define": "off",
        "no-param-reassign": "off",
        "no-plusplus": [
            "error",
            {
                "allowForLoopAfterthoughts": true
            }
        ],
        "import/extensions": [
            "error",
            "ignorePackages",
            {
                "js": "never",
                "jsx": "never",
                "ts": "never",
                "tsx": "never"
            }
        ],
        "import/no-named-as-default": "off",
        "import/no-named-as-default-member": "off",
        "react/prefer-stateless-function": "off",
        // "react/prop-types": "off"
    },
    "plugins": [
        "prettier"
    ]
}
```

### Standalone prettier config

-   Create `.prettierrc.json`
    -   This will apply to other files (`.css`, `.less`,`.json`...)

```json
{
    "arrowParens": "always",
    "bracketSpacing": true,
    "jsxBracketSameLine": false,
    "printWidth": 80,
    "proseWrap": "preserve",
    "semi": true,
    "singleQuote": false,
    "tabWidth": 4,
    "trailingComma": "none",
    "useTabs": false
}
```

### Husky setup (if using husky)

-   In `package.json` at the same level as dependencies add:

```json
"husky": {
  "hooks": {
    "pre-commit": "lint-staged"
  }
},
"lint-staged": {
  "./src/*.{js,jsx,ts,tsx}": [
    "eslint --fix"
  ]
}
```

### Optional `.editorconfig`

```
root = true

[*]
indent_style = space
indent_size = 4
end_of_line = lf
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true

[{*.js,*.css,*.less,*.html}]
indent_style = space
indent_size = 4

[{*.json,*.yml}]
indent_style = space
indent_size = 4

[*.md]
trim_trailing_whitespace = false
```
