---
layout: post
title: "Fix npm vulnerabilities with yarn"
author: "Rohit"
img: npm.png
---

 Sometimes we get security alerts on GitHub because our project’s `npm` packages have security issues. With npm we can use `npm audit fix` to update our packages. But if you have used `yarn`, then `yarn` also has a command for auditing packages: `yarn audit` This command shows a list of vulnerable packages. But there is no `yarn audit --fix` ! So, as of now, it appears that there is no `yarn audit --fix`. So I am trying to figure out how to go about fixing my `npm` security bugs `yarn audit` errors. After trying `yarn upgrade`, it has fixed some of the errors in my `npm` packages, but there are still several remaining. I have tried a `yarn add <pakage>@latest` for the remaining high vulnerabilities, but it upgrades the version in our `package.json`, when I think the issues is coming from a dependency of a package that I am using. Here is an example of some of my remaining errors:

```
$ yarn audit
yarn audit v1.19.1
┌───────────────┬──────────────────────────────────────────────────────────────┐
│ moderate      │ Cross-Site Scripting                                         │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Package       │ serialize-javascript                                         │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Patched in    │ >=2.1.1                                                      │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Dependency of │ react-scripts                                                │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Path          │ react-scripts > terser-webpack-plugin > serialize-javascript │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ More info     │ https://www.npmjs.com/advisories/1426                        │
└───────────────┴──────────────────────────────────────────────────────────────┘
┌───────────────┬──────────────────────────────────────────────────────────────┐
│ moderate      │ Denial of Service                                            │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Package       │ handlebars                                                   │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Patched in    │ >=4.4.5                                                      │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Dependency of │ react-scripts                                                │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Path          │ react-scripts > jest > jest-cli > @jest/core >               │
│               │ @jest/reporters > istanbul-reports > handlebars              │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ More info     │ https://www.npmjs.com/advisories/1300                        │
└───────────────┴──────────────────────────────────────────────────────────────┘
┌───────────────┬──────────────────────────────────────────────────────────────┐
│ high          │ Arbitrary Code Execution                                     │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Package       │ handlebars                                                   │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Patched in    │ >=4.5.2                                                      │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Dependency of │ react-scripts                                                │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Path          │ react-scripts > jest > jest-cli > @jest/core >               │
│               │ @jest/reporters > istanbul-reports > handlebars              │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ More info     │ https://www.npmjs.com/advisories/1316                        │
└───────────────┴──────────────────────────────────────────────────────────────┘
┌───────────────┬──────────────────────────────────────────────────────────────┐
│ high          │ Arbitrary Code Execution                                     │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Package       │ handlebars                                                   │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Patched in    │ >=4.5.3                                                      │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Dependency of │ react-scripts                                                │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Path          │ react-scripts > jest > jest-cli > @jest/core >               │
│               │ @jest/reporters > istanbul-reports > handlebars              │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ More info     │ https://www.npmjs.com/advisories/1324                        │
└───────────────┴──────────────────────────────────────────────────────────────┘
┌───────────────┬──────────────────────────────────────────────────────────────┐
│ high          │ Prototype Pollution                                          │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Package       │ handlebars                                                   │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Patched in    │ >=4.5.3                                                      │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Dependency of │ react-scripts                                                │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Path          │ react-scripts > jest > jest-cli > @jest/core >               │
│               │ @jest/reporters > istanbul-reports > handlebars              │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ More info     │ https://www.npmjs.com/advisories/1325                        │
└───────────────┴──────────────────────────────────────────────────────────────┘
┌───────────────┬──────────────────────────────────────────────────────────────┐
│ moderate      │ Cross-Site Scripting                                         │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Package       │ serialize-javascript                                         │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Patched in    │ >=2.1.1                                                      │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Dependency of │ react-scripts                                                │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ Path          │ react-scripts > webpack > terser-webpack-plugin >            │
│               │ serialize-javascript                                         │
├───────────────┼──────────────────────────────────────────────────────────────┤
│ More info     │ https://www.npmjs.com/advisories/1426                        │
└───────────────┴──────────────────────────────────────────────────────────────┘
6 vulnerabilities found - Packages audited: 904851
Severity: 3 Moderate | 3 High
Done in 4.62s.
```

Here is an answer I found:
- The solution to this problem in yarn is called `selective version resolution` which is basically defining resolutions for the `transitive dependencies` in the `package.json`.
- The transitive dependencies are the dependencies of dependencies.
```bash
{
  "resolutions": { "**/**/lodash": "^4.17.12" }
}
```

So here even if the `lodash` isn’t a direct dependency of your package, the dependent package in your package uses the version defined in the resolutions. Specific resolutions can also be provided.
You can check the yarn documentation about [selective dependency resolutions](https://yarnpkg.com/lang/en/docs/selective-version-resolutions/).