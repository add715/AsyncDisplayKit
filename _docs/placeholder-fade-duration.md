---
title: Placeholders
layout: docs
permalink: /docs/placeholder-fade-duration.html
prevPage: image-modification-block.html
nextPage: layer-backing.html
---

## ASDisplayNodes may Implement Placeholders

Any `ASDisplayNode` subclass may implement the `-placeholderImage` method to provide a placeholder that covers content until a node's contents are finished displaying. To use placeholders, set `.placeholderEnabled = YES` and optionally set a `.placeholderFadeDuration`;

For image drawing, use the node's `.calculatedSize` property.

<div class = "note">
The <code>-placeholderImage</code> function may be called on a background thread, so it is important that this function is thread safe. Note that <code>-[UIImage imageNamed:]</code> is not thread safe when using image assets. Instead use <code>-[UIImage imageWithContentsOfFile:]</code>.
</div>

See our ancient <a href="https://github.com/facebook/AsyncDisplayKit/tree/master/examples_extra/placeholders">Placeholders sample app</a> to see this concept, first invented by the Facebook Paper team, in action. 

## `.neverShowPlaceholders`

Hear <a href="https://youtu.be/RY_X7l1g79Q">Scott Goodson explain</a> placeholders, `.neverShowPlaceholders` and why UIKit doesn't have them.  

## ASNetworkImageNode also have Default Images

In _addition_ to placeholders, `ASNetworkImageNode`s also have a `.defaultImage` property. While placeholders are meant to be transient, default images will persist if the image node's `.URL` property is `nil` or  if the URL fails to load. 

We suggest using default images for avatars, while using placeholder images for photos. 