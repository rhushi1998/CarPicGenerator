# CarPicGenerator

### Html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>car Pics Generator</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h3>car Pics Generator</h1>
        <button class="btn" id="btn">Get car</button>
        <div class="car-container">
            <img class="car-img" src="https://c.files.bbci.co.uk/F382/production/_123883326_852a3a31-69d7-4849-81c7-8087bf630251.jpg">
            <h3 class="car-name">car Name</h3>
        </div>
    </div>
    <script src="index.js"></script>
</body>
</html>

### Js

const btn = document.getElementById("btn");
const carContainer = document.querySelector(".car-container");
const carImg = document.querySelector(".car-img");
const carName = document.querySelector(".car-name");

btn.addEventListener("click", async function () {
  try {
    carImg.src = "spinner.svg";
    const response = await fetch("https://api.unsplash.com/photos/random?client_id=CkFO60TcgMR858-Cf0V_iIXrNGaRMVGS17HJwh-0bNo&query=car");
    const data = await response.json();
    btn.innerText = "Get Cars";
    carContainer.style.display = "block";
    carImg.src = data.links.download;
    carName.innerText = data.alt_description;
  } catch (error) {
    console.log(error);
    btn.disabled = false;
    btn.innerText = "Get car";
    carName.innerText = "An error happened, please try again";
  }
});
