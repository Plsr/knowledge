# npm cheatsheet
I often find myself googling for the same commands every few weeks. This is a collection of theses things so I do find them quicker.

* [`npm docs <package>`](https://docs.npmjs.com/cli/docs.html)  
  Navigate to the documentation of the given package (usually the npm or GitHub Repository)
* `npm init -y`  
  Quickly initialise a new npm project without answering all the quesitons.
  Resulting `package.json` looks like this:
  ```json
    {
      "name": "<PWD>",
      "version": "1.0.0",
      "description": "",
      "main": "index.js",
      "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
      },
      "keywords": [],
      "author": "",
      "license": "ISC"
    }
  ```

