# personal-eslint-setup-react
My eslint/prettier/husky configuration for react projects

- Run: `npm i eslint eslint-config-airbnb eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react prettier eslint-config-prettier eslint-plugin-prettier babel-eslint husky lint-staged -D`

- If using vscode, install [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) and [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
  - Add this to settings:
  
  ```json
    "editor.codeActionsOnSave": {
      "source.fixAll.eslint": true
    }
  ```
### ESLint + Prettier config
- Create `.eslintrc.json` (needs `.json` to work on windows machines) at project root. It should look like this:
```json
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
    ],
    "parser": "babel-eslint",
    "rules": {
        "react/jsx-filename-extension": [
            1,
            {
                "extensions": [
                    ".js",
                    ".jsx"
                ]
            }
        ],
        "prettier/prettier": [
            "error",
            {
                "arrowParens": "always",
                "bracketSpacing": true,
                "trailingComma": "es5",
                "singleQuote": false,
                "printWidth": 80,
                "tabWidth": 4
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
        "import/no-named-as-default": "off",
        "import/no-named-as-default-member": "off",
        "react/prefer-stateless-function": "off"
    },
    "plugins": [
        "prettier"
    ]
}
```
### Husky setup
- In `package.json` at the same level as dependencies add:
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
