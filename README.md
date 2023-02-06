# ThreeJS_Repos
 
Repository with tutorials / crash courses I followed along / projects I made with Three.js.

If any link doesn't work it most likely is due to a repo being private or the link is not right. Feel free to let me know if that happens.

| | Repository | Online at |
| - | - | - |
| :heavy_check_mark: | [Crash Course](https://github.com/JoaoASousa/Threejs_Tutorial_1) | [Click me!](https://joaoasousa.github.io/Threejs_Tutorial_1/) |




## Publishing Vite project
[Youtube video that helped](https://www.youtube.com/watch?v=5ccdo8iWR58)

1. `vite.config.js` | create the file if it doesn't exist already. `REPO_NAME` is placeholder for the name of the repo.
```js
// vite.config.js
export default {
    // config options
    base: '/REPO_NAME/'
}
```

2. add deploy script to `package.json`
```json
"scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview",
    "deploy": "gh-pages -d dist"
},
```

3. create `deploy.sh` replacing the appropriate fields | template in [Vite's website](https://vitejs.dev/guide/static-deploy.html)

Example for Three_js_Tutorial_1 Repo ([Live Here](https://joaoasousa.github.io/Threejs_Tutorial_1/))
```sh
#!/usr/bin/env sh

# abort on errors
set -e

# build
npm run build

# navigate into the build output directory
cd dist

# place .nojekyll to bypass Jekyll processing
echo > .nojekyll

# if you are deploying to a custom domain
# echo 'www.example.com' > CNAME

git init
git checkout -B main
git add -A
git commit -m 'deploy'

# if you are deploying to https://<USERNAME>.github.io
# git push -f git@github.com:<USERNAME>/<USERNAME>.github.io.git main

# if you are deploying to https://<USERNAME>.github.io/<REPO>
git push -f git@github.com:JoaoASousa/Threejs_Tutorial_1.git main:gh-pages

cd -
```

4.  add, commit, push
5.  run `npm install gh-pages --save -dev`
6.  add, commit, push (probably #4 is unecessary)
7.  `npm run build`
8.  `npm run deploy`
9.  Go to your Repo in Github and check if there is now a branch named gh-pages
10. Go to Settings -> Pages
11. In "Branch" it should say "Your GitHub Pages site is currently being built from the gh-pages branch."
12. After a couple of minutes (probably it took around 3 for me) it should right under "GitHub Pages" something like "Your site is live at" (etc etc)

Hope this can help someone that had some issues to get it working too.
