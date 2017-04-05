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

In css, more specific selectors override less specific ones regardless of order, so your text is red.
