# Calculator App
A simple and handy calculator application developed using Swift.
## ***[Copyright and Commercial Use Disclaimer](https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/README.md#please-carefully-read-licensemd-about-the-open-source-restrictions-and-the-personal-use-policy-of-this-project-under-gpl-30-license-any-commericial-uses-on-this-project-by-other-than-the-owner-krystalzhang612-or-the-authorized-users-and-organizations-including-unauthorized-modifications-forks-pull-requests-and-other-commercial-related-uses-will-be-subjected-to-copyright-violation-with-sebsequent-legal-concerns)***

⏬

### ***Please carefully read [LICENSE.md](https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/LICENSE) about the Open Source restrictions and the personal use policy of this project under [GPL-3.0 license](https://www.gnu.org/licenses/gpl-3.0.en.html), any commericial uses on this project by other than the owner [@KrystalZhang612](https://github.com/KrystalZhang612) or the authorized users and organizations, will be subjected to copyright violation with sebsequent potential legal concerns.***


# Build
[Method to Run & Test the Project Locally](https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/README.md#method-to-run--test-the-project-locally)<br/> 
[Synchronous Developing Notes](https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/README.md#synchronous-developing-notes)<br/> 
[Testing Result](https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/README.md#testing-result)<br/> 
[Tags and Topics](https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/README.md#tags-and-topics)<br/> 
# Contribution
[Author](https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/README.md#author)
# Compatibility
|   OS             | Supported          |
| -------          | ------------------ |
| iOS 10+          | :white_check_mark: |
| < iOS 10         | :x:                |
| macOS Mojave     | ✅                 |
| macOS Monterey   | ✅                 |
# Method to Run & Test the Project Locally
### Download the entire project to local directory
### Xcode must be `13.4` and higher versions with all Xcode dependencies updated.
### Compatible with `MacOS Monterey 12.0` or higher versions
### Run the project, choose Simulator `iPhone 14` or `iPhone 14 Pro` for best compatiability.
# 🛠️  Developing Languages, Tools, and Techniques Needed
[Xcode 14.0.1 iOS 16 iPhone 14 Pro Simulator](https://developer.apple.com/documentation/xcode-release-notes/xcode-14_0_1-release-notes)<br/>
[Swift5](https://www.swift.org/blog/swift-5-released/)<br/>
[SwiftUI](https://developer.apple.com/xcode/swiftui/)<br/>
<div>
  <img src ="https://github.com/devicons/devicon/blob/master/icons/xcode/xcode-plain.svg" title ="Xcode" alt ="Xcode" width ="60" height="60"/>&nbsp;
  <img src ="https://github.com/devicons/devicon/blob/master/icons/swift/swift-original.svg"  title ="SWIFT5" alt ="SWIFT5" width ="60" height="60"/>&nbsp;
</div>

# Synchronous Developing Notes
Add IBoutlets in [ViewController.swift](https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/Calculator-App/ViewController.swift):
```swift 
@IBOutlet var holder: UIView!
```
## ***Add buttons:***
Set up the zero button and make it display at the bottom center:
```swift 
 private func setupNumberPad() {
        let buttonSize = view.frame.size.width / 4
        let zeroButton = UIButton(frame: CGRect(x: 0, y:
holder.frame.size.height-buttonSize, width: buttonSize*3, height:
buttonSize))
        zeroButton.setTitleColor(.black, for: .normal)
        zeroButton.backgroundColor = .white
        zeroButton.setTitle("0", for: .normal)
        holder.addSubview(zeroButton)
}
```
[button zero displayed.PNG](https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/testing-result-Calculator-App/button%20zero%20displayed.PNG)<br/> 
Now add 1 2 3 buttons above using a for loop:
```swift 
  for x in 0..<3 {
        let button1 = UIButton(frame: CGRect(x: buttonSize *
CGFloat(x), y: holder.frame.size.height-(buttonSize*2), width:
buttonSize, height: buttonSize))
        button1.setTitleColor(.black, for: .normal)
        button1.backgroundColor = .white
        button1.setTitle("\(x+1)", for: .normal)
        holder.addSubview(button1)
}
```
[button 1 2 3 displayed.PNG](https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/testing-result-Calculator-App/button%201%202%203%20displayed.PNG)<br/>
Copy and paste the for loops twice and we got 0-9 buttons: <br/>
[0-9 buttons all displayed.PNG](https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/testing-result-Calculator-App/0-9%20buttons%20all%20displayed.PNG)<br/>
Add CLEAR ALL button:
```swift 
let clearButton = UIButton(
frame: CGRect(x: 0, y: holder.frame.size.height-(buttonSize*5),
   width: view.frame.size.width, height: buttonSize))
    clearButton.setTitleColor(.black, for: .normal)
    clearButton.backgroundColor = .white
    clearButton.setTitle("Clear ALL", for: .normal)
    holder.addSubview(clearButton)
```
Add mathematical operations:
```swift 
 let operations = ["+", "-", "x", "/"]
    for x in 0..<4 {
        let button4 = UIButton(frame: CGRect(x: buttonSize * 3, y:
holder.frame.size.height-(buttonSize*CGFloat(x+1)), width: buttonSize,
height: buttonSize))
        button4.setTitleColor(.white, for: .normal)
        button4.backgroundColor = .orange
        button4.setTitle(operations[x], for: .normal)
        holder.addSubview(button4)
}
```
Now CLEAR ALL and all mathematical operations displayed:<br/>
[clear all and all mathematical operations displayed.PNG](https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/testing-result-Calculator-App/clear%20all%20and%20all%20mathematical%20operations%20displayed.PNG)<br/> 
Now to let the initial result label display, define result label:
```swift 
 private var resultLabel: UILabel = {
        let label = UILabel()
        label.text = "0"
        label.textColor = .white
        label.textAlignment = .right
        label.font = UIFont(name: "Helvetica", size: 100)
        return label
}()
```
Confine the result label:
```swift 
  resultLabel.frame = CGRect(x: 20, y: clearButton.frame.origin.y -
110.0, width: view.frame.size.width-40 , height:100 )
  holder.addSubview(resultLabel)
```
Now the initial result label as 0 showing:<br/>
[initial result label displayed.PNG](https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/testing-result-Calculator-App/initial%20result%20label%20displayed.PNG)<br/>
Add a = button and make all actions align better:
```swift 
 clearButton.addTarget(self, action: #selector(clearResult), for:
.touchUpInside)
   }
    @objc func clearResult(){
        resultLabel.text="0"
```
[better aligned calculator.PNG](https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/testing-result-Calculator-App/better%20aligned%20calculator.PNG)<br/>
## ***Make number pressed responding:***
```swift 
 @objc func numberPressed(_ sender: UIButton){
        let tag = sender.tag - 1
        if resultLabel.text == "0"{
            resultLabel.text = "\(tag)"
        }
        else if let text = resultLabel.text {
            resultLabel.text = "\(text)\(tag)"
```
Also add targets to all buttons:
```swift
buttonX.addTarget(self, action: #selector(numberPressed(_:)), for: .touchUpInside)
```
Now the number buttons we pressed are responding and displaying on screen:<br/>
[number pressed responded and displayed.PNG](https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/testing-result-Calculator-App/number%20pressed%20responded%20and%20displayed.PNG)<br/>
Use switch statement to enable each action:
```swift
 switch operation {
                case .add:
                    let result = firstNumber + secondNumber
                    resultLabel.text = "\(result)"
                    break
                case .subtract:
                    let result = firstNumber - secondNumber
                    resultLabel.text = "\(result)"
                    break
                case .multiply:
                    let result = firstNumber * secondNumber
                    resultLabel.text = "\(result)"
                    break
                case .divide:
                    let result = firstNumber / secondNumber
                    resultLabel.text = "\(result)"
                    break
}
```
Now all mathematical operations work:<br/>
[8+9=17 addition works.PNG](https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/testing-result-Calculator-App/8%2B9%3D17%20addition%20works.PNG)<br/> 
[55-6=49 subtraction works.PNG](https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/testing-result-Calculator-App/55-6%3D49%20subtraction%20works.PNG)<br/> 
[25x4=100 multiplication works.PNG](https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/testing-result-Calculator-App/25x4%3D100%20multiplication%20works.PNG)<br/> 
[260/2=130 division works.PNG](https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/testing-result-Calculator-App/260%3A2%20%3D%20130%20division%20works.PNG)<br/> 

# Testing Result 

<p align = "center">
  <img src = "https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/testing-result-Calculator-App/button%20zero%20displayed.PNG" width = "380" height = "848.81818">&nbsp; 
  <img src = "https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/testing-result-Calculator-App/button%201%202%203%20displayed.PNG" width = "380" height = "848.81818">&nbsp; 
  <img src = "https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/testing-result-Calculator-App/0-9%20buttons%20all%20displayed.PNG" width = "380" height = "848.81818">&nbsp; 
  <img src = "https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/testing-result-Calculator-App/clear%20all%20and%20all%20mathematical%20operations%20displayed.PNG" width = "380" height = "848.81818">&nbsp; 
  <img src = "https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/testing-result-Calculator-App/initial%20result%20label%20displayed.PNG" width = "380" height = "848.81818">&nbsp; 
  <img src = "https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/testing-result-Calculator-App/better%20aligned%20calculator.PNG" width = "380" height = "848.81818">&nbsp; 
  <img src = "https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/testing-result-Calculator-App/number%20pressed%20responded%20and%20displayed.PNG" width = "380" height = "848.81818">&nbsp; 
  <img src = "https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/testing-result-Calculator-App/8%2B9%3D17%20addition%20works.PNG" width = "380" height = "848.81818">&nbsp; 
  <img src = "https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/testing-result-Calculator-App/55-6%3D49%20subtraction%20works.PNG" width = "380" height = "848.81818">&nbsp; 
  <img src = "https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/testing-result-Calculator-App/25x4%3D100%20multiplication%20works.PNG" width = "380" height = "848.81818">&nbsp; 
  <img src = "https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/testing-result-Calculator-App/260%3A2%20%3D%20130%20division%20works.PNG" width = "380" height = "848.81818">&nbsp; 
</p>





# Tags and Topics 
api, swiftui, xcode, swift, swift5, uikit, cgrect, calculator-app. 

# Author
Krystal Zhang
https://github.com/KrystalZhang612<hr>
*This file was generated by [CalculatorApp-readme](https://github.com/KrystalZhang612/KrystalZhang-Calculator-App/blob/main/README.md), on November 1st, 2022*
