My trip to EuroPython 2015 - Day One
####################################

:date: 2015-07-20 13:37
:tags: europython2015, python, conference
:slug: europython-day-one
:summary: My trip to the europython 2015 and a summary of the first day

Preface
=======
Note to myself: Dennis you are a lazy ass twat, you could have done this immediately but decided to sleep a additional hour. So now this
blogposts will be delayed by at least a week or even more. Take this as a lesson to get shit done immediately. Now back
to my story.

I have never been to a programmers conference in my still young life.

But since I started as a professional python developer and heard others talking about all the cool stuff happening at python conferences,
I always wanted to visit one. Getting in contact with other python programmers and learning new amazing stuff.
The PyCon in Germany dropped out pretty fast since it didn't get organized in the first place, so I looked around for
the european python conference ``EuroPython``.

Skip forward about half a year. I got my boss convinced to send my colleague and me for the EuroPython 2015 to Bilbao, Spain
and sponsor all of our trip. We got a nice hotel right next to the conference center and a flight to get to Bilbao in time.
We flew to Bilbao, landed there pretty hard and nearly got killed by our taxi driver who apparently thought he is Fernando Alonso.

EuroPython 2015
===============
.. figure:: images/bilbao.jpg
    :width: 100%
    :alt: Panorama from Bilbao Conference Center

After a good night full of sleep, we went our short ways to the conference center and got out conference cards,
our goddie bags, the t-shirts and finally... something to eat for breakfast. The people were streaming to the conference center
and more and more faces were showing up. Languages were mixing and laptops of all shapes, sizes and styles were unpacked.

With a bit of food and two cups of coffee consumed, we headed for the keynote.

Keynote: Organizational and Django Girls
========================================
We found some nice seats in the Google Room as they started with some organizational stuff. No drinks in the conference rooms,
no food too and we were already staring late, so everything was pushed back by 15 minutes.

After that, two girls, both named Ola, went on stage to presented the fairy tales of the Django Girls. It was a really great story
with a great visualization, so I recommend you check it our yourself. TLDR; They are pretty successful by now, which
neither of them expected to be. (A look into the future because I am writing this one day late: Even Guido van Rossum is
amazed by the work they both did).

They have written a tutorial for Python and Django that is specifically targeted at women and girls and explains it to
them in another way that is different from classic tutorial. You can check it out here: http://tutorial.djangogirls.org/en/index.html

And they also revealed a secret: They are writing a book, who's first presentation looks really promising.
There is no publication date yet, but you can already read about and subscribe to the newsletter at: http://www.yaypython.com

That was basically all of the keynote. You can find the video on Youtube and I tell you again to go watch their presentation.

Talk 1: Getting started with Bokeh
==================================
The first talk, of my first conference, of the first day I visited was about `Bokeh <http://bokeh.pydata.org/en/latest/>`_,
which is a data visualization library for the web. The actual web part is Javascript and you only create some json, that
is fed into the Javascript and creates well formed visualizations. Due to this fact there are implementations for a lot
of other programming languages besides Python.

The library looks very promising and is on one side easy to use for simple cases, but also customizable for more
complicated cases. You can also use it with pandas to load the data you want to visualize, so this also seems like a big
plus to me.

I will definetly try out `Bokeh <http://bokeh.pydata.org/en/latest/>`_ in one of my next projects. (If I ever get to
start and finsih one in the next time).

Talk 2: Python for IT Specialists' tasks automation
===================================================
This talk was a little bit disappointing because I expected something different, reading the description of the topic.
What I expected was a alternative or a best practise way of running reoccurring task on a server besides cronjobs or services.
What actually got presented were tools for your everyday developers' workflow on OS X. He also named some tools for Linux
and Windows but only demoed the tools he uses on his MacBook. To me this was pretty useless since I neither have a MacBook nor
do I plan to buy one in the foreseeable future.

For everyone else having a MacBook, I can really recommend to watch the talk and form an opinion yourself. The tools
themselves seemed pretty nice and handy. The only part they had to do with Python were the scripts you could write
to automate some tasks on a specific signal.

One tool that stuck to my mind was Alfred. I already forgot the other names of the tools.

Talk 3: It works on my machine
==============================
The third talk of the day was especially interesting for me since we use different platforms for different problems on our
day to day problem in the company. So it was really great for me to see what the best practises are, in running on multiple
platforms over multiple Python versions and multiple versions of librarys.

Kyle Knapp went over the differences of Python 2 and 3 first and recommended to use six, to have the incompatibilities
between the Python versions figured out and provides a compatibility for both versions. But still, six does not cover all
cases, so you will probably have do build a compat.py module to get all the other special cases.

If you need anything new, that has not been backported to Python 2, there is probably a third-party library for that.

When working across different OSes, Kyle recommends using the os module wherever possible. Python does already do a pretty
good job ironing out all the differences of those Systems. But still there are some cases where you just have to insert a
level of abstraction, for example when working with files on Linux and Windows. While windows only allows one file handle,
linux allows you to have multiple open and writing file handles.

When working over different library versions on one system it is good to use virtualenv to seperate all your dependecies,
from each other. Also it is good to keep your system clean and uncluttered.

Lunch @ EuroPython
==================
The lunch was actually quite good. They server small snacks, I think even typical spanish pyntxos (spoken: pinchos), which
are like tapas, but here in basque they are called pintxos. There were also salads server in different combinations.

All in all there was more than enough food for all the attendees and a lot of variations in the snacks server. They also
served drinks and desert which was also nice. I didn't expected it to be that good, but apparently they could afford it.

Talk 3.5: Knowing your garbage collector
========================================
After lunch I went into the garbage collector talk. I arrived late and saw that the room was packed. They chose the smallest
room even though they probably could have filled up one of the mid sized rooms.

I think the talk was given by one of the python core developers. He explained how the Garbage Collector works and how they
do the garbage collection. One special case is apparently cyclic dependecies and he also explained how they resolved that
problem.

I left pretty soon after, standing in the last row was just not my thing and they were aslo runing through the actual
C code of the GB. I left with a feeling of assurance that they are in full control of my python garbage.

Talking to the Red Hat Guys
===========================
Instead of going to the next talk I was walking around a bit and talking to some people. I had a really good talk with
the recruiting of Red Hat, that also changed my view of the company Red Hat. Having worked for IBM, Red Hat was also a
company that belonged to the old part of the internet, the beginnings of unixtime. Just knowing they do the OS I have
to work on and forgetting about their cloud division, they didn't really seemed interesting as an employer.

After learning that they "only" have 7000 employees and also a small location in Stuttgart, their attractiveness increased
a bit. They told me about the freedom they have at work and the startup atmosphere, that still roams their company.
Talking to recruiting guys, you always have to consume things like that with care.

I will definitely keep them in the back of my head for the future of my career.

Talk 4: Sustainable way of testing
==================================
The second to last talk I was sitting through was about a sustainable way of testing. Since we are not doing any tests
in our software by now, this was and still is a big point in our future agenda to better Python programs.

Unfortunately the speaker was a french guy with a very thick french accent in his english. It was really hard to listen
to him and people lost focus pretty fast. Me included. I tried to get his overall idea which was pretty great. He proposed
to write test like you write a user story. When ... then ... and ... So a new developer can have a look at your tests and
instantly figure out what your function is doing.

Have a look at his talk to see more precisely what he meant. Also you will probably have to listen two or more times to
really understand him. I will definitely re-watch the talk as soon as I am home again.

Talk 5: Writing quality code
============================
This last official talk for the day was really interesting as well. The main question of the talk was, how do we write
quality code and how do we actually measure quality of code?

Before the talk I had no clue of the size of this topic. I always thought that good code was readable, keeping to conventions
and being documented well enough. I also learned quite recently that tests are a big plus as well. But was this speaker
was laying out was a complete new concept of code quality.

Actually measuring the quality of code in a project using tools like pylint. He also talked about ways of measuring code
quality with cyclomatic complexity, halstead complexity measures and the maintainability index.

If code quality is a big problem for you and your team, you should really take this talk as an introduction to the topic
and go on from there till you have a good, high quality codebase.

Lightning Talks
===============
The first evening of Lightning talks was actually pretty short. We had this crazy british announcer that really knew how
to entertain the crowd. He could actually have a real chance with a youtube channel.

I haven't even made any notes, so it is again up to you to go to Youtube and watch the lightning talks. I can really recommend
them. Especially the one about the extreme I18N.

Hunting for food
================
After the first day of the europython, I was quite hungry for food and for a look into the city. We got a tip from our
hotel and form the organizers where to find some good bars. After walking up and down the "bar street" we went into a
chinese place, which looked somehow good. It actually was the idea of my colleague to eat there. I was hungry for some
good spanish food, but yay democracy.

After having some diner, we went back to the hotel, since none of my colleagues actually wanted anything to drink. So
this evening went without drinking and ended pretty early in my hotelroom.

What I think
============
This was a great first day on my first ever conference. People of all sorts giving out high quality giveaways was somehow
really amazing me. The talks were just like I thought and there were a lot of new ideas entering my mind.

So much for the first day. Read about the second day here tomorrow.