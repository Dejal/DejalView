DejalView
=========

DejalView is a UIView subclass to detect a tap outside a button (or other view) like UITableView's red Delete button.


Donations
---------

I wrote DejalView for my own use, but I'm making it available for the benefit of the iOS developer community.

If you find it useful, a donation via PayPal (or something from my Amazon.com Wish List) would be very much appreciated. Appropriate links can be found on the Dejal Developer page:

<http://www.dejal.com/developer>


Latest Version
--------------

You can find the latest version of this code via the GitHub repository:

<https://github.com/Dejal/DejalView>

For news on updates, also check out the Dejal Developer page or the Dejal Blog filtered for DejalView posts:

<http://www.dejal.com/blog/dejalview>


Requirements
------------

- Xcode 4 or later for the `weak` attribute and lack of ivars.
- Should work with all versions of iOS.
- Should work with or without ARC.


Features
--------

- Adds a viewDelegate property to the view.
- If set, a `-view:hitTest:withEvent:hitView:` method is invoked on the delegate.
- That delegate method can return the passed view to act normally, or return nil to ignore the tap.


Usage
-----

Include the DejalView.h and DejalView.m files in your project.

Then simply change a container UIView to DejalView in the view hierarchy, then set the delegate property to your view controller (via code or IB):

	self.view.viewDelegate = self;

Then implement the `-view:hitTest:withEvent:hitView:` delegate method in your view controller, e.g. as follows -- this will cause a tap on some special control (or if that control is hidden) to go through as normal, but tapping anywhere else in the view will hide the special control, without passing the tap on to whatever was actually tapped:

	- (UIView *)view:(DSView *)view hitTest:(CGPoint)point
		   withEvent:(UIEvent *)event hitView:(UIView *)hitView;
	{
		if (someSpecialControl.hidden || hitView == someSpecialControl)
			return hitView;
		
		someSpecialControl.hidden = YES;
		
		return nil;
	}


License and Warranty
--------------------

This code uses the standard BSD license.  See the included License.txt file.  Please also see the [Dejal Open Source License](http://www.dejal.com/developer/license/) web page for more information.

You can use this code at no cost, with attribution.  A non-attribution license is also available, for a fee.

You're welcome to use it in commercial, closed-source, open source, free or any other kind of software, as long as you credit Dejal appropriately.

The placement and format of the credit is up to you, but I prefer the credit to be in the software's "About" window or view, if any. Alternatively, you could put the credit in the software's documentation, or on the web page for the product. The suggested format for the attribution is:

> Includes DejalView code from [Dejal](http://www.dejal.com/developer/).

Where possible, please link the text "Dejal" to the Dejal Developer web page, or include the page's URL: <http://www.dejal.com/developer/>.

This code comes with no warranty of any kind.  I hope it'll be useful to you, but I make no guarantees regarding its functionality or otherwise.


Support / Contact / Bugs / Features
-----------------------------------

I can't promise to answer questions about how to use the code.

If you create an app that uses the code, please tell me about it.

If you want to submit a feature request or bug report, please use [GitHub's issue tracker for this project](https://github.com/Dejal/DejalView/issues).  Or preferably fork the code and implement the feature/fix yourself, then submit a pull request.

Enjoy!

David Sinclair  
Dejal Systems, LLC


Contact: <http://www.dejal.com/contact/?subject=Dejal+View&ref=dejalview>  
More open source projects: <http://www.dejal.com/developer>  
Open source announcements on Twitter: <http://twitter.com/dejalopen>  
General Dejal news on Twitter: <http://twitter.com/dejal>

