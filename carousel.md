## Bootstrap Carousel
A *carousel* is a component that allows the inclusion of a slideshow with captions as well as manual controls for the slideshow.

### How it works?
### (ONLY Slides (Without Controls))
To get started, we need to create a **div** container that will wrap our carousel and give it a few attributes.

**id="mycarousel** used by the carousel indicator(s)
**class="carousel slide"** *carousel* basically creates a carousel. While *slide* adds a CSS transition and animation effect when sliding from one item to the next
**data-ride="carousel"** - this attribute tells Bootstrap to begin animating the carousel immediately when the page loads. 

```
<div id="mycarousel" class="carousel slide" data-ride="carousel">
.
.
.
</div>
```
Moving on, we need to add an inner div container with class, **.inner-carousel**. This adds a slide to our carousel. So our code should be looking like this:

```
<div id="mycarousel" class="carousel slide" data-ride="carousel">
    <div class="inner-carousel" role="listbox">
    .
    .
    .
    </div>
</div>
```
As, we continue, we will now add another div with the classes, **.acrousel-item** and **.active**, which defines that this element will be our first visible slide in our carousel. Our code shoudl be looking like:
```
<div id="mycarousel" class="carousel slide" data-ride="carousel">
    <div class="inner-carousel" role="listbox">
        <div class="carousel-item active">
        .
        .
        .
        </div>
    </div>
</div>
```
Great, so at this point it is time to add our images. So basically, you will repeat up to this point, according to the number of images you want to add. You simple add your image tag with the following classes:
**.d-block** - creates a block element
**.img-fluid** - to make your image responsive

Our code should be looking like:
```
<div id="mycarousel" class="carousel slide" data-ride="carousel">
    <div class="inner-carousel" role="listbox">
        <div class="carousel-item active">
            <img class="d-block img-fluid src="some-source">
        </div>
    </div>
</div>
```
Lastly, we can add captions to our slides by adding a div element inside of our *carousel-item*, with class, **.carousel-caption**. Our code should be looking like:
```
<div id="mycarousel" class="carousel slide" data-ride="carousel">
    <div class="inner-carousel" role="listbox">
        <div class="carousel-item active">
            <img class="d-block img-fluid src="some-source">
            <div class="carousel-caption">
            ..
            </div>
        </div>
    </div>
</div>
```
### Adding Carousel Indicators
Next up, we will be adding indicators to our carousel to hint to us, which slide is currently being shown. To accomplish this, we will be using `<ol>`, as shown below:
```
<ol class="carousel-indicators">
    <li data-target="mycarousel" data-slide-to"0" class="active"></li>
    .
    .
    <li data-target="mycarousel" data-slide-to"num_i" class="active"></li>
</ol>
```
Thus, altogether, your code should be looking as follows:

```
<div id="mycarousel" class="carousel slide" data-ride="carousel">
    <div class="inner-carousel" role="listbox">
        <div class="carousel-item active">
            <img class="d-block img-fluid src="some-source">
            <div class="carousel-caption">
            ..
            </div>
        </div>
        <ol class="carousel-indicators">
            <li data-target="mycarousel" data-slide-to"0" class="active"></li>
            .
            .
            <li data-target="mycarousel" data-slide-to"num_i" class="active"></li>
        </ol>
    </div>
</div>
```

### Adding Controls 
To wrap things up, we will finally add some controls to enable the user to manual slide from left (previous) to right (next). To accomplish this, we will make use of our anchor tag.

```
<!--Previous Button-->
<a class="carousel-control-prev" href="#mycarousel" role="button" data-slide="prev">
    <span class="carousel-control-prev-icon"></span>
</a>

<!--Next Button-->
<a class="carousel-control-next" href="#mycarousel" role="button" data-slide="next">
    <span class="carousel-control-next-icon"></span>
</a>
```

Our final code should look as follows:
```
<div id="mycarousel" class="carousel slide" data-ride="carousel">
    <div class="inner-carousel" role="listbox">
        <div class="carousel-item active">
            <img class="d-block img-fluid src="some-source">
            <div class="carousel-caption">
            ..
            </div>
        </div>
        <ol class="carousel-indicators">
            <li data-target="mycarousel" data-slide-to"0" class="active"></li>
            .
            .
            <li data-target="mycarousel" data-slide-to"num_i" class="active"></li>
        </ol>

        <!--Previous Button-->
        <a class="carousel-control-prev" href="#mycarousel" role="button" data-slide="prev">
            <span class="carousel-control-prev-icon"></span>
        </a>

        <!--Next Button-->
        <a class="carousel-control-next" href="#mycarousel" role="button" data-slide="next">
            <span class="carousel-control-next-icon"></span>
        </a>
    </div>
</div>
```

### Adding More Control Using JavaScript (JQuery)
To add further control to our carousel, we can add some JS code to do things such as pause and resume. This section touches on how to accomplish the same.
So, right after our left and right control buttons, we will introduce a button. This button will toggle between pause and play base on user interaction (click).
```
    <button class="btn btn-danger btn-sm" id="carouselButton">
        <span class="fa fa-pause"></span>
    </button>
```
Thus far, we have not written/added any JS code so it is time to do so. Add `<script></script>` at the bottom of your page just before the closing body tag.Then add the following between them.
```
$(document).ready(function(){
    $("#mycarousel").carousel({interval: 2000});
    $("#carouselButton").click(function()
    {
        if($("#carouselButton").children("span").hasClass("fa fa-pause"))
        {
            $("#mycarousel").carousel("pause");
            $("#carouselButton").children("span").removeClass("fa fa-pause");
             $("#carouselButton").children("span").addClass("fa fa-play");
        }else if($("#carouselButton").children("span").hasClass("fa fa-play"))
        {
            $("#mycarousel").carousel("cycle");
            $("#carouselButton").children("span").removeClass("fa fa-play");
            $("#carouselButton").children("span").addClass("fa fa-pause");
        }
    });
});
```

The following CSS code is optional. It simply places your control button at the bottom right-hand corner of the screen.
```
#carouselButton{
    position: absolute;
    right: 0;
    bottom: 0;
}
```