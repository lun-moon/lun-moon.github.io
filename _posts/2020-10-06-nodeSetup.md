# Steps to follow in setting up a nodeJS environment (Ubuntu)
1. <https://snapcraft.io/node>
2. <https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally>
3. <https://snapcraft.io/code> + telemetry off
 -- note to run this you may need to enter on the bash command line to prevent some annoying keyboard shortcut problem
`GTK_IM_MODULE="xim" code` ;
3.1 <https://www.gatsbyjs.com/tutorial/part-zero/> (Prettier plugin for vscode)

# <https://www.gatsbyjs.com/docs/quick-start/>  
4. npm install -g gatsby-cli + telemetry off
5. gatsby new gatsby-site https://github.com/gatsbyjs/gatsby-starter-hello-world


# <https://www.gatsbyjs.com/docs/end-to-end-testing/>

5. cd gatsby-site
6. `npm install --save-dev cypress start-server-and-test`
7. vim cypress.json  [new file]
```
{
  "baseUrl": "http://localhost:8000/"
}
```

8. vim package.json, add the lines cy:open... and test:e2e... example shown below
```
{
  `"scripts": {`
    "develop": "gatsby develop",
    "cy:open": "cypress open",
    "test:e2e": "start-server-and-test develop http://localhost:8000 cy:open"
  }
}
```

9. `npm run test:e2e`
