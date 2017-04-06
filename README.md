# Front End Web Development Quiz Answers
Front End Web Development Quiz: http://davidshariff.com/quiz/

CSS Part:
- Does css properties are case sensitive? Answer: False
- Does margin-top or margin-bottom has effect on inline element? Answer: False
- Does padding-top or padding-bottom has effect on inline element? Answer: False
- If you have a paragraph tag element with font-size: 10rem, will the text be responsive when the user resizes / drags the browser window? Answer: False
- The pseudo class :checked will select inputs with type radio or checkbox, but not elements. Answer: False
- In a HTML document, the pseudo class :root always refers to the element. Answer: True
- The translate() function can move the position of an element on the z-axis. Answer: False
- Given the HTML below:
   ```
   <ul class="shopping-list" id="awesome">
      <li><span>Milk</span></li>
      <li class="favorite" id="must-buy"><span class="highlight">Sausage</span></li>
   </ul>
   ```
   What is the color of the text Sausage ?
   ```
   ul.shopping-list li .highlight {
       color: red;
   }
   ul.shopping-list li .highlight:nth-of-type(odd) {
       color: blue;
   }
   ```
   Answer: Blue

   The :nth-of-type(odd) selector matches every element that is the odd child, of a particular type, of its parent.
   highlight class only show up once, and ul.shopping-list li .highlight:nth-of-type(odd) has high specificity

- Given the HTML below:
   ```
   <ul class="shopping-list" id="awesome">
      <li><span>Milk</span></li>
      <li class="favorite" id="must-buy"><span class="highlight">Sausage</span></li>
   </ul>
   ```
   What is the color of the text Sausage ?
   ```
   #awesome .favorite:not(#awesome) .highlight {
       color: red;
   }
   #awesome .highlight:nth-of-type(1):nth-last-of-type(1) {
       color: blue;
   }
   ```
   Answer: Red

   The .favorite:not(#awesome) selector matches favorite class that is NOT id awesome.
   And it only has one hightlight class, so .highlight:nth-of-type(1):nth-last-of-type(1) is itself.
   However, the first css style has one id and two classes, and the second has same id and only one, so the first one has higher specificity.

   In CSS, more specific selectors override less specific ones regardless of order, so your text is red.

- Are unused style resources still downloaded by the browser?
   HTML:
   ```
   <div id="test1">
      <span id="test2"></span>
   </div>
   ```
   CSS:
   ```
   #i-am-useless {
       background-image: url('mypic.jpg');
   }
   ```
   Answer: No
   This is depend on each browser. Almost all browsers do not download unrequired images. 

- On page load, will mypic.jpg get downloaded by the browser?
   HTML:
   ```
   <div id="test1">
      <span id="test2"></span>
   </div>
   ```
   CSS:
   ```
   #test1 {
       display: none;
   }
   #test2 {
       background-image: url('mypic.jpg');
       visibility: hidden;
   }
   ```
   Answer: Yes

   The image still has been downloaded, and hidden.
   
- Does HTML5 support block-level links?
   HTML:
   ```
   <article>
      <a href="#">
          <h1>Hello</h1>
          <p>I am some text</p>
      </a>
   </article>
   ```
   Answer：Yes
   
- Does the HTML below trigger a http request when the page first loads ?
  HTML:
   ```
   <img src="mypic.jpg" style="visibility: hidden" alt="My picture">
   ```
   Answer: Yes 
   
   It will trigger a http request above, even though you use display:none or visibility:hidden. 
   
- Does the HTML below trigger a http request when the page first loads?
   HTML:
   ```   
   <div style="display: none;">
      <img src="mypic.jpg" alt="My photo">
   </div>
   ```
   Answer: Yes 
   
   It will trigger a http request above, even though you use display:none or visibility:hidden. 
   
- Does main1.css have to be downloaded and parsed before main2.css can be fetched?
   
   HTML:
   ```
   <head>
      <link href="main1.css" rel="stylesheet">
      <link href="main2.css" rel="stylesheet">
   </head>
   ```
   Answer: No
   
   CSS files are downloaded in parallel, which means both files are downloaded at the same time.
   
- Does main2.css have to be downloaded and parsed before Paragraph 1 is rendered
   HTML:
   ```
   <head>
      <link href="main1.css" rel="stylesheet">
   </head>
   <body>
      <p>Paragraph 1</p>
      <p>Paragraph 2</p>
      <link href="main2.css" rel="stylesheet">
   </body>
   ```
   
   Answer: No
   
   Since style1.css is in head, it will be downloaded before the page loads. After the page has rendered, it will download style2.css file. When it is finished, the style2.css will style the page.
   
- What is the order of values alerted?  
   ```
   var x = 3;

   var foo = {
       x: 2,
       baz: {
           x: 1,
           bar: function() {
               return this.x;
           }
       }
   }

   var go = foo.baz.bar;

   alert(go());
   alert(foo.baz.bar());
   ```
   Answer: 3，1
   
   Javascript scope. 

   The scope of go is window object. 
   ```
   var go = function() {
   rerurn this.x;
   }
   ```
   It is window.x, which is equal to 3.

   foo.baz.bar(), we should check the scope of foo.baz, foo.baz.x is equal to 1.
   
- What value is alerted?
   ```
   var x   = 4,
       obj = {
           x: 3,
           bar: function() {
               var x = 2;
               setTimeout(function() {
                   var x = 1;
                   alert(this.x);
               }, 1000);
           }
       };
   obj.bar();
   ```
   Answer: 4
   
   If code is not using "use strict" mode, the setTimeout() is point to window, so this.x is equal to window.x, which is 4
   
- What value is alerted?
   ```
   x = 1;
   function bar() {
       this.x = 2;
       return x;
   }
   var foo = new bar();
   alert(foo.x);
   ```
   Answer： 
   
- What value is alerted?
   ```
   function foo(a) {
       alert(arguments.length);
   }
   foo(1, 2, 3);
   ```
   Answer: 3
   
   In function foo, it only has one argument, arguments obejct can get all arguments of the function no matter of function foo only has one argument. So the foo(1, 2, 3).length is 3
   
- What value is alerted? 
   ```
   var arr = [];
   arr[0]  = 'a';
   arr[1]  = 'b';
   arr.foo = 'c';
   alert(arr.length);
   ```
   Answer: 2
   
   arr = ["a", "b", foo: "c"]
   The array object length only accounts for integer indexes. arr.foo = 'c', it is a property in arr object, it is not an integer value. The length of arrays only increase when it is integer indexes. 
   So the arr.length is 2, should not include foo.
   
- What value is alerted?
   ```
   function foo(a) {
       arguments[0] = 2;
       alert(a);
   }
   foo(1);
   ```

   Answer: 2
   Function's arguments object indicates the list of function arguments, the first one index starting at 0. So arguments[0] = 2 actually means the first argument a = 2.

