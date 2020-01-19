# personal-eslint-setup-react
My eslint configuration for react projects

- Run: `npm i eslint eslint-config-airbnb eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react prettier eslint-config-prettier eslint-plugin-prettier -D`

- `.eslintrc` looks like this:
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
                "printWidth": 120,
                "tabWidth": 4
            }
        ],
        "no-use-before-define": "off",
        "no-param-reassign": "off",
        "import/no-named-as-default": "off",
        "import/no-named-as-default-member": "off",
        "react/prefer-stateless-function": "off"
    },
    "plugins": [
        "prettier"
    ]
}
```

## Optional .editorconfig
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
