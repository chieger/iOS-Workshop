#iOS Workshop

##Typsy App
1.  Create a new Xcode Project
  * Select **Single View Application**
  * Set *Language* to **Swift**
  * Set *Devices* to **iPhone**

1.  Orientation
  * **Play** and **Stop** Button for deploying App to Emulator or Device
  * Select simulated phone or real device
     * When plugging in your phone for the first time, Xcode will download and process symbols. (This takes a minute, but you only have to do this once)
     * If your device is listed as *inelgible device*, you may need to change **Deployment Info -> Deployment Target** to **the version of iOS your device is currently running**
  * Click the *Play* button to build and run your app
  * Left side folders, **Image Assets** and **StoryBoard**

3.  Storyboard
  * Disable size classes  
![|800](http://i.imgur.com/zjqYSUT.gif)

4. Build out Static View based on Mock
  * Typsy Mock  
![|300](http://i.imgur.com/VLZWM0d.png)  
  * In the object library (bottom of utilities pane, right side of screen), search for **uilabel** 
  * Drag a **uilabel** onto the storyboard in the location where *Bill Amount* is in the mock.
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


