Pull to refresh jquery
======================
Easy to use library for implementing pull-to-refresh to any page. It works especially well for webapps installed on the homescreen. Or you can use it in your app webviews.

How to use
==========
See demo.html, call pull_to_refresh() on a block element and you're done. Easiest would be to point a wrapper element surrounding your entire content. 

The wrapper element will get a 'position: absolute' css style (to support the pulling), and will add a div above your wrapper which will hold the actual pullbar.

<pre>
  $('#wrapper').pull_to_refresh({
    refresh: function(stoploading){
      alert('start reload!');
      stoploading();
    }
  });
</pre>

Options
=======
There are several options available, which you can provide during setup:

<pre>
  var defaults = {
    refresh: function(callback){},
    pull_to_refresh_text: 'Pull down to refresh...',
    letgo_text: 'Release to refresh...',
    refreshing_text: 'Refreshing...',
    status_indicator_id: 'pull_to_refresh',
    refreshClass: 'refresh',
    visibleClass: 'visible',
  };
</pre>

*   refresh

    A function, which will be called when the refresh is triggered, it will get a callback method as only option. You can call this function to have the bar removed again.

*   pull_to_refresh_text
    The text that will show up when the bar is being pulled

* letgo_text

  The text that will show up when the bar is pulled enough to trigger the refresh callback
* refreshing_text

  Text that will show when the bar is let go, and the refresh callback will be triggered
* status_indicator_id

  id of the element to use for the status indicator, you probably won't have to change this
* refreshClass

  Class to be used when bar is being refreshed
* visibleClass

  Class to be used when the bar was pulled far enough to trigger the refresh callback

Problems?
=========
I haven't tested this with other libraries out there (jquery-mobile, iscroll, etc.), so I'm not sure whether this script will interfere with any of those. Then again, they probably provide their own solution :)

Caveats/TODO
============
- I'm not sure if this works on any Android devices, I don't have those around, so if anyone can test, that would be sweet :)
- The element you call will get a position absolute, to support the dragging
- We need to call e.preventDefault() so this will break the default bouncing of your webview, any tips would be appreciated
