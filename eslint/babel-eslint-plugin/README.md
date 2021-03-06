# @babel/eslint-plugin

Companion rules for `@babel/eslint-parser`. `@babel/eslint-parser` does a great job at adapting `eslint`
for use with Babel, but it can't change the built in rules to support experimental features.
`@babel/eslint-plugin` re-implements problematic rules so they do not give false positives or negatives.

> Requires Node 10.9 or greater

### Install

```sh
npm install @babel/eslint-plugin --save-dev
```

Load the plugin in your `.eslintrc.json` file:

```json
{
  "plugins": ["@babel/eslint-plugin"]
}
```

Finally enable all the rules you would like to use (remember to disable the
original ones as well!).

```json
{
  "rules": {
    "babel/new-cap": "error",
    "babel/camelcase": "error",
    "babel/no-invalid-this": "error",
    "babel/object-curly-spacing": "error",
    "babel/quotes": "error",
    "babel/semi": "error",
    "babel/no-unused-expressions": "error",
    "babel/valid-typeof": "error"
  }
}
```
### Rules

Each rule corresponds to a core `eslint` rule, and has the same options.

🛠: means it's autofixable with `--fix`.

- `babel/new-cap`: Ignores capitalized decorators (`@Decorator`)
- `babel/camelcase: doesn't complain about optional chaining (`var foo = bar?.a_b;`)
- `babel/no-invalid-this`: doesn't fail when inside class properties (`class A { a = this.b; }`)
- `babel/object-curly-spacing`: doesn't complain about `export x from "mod";` or `export * as x from "mod";` (🛠)
- `babel/quotes`: doesn't complain about JSX fragment shorthand syntax (`<>foo</>;`)
- `babel/semi`: doesn't fail when using `for await (let something of {})`. Includes class properties (🛠)
- `babel/no-unused-expressions`: doesn't fail when using `do` expressions or [optional chaining](https://github.com/tc39/proposal-optional-chaining) (`a?.b()`).
- `babel/valid-typeof`: doesn't complain when used with [BigInt](https://github.com/tc39/proposal-bigint) (`typeof BigInt(9007199254740991) === 'bigint'`).

#### Deprecated

| Rule                             | Notes                              |
|:---------------------------------|:-----------------------------------|
| `babel/generator-star-spacing`   | Use [`generator-star-spacing`](http://eslint.org/docs/rules/generator-star-spacing) since eslint@3.6.0 |
| `babel/object-shorthand`         | Use [`object-shorthand`](http://eslint.org/docs/rules/object-shorthand) since eslint@0.20.0 |
| `babel/arrow-parens`             | Use [`arrow-parens`](http://eslint.org/docs/rules/arrow-parens) since eslint@3.10.0 |
| `babel/func-params-comma-dangle` | Use [`comma-dangle`](http://eslint.org/docs/rules/comma-dangle) since eslint@3.8.0 |
| `babel/array-bracket-spacing`    | Use [`array-bracket-spacing`](http://eslint.org/docs/rules/array-bracket-spacing) since eslint@3.9.0 |
| `babel/flow-object-type`         | Use [`flowtype/object-type-delimiter`](https://github.com/gajus/eslint-plugin-flowtype#eslint-plugin-flowtype-rules-object-type-delimiter) since eslint-plugin-flowtype@2.23.0 |
| `babel/no-await-in-loop`         | Use [`no-await-in-loop`](http://eslint.org/docs/rules/no-await-in-loop) since eslint@3.12.0 |
