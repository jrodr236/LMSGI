# Condicionals i bucles

## If

```javascript
<!DOCTYPE html>
<html>
<body>
  <p>Click the button to get a time-based greeting:</p>
  <button onclick="myFunction()">Try it</button>
  <p id="demo"></p>

<script>
function myFunction() {
  var greeting;
  var time = new Date().getHours();
  if (time < 10) {
    greeting = "Good morning";
  } else if (time < 20) {
    greeting = "Good day";
  } else {
    greeting = "Good evening";
  }
  document.getElementById("demo").innerHTML = greeting;
}
</script>
</body>
</html>
```

[Exemple](https://www.w3schools.com/js/tryit.asp?filename=tryjs_elseif)

**Més informació a:** [w3schools.com - If](https://www.w3schools.com/js/js_if_else.asp)

## Switch

```javascript
<!DOCTYPE html>
<html>
<body>
  <h2>JavaScript Switch</h2>

  <p id="demo"></p>

<script>
var text;
switch (new Date().getDay()) {
    case 6:
        text = "Today is Saturday";
        break;
    case 0:
        text = "Today is Sunday";
        break;
    default:
        text = "Looking forward to the Weekend";
}
document.getElementById("demo").innerHTML = text;
</script>

</body>
</html>
```

[Exemple](https://www.w3schools.com/js/tryit.asp?filename=tryjs_switch)

**Més informació a:** [w3schools.com - Switch](https://www.w3schools.com/js/js_switch.asp)

## For

```javascript
<!DOCTYPE html>
<html>
<body>
  <h2>JavaScript For Loop</h2>

  <p id="demo"></p>

<script>
var text = "";
var i;
for (i = 0; i < 5; i++) {
    text += "The number is " + i + "<br>";
}
document.getElementById("demo").innerHTML = text;
</script>

</body>
</html>
```

[Exemple](https://www.w3schools.com/js/tryit.asp?filename=tryjs_loop_for_ex)

**Més informació a:** [w3schools.com - For Loop](https://www.w3schools.com/js/js_loop_for.asp)

## While

```javascript
<!DOCTYPE html>
<html>
<body>
  <h2>JavaScript While Loop</h2>

  <p id="demo"></p>

<script>
var text = "";
var i = 0;
while (i < 10) {
  text += "<br>The number is " + i;
  i++;
}
document.getElementById("demo").innerHTML = text;
</script>

</body>
</html>
```

[Exemple](https://www.w3schools.com/js/tryit.asp?filename=tryjs_while)

**Més informació a:** [w3schools.com - While Loop](https://www.w3schools.com/js/js_loop_while.asp)

