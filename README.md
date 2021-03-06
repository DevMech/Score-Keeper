Score-Keeper
==================

A simple iOS app with a single scroll view with score fields and stepper buttons.

###Step 1: Create a Navigation Controller
- Clone down this project (or create a new single view controller in Xcode)
- Create a UIViewController called ScoreViewController
- In the AppDelegate didFinishLaunching method initialize a UINavigationController with a scoreViewController instance as the rootViewController
- Make the navigationController the rootViewController of the window.

###Step 2: Set the ScrollView and Title
- Add a scrollView property to your class
- Initialize the scrollView and add it to the main view of scoreViewController
- Set the title of the view controller "Score Keeper"

###Step 3: Create an addScoreView method that takes an integer (index)
- Create an addScoreView method that will add a UIView to the scrollView
- In the method Initialize a UIView called view
- Initialize a UITextField for name, a UILabel for score, and a UIStepper for a button
- Lay them out by setting their frames in the new view
- Add that view to the scrollview
- You'll want to adjust the properties of each of those controls: 
  - Placeholder text for the textfields
  - Min and max values for the stepper
  
###Step 4: Store your scoreLabels
- Create a mutable array property called scoreLabels
- In the addScoreView method set the tag of your stepper to the index you passed in
- In the addScoreView method add the scoreLabel to your scoreLabels array

###Step 5: Add a target action to the stepper
- Create an action method for when the score stepper value changes
- Add self as target for the control event ValueChanged to the score stepper
- In the action method capture the value of the stepper
- Get the label from the array of labels that is at the index matching the tag of stepper
- Update the text of the label to match the value of the stepper

###Step 6: Dismiss the keyboard when done editing name
- Set self as the delegate of the nameTextField
- Add a textFieldShouldReturn delegate method
- In that method have the textField resign firstResponder


###Black Diamond
- **Add buttons that add and remove score rows**
  - Create an array property that holds views
  - Store your scoreView in the array at the end of the addScoreView method
  - Create a removeLastScore method
    - Grab the last view in the scoreViews array and remove it from the view
    - Remove that object from the scoreViews array
  - Add 2 UIButtons as class properties 
  - Create an updateButtonView method
    - In the updateButton method check to see if they have already been initialized
      - If they haven't, initialize them and add them to the scrollview
      - Give the addScore button a title "Add Score"
        - Add self as the target of the addScore button and call the addScoreView method with controlEvent TouchUpInside
      - Give the removeScore button a title "Remove Score"
        - Add self as the target of the removeScore button and call the removeLastScore method with controlEvent TouchUpInside
    - Set the frames of the buttons based on the number of views in the scoreView array, so that they are always below the scores
  - Update the scrollViewContentSize based on the number of views in the scoreView array plus the add/remove buttons
  

- **Allow the user to edit score in the scoreTextField**
  - Change the scoreLabel to a ScoreTextField
  - Set the scoreTextField enabled to YES
  - Set self as the delegate of the scoreTextField
  - Add a textFieldShouldReturn delegate method
  - In the method check if the textField's tag is -1 (which means it's a name field)
  - If the textField's tag is not -1, get the score stepper at the index of the textField's tag
  - Update the value of the score stepper to the double value of the text

