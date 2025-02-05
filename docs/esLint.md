# EsLint

## 基本配置

1. 安装 EsLint `npm install eslint --save-dev`

2. 生成一个基本的配置文件 .eslintrc.json `npx eslint --init`

3. 在配置文件中修改规则

    ```json
    import globals from "globals";
    
    
    /** @type {import('eslint').Linter.Config[]} */
    export default [
      {
        files: ["**/*.js"], 
        languageOptions: {sourceType: "commonjs"},
        rules: {
            // 不允许未使用的变量，但忽略以下划线开头的参数
            "no-unused-vars": ["error", { "argsIgnorePattern": "^_" }], 
            // 语句结尾必须加分号
            "semi": ["error", "always"],
            // 缩进必须是4个空格
            "indent": ["error", 4],
            // 必须使用全等号
            "eqeqeq": ["error", "always"],
            // 必须使用花括号包裹代码块
            "curly": ["error", "all"],
        }
    },
      {languageOptions: { globals: globals.node }},
    ];
    ```

4. 在 package.json 中加入 `"scripts": { "lint": "eslint ."}`

5. 控制台输入 `npm run lint`

