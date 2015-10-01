## Week 2 Project: Carousel

**Due:** {{PROJECT(2) | longdate}} at 11:59pm

### Overview

The purpose of this homework is to leverage views, view properties, and events to create a high fidelity prototype that is difficult to distinguish from a production app. We're going to use the techniques from this week to implement the Carousel app from the signed out state to the basic signed in state.

![Carousel GIF|250](http://i.imgur.com/TBJkE46.gif)

### Project Requirements

- Static photo tiles on the initial screen
  - Optional: Photo tiles move with scrolling
- Sign In
  - Tapping on email/password reveals the keyboard and shifts the scrollview and Sign In button up.
  - User sees an error alert when no email is present or no password is present.
  - User sees a loading screen upon tapping the Sign In button.
    - `alertController.dismissViewControllerAnimated(true, completion: nil)` dismisses the alert controller loading screen with no buttons.
  - User sees an error alert when entering the wrong email/password combination.
  - User is taken to the tutorial screens upon entering the correct email/password combination.
  - Optional: When the keyboard is visible, if the user pulls down on the scrollview, it will dismiss the keyboard.
  - Optional: On appear, scale the form up and fade it in.
- Optional: Sign Up
  - Optional: Tapping in the form reveals the keyboard and shifts the scrollview and "Create a Dropbox" button up.
  - Optional: Tapping the Agree to Terms checkbox selects the checkbox.
  - Optional: Tapping on Terms shows a webview with the terms.
  - Optional: User is taken to the tutorial screens upon tapping the "Create a Dropbox" button.
- Tutorial Screens
  - User can page between the screens
  - Optional: User can page between the screens with updated dots
  - Optional: Upon reaching the 4th page, hide the dots and show the "Take Carousel for a Spin" button.
- Image Timeline
  - Display a scrollable view of images.
  - User can tap on the conversations button to see the conversations screen (push).
  - User can tap on the profile image to see the settings view (modal from below).
- Settings
  - User can dismiss the settings screen.
  - User can log out
- Optional: Learn more about Carousel
  - Optional: Show the "Learn more about Carousel" button in the photo timeline.
  - Optional: Tap the X to dismiss the banner
  - Optional: Track the 3 events:
     - View a photo full screen
     - Swipe left and right
     - Share a photo
  - Optional: Upon completion of the events, mark them green.
  - Optional: When all events are completed, dismiss the banner.

### Assets

You can download the Carousel assets [here](https://www.dropbox.com/s/53llomcr20qicxo/Carousel%20Assets.zip).

### Milestones

The key to implementing a complex app is to break it up into a bunch of small pieces until it's easy to implement any given piece. You should try implementing this homework by following the milestones below. Be sure to run the simulator frequently as you hit milestones.

0. **Setup:**
  - Create a new project (disable Auto Layout). [New Project](https://guides.codepath.com/ios/New-Project-%28designers%29)
  - Add the image assets above. [Adding Image Assets](https://guides.codepath.com/ios/Adding-Image-Assets)
  - Configure the app icon and splash screen. [App icon and launch image](https://guides.codepath.com/ios/Adding-Image-Assets#app-icon-and-launch-image)
  - Add the [Common.swift](https://www.dropbox.com/s/van89swo47j0im1/Common.swift?dl=0) file to your project. Be sure to select "Copy items if needed".
1. **Intro Screen**
  - In the Storyboard, add a custom view controller for the IntroViewController. [Creating Custom View Controller](https://guides.codepath.com/ios/Creating-Custom-View-Controllers)
  - Configure the view controller to be freeform, so that you can make it long enough to see the entire intro page. [Creating Free Form View Controller](https://guides.codepath.com/ios/Creating-a-Free-Form-View-Controller)
  - Add UIImageViews for each photo tile in the region below. [Using UIImageView](https://guides.codepath.com/ios/Using-UIImageView)
  - Configure the content size of the scroll view. [Using UIScrollView](https://guides.codepath.com/ios/Using-UIScrollView)
  - **Optional:** Tiles translate, scale and rotate into place as user scrolls
     - Register for the scroll view scroll events [Registering for scroll events](https://guides.codepath.com/ios/Using-UIScrollView#registering-for-scroll-events)
     - Whenever a scroll event happens, configure the transform property on the image view. [Using View Transforms](https://guides.codepath.com/ios/Using-View-Transforms)
2. **Sign In**
  - Add all the view elements for the Sign In View Controller in Storyboard
     - Sign in nav bar as UIImageView 
     - UIScrollView
     - Form the background with a blank UIView 
     - Sign In text as UIImageView 
     - Sign In Form as UIImageView
     - UITextFields for email and password
     - Sign In button as UIImageView
     - UIButton placed over Sign In button, transparent
  - Tapping the Sign In button
     - If either of the email or ``||`` password fields are blank, ``textField.text!.isEmpty``, show an error alert using a UIAlertViewController. [Using UIAlertController](https://guides.codepath.com/ios/Using-UIAlertController)
     - If the populated email and ``&&`` password fields have incorrect credentials:
        - Display an UIActivityIndicator for 2 seconds using a delay closure.
        - After the delay, display an error for incorrect email/password using a UIAlertController. ([Calling a Method After Delay](https://guides.codepath.com/ios/Calling-a-Method-After-Delay)):
     - If the populated email and ``&&`` password fields contain the correct credentials:
        - Display an UIActivityIndicator for 2 seconds using a delay closure.
        - After the delay, transition to the tutorial screen
           - Create a modal Segue from the Sign In UIViewController to the Tutorial UIViewController
           - Trigger the segue, ``performSegueWithIdentifier("loginSegue", sender: nil)``
  - **Optional** The scrollview should only be scrollable when the keyboard is shown.
     - ``scrollView.scrollEnabled = true``, ``scrollView.scrollEnabled = false``
3. **Tutorial Screens**
  - Create a custom free form view controller that is wide enough for 4 screens. [Creating Custom View Controllers](https://guides.codepath.com/ios/Creating-Custom-View-Controllers), [Creating a Free Form View Controller](https://guides.codepath.com/ios/Creating-a-Free-Form-View-Controller)
  - Add a UIScrollView with paging enabled. 
  - Add 4 UIImageViews for the welcome screens (Note: we're explicitly not using UIPageViewController, which requires extra coding, to build these screens)
  - Add a UIPageControl 
     - The UIPageControl should be outside and in front of the scrollview. 
     - Set the page of the UIPageControl by referencing events from the UIScrollView. [Using UIPageControl](https://guides.codepath.com/ios/Using-UIPageControl)
  - Add the "Take Carousel for a Spin" button (should be outside the scrollview). 
     - Set the button to have an initial alpha of 0, 
     - Upon reaching the 4th page, the alpha should be set to 1 
  - Tapping the "Take Carousel for a Spin" button should launch the Image Timeline modally.
     - Since the Image Timeline will have a NavigationController, the above modal Segue should point to the Image Timeline NavigationController. 
4. **Image Timeline**
  - Add a UIImageView for the custom nav bar
  - Add a UIScrollView for the image feed.
  - Add UIButtons for Settings and Conversations.
  - Tapping the Conversation button should *push* the ConversationsViewController.
  - Tapping the Settings button should *modally* present the SettingsViewController.
5. **Create Account**
  - Add custom nav bar, form background, text fields, text, terms text and button, and Create Account button.
  - Add all the view elements for the Sign In View Controller in Storyboard
     - Sign in nav bar as UIImageView 
     - ScrollView
     - Form the background with a blank UIView 
     - Sign In text as UIImageView 
     - Sign In Form as UIImageView
     - UITextFields for email and password
     - Sign In button as UIImageView
     - transparent UIButton placed over Sign In button
  - Upon showing the keyboard, move the elements to be visible. [Registering for Keyboard Events](https://guides.codepath.com/ios/Registering-for-Keyboard-Events)
  - Add a selected state for the terms button. [Configure a Button](https://guides.codepath.com/ios/Configure-a-Button)
  - Terms opens webview w/ mobile terms of service page.

### Submission instructions

Follow the guide for [[Submitting Assignments]]. Remember to include an animated gif and # of hours spent in the README.
