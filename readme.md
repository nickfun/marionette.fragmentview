# FragmentView

This is a plugin for [Marionette](https://github.com/marionettejs/backbone.marionette), an execellent JavaScript framework. 

## Goals

A FragmentView is a replacement for the standard CollectionView provide by Marionette. It internally uses a Document Fragment to handle rendering
its collection of ItemViews. This should lead to some performance gains.

## Differences

A CollectionView is given a collection and it will listen for `add` events. When an `add` event happens, the CollectionView will
build an ItemView for the added model and immediatly render it to the CollectionView.$el.

A FragmentView is also given a collection, and it also listens for `add` events. However, when the event happens a ItemView is created 
and appended to an internal managed Document Fragment. The created ItemView is not immediatly rendered. The DOM is not touched when an `add` event is fired.

Instead, the FragmentView waits for `render()` to be called on it, or for the `ready` event to be fired on the collection. At that point, the Document Fragment
is added to the DOM.
