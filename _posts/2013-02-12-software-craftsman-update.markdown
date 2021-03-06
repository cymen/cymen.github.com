---
date: '2013-02-12 21:08:00'
layout: post
slug: software-craftsman-update
status: publish
title: Software Craftsman Update
---

JavaScript
----------

I've been working as a Software Craftsman with 8th Light for a little over seven months. The projects I've worked on have been interesting.
All of them have involved JavaScript to some degree. I enjoy working with JavaScript but I've also started to see where frameworks can
cause pain and where event-heavy code can become difficult to work with when the tools lag behind the practices. I want to spend some time
digging into PhantomJS to see if it is possible to hook into events to make debugging easier. I spent some time digging around but it is
early days.

I'm also interested in see if it would be possible to get more information on memory usage. Identifying DOM leakage is difficult. And of
course identifying it on webkit is only going to help for browsers based on webkit however it would be a start. I would expect there to
be more tools to help with this but I want tools I can run on the command line and have interfaces which can be used with tests.

In short, the developer tools with Chrome and other browsers are phenomenal however sometimes things seem more painful than
they should be. Note that I am not blaming the tools but rather pointing out it seems like some don't exist yet.


Apprenticeship
--------------

I took on a novice apprentice named Andrew beginning in January, 2013. It has been challenging his pipeline full while keeping up with
all the other regular duties however it has also been rewarding to see the apprenticeship from the other side. He has made great
progress with picking up TDD and with programming in general.

Waza
----

At 8th Light, we have Friday afternoons to work on whatever we would like to. I have been spending my time working on Abacus which is
an invoicing system. The front end is written in Backbone.js with Mustache templates and the backend is in Ruby on Rails. The purpose
of the system is to produce a PDF which has the invoice. I've started to move that to Clojure and iText after becoming frustrated with
Prawn (Ruby PDF generation). Prawn is very capable however it has been hard to keep it from turning into a big ball of mud. I've also
been working on putting Cucumber tests on the application using poltergiest (PhantomJS wrapped to use with Cucumber). The idea is to
make it easier to simplify the backend so that it doesn't have the requirement to generate PDFs and make it possible to refactor the
application without breaking it.
