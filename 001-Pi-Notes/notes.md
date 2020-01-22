<html>
  <head>
    <title>Pi Info - Markdown version</title>
    <meta charset="UTF-8">
    <!-- Yes, it's jammed together so it doesn't take a lot of vertical space when writing notes -->
    <script type="application/javascript" src='https://cdnjs.cloudflare.com/ajax/libs/showdown/1.9.1/showdown.min.js'></script>
    <script> document.addEventListener('DOMContentLoaded', (event) => { var converter = new showdown.Converter(); converter.setFlavor('github'); html = converter.makeHtml(document.getElementsByTagName('body')[0].textContent); document.getElementsByTagName('body')[0].innerHTML = html; }); </script>
  </head>
  <body>

***Note that you will have to change the FILE variable in the spws script to refer to this file (notes.md) in order to load it.***

# Super-secret project (Pi 4 only)

(This is an example of using github style Markdown to format the whole body, making it a bit less onerous than HTML.)

**Resumption notes:**

Working on the new thing. See answers.js

**Exposed ports:**
* 88 (http) - This web page - disable this in /etc/rc.local
* 3000 (http) - The generic node web port
* 1883 (mqtt) - The mqtt server
* 3306 (mysql) - Database

Who to call when things go boom:
* Fred
* ~~Marshall~~ Don't call me, I'm busy.
* Ben

**Note: Fred's personal key will log you in to the shell on the pi user.**

*This image has not been secured at all!*

---
**Some markdown tests...**

(Note that some of these WILL likely fail - I believe we can set some styles up to make this render better. Maybe later!)

This is rendered using the [showdown javascript library](https://github.com/showdownjs/showdown)

GLADoS says..... "Let's do some tests!":


Inline code can be shown like this: `sudo su` <- There be dragons here!!

The obligatory link to [GitHub](https://github.com)

Task lists:
- [X] Collect underpants
- [ ] ???????
- [ ] Profit

Emojis:

@octocat :+1: This PR looks great - it's ready to merge! :shipit:

Syntax Highlighting:
```javascript
var s = "JavaScript syntax highlighting";
alert(s);
function xyz(q) {
  // The parameter above is REALLY dim!
  // Wonder if we can style it?
  a = 1 + 3;
  var z = document.getElementById("hithere");
}
```
 
```python
s = "Python syntax highlighting"
print s
```
 
```
No language indicated, so no syntax highlighting. 
```

Tables:

Sloppy table markup:
Markdown | Less | Pretty
--- | --- | ---
*Still* | `renders` | **nicely**
1 | 2 | 3

Nice table markup (with alignments):
| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

Here's a blockquote:
> “With software there are only two possibilites: either the users control the programme or the programme controls the users. If the programme controls the users, and the developer controls the programme, then the programme is an instrument of unjust power.”
> 
> ― Richard M. Stallman


  </body>
