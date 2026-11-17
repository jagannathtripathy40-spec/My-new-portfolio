
<!DOCTYPE html>
<html>
<head>
<title>Modern House Design</title>
<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: linear-gradient(skyblue, white);
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: Arial;
}

.house {
  position: relative;
  width: 350px;
  height: 260px;
  background: #f5deb3;
  border: 5px solid #9b7653;
  margin-top: 80px;
}

.roof {
  position: absolute;
  top: -105px;
  left: -35px;
  width: 410px;
  height: 110px;
  background: #8b0000;
  clip-path: polygon(50% 0, 100% 100%, 0 100%);
}

.window {
  position: absolute;
  top: 35px;
  width: 75px;
  height: 80px;
  background: #87ceeb;
  border: 7px solid white;
}

.window1 { left: 35px; }
.window2 { right: 35px; }

.door {
  position: absolute;
  bottom: 0;
  left: 130px;
  width: 85px;
  height: 145px;
  background: #704214;
  border: 5px solid white;
}

.door::after {
  content: "";
  position: absolute;
  right: 10px;
  top: 70px;
  width: 9px;
  height: 9px;
  background: gold;
  border-radius: 50%;
}

.ground {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 100px;
  background: green;
  z-index: -1;
}

h1 {
  position: absolute;
  top: 30px;
  color: #333;
  text-align: center;
}
</style>
</head>

<body>

<h1>🏡 My Dream House</h1>

<div class="house">
  <div class="roof"></div>
  <div class="window window1"></div>
  <div class="window window2"></div>
  <div class="door"></div>
</div>

<div class="ground"></div>

</body>
</html>

