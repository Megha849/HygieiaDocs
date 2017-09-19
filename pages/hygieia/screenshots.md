---
title: Screenshots
tags:
keywords:
summary:
sidebar: hygieia_sidebar
permalink: screenshots.html
---
Screenshots of the various Hygieia dashbaord views:

<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
* {box-sizing:border-box}
body {margin:0}
.mySlides {display:none}

/* Slideshow container */
.slideshow-container > div {
  position: relative;
  max-width: 1000px;
  width: 100%;
  height: 500px;
  max-height: 100%;
  margin: auto;
}

.slideshow-container > div > img {
    height: 100%;
    width: 100%;
}
/* Next & previous buttons */
.prev, .next {
  cursor: pointer;
  position: absolute;
  top: 50%;
  width: auto;
  padding: 16px;
  margin-top: -22px;
  color: white;
  font-weight: bold;
  font-size: 18px;
  transition: 0.6s ease;
  border-radius: 0 3px 3px 0;
}

@media screen and (min-width:900px) 
{ .col-md-9 img {
				max-width: 850px !important;
				}
}

/* Position the "next button" to the right */
.next {
  right: 0px;
  border-radius: 3px 0 0 3px;
}

@media screen and (min-width:900px) {
  .next{
  right: 18px;
  }
  }

/* On hover, add a black background color with a little bit see-through */
.prev:hover, .next:hover {
  background-color: rgba(0,0,0,0.8);
}

/* Caption text */
.text {
  color: #f2f2f2;
  font-size: 15px;
  padding: 8px 12px;
  position: absolute;
  bottom: 35%;
  width: 100%;
  text-align: center;
}

/* The dots/bullets/indicators */
.dot {
  cursor:pointer;
  height: 13px;
  width: 13px;
  margin: 0 2px;
  background-color: #bbb;
  border-radius: 50%;
  display: inline-block;
  transition: background-color 0.6s ease;
}

.active, .dot:hover {
  background-color: #717171;
}

/* Fading animation */
.fade {
  -webkit-animation-name: fade;
  -webkit-animation-duration: 1.5s;
  animation-name: fade;
  animation-duration: 1.5s;
}

@-webkit-keyframes fade {
  from {opacity: .4} 
  to {opacity: 1}
}

@keyframes fade {
  from {opacity: .4} 
  to {opacity: 1}
}

/* On smaller screens, decrease text size */
@media only screen and (max-width: 300px) {
  .prev, .next,.text {font-size: 11px}
}
</style>

<div class="slideshow-container">

<div class="mySlides">
  <img src=".\media\images\Screenshots\hygiea-screenshot.jpg" style="width:100%">
  <div class="text">Widget View</div>
</div>

<div class="mySlides">
  <img src=".\media\images\Screenshots\pipeline_view.png" style="width:100%">
  <div class="text">Pipeline View</div>
</div>

<div class="mySlides">
  <img src=".\media\images\Screenshots\hygieia-product-dashboard.png" style="width:100%">
  <div class="text">Product View</div>
</div>

<div class="mySlides" style="width:100%">
  <img src=".\media\images\Screenshots\Cloud-Overview.png" style="width:100%">	
  <div class="text">Cloud - Overview</div>
</div>

<div class="mySlides">
  <img src=".\media\images\Screenshots\Cloud-Detail.png" style="width:100%">
  <div class="text">Cloud - Detail View</div>
</div>

<a class="prev" onclick="plusSlides(-1)">&#10094;</a>
<a class="next" onclick="plusSlides(1)">&#10095;</a>

</div>
<br />

<div style="text-align:center">
  <span class="dot" onclick="currentSlide(1)"></span> 
  <span class="dot" onclick="currentSlide(2)"></span> 
  <span class="dot" onclick="currentSlide(3)"></span> 
  <span class="dot" onclick="currentSlide(4)"></span>
  <span class="dot" onclick="currentSlide(5)"></span>
</div>

<script>
var slideIndex = 1;
showSlides(slideIndex);

function plusSlides(n) {
  showSlides(slideIndex += n);
}

function currentSlide(n) {
  showSlides(slideIndex = n);
}

function showSlides(n) {
  var i;
  var slides = document.getElementsByClassName("mySlides");
  var dots = document.getElementsByClassName("dot");
  if (n > slides.length) {slideIndex = 1}    
  if (n < 1) {slideIndex = slides.length}
  for (i = 0; i < slides.length; i++) {
      slides[i].style.display = "none";  
  }
  for (i = 0; i < dots.length; i++) {
      dots[i].className = dots[i].className.replace(" active", "");
  }
  slides[slideIndex-1].style.display = "block";  
  dots[slideIndex-1].className += " active";
}
</script>
