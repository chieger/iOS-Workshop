#iOS Workshop

##Tpsy (Tip Calculator App)
###1.  Create a new Xcode Project
  * Select **Single View Application**
  * Set *Language* to **Swift**
  * Set *Devices* to **iPhone**

###2.  Orientation and Initial Setup
  * **Play** and **Stop** Button for deploying App to Emulator or Device
  * Select simulated phone or real device
     * When plugging in your phone for the first time, Xcode will download and process symbols. (This takes a minute, but you only have to do this once)
     * If your device is listed as *inelgible device*, you may need to change **Deployment Info -> Deployment Target** to **the version of iOS your device is currently running**
  * Click the *Play* button to build and run your app
  * Left side folders, **Image Assets** and **StoryBoard**
  * Click the Storyboard
     * Uncheck the *Use Auto Layout* checkbox 
     * Disable size classes  
![|800](http://i.imgur.com/zjqYSUT.gif)  

###3. Build out Static View based on Mock
  * Typsy Mock  
<src img="http://i.imgur.com/VLZWM0d.png" width="250" />  
  
  * In the object library (bottom of utilities pane, right side of screen), search for **uilabel** 
  * Drag a **uilabel** onto the screen (ViewController) in the location where *Bill Amount* is in the mock.
  * Use ``opt + drag`` to clone the uilabel.
     * position cloned labels in the positions where *Tip*, *Total*, and their respective *amounts* appear in the mock.
  * Double click on the labels to add the correct **text** (add fake, temporary **$ amounts** for the *amount* labels)  
![|800](http://i.imgur.com/s5WgRWi.gif)  
  * Extend the uilabels for the *amounts* to make room for a big tip :) 
  * Click the Attributes inspector icon
     * Set *Alignment* for each *amount label* to **right justify**   
     * Set *Font* to **System Bold**	, *Size* **30** for the *Total* Label and *Total Amount* Label.
     * Use ``cmd + =`` to auto resize the label to fit the contents.  
![|800](http://i.imgur.com/U8NKdXY.gif) 
  * In the object library, search for **uiview**
  * Drag a **uiview** onto the ViewController
  * Drag to resize the uiview to match the bar in the mock.
  * In the **Attributes Inspector** Change the background color to *Dark Grey Color*
![|800](http://i.imgur.com/bm0bShS.gif)
  * Add uitextview for *Bill Amount*
    * In the object library (bottom of utilities pane, right side of screen), search for **uitextfield**  
    * Drag and drop the *textfield* so it is positioned in the *Bill Amount* area of the ViewController.
![|800](http://i.imgur.com/yPNmeVO.gif) 

  * Add **Segmented Control**
     * In the object library (bottom of utilities pane, right side of screen), search for **segmented control**  
     * Drag and drop the segemented control into position.
     * Drag the edges to resize the segmented control.
     * In the *Attributes Inspector*
        * Set **Segments** to **3**
        * Use the **Segment** drop down menu to select which segment title you want to edit.
        * Change the title of each segment to 18%, 20% and 25% respectively.
![|800](http://i.imgur.com/0bwbBVc.gif) 

  * Run your App!!!  
 ![|800](http://i.imgur.com/QyHIM9o.gif) 
 
###4. Program Dynamic Behavior
* Hide the Navigator and utilities panes by clicking the outer left and right icons in the upper conner of Xcode.
* Click on the "Venn Diagram" icon near the top right of Xcode. This opens up the **Assistant Editor**. 
![|800](http://i.imgur.com/yyiJTn8.gif)
* Add Outlets for all the Amount Labels and Fields
  * ``ctrl + drag`` from the label or field in the Storyboard to right beneath the ``class ViewController: UIViewController {`` in the **Assistant Editor**.
  * Naming
     * Use "camelCase" naming convetion. 
     * name should include, function i.e "tip" + object type i.e "label" combined i.e "tipLabel".
![|800](http://i.imgur.com/M6DAxDO.gif)
* **COMMON ERROR!** this class is not key value coding compliant fro the key...
  * Fix it
    * Click on the yellow button at the top of your view controller.
    * In the Utilities pane, click on the **Conections Inspector** icon (circle with arrow at top far right)
    * Look for the *conection* with an ``!`` to the right of it and delete it by clicking the little ``x`` button.
    * Hide the Utilities Pane and return to the Assistant Editor.
    * Highlight and delete the outlet you created.
    * Hook up a fresh outlet by ``ctrl + drag`` from object to your code file.
![|800](http://i.imgur.com/B16oB50.gif)

* Configure/initialize labels
  * Within the ``viewDidLoad`` method add...

```Swift
tipLabel.text = "$0.00"
totalLabel.text = "$0.00"
```
![|800](http://i.imgur.com/HZAR1aG.gif)

* Change keyboard to numeric keypad
  * Click on **text field**
  * Utilities -> Attributes Inspector -> Keyboard Type -> **Decimal Pad**   
![|800](http://i.imgur.com/7p1BUKv.gif)  

* Update **tip** and **total** fields when **Bill Amount** is entered into ``billField``.
  * Create an Action by ``ctrl + dragging`` from the ``billField`` down to the bottom of your code file but above the last *curly brace* ``}``
     * Set the *Connection* to **Action**
     * Set the *Event* to **Editing Changed**
     * Name, ``onEditingChanged``
     * Click, **Connect**
  * Within the curly braces of the ``onEditingChanged`` method you just created, add...

```Swift
println("user editing bill")
```
* Run the app and look for output in he console at the bottom of Xcode.
 ![|800](http://i.imgur.com/rDTIcmY.gif)
 
* Create a variable to hold the amount typed into ``billField`` and convert it to a ``double``.

```Swift
 var billAmount = NSString(string: billField.text).doubleValue
```
* Compute and store the tip and total amounts (hard coded to 20% or 0.2 for now)

```Swift
var tip = billAmount * 0.2
var total = billAmount + tip 
```

* Set text of **tip** and **total** fields.

```Swift
tipLabel.text = "\(tip)"
totalLabel.text = "\(total)"
``` 
* Run your project  
![|300](http://i.imgur.com/IarRUMY.gif)

* Format ``tipLabel`` and ``totalLabel`` to show the correct amount of decimals.

```Swift
 tipLabel.text = String(format: "$%.2f", tip)
 totalLabel.text = String(format: "$%.2f", total)
```

* Run your App  

![|300](http://i.imgur.com/pFEFhVS.gif)

* Dismiss Keyboard
  * In the object library, search for **gesture** 
  * drag and drop a **Tap Gesture Recognizer** onto the screen
  * Add an **Action** by ``ctrl + Drag`` from the gesture recognizer icon (that appears on the top part of the ViewController) to the bottom of the Assistant editor code file, just below the previous method you created.
  * Set the *Connection* to **Action**
  * Name, ``didTap``
  * Click, **Connect**  

![|800](http://i.imgur.com/0v3F1m1.gif)

  * Within the ``didTap`` method, add...

```Swift
view.endEditing(true)
```
* Run Your App  

![|300](http://i.imgur.com/aqcc7gu.gif)

* Configure the tip percentage buttons

  * At the top of your ``onEditingChanged`` method, create an array for the different percentage values

```Swift
var tipPercentage = [0.18, 0.2, 0.25]
```
  * Create an Outlet for the segmented tip controller.
  * Add an **Outlet** by ``ctrl + Drag`` from the **segmented control** to the top of the Assistant editor code file, with all your other outlets  
  * Set the *Connection* to **Outlet**
  * Name, ``tipControl``
  * Click, **Connect**   

![|800](http://i.imgur.com/ltD7HPS.gif) 

  * In order to grab a single tip Percentage from your ``tipPercentages`` array, use...

```Swift
var tipPercentage = tipPercentages[tipControl.selectedSegmentIndex]
```
  * Change your hard coded tip percentage in ``billAmount`` to ``tipPercentage``

```Swift
var tip = billAmount * tipPercentage
```
* Update tip amount when tip controller is changed
  * Right-Click on the segmented control to bring up methods that are called on it.
  * ``ctrl + drag`` from **value changed** to your ``onEditingChanged`` in the Assistant Editor window. Now, when there is a change with the segmented control, it will call the ``onEditingChanged`` method and update everything.

![|800](http://i.imgur.com/1dPYXhD.gif) 

* Run your app

![|300](http://i.imgur.com/6plXL5Z.gif)

##Now Don't Forget to tip your Bartender!!!




