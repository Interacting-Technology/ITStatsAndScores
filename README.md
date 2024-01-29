# ITStatsAndScores

A Swift Package SDK for UIKit/SwiftUI providing presentable screens for Scores and Statistics of past, future and live matches of a variety sports.

## Version
- 0.1.34

## Important changes, additions and notices
- [x] Since server is https NOW then there is NO NEED to set in your target info.plist "App Transport Security Settings" -> Allow Arbitrary Loads = YES
- [x] ITStatsAndScoresDelegate has been deprecated. It has been renamed ITScoresDelegate
- [x] presentScoresScreen(in viewController: UIViewController, delegate: ITScoresDelegate)
- [x] presentHead2HeadScreen(fixtureId: String, in viewController: UIViewController)
- [x] presentLineupsScreen(fixtureId: String, in viewController: UIViewController)
- [x] presentLiveUpdatesScreen(fixtureId: String, in viewController: UIViewController)
- [x] presentStatisticsScreen(fixtureId: String, in viewController: UIViewController)

## What's New/Fixed
- [x] Changed and new API calls to show stand alone Fixture pages Head to Head/Line Ups/Live Updates/Stats (see Important changes, additions and notices)
- [x] Delegates 'getFollowingAndReminders' and 'setReminderButtonTappedFor' (see #Implementation for more details)
- [x] 'getFollowingAndReminders' is triggered when configuring - ITStatsAndScoresAccess.shared.configure
- [x] Click on set reminder bell will trigger delegate 'setReminderButtonTappedFor'
- [x] LiteFixture screen Head to Head/Line Ups/Live Updates/Stats
- [x] FirebaseAnalytics NOT embedded for now

## Scores Screen Features
- [x] Live updates of matches
- [x] Filter by Followings
- [x] Filter by All
- [x] Filter by Live

## Fixture Pages Features
- [x] LiteFixture access by clicking on a match in Scores Screen -> Match events and 4 Tabs: Head to Head/Line Ups/Live Updates/Stats 
- [x] Stand alone access to Fixture page Head to Head
- [x] Stand alone access to Fixture page Lineups
- [x] Stand alone access to Fixture page Statistics
- [x] Fixture page Head to Head: Positions, Historic Rates charts, Momentum, Historic Matches
- [x] Fixture page Line Ups: Formations, Substitutions, Substitutes, Coaches
- [x] Fixture page Live Updates: Commentaries
- [x] Fixture page Statistics: Possession chart, Performance charts, Radar chart

## Disabled for this version
- [x] Scores screen Sports Picker. Shows only Football/Soccer. No bottom sheet selection for sports.

## Known Issues

## Dependencies and ThirdParty sdks/libraries/frameworks
- [x] MQTT-NIO. https://swiftpackageindex.com/sroebert/mqtt-nio
- [x] FirebaseAnalytics NOT embedded for now. https://firebase.google.com/docs/analytics / https://github.com/firebase/firebase-ios-sdk

## Requirements

| Platform | Minimum Swift Version | Installation | Status |
| --- | --- | --- | --- |
| iOS 14.0+ | 5.8.1 |

## Installation

### Manually

Currently you may only integrate ITStatsAndScores into your project manually as a package dependency (Swift Package)

- Unzip the ITStatsAndScores.zip file and place the unzipped folder in a permanent location
- Open your Xcode project 
- In the Navigator -> click on your Project
- Select -> Package Dependencies
- Click the plus button to add a dependency
- In the "search or enter Package URL" field, enter the file PATH to the unzipped folder. (It will not work if you click "Add Local...")
- Example file PATH: file:///Users/admin/Development/SwiftPackages/ITStatsAndScores
- Set -> Dependency Rule: Up to Next Major Version 0.1.34 < 
- Click Add Package
- Click Add Package
- You should see in the Navigator under Package Dependencies -> ITStatsAndScores
- Build project
- Since matches/fixtures server is http, you must set in your target info.plist "App Transport Security Settings" -> Allow Arbitrary Loads = YES

## Implementation
- ITConfiguration properties are: userId, language (ISO 639 alpha-2 code, i.e. 2 letter “en”/”es”/”pt”), country (to letters like "ES"/"UK")
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

## Implementation of Single Fixture screens
- presentHead2HeadScreen, presentLineupsScreen, presentLiveUpdatesScreen, presentStatisticsScreen.
- It is a similar process to present a single stand alone Fixture screens as it is for presentScoresScreen 
- You must provide a real fixtureId in the method, Here is an example implementation of one of the screens In UIKit:
```
import UIKit
import ITStatsAndScores

class Head2HeadViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()

        ITStatsAndScoresAccess.shared.presentHead2HeadScreen(fixtureId: "<someFixtureId>", in: self)
    }
}
