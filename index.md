---
layout: default
title: Blog
---
<!-- Hero section -->
<section id="infinite" class="text-white tm-font-big tm-parallax">
  <!-- Navigation -->
  <nav class="navbar navbar-expand-md tm-navbar" id="tmNav">
    <div class="container">
      <div class="tm-next">
          <a href="#infinite" class="navbar-brand">Travel Palette</a>
      </div>

      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <i class="fas fa-bars navbar-toggler-icon"></i>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav ml-auto">
          <li class="nav-item">
              <a class="nav-link tm-nav-link" href="#infinite">Home</a>
          </li>
          <li class="nav-item">
              <a class="nav-link tm-nav-link" href="#whatwedo">What We Do</a>
          </li>
          <li class="nav-item">
            <a class="nav-link tm-nav-link" href="#testimonials">Testimonials</a>
          </li>
          <li class="nav-item">
              <a class="nav-link tm-nav-link" href="#gallery">Gallery</a>
          </li>
          <li class="nav-item">
              <a class="nav-link tm-nav-link" href="#contact">Contact</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>

  <div class="text-center tm-hero-text-container">
    <div class="tm-hero-text-container-inner">
        <h2 class="tm-hero-title">Infinite Loop</h2>
        <p class="tm-hero-subtitle">
          Bootstrap 4.0 Parallax Theme
          <br>Free HTML Template by TOOPLATE
        </p>
    </div>
  </div>

  <div class="tm-next tm-intro-next">
    <a href="#whatwedo" class="text-center tm-down-arrow-link">
      <i class="fas fa-2x fa-arrow-down tm-down-arrow"></i>
    </a>
  </div>
</section>

{% for post in site.posts %}
  <section id="{{post.section}}" class="{{post.class}}">
    <!-- <h1><a href="{{ post.url }}">{{ post.title }}</a></h1>
    <p>{{ post.date | date_to_string }} - {{ post.author }}</p> -->
    <div class="container container-narrow">
      <div class="row">
        <div class="text-center col-12">
            <h2 class="tm-text-primary tm-section-title mb-4">{{ post.title }}</h2>
        </div>
      </div>
      <div class="row">
          <div class="col-4">
            <figure class="palette-img-item-v">
              <img src="{{ post.image_url }}" alt="Image" class="img-fluid mx-auto">
              <blockquote>This background image includes a semi-transparent overlay layer. This section also has a parallax image effect.</blockquote>
              <figcaption>
                <h2><i>Physical Health <span>Exercise!</span></i></h2>
              </figcaption>
            </figure>
          </div>
          <div class="col-8 palette-container">
            <p class="mx-auto tm-section-desc">
              {{ post.description }}
            </p>
            <div class="palette-item-v">
            {% for color in post.colors %}
              <div class="color-item-v" style="background-color: {{ color.hex }}"></div>
            {% endfor %}
            </div>
            <div class="colors-strip">
              <span class="colors-strip-text">
                {{ post.colors | map: "hex" | join: "•" }}
              </span>
            </div>
          </div>
        </div>
    </div>
  </section>
{% endfor %}

<script>
$(function(){
  // Hero Section - Background Parallax
  background_image_parallax($(".tm-parallax"), 0.30, false);
  background_image_parallax_2($("#contact"), 0.80);
  background_image_parallax_2($("#testimonials"), 0.80);

  // Handle window resize
  window.addEventListener('resize', function(){
    background_image_parallax($(".tm-parallax"), 0.30, true);
  }, true);

  // Detect window scroll and update navbar
  $(window).scroll(function(e){
    if($(document).scrollTop() > 120) {
      $('.tm-navbar').addClass("scroll");
    } else {
      $('.tm-navbar').removeClass("scroll");
    }
  });

  // Close mobile menu after click
  $('#tmNav a').on('click', function(){
    $('.navbar-collapse').removeClass('show');
  })

  // Scroll to corresponding section with animation
  $('#tmNav').singlePageNav({
    'easing': 'easeInOutExpo',
    'speed': 600
  });

  // Add smooth scrolling to all links
  // https://www.w3schools.com/howto/howto_css_smooth_scroll.asp
  $("a").on('click', function(event) {
    if (this.hash !== "") {
      event.preventDefault();
      var hash = this.hash;

      $('html, body').animate({
        scrollTop: $(hash).offset().top
      }, 600, 'easeInOutExpo', function(){
        window.location.hash = hash;
      });
    } // End if
  });

  // Pop up
  $('.tm-gallery').magnificPopup({
    delegate: 'a',
    type: 'image',
    gallery: { enabled: true }
  });

  $('.tm-testimonials-carousel').slick({
    dots: true,
    prevArrow: false,
    nextArrow: false,
    infinite: false,
    slidesToShow: 3,
    slidesToScroll: 1,
    responsive: [
      {
        breakpoint: 992,
        settings: {
          slidesToShow: 2
        }
      },
      {
        breakpoint: 768,
        settings: {
          slidesToShow: 2
        }
      },
      {
        breakpoint: 480,
        settings: {
            slidesToShow: 1
        }
      }
    ]
  });

  // Gallery
  $('.tm-gallery').slick({
    dots: true,
    infinite: false,
    slidesToShow: 5,
    slidesToScroll: 2,
    responsive: [
    {
      breakpoint: 1199,
      settings: {
        slidesToShow: 4,
        slidesToScroll: 2
      }
    },
    {
      breakpoint: 991,
      settings: {
        slidesToShow: 3,
        slidesToScroll: 2
      }
    },
    {
      breakpoint: 767,
      settings: {
        slidesToShow: 2,
        slidesToScroll: 1
      }
    },
    {
      breakpoint: 480,
      settings: {
        slidesToShow: 1,
        slidesToScroll: 1
      }
    }
  ]
  });
});
</script>
