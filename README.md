### **Simple Analog Clock Webpage**
**Code: HTML, CSS-Bootstrap Framework, Java Script**
# You can try it yourself ⬇️
- File name: index.html
  
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Analog Clock</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha3/dist/css/bootstrap.min.css" rel="stylesheet"
    integrity="sha384-KK94CHFLLe+nY2dmCWGMq91rCGa5gtU4mk92HdvYe+M/SXH301p5ILy+dN9+nJOZ" crossorigin="anonymous">
  <link rel="stylesheet" href="./styles.css">
</head>

<body>


  <!-- Title -->
  <section id="title" class="gradient-background">

    <div class="container col-xxl-8 px-4 pt-5">
      <div class="row flex-lg-row-reverse align-items-center g-5 pt-5">
        <div class="col-10 col-sm-8 col-lg-6">
          <div class="d-block mx-lg-sm-auto img-fluid" alt="Bootstrap Themes" height="200"
            loading="lazy">
            <div class="clock">
              <div class="outer-clock-face">
                <div class="marking marking-one"></div>
                <div class="marking marking-two"></div>
                <div class="marking marking-three"></div>
                <div class="marking marking-four"></div>
                <div class="inner-clock-face">
                  <div class="hand hour-hand"></div>
                  <div class="hand min-hand"></div>
                  <div class="hand second-hand"></div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="col-lg-6">
          <h1 class="display-5 fw-bold text-body-emphasis lh-1 mb-3">
            <br> Web Development and Design
            <br><br> <i> Analog Clock</i>
            <br><br>Designed By,
            <br> <i> R Pritto Ruban</i>
          </h1>
        </div>
      </div>
    </div>
    <script src="./script.js"></script>
</section>
```

- File name: styles.css

```css
html{
  background: linear-gradient(300deg, #799dd3, #c4fff3, #00bfff);
  background-size: 180% 180%;
  animation: gradient-animation 18s ease infinite;
}

.gradient-background {
  background: linear-gradient(300deg, #00bfff, #c4fff3, #799dd3);
  background-size: 180% 180%;
  animation: gradient-animation 18s ease infinite;
}

@keyframes gradient-animation {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

.icon-square {
  width: 3rem;
  height: 3rem;
  border-radius: 0.75rem;
}

.profile-img {
  border-radius: 50%;
  height: 100px;
}

.clock {
  width: 30rem;
  height: 30rem;
  border: 7px solid black;
  border-radius: 50%;
  margin: 50px auto;
  position: relative;
  padding: 2rem;
 
}

.outer-clock-face {
  position: relative;
  width: 100%;
  height: 100%;
  border-radius: 100%;
  background: #282828;
  overflow: hidden;
}

.outer-clock-face::after {
    -webkit-transform: rotate(90deg);
    -moz-transform: rotate(90deg);
    transform: rotate(90deg)
  }

.outer-clock-face::before,
.outer-clock-face::after,
.outer-clock-face .marking{
  content: '';
  position: absolute;
  width: 5px;
  height: 100%;
  background: #cfd0cf;
  z-index: 0;
  left: 49%;
}

.outer-clock-face .marking {
  background: #bdbdcb;
  width: 3px;
}

.outer-clock-face .marking.marking-one {
  -webkit-transform: rotate(30deg);
  -moz-transform: rotate(30deg);
  transform: rotate(30deg)
}

.outer-clock-face .marking.marking-two {
  -webkit-transform: rotate(60deg);
  -moz-transform: rotate(60deg);
  transform: rotate(60deg)
}

.outer-clock-face .marking.marking-three {
  -webkit-transform: rotate(120deg);
  -moz-transform: rotate(120deg);
  transform: rotate(120deg)
}

.outer-clock-face .marking.marking-four {
  -webkit-transform: rotate(150deg);
  -moz-transform: rotate(150deg);
  transform: rotate(150deg)
}

.inner-clock-face {
  position: absolute;
  top: 10%;
  left: 10%;
  width: 80%;
  height: 80%;
  background: linear-gradient(300deg, #00bfff, #b5f4f1, #f8d0cb);
  -webkit-border-radius: 100%;
  -moz-border-radius: 100%;
  border-radius: 100%;
  z-index: 1;
}

.inner-clock-face::before {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 16px;
  height: 16px;
  border-radius: 18px;
  margin-left: -9px;
  margin-top: -6px;
  background: #1d5672;
  z-index: 11;
}

.hand {
  width: 50%;
  right: 50%;
  height: 6px;
  background: #3f35cf;
  position: absolute;
  top: 50%;
  border-radius: 6px;
  transform-origin: 100%;
  transform: rotate(90deg);
  transition-timing-function: cubic-bezier(0.1, 2.7, 0.58, 1);
}

.hand.hour-hand {
  width: 30%;
  z-index: 3;
}

.hand.min-hand {
  height: 3px;
  z-index: 10;
  width: 40%;
}

.hand.second-hand {
  background: rgb(6, 42, 42);
  width: 45%;
  height: 2px;
}

/* Media Queries */
@media (max-width: 768px) {
  .clock {
    width: 20rem;
    height: 20rem;
  }
}

@media (max-width: 576px) {
  .clock {
    width: 15rem;
    height: 15rem;
  }
}
```

- File name: script.js

```js
const secondHand = document.querySelector('.second-hand');
const minsHand = document.querySelector('.min-hand');
const hourHand = document.querySelector('.hour-hand');

function setDate() {
  const now = new Date();

  const seconds = now.getSeconds();
  const secondsDegrees = ((seconds / 60) * 360) + 90;
  secondHand.style.transform = `rotate(${secondsDegrees}deg)`;

  const mins = now.getMinutes();
  const minsDegrees = ((mins / 60) * 360) + ((seconds/60)*6) + 90;
  minsHand.style.transform = `rotate(${minsDegrees}deg)`;

  const hour = now.getHours();
  const hourDegrees = ((hour / 12) * 360) + ((mins/60)*30) + 90;
  hourHand.style.transform = `rotate(${hourDegrees}deg)`;
}

setInterval(setDate, 1000);

setDate();
```
