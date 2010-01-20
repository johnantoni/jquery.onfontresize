Tested with jQuery 1.2.3+ in: IE6/7, FF2 (Windows XP), FF2 (OS X), Safari 2.0.4

    * uses an iframe, sized in ems, to detect font size changes and trigger a "fontresize" event
    * heavily based on code by Hedger Wang: http://www.hedgerwow.com/360/dhtml/js-onfontresize.html
    * "fontresize" event is triggered on the document object
    * subscribe to event using: $(document).bind("fontresize", function (event, data) {});
    * "data" contains the current size of 1 em unit (in pixels)

NOTE: Unlike any other "onfontresize" technique I've seen, Hedger's doesn't use a setInterval-style polling mechanism to detect the font size. Instead, it leverages browser native onresize events that are fired when a hidden iframe is sized in ems.

KNOWN ISSUES: Depending upon how the base font size in your document is specified (em, %, or keyword) the "pixels per em" calculation may not be consistent across browsers. Also, the event doesn't fire in IE if fonts are sized in px units.

// execute this code then use the browser
// font controls to see the event in action

$(document).bind("fontresize", function (event, data) {
	$("#log").val(data + "px");
});