<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1" />
<style>
   * {
      box-sizing: border-box;
   }
   input {
      width: 100%;
      padding: 12px;
      margin-top: 6px;
      margin-bottom: 16px;
   }
   input[type="submit"] {
      background-color: rgb(69, 27, 117);
      color: white;
      font-weight: bold;
      font-size: 20px;
      font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
   }
   form {
      padding: 20px;
   }
   #checksField {
      display: none;
      background: #f1f1f1;
      color: #000;
      position: relative;
      padding: 20px;
      margin-top: 10px;
   }
   #checksField p {
      padding: 10px 35px;
      font-size: 18px;
   }
   .correct {
      color: rgb(28, 0, 128);
   }
   .correct:before {
      position: relative;
      left: -35px;
      content: "✔";
   }
   .wrong {
      color: red;
   }
   .wrong:before {
      position: relative;
      left: -35px;
      content: "✖";
   }
</style>
</head>
<body>
<h1 style="text-align: center;">Password Validation Example</h1>
<form>
<label for="uname">Username</label>
<input type="text" id="uname" name="uname" required />
<label for="pass">Password</label>
<input
type="password"
id="pass"
name="pass"
pattern="(?=.*\d)(?=.*[a-z])(?=.*[A-Z]).{8,}"
title="Must contain at least one number and one uppercase and lowercase letter, and at
least 8 or more characters"
required
/>
<input type="submit" value="Submit" />
</form>
<div id="checksField">
<h3>Password must contain the following:</h3>
<p id="letter" class="wrong">A <b>lowercase</b> letter</p>
<p id="capital" class="wrong">A <b>capital (uppercase)</b>letter</p>
<p id="number" class="wrong">A <b>number</b></p>
</div>
<script>
   var myInput = document.getElementById("pass");
   var letter = document.getElementById("letter");
   var capital = document.getElementById("capital");
   var number = document.getElementById("number");
   myInput.onfocus = function() {
      document.getElementById("checksField").style.display = "block";
   };
   myInput.onblur = function() {
      document.getElementById("checksField").style.display = "none";
   };
   myInput.onkeyup = function() {
      var lowerCaseLetters = /[a-z]/g;
      if (myInput.value.match(lowerCaseLetters)) {
         letter.classList.remove("wrong");
         letter.classList.add("correct");
      } else {
         letter.classList.remove("correct");
         letter.classList.add("wrong");
      }
      var upperCaseLetters = /[A-Z]/g;
      if (myInput.value.match(upperCaseLetters)) {
         capital.classList.remove("wrong");
         capital.classList.add("correct");
      } else {
         capital.classList.remove("correct");
         capital.classList.add("wrong");
      }
      var numbers = /[0-9]/g;
      if (myInput.value.match(numbers)) {
         number.classList.remove("wrong");
         number.classList.add("correct");
      } else {
         number.classList.remove("correct");
         number.classList.add("wrong");
      }
   };
</script>
</body>
</html>
