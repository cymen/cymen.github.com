---
date: '2012-06-11 16:42:00'
layout: post
slug: pairing-tour-josh-cheek 
status: publish
title: 'Pairing tour: Josh Cheek'
categories:
- 8th Light
- Apprenticeship 
---

I met [Josh](http://www.8thlight.com/our-team/josh-cheek) downtown for the first of two pairing days. On the way in, I ran into Craig, Chris and Mark who were also onsite at the same client. The project is a large web application that relies on a number of compartmentalized Rails applications. The setup was interesting and not without some minor issues.

Josh picked up a 3.3 point story and we started working on it. The compartmentalization meant it took a little while to figure out where things were and how they tied together but pairing makes that all much easier. One of the interesting side effects of the compartmentalization is that when communicating from one Rails instance to another the controller input gets converted to strings. So for example, a boolean value of true gets converted to the string 'true'. However that was not true in testing depending on where we were injecting values. So the code ended up looking a bit like this:

        if (params[:my_boolean].to_s == 'true')
          ...

The `to_s` would handle the case where the tests injected a boolean value and the case where the controller action parsed the input to a 'true' string.

I did think the setup was interesting as it compartmentalized testing. I only read a small portion of the code base but I could imagine that if it were all combined into one large application it would be painful in other ways. So it's not really a case of good and bad but just knowing what the trade offs are and being prepared for them.

While coding with Josh I was thrown off a couple times by RSpec matchers that I didn't know about. It was exciting to learn about some of them and it was clear that I should learn some more RSpec. At the end of the day, we had completed the 3.3 point story and Josh paired with another person on another 0.5 point story to set some configuration data. It made me happy that our work implemented the required functionality without overly complicated tests or an excessive number of lines of code (each line was warranted).
