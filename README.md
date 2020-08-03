git clone https://github.com/LearnWebCode/travel-site-files.git  
git remote -v  
git remote set-url origin https://github.com/vivamus/udemy-GitWebWorkflow.git  
git status  
git add -A  
git commit -m 'a b'  
git mv old new  
git push origin master  
git commit -a     #skip staging  
git config --global alias.last 'log -1 HEAD'  
git config --global alias.ca 'commit -a'  
git config --global alias.pom 'push origin master'  

nodejs.org npmjs.org  
npm init -y  
npm install lodash  
npm install normalize.css  
rm -r node_modules/  
npm install  
  grep node_modules .gitignore  

npm install webpack webpack-cli --save-dev  
webpack.config.js to bundled.js and watch: true  
npm run dev  

15. **CSS with webpack -- using PostCSS**    
    npm install css-loader style-loader --save-dev  
    in App.js import styles.css  
    in webpack.config.js add module --> css-loader --> added to bundle.js  

17. **CSS file architechture**   
    postcss import normalize   
    position large-hero__text-content on top of image and center  

18. **what is BEM?**  
  from `.large-hero h1` to `<h1 class=.large-hero__title>`  
  B.E.M. == Block `__Element` (only within a block) `--Modifier` (change default)  
    direct with classes (no cascade)  
    single responsibility blocks, no descendant selectors, flat architechture  
    PostCSS '&' compiles to outer class name!

19. **complete two blocks** -- large-hero and btn   
  large-hero -- margin: 0  
    rem -- root of the page em (i.e. of 16 pixels)  
    position shadow splitline etc  
  btn btn--orange modifier  text-decoration:none  

20. **webpack dev server** -- reload browser by filesave, accross the network  
  npm install webpack-dev-server --save-dev  
  webpack.config.js devServer hot port:3000, no need for watch:true anymore  
  package.json -- webpack-dev-server ++ App.js accept  
  localhost:3000  
  does not reload page -- if you select element and change CSS, selection stays (keeps current state)
  was watching CSS, but not index.html, inserted `before:` in devServer of webpack -- full page reload though
  **across WiFi network** devServer `host: '0.0.0.0' -- need local (not public()) IP address
  Windows: ipconfig  IPv4 Address -- 192.168.1.111 (MAc Syestem Preference > Network)
    on smartphone -- `192.168.1.111:3000` -- did not work for me? maybe because VPN?
    now we may delete buindled.js, it exists in RAM as localhostL300/bundled.js

  21. **"Mobile-first"**
    progressively enhance design for larger screen, no unnesecessary data  
    decreese horizontal widht of the browser -- font too large  
    start with css __title font-size 1.2 @media min-width 530px 4.8 (your clarity jumps small if width decreases)  
    npm install postcss-mixins --save-dev  webpack require
    base/_mixin.css @mixin atSmall
    default is smallest then Small,Medium,Large

  22. **Responsive Images**
    2 reasons for different images: crop; filesize
    ```<picture> <source srcset="medium.jpg" media="(min-width: 760px)">
          <img src="small.jpg"> </picture>```
      

