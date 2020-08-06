git clone https://github.com/LearnWebCode/travel-site-files.git  
git remote -v  
git remote set-url origin https://github.com/vivamus/udemy-GitWebWorkflow.git  
git status  
git add -A  
git commit -m 'a b'  
git mv old new  
git push origin master  
git commit -a     #skip staging  
rm foo, git restore foo  
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
**npm run dev**  

15. **CSS with webpack -- using PostCSS**    
    npm install css-loader style-loader --save-dev  
    in App.js import styles.css  
    in webpack.config.js add module --> css-loader --> added to bundle.js  
16.
 17. **CSS file architechture**   
    postcss import normalize   
    position `large-hero__text-content` on top of image and center  

18. **what is BEM?**  
  from `.large-hero h1` to `<h1 class=.large-hero__title>`  
  B.E.M. == `Block` `__Element` (only within a block) `--Modifier` (change default)  
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

### *Section 7: Mobile-first Essentials*     

21. **"Mobile-first"**  
  progressively enhance design for larger screen, no unneeded data  
  decrease horizontal widht of the browser -- font too large  
  start with css __title font-size 1.2 @media min-width 530px 4.8 (your clarity jumps small if width decreases)  
  npm install postcss-mixins --save-dev  webpack require  
  base/_mixin.css @mixin atSmall  
  default is smallest then Small,Medium,Large  

22. **Responsive Images**  
  2 reasons for different images: crop; filesize  
  i) crop: ```<picture> <source srcset="medium.jpg" media="(min-width: 760px)">  
        <img src="small.jpg"> </picture>```  
  ii) filesize `<img srcset Small.jpg 570w, medium.jpg 1200w, large.jpg 1920w>`  
    browser itself decides which resolution Width to pick  
      
23. **Testing Responsive Images**  
  -i.jpg version for "info"-images 1920 X 654   
  testing e.g. hi-dpi -- Chrome Developer Tool -- right-click Inspect  
    * open devices icon (upper leftish) emulation  
    * with Responsive set device pixel ratio 2 (3 dots menu chose DPR)  -- for different jpg resolution  
    * change Responsive to e.g. iPhoneX  

### *Section 8: Let's build!*     

24. **Creating Reusable Blocks**  
  with iPhoneX emulation  
   * _wrapper.css -- padding  
   * __title increase fontsize  
  image -- we add border-bottom to large-hero  
  * whiteline appeared `<img ... class="large-hero__image>` -- change display from `inline-block` to `block`  
  * default image is inline-block  
  design pattern for spacing -- page-section  
  wrapper for padding center  

25. **Headline Block**  
  headline-- modifiers  
  wrapper--medium modifier  
  adjust atSmall atMedium -- page-section and headline  
  .wrapper inside .wrapper has paddings 0  

26. **Column Layout Block**  
  row__4 row__8 float: left  
  trick -- empty div with clear:both  
  better &::after content "", clear both, display table  
  `&--gutters > div` for children's padding --exceeds the total 100%  
  `box-sizing: border-box` to _global.css!  
  last column protruding 65px: neg margin, overflow hidden (i.e. gutter exists but not visible)  
  row__medium-4/8 -- single column on iPhone  

27. **Attention to detail I**  -- images and margins
  margin between 2 images -- wrapper-b-margin  
  row__medium-4--larger  
  3 versions of our-start image -- <picture> srcset  
  hi-dpi -- browser assumes whole browser width -- <source sizes=404px>
  `sizes="(min-width: 970px) 976px, 100vw"`  

28. **Attention to detail II**  -- margins and line-height    
  right col, eliminate top margin headline--no-t-margin  
  `generic-content-container`  `line-height: 1.65`  no BEM -- pure p  
  row__b-margin-until-medium    


### *Section 9: Git Timeout*  
  
28. **Git branches**    
  `git branch`  -- list of branches  
  git reset filename -- unstage  
  git branch count-to-ten; git branch  
  git checkout count-to-ten; git add, commit  
  git push origin count-to-fifteen  -- merge pull request on github (assigned to self)   
  git checkout master  
  git merge count-to-ten  
  if conflicts, manuall edit, do git add file, and then git merge --continue?  
