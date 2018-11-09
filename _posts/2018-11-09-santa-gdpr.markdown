---
layout: post
title:  Is Santa in Violation of GDPR?
date: 2018-11-09 14:04:00
description: Santa Clause is in contravention of article 4 of the General Data Protection Regulation
image: /assets/img/posts/santa-gdpr/94b0wsric9x11.jpg
social: true
tag: programming
relatedposts: true
---

<div class="">
    <img class="col three" src="{{ site.baseurl }}/assets/img/posts/santa-gdpr/94b0wsric9x11.jpg" alt="" title="Santa is in big trouble"/>
</div>
<div class="col three caption">
    He knows if you've been bad or good so consent to tracking for goodness sake. Courtesy of [Reddit][reddit-printout].
</div>

He sees your location when you're sleeping. He knows when your phone is awake. He knows if you liked your friend's most recent instagram post or not and put that into a big data Hadoop cluster that predicts the most relevant content that will extend your app usage by 2 minutes and 17 seconds.

Santa is tracking your location, and if he's as good as they say he is, he's probably working at Facebook's big data department.

This wouldn't really be much of a problem if Santa lived outside of the EU. Maybe somewhere like the North Pole. Then he could just [take the easy route and block all EU users][sites-blocking-eu-users] from receiving gifts.

Recently however, I have been informed that Santa's Village is in fact located in Rovaniemi, Finland- an EU country.

<div class="">
    <img class="col three" src="{{ site.baseurl }}/assets/img/posts/santa-gdpr/santas_village_hires.png" alt="" title="Santa's Village, Rovaniemi, Finland"/>
</div>
<div class="col three caption">
    Santa's Village- Rovaniemi, Finland
</div>

Ignoring why of all places Santa choose Finland (someone with that level of surveillance tech is obviously headquartered in the Valley or a manufacturing dreamland like Guangzhou), Santa has some answers he has to give- seriously. According to Articles [12][article-12] and [13][article-13] of GDPR, Santa must disclose all information he has gathered on us when requested.

He's also not supposed to be gathering any of our data without explicit consent. And I don't remember consenting to all of Santa's tracking.

Now I'm not an expert in international privacy laws. In fact, I'm not an expert in anything. I do know how to program however. And just like every programmer out there, whenever I don't know the answer to something and can't bullshit my way out, I stack overflow it.

Or stackexchange it. Whatever they're basically the same thing. Luckily, somebody much smarter (and way more time to waste believe or not) [wrote an excellent answer][stackexchange-answer] regarding Santa's potential violation of the General Data Protection Regulation.

The answer is kinda interesting. User /u/Giter claims that Santa's surveillance is not only compliant with GDPR standards; /u/Giter claims that Santa *does a better job than even most tech companies*. For example:

<blockquote>
You better watch out
<br />
You better not cry
<br>
Better not pout
<br>
I'm telling you why
<br>
<b>Santa Claus is coming to town</b>
</blockquote>

Santa makes it clear that he in fact coming to town and tracking you.

<blockquote>
He's making a list
<br>
And checking it twice;
<br>
Gonna find out Who's naughty and nice
<br>
Santa Claus is coming to town
</blockquote>

Santa not only tells us *explicitly* that he is collecting our data in this verse; Santa tells us exactly why he's collecting our data- to find out if we've been naughty or nice.

/u/Giter's answer is pretty well thought out, and even mentions how by agreeing to receive presents, we have consented to Santa's tracking. I'm not sure about you, but it seems like Santa has some really good GDPR lawyers.

Of course, maybe you're not convinced that Santa's alibi is tight. Maybe you were on the naughty list and Santa brought you coal and you never consented to being tracked just to get coal. 

Well, you're still out of luck. He may go by Santa now, but his real name is Nicholas- Saint Nicholas, and he's a catholic bishop. And according to /u/Molot's answer, religious organizations are exempt from GDPR:

<blockquote>
The new Regulation will maintain the existing exemption which allows churches and other bodies with a 'religious... aim' to process sensitive data:
<br>
<br>
● 'in the course of its legitimate activities...';
<br>
● '...with appropriate safeguards';
<br>
● ..* '...on condition that the processing relates solely to the members or to former members of the body or to persons who have regular contact with it in connection with its purposes'; and
<br>
● ..* on condition that 'the data are not disclosed outside that body without the consent of the data subject'.

</blockquote>

So much for separation of church and state...

The verdict? Well first off, for a dude who breaks and enters into millions of homes once per year, Santa is really good at following GDPR law. Second, if I were startup I would try reorganizing as a religious organization. A good startup is already [supposed to be a cult][startup-cult], so it shouldn't be that hard to add a religious component in too.

Closing thoughts: I need to find a new hobby.

<div class="">
    <img class="col three" src="{{ site.baseurl }}/assets/img/posts/santa-gdpr/naughty-nice-slaneconz_large.jpg" alt="" title="Santa watching us"/>
</div>
<div class="col three caption">
    The real Santa uses a Tensorflow Neural Network to predict naughty or good.
</div>
<hr />
<br>
<br>


[reddit-printout]: https://www.reddit.com/r/datascience/comments/9vihdt/gdpr_you_cant_even_make_a_list/
[sites-blocking-eu-users]: http://www.niemanlab.org/2018/08/more-than-1000-u-s-news-sites-are-still-unavailable-in-europe-two-months-after-gdpr-took-effect/
[article-12]: https://gdpr-info.eu/art-12-gdpr/
[article-13]: https://gdpr-info.eu/art-13-gdpr/
[stackexchange-answer]: https://worldbuilding.stackexchange.com/questions/114033/how-can-santa-keep-his-lists-when-the-gdpr-is-around
[startup-cult]: https://www.wired.com/2014/09/run-startup-like-cult-heres/