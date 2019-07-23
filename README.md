# Bookmarklets

## Table of contents
* [Accessibility](#accessibility--validation)
* [Archival](#archival)
* [Debug](#debug)
* [Fonts](#fonts)
* [Performance](#performance)
* [Search Engine Optimization](#search-engine-optimization)
* [Miscellaneous](#miscellaneous)

## Accessibility & Validation
**[a11y.css](https://github.com/ffoodd/a11y.css):** This CSS file intends to warn developers about possible risks and mistakes that exist in HTML code. It can also be used to roughly evaluate a site's quality by simply including it as an external stylesheet.

```javascript
javascript:(function(d){'use strict';var a11ycss=d.createElement('link');a11ycss.href='https://rawgit.com/ffoodd/a11y.css/master/css/a11y-en.css';a11ycss.rel='stylesheet';a11ycss.media='all';(d.body||d.getElementsByTagName('body')[0]).appendChild(a11ycss);})(document);
```

**[HTML_CodeSniffer](https://github.com/squizlabs/HTML_CodeSniffer):** HTML_CodeSniffer is a client-side JavaScript that checks a HTML document or source code, and detects violations of a defined coding standard.

```javascript
javascript:(function(d){'use strict';var _p='https://squizlabs.github.io/HTML_CodeSniffer/build/',options={path:_p};function _i(s,cb){var sc=d.createElement('script');sc.onload=function(){sc.onload=null;sc.onreadystatechange=null;cb.call(this);};sc.onreadystatechange=function(){if(/^(complete|loaded)$/.test(this.readyState)===true){sc.onreadystatechange=null;sc.onload();}};sc.src=s;(d.head||d.getElementsByTagName('head')[0]).appendChild(sc);}_i(_p+'HTMLCS.js',function(){HTMLCSAuditor.run('WCAG2AA',null,options);});})(document);
```

**[Readability Bookmarklet](http://accessibility.oit.ncsu.edu/tools/readability/):** This tool will show you how readable selected text is on a page. The readability guidelines are based on WCAG 2 Level AAA Conformance. Note, there is no readability requirement for WCAG 2, Level AA Conformance. The results are based on six tests.

```javascript
javascript:(function(d){'use strict';var yourURL='https://webapps.ncsu.edu/accessibility-readability/readability.php';function getScript(url,success){var script=d.createElement('script'),head=d.head||d.getElementsByTagName('head')[0],done=false;script.src=url;script.onload=script.onreadystatechange=function(){if(!done&&(!this.readyState||this.readyState==='loaded'||this.readyState==='complete')){done=true;success();script.onload=script.onreadystatechange=null;head.removeChild(script);}}head.appendChild(script);}getScript(yourURL,function(){});})(document);
```

**[REVENGE.CSS](https://github.com/Heydon/REVENGE.CSS):** The premise of revenge.css is simple: A CSS bookmarklet that uses selectors to find bad markup, displaying ugly pink error messages in comic sans serif wherever you write bad HTML.

```javascript
javascript:(function(d){'use strict';var revenge=d.createElement('link');revenge.href='https://rawgit.com/Heydon/REVENGE.CSS/master/revenge.css';revenge.rel='stylesheet';revenge.media='all';(d.body||d.getElementsByTagName('body')[0]).appendChild(revenge);})(document);
```

**[Trashy.css](https://t7.github.io/trashy.css/):** "The throwaway CSS library with no `class`" outlines the semantic elements of a document and points out accessibility errors similarly to a11y.css.

```javascript
javascript:(function(d){'use strict';var l=d.querySelectorAll('[rel=\'stylesheet\']'),s=d.querySelectorAll('style'),t=d.createElement('link'),n=l.length;while(n--)l[n].setAttribute('rel','');for(n=s.length;s--;)s[n].innerHTML='';t.setAttribute('rel','stylesheet');t.setAttribute('href','https://t7.github.io/trashy.css/css/bookmarklet.css');(d.head||d.getElementsByTagName('head')[0]).appendChild(t);})(document);
```

**[Web Evaluation Tools Bookmarklet](http://accessibility.oit.ncsu.edu/tools/web-evaluation-tools):** This set of tools allows you to check for several aspects of Web accessibility that other tools do not. It is not designed to replace any other tools, but rather to supplement them.

```javascript
javascript:(function(d){'use strict';var yourURL='https://webapps.ncsu.edu/web-evaluation-tools/web-evaluation-tools.php';function getScript(url,success){var script=d.createElement('script'),head=d.head||d.getElementsByTagName('head')[0],done=false;script.src=url;script.onload=script.onreadystatechange=function(){if(!done&&(!this.readyState||this.readyState==='loaded'||this.readyState==='complete')){done=true;success();script.onload=script.onreadystatechange=null;head.removeChild(script);}};head.appendChild(script);}getScript(yourURL,function(){});})(document);
```

## Archival
**[Archive.is](http://archive.is/) (also .li and .today):** Send the current page to a Web-archiving service, through one of its domain names.
```javascript
javascript:void(window.open('https://archive.is/?run=1&url='+encodeURIComponent(location.href)).opener=null);
```
```javascript
javascript:void(window.open('https://archive.li/?run=1&url='+encodeURIComponent(location.href)).opener=null);
```
```javascript
javascript:void(window.open('https://archive.today/?run=1&url='+encodeURIComponent(location.href)).opener=null);
```

**[FreezePage](http://www.freezepage.com/button):** This archiver works well in conjunction with Archive.is, to get the text-content of rich pages and then archive that more permanently; free registration is required.
```javascript
javascript:void(window.open('http://www.freezepage.com/?button=1&url='+encodeURIComponent(location.href)+'&name='+encodeURIComponent(document.title)).opener=null);
```

**[WebCite](http://webcitation.org/):** Yet Another Website Archiver
```javascript
javascript:void(window.open('http://www.webcitation.org/query.php?url='+encodeURIComponent(location.href)).opener=null);
```

## Debug
**[45-75](https://css-tricks.com/bookmarklet-colorize-text-45-75-characters-line-length-testing/):** Check whether lines are between 45 and 75 characers, for optimal readability; this especially helps with font sizing for responsive web design.

```javascript
javascript:(function(d){'use strict';var loadScript;function init(){var $=jQuery.noConflict(true),redOutline={outline:'2px solid red'},text,textyElements='p,li,dt,dd,h1,h2,h3,h4,h5,h6';$(textyElements).on('mouseover.red',function(){$(this).css(redOutline);}).on('mouseleave.red',function(){$(this).removeAttr('style');}).on('click.red',function(){text=$(this).text();var e=text.substring(0,45),t=text.substring(45,75),n=text.substring(75,text.length),r=e+'<span style="color:red;">'+t+'</span>'+n;$(this).html(r);$(textyElements).off('mouseover.red mouseleave.red click.red');$(this).removeAttr('style');});}if(typeof jQuery==='undefined'||typeof $==='undefined'||$!==jQuery){loadScript=function loadScript(a,b){var c=d.createElement('script'),head=d.head||d.getElementsByTagName('head')[0],done=false;c.type='text/javascript';c.onload=c.onreadystatechange=function(){if(!done&&(!this.readyState||this.readyState==='loaded'||this.readyState==='complete')){done=true;b();}};head.appendChild(c).src=a;};loadScript('https://cdn.jsdelivr.net/jquery/1.12.4/jquery.min.js',init);}else init();})(document);
```

**[CSS Debugger](https://github.com/roykolak/css-debugger):** CSS styles to highlight problematic and malformed html

```javascript
javascript:(function(d){'use strict';(d.body||d.getElementsByTagName('body')[0]).appendChild(d.createElement('script')).src='https://roykolak.github.io/css-debugger/bookmarklet.js';})(document);
```

**[CSS Layout Debugger](https://gist.github.com/addyosmani/fd3999ea7fce242756b1):** A tweet-sized debugger for visualizing your CSS layouts. Outlines every DOM element on your page a random (valid) CSS hex color.
```javascript
javascript:(function(d){'use strict';var elts=(d.body||d.getElementsByTagName('body')[0]).getElementsByTagName('*'),i=elts.length;while(i--)elts[i].style.outline='1px solid #'+(~~(Math.random()*(1<<24))).toString(16);})(document);
```

**[Debug CSS](https://gist.github.com/ozgrozer/91e8b759a1aaff39d9d5#file-debugcss-js)**

```javascript
javascript:(function(d){'use strict';var s=d.createElement('style'),e=d.getElementById('debugCss');;s.id='debugCss';s.innerHTML='*{background-color: rgba(0, 0, 0, .05) !important;outline: 1px solid #fff !important;}';if(null==e)(d.head||d.getElementsByTagName('head')[0]).appendChild(s);else e.parentNode.removeChild(e);})(document);
```

**[Firebug Lite](https://getfirebug.com/):** The project itself is dead, but just in case you want to use it on very old browsers without their own DevTools, the scripts and assets have been saved on the Internet Archive.

```javascript
javascript:(function(F,i,r,e,b,u,g,L,I,T,E){'use strict';if(F.getElementById(b))return;E=F[i+'NS']&&F.documentElement.namespaceURI;E=E?F[i+'NS'](E,'script'):F[i]('script');E[r]('id',b);E[r](b,u);(F.head||F.body||F[e]('head')[0]||F[e]('body')[0]||F[e]('frameset')[0]).appendChild(E).src=I+g+T;E=new Image;E[r]('src',I+L);})(document,'createElement','setAttribute','getElementsByTagName','FirebugLite','4','firebug-lite.js','releases/lite/latest/skin/xp/sprite.png','https://web.archive.org/web/20171119035137id_/https://getfirebug.com/','#startOpened');
```

Beta

```javascript
javascript:(function(F,i,r,e,b,u,g,L,I,T,E){'use strict';if(F.getElementById(b))return;E=F[i+'NS']&&F.documentElement.namespaceURI;E=E?F[i+'NS'](E,'script'):F[i]('script');E[r]('id',b);E[r](b,u);(F.head||F.body||F[e]('head')[0]||F[e]('body')[0]||F[e]('frameset')[0]).appendChild(E).src=I+g+T;E=new Image;E[r]('src',I+L);})(document,'createElement','setAttribute','getElementsByTagName','FirebugLite','4','firebug-lite-beta.js','releases/lite/latest/skin/xp/sprite.png','https://web.archive.org/web/20171119035137id_/https://getfirebug.com/','#startOpened');
```

Debug

```javascript
javascript:(function(F,i,r,e,b,u,g,L,I,T,E){'use strict';if(F.getElementById(b))return;E=F[i+'NS']&&F.documentElement.namespaceURI;E=E?F[i+'NS'](E,'script'):F[i]('script');E[r]('id',b);E[r](b,u);(F.head||F.body||F[e]('head')[0]||F[e]('body')[0]||F[e]('frameset')[0]).appendChild(E).src=I+g+T;E=new Image;E[r]('src',I+L);})(document,'createElement','setAttribute','getElementsByTagName','FirebugLite','4','firebug-lite-debug.js','releases/lite/latest/skin/xp/sprite.png','https://web.archive.org/web/20171119035137id_/https://getfirebug.com/','#startOpened');
```

**[Yahoo! debugCSS](https://github.com/yahoo/debugCSS):** debugCSS is meant to be loaded on an existing page to highlight potentially broken, malformed or legacy (X)HTML.

```javascript
javascript:(function(d,i){'use strict';var l=d.getElementById(i);if(l){l.parentNode.removeChild(l);return;}l=d.createElement('link');l.id=i;l.rel='stylesheet';l.type='text/css';l.href='https://yahoo.github.io/debugCSS/debugCSS.css';(d.head||d.getElementsByTagName('head')[0]).appendChild(l);})(document,'debugCSS');
```

## Fonts
**[FFFFALLBACK](http://ffffallback.com/):** Web fonts are here, sparking an exciting new era in web design. FFFFALLBACK makes it easy to find the perfect fallback fonts, so that your designs degrade gracefully.

```javascript
javascript:(function(d){'use strict';var body=d.body||d.getElementsByTagName('body')[0],scriptTag=d.createElement('script'),linkTag=d.createElement('link');scriptTag.setAttribute('src','https://rawgit.com/jbrewer/ffffallback/master/bookmarklet/ffffallback.js');linkTag.setAttribute('href','https://rawgit.com/jbrewer/ffffallback/master/bookmarklet/ffffallback.css');linkTag.setAttribute('rel','stylesheet');body.appendChild(scriptTag);body.appendChild(linkTag);})(document);
```

**[FontFriend](http://somadesign.ca/projects/fontfriend/):** Font­Friend is a book­marklet for typo­graph­i­cally obsessed web design­ers. It enables rapid check­ing of fonts and font styles directly in the browser with­out edit­ing code and refresh­ing pages, mak­ing it the ideal com­pan­ion for cre­at­ing CSS font stacks.

```javascript
javascript:(function(d){'use strict';var head=d.head||d.getElementsByTagName('head')[0],_my_script=d.createElement('script'),jqit;if(typeof jQuery==='undefined'){jqit=d.createElement('script');jqit.type='text/javascript';jqit.src='https://cdn.jsdelivr.net/jquery/1.12.3/jquery.min.js';head.appendChild(jqit);}_my_script.type='text/javascript';_my_script.src='https://rawgit.com/lewisje/font-friend/master/font-friend.js';head.appendChild(_my_script);})(document);
```

**[Fount](http://fount.artequalswork.com/):** Identify webfonts on any site.

```javascript
javascript:(function(d){'use strict';if(!d.getElementById('fountscripton')&&!d.getElementById('fountscript')){var founts=d.createElement('script');founts.src='http://fount.artequalswork.com/fount.js';founts.id='fountscript';(d.body||d.getElementsByTagName('body')[0]).appendChild(founts);}else fountReset(false);})(document);
```

**[Flippant](http://flippant.artequalswork.com/):** View any site from all angles.

```javascript
javascript:(function(d){'use strict';if(!d.getElementById('flippantscript')){var flipscript=d.createElement('script');flipscript.src='http://flippant.artequalswork.com/flippant.js';flipscript.id='flippantscript';(d.body||d.getElementsByTagName('body')[0]).appendChild(flipscript);}else flippant();})(document);
```

**[MIN](http://min.artequalswork.com/):** Basic looks at type and layout.

```javascript
javascript:(function(d){'use strict';if(!d.getElementById('minscript')){var minscript=d.createElement('script');minscript.src='http://min.artequalswork.com/min.js';minscript.id='minscript';(d.body||d.getElementsByTagName('body')[0]).appendChild(minscript);}else m();})(document);
```

**[WebFontPicker](https://github.com/danielgavrilov/WebFontPicker):** A bookmarklet that helps preview Google Web Fonts live on any website.

```javascript
javascript:(function(w,d){'use strict';var t=w.WFP=w.WFP||{},e='https:'===w.location.protocol?'https:':'http:';t.bookmarklet=3,t.Picker&&t.Picker.show(),t.attached||t.Picker||((function(t){var e=d.createElement('link');e.rel='stylesheet',e.type='text/css',e.href=t,(d.head||d.getElementsByTagName('head')[0]).appendChild(e)})(e+'//gavrilov.co.uk/wfp/WFP.css'),(function(t){var e=d.createElement('script');e.type='text/javascript',e.src=t,(d.head||d.getElementsByTagName('head')[0]).appendChild(e)})(e+'//gavrilov.co.uk/wfp/WFP.full.min.js'),t.attached=!0)})(window,document);
```

**[WhatFont](https://github.com/chengyin/WhatFont-Bookmarklet):** WhatFont is a JavaScript script to detect what font in the stack is being used on any elements of a web page.

```javascript
javascript:(function(d){'use strict';var s=d.createElement('script'),b=(d.body||d.getElementsByTagName('body')[0]),l=d.location;s.setAttribute('src','http://chengyinliu.com/wf.js?o='+encodeURIComponent(l.href)+'&t='+(new Date().getTime()));b.appendChild(s)})(document);
```

## Performance
**[CriticalCSS](https://gist.github.com/PaulKinlan/6284142):** CriticalCSS Bookmarklet and Devtool Snippet.js

```javascript
javascript:(function(win,doc){'use strict';function CSSCriticalPath(w,d,opts){var opt=opts||{},css={},splitRegex=/;(?![A-Za-z0-9])/;function pushCSS(r){if(!css[r.selectorText])css[r.selectorText]={};var styles=r.style.cssText.split(splitRegex);for(var i=0;i<styles.length;i++){if(!styles[i])continue;var pair=styles[i].split(': ');pair[0]=pair[0].trim();pair[1]=pair[1].trim();css[r.selectorText][pair[0]]=pair[1];}}function parseTree(){var height=w.innerHeight,walker=d.createTreeWalker(d,NodeFilter.SHOW_ELEMENT,function(node){return NodeFilter.FILTER_ACCEPT;},true);while(walker.nextNode()){var node=walker.currentNode,rect=node.getBoundingClientRect();if(rect.top<height||opt.scanFullPage){var rules=w.getMatchedCSSRules(node);if(!!rules)for(var r=0;r<rules.length;r++)pushCSS(rules[r]);}}}this.generateCSS=function(){var finalCSS='';for(var k in css)if(css.hasOwnProperty(k)){finalCSS+=k+' { ';for (var j in css[k])if(css[k].hasOwnProperty(j))finalCSS+=j+': '+css[k][j]+';';finalCSS+='}\n';}return finalCSS;};parseTree();}var cp=new CSSCriticalPath(win,doc),css=cp.generateCSS();console.log(css);return false;})(this,document);
```

**[ CSS Stress Test](https://github.com/andyedinborough/stress-css):** This project is a bookmarklet for stress testing the CSS on any given webpage.
It indexes all the elements and their classes, and then--class by class--it removes one, and times how long it takes to scroll the page. Selectors that save a considerable amount of time when removed indicate problem areas.

```javascript
javascript:(function(d){'use strict';var s=d.createElement('script');function doit(){if(typeof stressTest!=='undefined')stressTest.bookmarklet();else setTimeout(doit,100);}s.src='https://rawgit.com/andyedinborough/stress-css/master/stressTest.js?_='+Math.random();(d.head||d.getElementsByTagName('head')[0]).appendChild(s);doit();})(document);
```

**[pagespeedThis](https://github.com/kimblim/pagespeedThis):** A very simple bookmarklet that analyses the pagespeed of the current page in the browser

```javascript
javascript:window.location='https://developers.google.com/speed/pagespeed/insights/?url='+encodeURI(window.location);
```

**[perfmap](https://github.com/zeman/perfmap):** A bookmarklet to create a front-end performance heatmap of resources loaded in the browser using the Resource Timing API. A browser with support for the Resource Timing API is required.

```javascript
javascript:(function(d){var el=d.createElement('script');el.src='https://zeman.github.io/perfmap/perfmap.js';(d.body||d.getElementsByTagName('body')[0]).appendChild(el);})(document);
```

**[Performance-Bookmarklet](https://github.com/micmro/performance-bookmarklet):** Bookmarklet to analyze the current page through the Resource Timing API, Navigation Timing API and User-Timing - requests by type, domain, load times, marks and more - sort of a light live WebPageTest.

```javascript
javascript:(function(d){var l='https://micmro.github.io/performance-bookmarklet/dist/performanceBookmarklet.min.js',el=d.createElement('script');el.type='text/javascript';el.src=l;el.onerror=function(){alert('Looks like the Content Security Policy directive is blocking the use of bookmarklets\n\nYou can copy and paste the content of\n\n"+l+"\n\ninto your console instead\n\n(link is in console already)');console.log(l);};(d.body||d.getElementsByTagName('body')[0]).appendChild(el);})(document);
```

**[stats.js](https://github.com/mrdoob/stats.js):** This class provides a simple info box that will help you monitor your code performance. FPS Frames rendered in the last second. The higher the number the better. MS Milliseconds needed to render a frame. The lower the number the better.

```javascript
javascript:(function(d){'use strict';var raf=typeof requestAnimationFrame==='function'?requestAnimationFrame:function(f){return setTimeout(f,15);},s=d.createElement('script');s.onload=function(){var s=new Stats();function loop(){s.update();raf(loop)}s.domElement.style.cssText='position:fixed;left:0;top:0;z-index:10000';(d.body||d.getElementsByTagName('body')[0]).appendChild(s.domElement);raf(loop);};s.src='https://rawgit.com/mrdoob/stats.js/master/build/stats.min.js';(d.head||d.getElementsByTagName('head')[0]).appendChild(s);})(document);
```

**[timing.js](https://github.com/addyosmani/timing.js):** Timing.js is a small set of helpers for working with the Navigation Timing API to identify where your application is spending its time. Useful as a standalone script, DevTools Snippet or bookmarklet.

```javascript
javascript:(function(w){'use strict';w.timing=w.timing||{getTimes:function(opt){var p=w.performance||w.webkitPerformance||w.msPerformance||w.mozPerformance;if(!p){console.log('Unfortunately, your browser does not support the Navigation Timing API');return;}var timing=p.timing,api={},o=opt||{},k,f;if(timing){if(o&&!o.simple)for(k in timing)if(timing.hasOwnProperty(k))api[k]=timing[k];if(null==api.firstPaint){f=0;if(w.chrome&&w.chrome.loadTimes){f=w.chrome.loadTimes().firstPaintTime*1e3;api.firstPaintTime=f-w.chrome.loadTimes().startLoadTime*1e3;}else if(typeof p.timing.msFirstPaint==='number'){f=p.timing.msFirstPaint;api.firstPaintTime=f-p.timing.navigationStart;}if(o&&!o.simple)api.firstPaint=f}api.loadTime=timing.loadEventEnd-timing.navigationStart;api.domReadyTime=timing.domComplete-timing.domInteractive;api.readyStart=timing.fetchStart-timing.navigationStart;api.redirectTime=timing.redirectEnd-timing.redirectStart;api.appcacheTime=timing.domainLookupStart-timing.fetchStart;api.unloadEventTime=timing.unloadEventEnd-timing.unloadEventStart;api.lookupDomainTime=timing.domainLookupEnd-timing.domainLookupStart;api.connectTime=timing.connectEnd-timing.connectStart;api.requestTime=timing.responseEnd-timing.requestStart;api.initDomTreeTime=timing.domInteractive-timing.responseEnd;api.loadEventTime=timing.loadEventEnd-timing.loadEventStart;}return api;},printTable:function(opts){var table={},data=this.getTimes(opts);Object.keys(data).sort().forEach(function(k){table[k]={ms:data[k],s:+(data[k]/1e3).toFixed(2)};});console.table(table)},printSimpleTable:function(){this.printTable({simple:true});}};return w.timing.printSimpleTable();})(this);
```

**[YSLOW](http://yslow.org/):** YSlow analyzes web pages and why they're slow based on Yahoo!'s rules for high performance web sites

```javascript
javascript:(function(y){'use strict';var b=y.body||y.getElementsByTagName('body')[0],p=b.appendChild(y.createElement('iframe')),o=p.contentWindow.document;p.id='YSLOW-bookmarklet';p.style.cssText='display:none';o.open().write('<head></head><body onload="YUI_config={win:window.parent,doc:window.parent.document};var d=document;(d.head||d.getElementsByTagName(\'head\')[0]).appendChild(d.createElement(\'script\')).src=\'http://yslow.org/yslow-bookmarklet.js\'"></body>');o.close();})(document);
```

## Search Engine Optimization
**[OuiSEO](https://github.com/carlsednaoui/seo-bookmarklet):** An open-source bookmarklet that shows you on-page SEO and social metadata information.

```javascript
javascript:(function(d){if(typeof ouiseo==='undefined'){var jsCode=d.createElement('script');jsCode.setAttribute('src','https://carlsednaoui.s3.amazonaws.com/ouiseo/ouiseo.min.js');(d.body||d.getElementsByTagName('body')[0]).appendChild(jsCode);}else if(ouiseo&&!d.getElementById('ouiseo')){ouiseo();}else console.log('OuiSEO is already open');})(document);
```

**[SEO Bookmarklet](http://twkm.ca/projects/seo-bookmarklet):** A One-Stop SEO Bookmarklet to Quickly Review On-Site SEO

```javascript
javascript:(function(d){'use strict';var da=new Date(),b=d.body||d.getElementsByTagName('body')[0],ex=d.getElementById('twkmSEOScript'),z;try{if(!b)throw new ReferenceError('The body has not loaded yet.');if(!ex){z=d.createElement('script');z.setAttribute('src','https://twkm.ca/min/f=gadgets/resources/seo-bookmarklet/seo-stable.js?ts='+da.getTime());z.setAttribute('id','twkmSEOScript');z.setAttribute('class','03');b.appendChild(z);}else twkm_closeThisBox();}catch(_){console.log(_.message);}})(document);
```

Beta Version

```javascript
javascript:(function(d){'use strict';var da=new Date(),b=d.body||d.getElementsByTagName('body')[0],ex=d.getElementById('twkmSEOScript'),z;try{if(!b)throw new ReferenceError('The body has not loaded yet.');if(!ex){z=d.createElement('script');z.setAttribute('src','https://twkm.ca/min/f=gadgets/resources/seo-bookmarklet/seo-latest.js?ts='+da.getTime());z.setAttribute('id','twkmSEOScript');z.setAttribute('class','03');b.appendChild(z);}else twkm_closeThisBox();}catch(_){console.log(_.message);}})(document);
```

## Miscellaneous
**[ThemeForest Live Preview](https://gist.github.com/ozgrozer/91e8b759a1aaff39d9d5#file-themeforestlivepreview-js):**

```javascript
javascript:(function(d){'use strict';var u=d.URL,a=d.createElement('a'),v=['themeforest.net','www.themeforest.net'],l,s;a.href=u;if(v.indexOf(a.hostname)!==-1){l=d.getElementsByClassName('btn-icon live-preview')[0].href;s=document.createElement('script');s.src='https://akillidergi.com/app/themeforest/findNextURL.js?url='+encodeURIComponent(l);if(!(d.head||d.getElementsByTagName('head')[0]).appendChild(s))console.warn("Script tag couldn't be created!");}else console.error('This bookmarklet only runs on Themeforest pages.');})(document);
```

**[Get v.redd.it links!](https://www.vrddit.com/bookmarklet)**

```javascript
javascript:(function(d){'use strict';function S(u){var s=d.createElement('script');s.src=u;d.head.appendChild(s)}function b(s){var t=d.createElement('textarea');t.value=s;d.body.appendChild(t);t.select();d.execCommand('copy');d.body.removeChild(t)}function F(u){var p=u.indexOf('r/');if(-1!==p)return 'https://www.reddit.com/'+u.substring(p,u.length)}function c(u){return u.split('/').slice(0,-2).join('/').replace('reddit.com/r','vrddit.com/r')}function V(u){var r=new XMLHttpRequest();u=F(u);r.open('GET',u+'/.json',true);r.onload=function(){var a,p,t,v,i,C,D,R;try{a=JSON.parse(r.responseText)}catch(_){return swal({title:'Error',text:'Video request failed',type:'error',showCloseButton:true,showConfirmButton:false})}if(r.status>=200&&r.status<400){try{p=a[0].data.children[0].data;if(p.crosspost_parent_list)V(p.crosspost_parent_list[0].permalink);else{t=p.title;v=p.media.reddit_video;i=p.id;if(v){C=c(u);D=v.fallback_url;R='https://www.reddit.com/mediaembed/'+i;swal({title:'<strong>Links for this v.redd.it video</strong>',html:'<style>.vrdditBtn{display:inline-block;padding:3px 12px;font-size:14px;font-weight:400;line-height:1.42857143;text-align:center;white-space:nowrap;vertical-align:middle;cursor:pointer;-webkit-user-select:none;-moz-user-select:none;-ms-user-select:none;user-select:none;background-image:none;border:1px solid transparent;color:#fff;background-color:#28a745;border-color:#28a745;border-radius:3px}</style><label for="custom-input" style="display:block;margin:5px auto">Custom Player</label><a href="'+C+'" target="_blank"><input name="custom-input" value="'+C+'" style="display:block;width:100%;text-align:center;margin:5px auto;color:blue;text-decoration:underline;cursor:pointer"></a><input id="btnCustomPlyr" class="vrdditBtn" type="button" style="display:block;margin:5px auto 10px auto" value="Copy"><label for="reddit-input" style="display:block;margin:5px auto">Reddit Player</label><a href="'+R+'" target="_blank"><input name="reddit-input" value="'+R+'" style="display:block;width:100%;text-align:center;margin:5px auto;color:blue;text-decoration:underline;cursor:pointer"></a><input id="btnRedditPlyr" class="vrdditBtn" type="button" style="display:block;margin:5px auto 10px auto" value="Copy"><label for="direct-input" style="display:block;margin:5px auto">Direct (No Sound)</label><a href="'+D+'" target="_blank"><input name="direct-input" value="'+D+'" style="display:block;width:100%;text-align:center;margin:5px auto;color:blue;text-decoration:underline;cursor:pointer"></a><input id="btnDirectPlyr" class="vrdditBtn" type="button" style="display:block;margin:5px auto 10px auto" value="Copy">',showCloseButton:true,showConfirmButton:false});d.addEventListener('click',function(e){var l=e.target;if('btnCustomPlyr'===l.id)b(C);else if('btnRedditPlyr'===l.id)b(R);else if('btnDirectPlyr'===l.id)b(D)})}}}catch(_){swal({title:'Error',text:"URL doesn't have a v.redd.it video",type:'error',showCloseButton:true,showConfirmButton:false})}}else swal({title:a.error,text:a.message,type:'error',showCloseButton:true,showConfirmButton:false})};r.onerror=function(){var e='Video request failed';if(navigator.userAgent.toLowerCase().indexOf('firefox')>-1)e=" (Possibly blocked by Firefox's Tracking Protection)";swal({title:'Error',text:e,type:'error',showCloseButton:true,showConfirmButton:false})};r.send()}S('https://www.vrddit.com/sweetalert2/sweetalert2.all.min.js');var u=location.href;if(u)V(u);else swal({title:'Error',text:'URL not found',type:'error',showCloseButton:true,showConfirmButton:false})})(document)
```

**[Instantgram](https://theus.github.io/instantgram/)**

```javascript
javascript:(function(y,h,v,o,i,s,_,d,u,l,g){"use strict";!function(a){var n={};function r(e){if(n[e])return n[e].exports;var t=n[e]={i:e,l:!1,exports:{}};return a[e].call(t.exports,t,t.exports,r),t.l=!0,t.exports}r.m=a,r.c=n,r.d=function(e,t,a){r.o(e,t)||s(e,t,{enumerable:!0,get:a})},r.r=function(e){"undefined"!=typeof Symbol&&Symbol.toStringTag&&s(e,Symbol.toStringTag,{value:"Module"}),s(e,"__esModule",{value:!0})},r.t=function(t,e){if(1&e&&(t=r(t)),8&e)return t;if(4&e&&"object"==typeof t&&t&&t.__esModule)return t;var a=o.create(null);if(r.r(a),s(a,"default",{enumerable:!0,value:t}),2&e&&"string"!=typeof t)for(var n in t)r.d(a,n,function(e){return t[e]}.bind(null,n));return a},r.n=function(e){var t=e&&e.__esModule?function(){return e.default}:function(){return e};return r.d(t,"a",t),t},r.o=function(e,t){return i.hasOwnProperty.call(e,t)},r.p="",r(r.s=4)}([function(e,t,a){s(t,"__esModule",{value:!0}),t.default=function(e,t){t=t||y||h.documentElement;var a=e.getBoundingClientRect();return 0<a.bottom&&0<a.right&&a.left<(t.innerWidth||t.clientWidth)&&a.top<(t.innerHeight||t.clientHeight)}},function(e,t,a){s(t,"__esModule",{value:!0}),t.default=function(e){var t=[];for(t.push(e);e.parentNode;)t.unshift(e.parentNode),e=e.parentNode;return t}},function(e,t,a){s(t,"__esModule",{value:!0});var n,r=(n=a(5))&&n.__esModule?n:{default:n},o={de:"de-DE",pt:"pt-BR",en:"en-US","en-GB":"en-US"}[navigator.language];function i(t){var a=1<arguments.length&&void 0!==arguments[1]?arguments[1]:o;try{if(r.default.langs.hasOwnProperty(a)||(a="en-US"),r.default.langs[a][t])return r.default.langs[a][t]}catch(e){return _.error("[instantgram]LOC error:",e),"oops, an error ocurred in the localization system. Enter in https://github.com/theus/instantgram/issues/new and open an issue with this code: 'LOC_dont_found_str_neither_default:["+a+"->"+t+"]'\n  for more information open the console"}}_.info(i("helpers.localize_defaultlang").replace("${LANG_DEFAULT}",o)),t.default=i},function(e,t,a){s(t,"__esModule",{value:!0}),t.default=function(e,t,a){for(;0<e.length;0)t.call(a,0,e[0])}},function(e,t,a){var n=c(a(2)),r=c(a(6)),o=c(a(3)),i=c(a(0)),s=c(a(7)),d=c(a(8)),u=c(a(9)),l=c(a(10)),g=c(a(12)),m=c(a(13));function c(e){return e&&e.__esModule?e:{default:e}}var f={VERSION:"3.0.0",hostname:v.hostname,path:v.pathname,images:[],imagesOnViewPort:[],videos:h.querySelectorAll("video"),regexOriginalImage:/\/[a-z] \d [a-z]?x\d [a-z]?/,regexMaxResImage:/\/[a-z] [1080] [a-z]?x[1080] [a-z]?/,regexPath:/^\/p\//,regexHostname:/instagram\.com/,regexStoriesURI:/stories\/(.*) /,regexURL:/([--:\w?@%& ~#=]*\.[a-z]{2,4}\/{0,2})((?:[?&](?:\w )=(?:\w )) |[--:\w?@%& ~#=] )?/,foundByModule:null,probablyHasAGallery:{check:null,byModule:""},setImageLink:function(e){this.imageLinkBeforeParse=e,this.regexMaxResImage.test(e)?this.imageLink=e:this.imageLink=this.regexOriginalImage.test(e)?e.replace(this.regexOriginalImage,""):e},foundVideo:!1,foundImage:!1,imageLink:!1,imageLinkBeforeParse:!1,alertNotInInstagramPost:!1,context:{hasMsg:!1,msg:""}},p=h.images;(0,o.default)(p,function(e,t){((0,s.default)(t)||2===p.length)&&(f.images.push(t),(0,i.default)(t)&&f.imagesOnViewPort.push(t))}),f.regexHostname.test(f.hostname)||alert((0,n.default)("index@alert_onlyWorks")),f.regexHostname.test(f.hostname)&&(!1===(0,m.default)(f)&&!1===(0,g.default)(f)&&!1===(0,u.default)(f)&&!1===(0,d.default)(f)&&!1===(0,l.default)(f)&&(f.context.hasMsg=!1),f.context.hasMsg&&alert((0,n.default)(f.context.msg)),!f.alertNotInInstagramPost||f.foundVideo||f.foundImage||alert((0,n.default)("index#program@alert_dontFound")),(0,r.default)(f.VERSION))},function(e,t,a){s(t,"__esModule",{value:!0}),t.default={langs:{"en-US":{"helpers.localize_defaultlang":"[instantgram] set language: ${LANG_DEFAULT}\n For more information about available languages please check http://theus.github.io/instantgram","modules.update@oudated_outdated":"[instantgram] is outdated. Please check http://theus.github.io/instantgram for available updates.","modules.update@oudated_localInfo":"[instantgram] Installed version: ${data.version} | New update: ${data.gitVersion}","modules.update@determineIfGetUpdateIsNecessary_contacting":"[instantgram] is looking for available updates…","modules.update@determineIfGetUpdateIsNecessary_updated":"[instantgram] updated your current version.","modules.update@determineIfGetUpdateIsNecessary_@alert_found":'[instantgram] found a new available update.\nPlease check <a href="http://theus.github.io/instantgram" rel="noopener noreferrer nofollow" target="_blank">http://theus.github.io/instantgram</a> to install it.',"index@alert_onlyWorks":"[instantgram] only works on instagram.com.","index#program#modal@alert_dontFound":"[instantgram] didn't find any image in this Instagram post. Please try to open the link in a new tab.","index#program#post@alert_dontFound":"Oops, [instantgram] couldn't find any image :-(","index#program#screen@alert_dontFound":"[instantgram] found more than 1 image. Are you on a profile page? If yes, please open a single post first and open [instantgram] again.","index#program@alert_dontFound":"Oops, did you open any Instagram post? Like for example instagram.com/p/82jd828jd","index#program@alert_videoBlob":"If you're trying open a video, try enter on Instagram post page. Like for example instagram.com/p/82jd828jd. If you're already in it, try refreshing the page before running [instantgram] or open the post in a new tab. (this proccess is neccessary only for videos)"},"pt-BR":{"helpers.localize_defaultlang":"[instantgram] idioma configurado: ${LANG_DEFAULT}\npara mais informações sobre os idiomas suportados, acesse http://theus.github.io/instantgram","modules.update@oudated_outdated":"[instantgram] está desatualizado. Acesse http://theus.github.io/instantgram para atualizar","modules.update@oudated_localInfo":"[instantgram] versão local: ${data.version} | nova versão: ${data.gitVersion}","modules.update@determineIfGetUpdateIsNecessary_contacting":"[instantgram] está procurando atualizações...","modules.update@determineIfGetUpdateIsNecessary_updated":"[instantgram] informações locais atualizadas","modules.update@determineIfGetUpdateIsNecessary_@alert_found":"[instantgram] encontrou uma atualização.\n acesse theus.github.io/instantgram para atualizar","index@alert_onlyWorks":"[instantgram] somente funciona no instagram.com","index#program#modal@alert_dontFound":"[instantgram] não encontrou uma imagem em um post. Tente abrir o link em uma nova aba.","index#program#post@alert_dontFound":"oops, [instantgram] não encontrou a imagem :-(","index#program#screen@alert_dontFound":"[instantgram] a procura por imagem na tela encontrou mais de 1 imagem. Você está em um perfil? Se sim, abra alguma imagem antes de rodar o [instantgram]","index#program@alert_dontFound":"oops, você está em algum post do instagram? ex: instagram.com/p/82jd828jd","index#program@alert_videoBlob":"Se você está tentando abrir um vídeo, tente entrar na página do post do Instagram. ex: instagram.com/p/82jd828jd. Se você já está na página, tente atualizar a página antes de executar o [instantgram] ou abra o post em uma nova aba. (este processo só é necessário com vídeos)"},"de-DE":{"helpers.localize_defaultlang":"Ausgewählte Sprache: ${LANG_DEFAULT}\n Weitere Informationen zu den unterstützten Sprachen findest du auf http://theus.github.io/instantgram","modules.update@oudated_outdated":"[instantgram] ist veraltet. Bitte besuche die Seite http://theus.github.io/instantgram für ein Update.","modules.update@oudated_localInfo":"[instantgram] Installierte Version ${data.version} | Neue Version: ${data.gitVersion}","modules.update@determineIfGetUpdateIsNecessary_contacting":"[instantgram] sucht nach neuen verfügbaren Updates...","modules.update@determineIfGetUpdateIsNecessary_updated":"[instantgram] wurde aktualisiert.","modules.update@determineIfGetUpdateIsNecessary_@alert_found":"[instantgram] hat ein neues Update gefunden.\nBitte besuche die Seite http://theus.github.io/instantgram, um das Update zu installieren.","index@alert_onlyWorks":"[instantgram] funktioniert nur mit instagram.com.","index#program#modal@alert_dontFound":"[instantgram] konnte kein Bild in diesem Post finden. Bitte öffne den Link in einem neuen Tab.","index#program#post@alert_dontFound":"Oops, [instantgram] konnte leider kein Bild finden  :-(","index#program#screen@alert_dontFound":"[instantgram] hat mehr als 1 Bild gefunden. Bist du in der Profilansicht? Falls ja, öffne bitte zuerst einen einzelnen Post und führe [instantgram] erneut aus.","index#program@alert_dontFound":"Oops, hast du einen Instagram Post geöffnet? Zum Beispiel instagram.com/p/82jd828jd","index#program@alert_videoBlob":"If you're trying open a video, try enter on Instagram post page. Like for example instagram.com/p/82jd828jd. If you're already in it, try refreshing the page before running [instantgram] or open the post in a new tab. (this proccess is neccessary only for videos) // we need translate this string to Deutsch, if you can help us enter in contact by Github"}}}},function(e,t,a){s(t,"__esModule",{value:!0});var n,o=(n=a(2))&&n.__esModule?n:{default:n};function i(e){_.warn((0,o.default)("modules.update@oudated_outdated")),_.warn((0,o.default)("modules.update@oudated_localInfo").replace("${data.version}",e.version).replace("${data.gitVersion}",e.gitVersion))}t.default=function(n){var e,r=n.replace(/\./g,"");if(r=g(r),!(e=l.getItem("instantgram"))||((e=d.parse(e)).version!==e.gitVersion&&i(e),u.now()>e.dateExpiration)){var t=new XMLHttpRequest;t.addEventListener("readystatechange",function(){if(_.info((0,o.default)("modules.update@determineIfGetUpdateIsNecessary_contacting")),4===this.readyState){var e=new Date;e.setDate(e.getDate()+2),l.setItem("instantgram",d.stringify({version:n,gitVersion:d.parse(this.responseText).version,lastVerification:u.now(),dateExpiration:e.valueOf()}));var t=d.parse(this.responseText).version;if(t=t.replace(/\./g,""),t=g(t),_.info((0,o.default)("modules.update@determineIfGetUpdateIsNecessary_updated")),r<t){var a=d.parse(l.getItem("instantgram"));alert((0,o.default)("modules.update@determineIfGetUpdateIsNecessary_@alert_found")),i(a)}else _.info(l.getItem("instantgram"))}}),t.open("GET","https://theus.github.io/instantgram/package.json"),t.send()}}},function(e,t,a){s(t,"__esModule",{value:!0}),t.default=function(e){return 0<(0,r.default)(e).filter(function(e){return"article"===e.nodeName.toLowerCase()}).length};var n,r=(n=a(1))&&n.__esModule?n:{default:n}},function(e,t,a){s(t,"__esModule",{value:!0}),t.default=function(e){var t=!1,a=2<e.images.length;if(a&&e.regexPath.test(e.path)&&(e.probablyHasAGallery.check=a,e.probablyHasAGallery.byModule="searchImage"),e.regexPath.test(e.path)&&!e.imageLink&!1===a){if(!e.foundVideo&&!e.foundImage){try{if(2===h.getElementsByTagName("article").length){var n=h.getElementsByTagName("article")[1].querySelector("header + div img").src;n?(e.setImageLink(n),y.open(e.imageLink),t=!0,e.foundByModule="searchImage"):e.context={hasMsg:!0,msg:"index#program#modal@alert_dontFound"}}}catch(t){_.error("searchImage()","[instantgram] "+e.VERSION,t)}try{if(1===h.getElementsByTagName("article").length){var r=h.querySelector("article > div img").src;e.setImageLink(r),e.imageLink?(y.open(e.imageLink),t=!0,e.foundByModule="searchImage"):e.context={hasMsg:!0,msg:"index#program#post@alert_dontFound"}}}catch(t){_.error("searchImage()","[instantgram] "+e.VERSION,t)}}}else e.alertNotInInstagramPost=!0;return t}},function(e,t,a){s(t,"__esModule",{value:!0}),t.default=function(e){var t=!1;try{e:{var a=!0,n=!1,r=void 0;try{for(var o,i=e.videos[Symbol.iterator]();!(a=(o=i.next()).done);a=!0){var s=o.value;if((0,u.default)(s)){var d=s.src;if(d){if(-1!==d.indexOf("blob:")){e.context={hasMsg:!0,msg:"index#program@alert_videoBlob"};break e}y.open(d),t=!0,e.foundVideo=!0,e.foundByModule="searchVideoOnScreen",e.alertNotInInstagramPost=!0}break e}}}catch(e){n=!0,r=e}finally{try{!a&&i.return&&i.return()}finally{if(n)throw r}}}}catch(t){_.error("searchVideoOnScreen()","[instantgram] "+e.VERSION,t)}return t};var n,u=(n=a(0))&&n.__esModule?n:{default:n}},function(e,t,a){s(t,"__esModule",{value:!0}),t.default=function(e){var t=!1;try{if(!e.imageLink&&!e.foundVideo)e:{e.images.reverse();var a=!0,n=!1,r=void 0;try{for(var o,i=e.images[Symbol.iterator]();!(a=(o=i.next()).done);a=!0){var s=o.value;if((0,f.default)(s)&&!(0,h.default)(s)){var d=0<(0,p.default)(s).filter(function(e){return"ul"===e.nodeName.toLowerCase()}).length;if(d){e.probablyHasAGallery.check=d,e.probablyHasAGallery.byModule="searchImageOnScreen";var u=(0,p.default)(s).filter(function(e){return e.style&&e.style.transform&&""!==e.style.transform})[0],l=u.querySelector("ul"),g=u.style.transform.split("(")[1].replace("px)","")/s.width,m=g<0?-1*g:g,c=l.children[m].querySelector("img");e.setImageLink(c.src)}else e.setImageLink(s.src);e.imageLink?(y.open(e.imageLink),t=e.foundImage=!0,e.foundByModule="searchImageOnScreen"):e.context={hasMsg:!0,msg:"index#program#screen@alert_dontFound"},e.alertNotInInstagramPost=!1;break e}}}catch(e){n=!0,r=e}finally{try{!a&&i.return&&i.return()}finally{if(n)throw r}}}}catch(t){_.error("searchImageOnScreen()","[instantgram] "+e.VERSION,t)}return t};var f=n(a(0)),p=n(a(1)),h=n(a(11));function n(e){return e&&e.__esModule?e:{default:e}}},function(e,t,a){s(t,"__esModule",{value:!0}),t.default=function(e){return"a"===e.parentElement.localName||0<(0,r.default)(e).filter(function(e){return"header"===e.nodeName.toLowerCase()}).length};var n,r=(n=a(1))&&n.__esModule?n:{default:n}},function(e,t,a){s(t,"__esModule",{value:!0}),t.default=function(n){var e=!1;try{if(n.regexStoriesURI.test(n.path)){var t=h.getElementById("react-root").querySelectorAll("section section div"),r="";if((0,o.default)(t,function(e,t){var a=t.style.backgroundImage.match(n.regexURL);null!==a&&(r=a[0])}),0<r.length&&(n.setImageLink(r),y.open(n.imageLink),e=!0,n.foundImage=!0,n.foundByModule="searchStories"),!1===e&&0<n.videos.length){var a=n.videos[0].src;!a&&n.videos[0].children&&(a=n.videos[0].children[0].src),a&&(y.open(a),e=!0,n.foundVideo=!0,n.alertNotInInstagramPost=!0,n.foundByModule="searchStories")}}}catch(e){_.error("searchStories()","[instantgram] "+n.VERSION,e)}return e};var n,o=(n=a(3))&&n.__esModule?n:{default:n}},function(e,t,a){s(t,"__esModule",{value:!0}),t.default=function(e){var t=!1;try{if(!e.imageLink&&!e.foundVideo){var a=h.querySelector('[property="og:video"]')?h.querySelector('[property="og:video"]'):h.querySelector('[property="og:video:secure_url"]')?h.querySelector('[property="og:video:secure_url"]'):null,n=!!a&&a.content;n&&(y.open(n),t=!0,e.foundVideo=!0,e.alertNotInInstagramPost=!0)}}catch(e){_.error("getVideoOnPage()","[instantgram] 3.0.0",e)}return t}}])})(window,document,location,Object,Object.prototype,Object.defineProperty,console,JSON,Date,localStorage,parseInt)
```
