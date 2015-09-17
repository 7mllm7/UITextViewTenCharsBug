# UITextViewTenCharsBug
This project reproduces a bug where UITextView with less than 10 characters set as text will hang iOS app on iOS 9.

Stackoverflow post: http://stackoverflow.com/questions/32611789/uitextview-with-text-less-than-10-characters-hangs-ios-9

I also submitted a bug report to Apple (bug no. 22736256, although you probably can't see it there yet).

## Summary:
Starting from iOS 9.0 (13A4325c) and Xcode 7.0 beta 6 (7A192o) (and probably later versions), an Objective-C app with UITextView will hang if the text view's text is less than 10 characters long. CPU usage goes up to 99-100% and the whole system hangs.

## Steps to Reproduce:
1. Create a brand new single view app from template (or anything else).
In storyboard, add a UITextView with default settings anywhere in the main view.
2. Set the text to a string that is less than 10 characters long.
3. Launch the app in simulator (any device, as long as it's iOS 9).
4. Upon launch, before displaying the single view, the system will hang and CPU usage will go to maximum forever.
5. Set the text to any other text that's more than 10 characters and the app runs correctly.a

Looks like constraints or any other settings do not affect this behaviour.

## Expected Results:
UITextView should show text that is less than 10 characters long

## Actual Results:
System hangs (CPU 100% usage), UI does not respond, code execution does not continue.

## Version:
iOS 9.0 (13A4325c) and Xcode 7.0 beta 6 (7A192o), and probably later

## Configuration:
Any iPhone/iPad (incl. simulator)
