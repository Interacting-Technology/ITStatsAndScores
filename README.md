# ITStatsAndScores

A Swift Package SDK for UIKit/SwiftUI providing presentable screens for Scores and Statistics of past, future and live matches of a variety sports.

## Version
- 0.1.46

## What's New/Fixed & Important changes, additions and notices
- [x] The SDK is available as a Swift Package on GitHub. https://github.com/Interacting-Technology/ITStatsAndScores
- [x] Since server is https then there is NO NEED to set in your target info.plist "App Transport Security Settings" -> Allow Arbitrary Loads = YES
- [x] ITAnalyticsDelegate. (see: Main Public classes/structs, API Calls and Delegates) (See: Implementation of ITAnalyticsDelegate - Analytics)

## Score Center Screen Features
- [x] See scores of past matches
- [x] See scores of live matches updating at near real time
- [x] See times for future matches
- [x] Select a day with the Day Picker to show matches on that day
- [x] Jump to past or future matches with a Date Picker
- [x] Filter to focus only on live matches
- [x] Filter by Top Competitions
- [x] Filter by Followings
- [x] Filter by All
- [x] Set Reminders for select matches
- [x] Click on a match to see the Fixture Pages (Head to Head/comparison, Lineups, Commentaries/Live updates, Statistics)

## Fixture Pages Features
- [x] LiteFixture access by clicking on a match in Score Center Screen
- [x] Fixture page Head to Head: Positions, Historic Rates charts, Momentum, Historic Matches
- [x] Fixture page Line Ups: Formations, Substitutions, Substitutes, Coaches
- [x] Fixture page Live Updates: Commentaries
- [x] Fixture page Statistics: Possession chart, Performance charts, Radar chart
- [x] Stand alone access to Fixture page Head to Head via API (see: Main Public classes/structs, API Calls and Delegates)
- [x] Stand alone access to Fixture page Lineups via API (see: Main Public classes/structs, API Calls and Delegates)
- [x] Stand alone access to Fixture page Commentaries via API (see: Main Public classes/structs, API Calls and Delegates)
- [x] Stand alone access to Fixture page Statistics via API (see: Main Public classes/structs, API Calls and Delegates)

## Limitations
- [x] Scores screen Sports Picker supports only Soccer/Football. No bottom sheet selection for sports

## Main Public classes/structs, API Calls and Delegates
- [x] Initialization and Configuration:
- [x] ITStatsAndScoresAccess.shared.configure(with configuration: ITConfiguration)
- [x] ITConfiguration(userId: String, language: String, country: String)
- [x] Score Center:
- [x] NOTE: ITStatsAndScoresDelegate has been deprecated. It has been renamed ITScoresDelegate
- [x] presentScoresScreen(in viewController: UIViewController, delegate: ITScoresDelegate)
- [x] Delegates 'getFollowingAndReminders' and 'setReminderButtonTappedFor'
- [x] Delegate: 'getFollowingAndReminders' is triggered when configuring - ITStatsAndScoresAccess.shared.configure
- [x] Delegate: 'setReminderButtonTappedFor' is triggered when clicking on set reminder bell of a match in Score Center
- [x] Stand alone Fixture Pages:
- [x] presentHead2HeadScreen(fixtureId: String, in viewController: UIViewController, contentHeight: @escaping (CGFloat) -> Void)
- [x] presentLineupsScreen(fixtureId: String, in viewController: UIViewController, contentHeight: @escaping (CGFloat) -> Void)
- [x] presentLiveUpdatesScreen(fixtureId: String, in viewController: UIViewController, contentHeight: @escaping (CGFloat) -> Void)
- [x] presentStatisticsScreen(fixtureId: String, in viewController: UIViewController, contentHeight: @escaping (CGFloat) -> Void)
- [x] Stand alone Fixture Pages - UIView versions:
- [x] getUIViewForHead2HeadScreen(fixtureId: String, contentHeight: @escaping (CGFloat) -> Void) -> UIView
- [x] getUIViewForLineupsScreen(fixtureId: String, contentHeight: @escaping (CGFloat) -> Void) -> UIView
- [x] getUIViewForLiveUpdatesScreen(fixtureId: String, contentHeight: @escaping (CGFloat) -> Void) -> UIView
- [x] getUIViewForStatisticsScreen(fixtureId: String, contentHeight: @escaping (CGFloat) -> Void) -> UIView
- [x] Analytics - ITAnalyticsDelegate:
- [x] report(event: AnalyticsEvent, parameters: [String: Any])

## Known Issues
- [x] None

## Dependencies and ThirdParty sdks/libraries/frameworks
- [x] MQTT-NIO. https://swiftpackageindex.com/sroebert/mqtt-nio

## Requirements

| Platform | Minimum Swift Version | Installation | Status |
| --- | --- | --- | --- |
| iOS 14.0+ | 5.8.1 |

## Installation

### Via Swift Package Manager (SPM)
You may integrate ITStatsAndScores into your project as a package dependency (Swift Package) available on GitHub:

- Open your Xcode project
- In Xcode Project Navigator click on the Project -> Package Dependencies
- Click the plus button
- In the search field enter the package URL: https://github.com/Interacting-Technology/ITStatsAndScores
- Dependency Rule -> Up to Next Major \<major.minor.patch> (example: 0.1.46)
- Add to Project -> <Your Project>
- Click Add Package
- Click Add Package
- You should see in the Navigator under Package Dependencies -> ITStatsAndScores
- Build project

## Implementation
- ITConfiguration properties are: userId, language (ISO 639 alpha-2 code, i.e. 2 letter “en”/”es”/”fr”), country (2 letters like "ES"/"US"/"FR")
- In UIKit AppDelegate:
```
import UIKit
import ITStatsAndScores

@main
class AppDelegate: UIResponder, UIApplicationDelegate {

    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        
        ITStatsAndScoresAccess.shared.configure(with: .init(userId: "<UserId>", language: "<example: \"en\">", country: "<example: \"ES\">"))
        
        return true
    }
}
```
- Then in a UIViewController you use to present in Navigation or Tab:
```
import UIKit
import ITStatsAndScores

class StatsAndScoresViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()

        ITStatsAndScoresAccess.shared.presentScoresScreen(in: self, delegate: self)
    }
}

extension StatsAndScoresViewController: ITStatsAndScoresDelegate {
    
    func navigateTo(destinationDetails jsonString: String, navigationType: ITStatsAndScores.ITNavigationType) {
        // print(jsonString)
        // Perform app navigation
    }
}
```


- OR, in a SwiftUI in @main App struct
```
import SwiftUI
import ITStatsAndScores

@main
struct ITStatsAndScoresInternalBuildApp: App {
    
    init() {
        ITStatsAndScoresAccess.shared.configure(with: .init(userId: "<UserId>", language: "<example: \"en\">", country: "<example: \"ES\">"))
    }
    
    var body: some Scene {
        WindowGroup {
            MainTabView().preferredColorScheme(.dark) // Forcing dark mode
        }
    }
}
```
- View And Delegate... 
- Then in the (Navigation/Tab) View you wish to present - (Provide a ViewController and Delegate)
```

import SwiftUI
import ITStatsAndScores

struct MainTabView: View {
    var body: some View {
        ITStatsAndScoresAccess.shared.presentScoresScreenView(in: statsAndScoresVC, delegate: statsAndScoresVC)
    }
}

import UIKit
import ITStatsAndScores

let statsAndScoresVC = StatsAndScoresViewController()

class StatsAndScoresViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()

        ITStatsAndScoresAccess.shared.presentScoresScreen(in: self, delegate: self)
    }
}

extension StatsAndScoresViewController: ITScoresDelegate {
    
    func navigateTo(destinationDetails jsonString: String, navigationType: ITNavigationType) {
        // print(jsonString)
        // Perform app navigation
    }
    
    func getFollowingAndReminders(followingListJSON: @escaping (ITStatsAndScores.FollowingListJSONString) -> ()) {
        let jsonString = "" // Provide appropriate JSON String (See example file FollowingList.json)
        // print(jsonString)
        followingListJSON(jsonString)
    }
    
    func setReminderButtonTappedFor(fixtureId: String, setReminderTurnOn: @escaping (Bool) -> ()) {
        // Do what you need and then either
            setReminderTurnOn(true) // OR setReminderTurnOn(false)
    }
}
```

## Implementation of single - Stand alone Fixture screens
- presentHead2HeadScreen, presentLineupsScreen, presentLiveUpdatesScreen, presentStatisticsScreen.
- It is a similar process to present a single stand alone Fixture screen as it is for presentScoresScreen 
- You must provide a real fixtureId in the method, Here is an example implementation of one of the screens In UIKit:
```
import UIKit
import ITStatsAndScores

class Head2HeadViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()

        ITStatsAndScoresAccess.shared.presentHead2HeadScreen(fixtureId: String, in viewController: UIViewController, contentHeight: @escaping (CGFloat) -> Void)
    }
}
```

## Implementation of ITAnalyticsDelegate - Analytics
- Create a conforming class/struct and create an instance of it or use an existing appropriate class an conform to ITAnalyticsDelegate)
- In UIKit AppDelegate (or other appropriate place) add:
```
import UIKit
import ITStatsAndScores

struct ITAnalytics: ITAnalyticsDelegate {
    
    func report(event: ITStatsAndScores.AnalyticsEvent, parameters: [String : Any]) {
        // To log in Firebase Analytics use your firebase class like so:
        yourFBanalyticsService.logEvent(event.rawValue, parameters: parameters)
    }
}

@main
class AppDelegate: UIResponder, UIApplicationDelegate {

    let itAnalytics = ITAnalytics()

    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        
        ...
        ITStatsAndScoresAccess.shared.analyticsDelegate = itAnalytics
        
        return true
    }
}
```
