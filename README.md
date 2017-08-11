# Drupal Horizontal Tabs

Module for Drupal 8 that adds 'horizontal_tabs' form element, similar to the
'vertical_tabs' element that is already included in core.

The 'vertical_tabs' form element in core is a great addition to Form API in
Drupal 8, which let's you easily add vertical tabs to any form with a minimum
amount of code to write. Unfortunately there isn't a corresponding horizontal
tabs form element.

I've only found an issue in the issue queue on drupal.org, that isn't really
frequented very much: https://www.drupal.org/node/1168364.

This module aims to fill this gap. It's basically a shameless 1:1 copy of core's
vertical tab form element (renamed everything to horizontal of course) with an
adjusted CSS that displays the tabs horizontally instead of vertically. This
makes it exactly as easy to use as the vertical_tabs element, meaning that you
could easily swap any usage of vertical tabs to horizontal ones just by
changing the form elements type form 'vertical_tabs' to 'horizontal_tabs'.

## Important Notes

**Note that the [field_group module](https://www.drupal.org/project/field_group)
already offers already horizontal tabs.**

So it's a legitimate question why I started this project instead of just using
that one. The answer is: I tried to but I failed.

Field group is great to use, as long you want to use it on entity forms and
define and configure the field groups via Field UI. As soon as you want to use
e.g. their horizontal tabs in any other form than an entity form, things get
complicated (it's maybe even impossible to do so), as it seems to be closely
coupled to entity forms (e.g. it relies on having entity type and bundle defined
while making theme hook suggestions).

It even gets complicated, if you want it to use in an entity form
programmatically. There's a lot of more stuff you will have to define in your
form. When I tried to accomplish this, I have found myself digging more and more
into the form processing that is happening inside field_group.module, trying to
rebuild the necessary parts. When I then saw that the extra stuff I've added to
my form elements were removed inside another processing step of field group,
I've decided to rather build a lightweight solution for my problem that
orientates on core's vertical tabs instead. I've accomplished that in about
half an hour, while I was before trying to fix the field_group approach for a
couple of hours.

## Compatibility, Status and next steps

While I haven't tried it so far, it's theoretically impossible that you can have
this module AND field_group installed on the same site, because both modules
are defining a form element named 'horizontal_tabs'. There can't be two
different form elements with the same ID.

You may now ask, why I then was so stupid to don't assign any other name. There
are a few good reasons why I did that:

* 'horizontal_tabs' is the only logical name, especially to emphasize the close
  relationship to core's 'vertical_tabs'.
* If core ever wants to add such an element, it would have exactly this ID. In
  that case, field_group would be forced to rename it anyway or refactor to
  build on top of it. Additionally, my module here would get deprecated anyway
  at that point because this functionality would have then got merged 1:1 in
  core.
* I'm hoping/trying to contact field_group maintainer(s) and advocate for
  refactoring their form element in a way that it can be used in exactly the
  same matter as this module, which I could then also deprecate.

### Status

This module is basically stable, usable and more or less in a final state
already. The only enhancements and changes I could imagine would be maybe a CSS
optimization and of course unit tests. Both are things I don't plan to work on
in the near future. So this would have to come from the community.

The only reason, why I currently only host this project on Github instead of
drupal.org, is that I first want to clarify if there's the need for another
standalone project on drupal.org, if there's a chance to get this merged into
field_group or even Drupal Core, and/or if there's enough demand from the
community for this module.

I'd be happy to discuss this either in the issue queue here and/or on Slack or
[Twitter](https://twitter.com/agoradesign_at).

## Credits

Commerce Quantity Increments module was originally developed and is currently
maintained by [Mag. Andreas Mayr](https://www.drupal.org/u/agoradesign).

All initial development was sponsored by [agoraDesign KG](http://www.agoradesign.at/).
