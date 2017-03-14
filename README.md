# vacationPlanner
This is a tutorial for learning how to use basic animations.

  <div style="text-align:center"><img src ="https://github.com/samkerm/vacationPlanner/blob/master/appScreenShot.png" /></div>
  
  Thank you for visiting our account. We are going to learn about some basic animations by making a Vacation Planner app login page in an hour. If would you like to study yourself before hands-on, or review what you have learned in the session, please use the following material.

## Meetup
  We are providing free hands-on on a monthly basis<br>
  https://www.meetup.com/iOS-Development-Meetup-for-Beginner/

## Do you need a tutor?
  We also hold face-to-face or group lesson for individual interested in making iOS app themselves<br>
  http://ios-class-for-beginner.esy.es/

## Development Environment
  XCode 8.1 / Swift 3

## Full procedure

#### 0, Create your project

> 0-1. Open XCode  

> 0-2. Select "Create a new XCode project"

> 0-3. Select "Single View Application" and then tap "Next"

> 0-4. Fill "Product name" and then tap "Next"

> 0-5. Select the place for saving your project and then tap "Create"

#### 1, Collect photos → Drag & Drop your resources into your project
  <a href="https://github.com/iosClassForBeginner/musicPlayer-en/blob/master/Resources/1.gif">resources</a>
  <div style="text-align:center"><img src ="https://github.com/samkerm/vacationPlanner/blob/master/Resources/vid1.gif" /></div>

#### 2, Design app
> 2-1. Drap & Drop "UIImageView" from UI components
  <div style="text-align:center"><img src ="https://github.com/samkerm/vacationPlanner/blob/master/Resources/vid2.gif" /></div>

> 2-2. Resize the imageView
  <div style="text-align:center"><img src ="https://github.com/samkerm/vacationPlanner/blob/master/Resources/vid3.gif" /></div>

> 2-3. Set "Autoresizing" for adjusting frame depending on devices
  <div style="text-align:center"><img src ="https://github.com/samkerm/vacationPlanner/blob/master/Resources/vid4.gif" /></div>

> 2-5. Specify the image name and content mode
  <div style="text-align:center"><img src ="https://github.com/samkerm/vacationPlanner/blob/master/Resources/vid5.gif" /></div>

> 2-5. Add UIButton in the same process from 2-1 to 2-3
  <div style="text-align:center"><img src ="https://github.com/samkerm/vacationPlanner/blob/master/Resources/vid6.gif" /></div>
  <div style="text-align:center"><img src ="https://github.com/samkerm/vacationPlanner/blob/master/Resources/vid7.gif" /></div>  
  
> 2-6. Connect UI components on Storyboard to ViewController.swift
  ★  control + drag in storyboard to create a control segue<br>
  <div style="text-align:center"><img src ="https://github.com/samkerm/vacationPlanner/blob/master/Resources/vid8.gif" /></div>

#### 3, Add code blocks in ViewController.swift
  ★  It's preferable to write following code yourself. It will help you to understand code more.

```Swift  
import UIKit

class ViewController: UIViewController {

    // MARK: IB outlets
    
    @IBOutlet weak var usernameButton: UITextField!
    @IBOutlet weak var passwordButton: UITextField!
    @IBOutlet weak var loginButton: UIButton!

    // MARK: further UI
    
    let spinner = UIActivityIndicatorView(activityIndicatorStyle: UIActivityIndicatorViewStyle.white)
    
    
    // MARK: IB actions
    
    @IBAction func login(_ sender: Any) {
       
        spinner.isHidden = !spinner.isHidden
        
    }
    
    // MARK: view controller methods
    
    
    // Gets called once during loading of the view
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        //set up the UI
        loginButton.layer.cornerRadius = 8.0
        loginButton.layer.masksToBounds = true
        
        spinner.frame = CGRect(x: -20.0, y: 6.0, width: 20.0, height: 20.0)
        spinner.startAnimating()
        spinner.center = CGPoint(x: spinner.bounds.midX + 5.0,
                                 y: loginButton.bounds.midY)
        loginButton.addSubview(spinner)
        
    }
    
    // Gets called every time before view appears
    
    override func viewWillAppear(_ animated: Bool) {
        usernameButton.center.x  -= view.bounds.width
        passwordButton.center.x -= view.bounds.width
        loginButton.center.x -= view.bounds.width
    }
    
    // Gets called right after the view apears
    
    override func viewDidAppear(_ animated: Bool) {
        
        spinner.isHidden = true
        
        UIView.animate(withDuration: 0.5, animations: {
            self.usernameButton.center.x += self.view.bounds.width
        })
        
        UIView.animate(withDuration: 0.5, delay: 0.3, options: [], animations: {
            self.passwordButton.center.x += self.view.bounds.width
        }, completion: nil)
        
        UIView.animate(withDuration: 0.5, delay: 0.4, options: [], animations: {
            self.loginButton.center.x += self.view.bounds.width
        }, completion: nil)
    }

    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
        // Dispose of any resources that can be recreated.
    }


}

```
