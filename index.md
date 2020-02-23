---
layout: default
title: Blog
---
{% include header.html %}
{% for post in site.posts %}
  <section id="{{post.section}}" class="{{post.class}}">
    <div class="container container-narrow">
    <div class="card post-card">
      <div class="row">
          {% if "vertical" == post.image_orientation %}
          <div class="col-6">
            <div class="palette-img-v">
              <img src="{{ post.image_url }}" alt="Image" class="palette-img-item-v img-fluid mx-auto">
              <div class="palette-item-h">
                {% for color in post.colors %}
                <div class="color-item-h" style="background-color: {{ color.hex }}"></div>
                {% endfor %}
              </div>
            </div>
            <div class="colors-strip">
            {% for color in post.colors %}
              <div class="colors-strip-item card">
                <div class="colors-strip-item-palette" style="background-color: {{ color.hex }}"></div>
                <div class="colors-strip-item-text">{{ color.hex }}</div>
              </div>
            {% endfor %}
            </div>
          </div>
          {% else %}
          <div class="col-6">
            <div class="palette-img-h">
              <img src="{{ post.image_url }}" alt="Image" class="palette-img-item-h img-fluid mx-auto">
              <div class="palette-item-v">
                {% for color in post.colors %}
                <div class="color-item-v" style="background-color: {{ color.hex }}"></div>
                {% endfor %}
              </div>
            </div>
            <div class="colors-strip">
            {% for color in post.colors %}
              <div class="colors-strip-item card">
                <div class="colors-strip-item-palette" style="background-color: {{ color.hex }}"></div>
                <div class="colors-strip-item-text">{{ color.hex }}</div>
              </div>
            {% endfor %}
            </div>
          </div>
          {% endif %}
          <div class="col-6">
            <div class="card post-card">

              <h2 class="mb-4">Color palette {{ post.title }}</h2>

              <p class="mx-auto tm-section-desc">
                {{ post.description }}
              </p>

              <p class="mx-auto tm-section-desc tags">
              {% for tag in post.tags %}
                <a class="badge badge-light" href="tags/{{tag}}">{{tag}}</a>
              {% endfor %}
              </p>
            </div>
          </div>
          <!-- <div class="col-8 palette-container">
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
            <div class="card post-card">
              <p class="mx-auto tm-section-desc">
                {{ post.description }}
              </p>
            </div>
          </div> -->
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
