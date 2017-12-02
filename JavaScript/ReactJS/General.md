# General

### [Adding a Favicon to your Application](https://serverless-stack.com/chapters/add-app-favicons.html)
Basically the same as adding a favicon to every other static site. Generate the favicon files and place them in the `/public` folder. Then include them in the `public/index.html`.  
Since they are placed in the public folder, the `href`s in the `<link>` tags do need the `%PUBLIC_URL%` prefix to locate the files.
