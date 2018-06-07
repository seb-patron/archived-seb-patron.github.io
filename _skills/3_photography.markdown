---
layout: page
title: photography
description: my personal photography
img: /assets/img/skills/photography/icon-boat.jpg
---

Images taken with a Sony A7, Ricoh GR II, or iPhone SE. Click or tap on an image to make it larger.

<link rel="stylesheet" href="{{ site.baseurl }}/assets/css/modal.css">

<div class="img_row">
    <img class="col three" src="{{ site.baseurl }}/assets/img/skills/photography/costa-rica-blog-1.jpg" alt="" title="costa rica pano"/>
</div>
<div class="col three caption">
    Off the Nicoya Peninsula, Costa Rica
</div>

<div class="img_row">
    <img class="col two" src="{{ site.baseurl }}/assets/img/skills/photography/missing-the-beach-2.jpg" alt="" title="costa rican beach"/>
    <img class="col one" src="{{ site.baseurl }}/assets/img/skills/photography/ship-in-ocean.jpg" alt="" title="costa rican boat in the distance"/>
</div>
<div class="col three caption">
    The beauty of Santa Teresa, Costa Rica.
</div>

<div class="img_row">
    <img class="col one" src="{{ site.baseurl }}/assets/img/skills/photography/brutus-costa-dog.jpeg" alt="" title="brutus, the cuddly dog :)"/>
    <img class="col two" src="{{ site.baseurl }}/assets/img/skills/photography/costa-rica-landscape.jpeg" alt="" title="where Brutus took me"/>
</div>
<div class="col three caption">
    My Costa Rican pal Brutus :dog: took me on a hike.
</div>

<div class="img_row">
    <img class="col two" src="{{ site.baseurl }}/assets/img/skills/photography/coffee-beans.jpeg" alt="" title="some coffee beans drying"/>
    <img class="col one" src="{{ site.baseurl }}/assets/img/skills/photography/coffee-beans-thrown.jpeg" alt="" title="don't drop the coffee beans!"/>
</div>
<div class="col three caption">
    Checking out a coffee bean drying warehouse.
</div>

<div class="img_row">
    <img class="col one" src="{{ site.baseurl }}/assets/img/skills/photography/brutus-with-stick-2.jpg" alt="" title="my friend Brutus again :)"/>
    <img class="col one" src="{{ site.baseurl }}/assets/img/skills/photography/beach-pig.jpeg" alt="" title="a beach pig that stole my food!"/>
    <img class="col one" src="{{ site.baseurl }}/assets/img/skills/photography/costa-bird-1.jpeg" alt="" title="nice bird"/>
</div>
<div class="col three caption">
    Some of the friends I made in Costa Rica.
</div>

<div class="img_row">
    <img class="col one" src="{{ site.baseurl }}/assets/img/skills/photography/costa-pig.jpeg" alt="" title="another Costa Rican pig!"/>
    <img class="col two" src="{{ site.baseurl }}/assets/img/skills/photography/costa-rica-tree-line.jpeg" alt="" title="it sure rained alot!"/>
</div>
<div class="col three caption">
    Costa Rica.
</div>

<div class="img_row">
    <img class="col one" src="{{ site.baseurl }}/assets/img/skills/photography/budapest-3.jpeg" alt="" title="budapest"/>
    <img class="col one" src="{{ site.baseurl }}/assets/img/skills/photography/budapest-1.jpeg" alt="" title="budapest"/>
    <img class="col one" src="{{ site.baseurl }}/assets/img/skills/photography/budapest-2.jpeg" alt="" title="budapest"/>
</div>
<div class="col three caption">
    Series of images from budapest.
</div>

<div class="img_row">
    <img class="col three" src="{{ site.baseurl }}/assets/img/skills/photography/budapest-wide.jpeg" alt="" title="budapest"/>
</div>
<div class="col three caption">
    Pano from budapest.
</div>

<div class="">
    <img class="col three" src="{{ site.baseurl }}/assets/img/skills/photography/mt-humphreys-1.jpg" alt="" title="Mt. Humphreys, Flagstaff Arizona"/>
</div>
<div class="col three caption">
    A climb up Mt. Humphreys.
</div>

<div class="img_row">
    <img class="col one" id="myModal myImg" src="{{ site.baseurl }}/assets/img/skills/photography/beach-mack.jpg" alt="" title="another Costa Rican pig!"/>
    <img class="col two" id="myModal myImg" data-toggle="modal" data-target="#myModal" src="{{ site.baseurl }}/assets/img/skills/photography/friends-trip.jpg" alt="" title="it sure rained alot!"/>
</div>
<div class="col three caption" id="caption">
    Some foolery with my friends.
</div>




<div id="myModal" class="modal fade" role="dialog">
    <div class="modal-dialog">
        <div class="modal-content">
            <div class="modal-body image-container">
                <img class="img-responsive" src="" />
            </div>
            <div class="modal-footer">
                <!-- <button type="button" class="btn btn-default" data-dismiss="modal">Close</button> -->
                <span class="close">&times;</span>
            </div>
        </div>
    </div>
</div>



<script
  src="https://code.jquery.com/jquery-3.3.1.min.js"
  integrity="sha256-FgpCb/KJQlLNfOu91ta32o/NMZxltwRo8QtmkMRdAu8="
  crossorigin="anonymous"></script>
<script>
     $(document).ready(function () {
    $('img').on('click', function () {
        var image = $(this).attr('src');
     //    alert(image);
     $(".img-responsive").attr("src", image);
     $('#myModal').show()
     console.log("before the  function")
     //    $('#myModal').click('show.bs.modal', function () {
     //         console.log('this function got called')
     //        $(".img-responsive").attr("src", image);
     //    });
    });
});

$('.close').on('click', function () {
    $('#myModal').hide()
})

// When the user clicks anywhere outside of the modal, close it
window.onclick = function(event) {
    if (event.target == $('#myModal').is(":visible")) {
        $('#myModal').hide()
    }
}
</script>