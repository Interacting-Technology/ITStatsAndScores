# ITStatsAndScores

A Swift Package SDK for UIKit/SwiftUI providing presentable screens for Scores and Statistics of past, future and live matches of a variety sports.

## Version
- 0.1.85

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
- [x] (IN Development):
- [x] Click on a competition to see the Competition Pages (Matches, Table, League Stats, Player Stats) (IN Development) 
- [x] Click on Top Competitions Selector to jump to a Competition Page (IN Development) 
- [x] Click on Search to search for Competitions, Teams or Players (IN Development) 

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
- [x] (IN Development):
- [x] Click on Team name/logo in some places to jump to a Team Page (IN Development) 

## Competition Pages Features (IN Development)
- [x] LiteCompetition access by clicking on a competition in Score Center Screen
- [x] LiteCompetition - Switch between different years of the competition 
- [x] Competition page Matches: See all matches for the competition based on year and match days
- [x] Competition page Table: Team Positions and comparisons chart table (Summary/Complete/Form)
- [x] Competition page League Stats
- [x] Competition page Players Stats
- [x] Click on Team name/logo in some places to jump to a Team Page (IN Development)
- [x] Stand alone access to Competition page Matches via API (see: Main Public classes/structs, API Calls and Delegates)
- [x] Stand alone access to Competition page Table via API (see: Main Public classes/structs, API Calls and Delegates)
- [x] Stand alone access to Competition page League Stats via API (see: Main Public classes/structs, API Calls and Delegates)
- [x] Stand alone access to Competition page Players Stats via API (see: Main Public classes/structs, API Calls and Delegates)

## Team Pages Features (IN Development)
- [x] LiteTeam access by clicking on a team in some places - select between competitions and years
- [x] LiteTeam - Switch between competitions in different years 
- [x] Team page Matches: See all matches for the team based on year and match days
- [x] Team page Overview: See last match, positions and last 5 matches
- [x] Team page Table: Team Positions and comparisons chart table (Summary/Complete/Form)
- [x] Team page Squad
- [x] Team page Team Stats
- [x] Team page Players Stats
- [x] Stand alone access to Team page Matches via API (see: Main Public classes/structs, API Calls and Delegates)
- [x] Stand alone access to Team page Overview via API (see: Main Public classes/structs, API Calls and Delegates)
- [x] Stand alone access to Team page Table Stats via API (see: Main Public classes/structs, API Calls and Delegates)
- [x] Stand alone access to Team page Squad Stats via API (see: Main Public classes/structs, API Calls and Delegates)
- [x] Stand alone access to Team page Team Stats via API (see: Main Public classes/structs, API Calls and Delegates)
- [x] Stand alone access to Team page Players Stats via API (see: Main Public classes/structs, API Calls and Delegates)

## Search Page
- [x] Search for Competitions, Teams or Players
- [x] Select from previous/recent Searches

## Limitations
- [x] Scores screen Sports Picker supports only Soccer/Football. No bottom sheet selection for sports

## Main Public classes/structs, API Calls and Delegates
- [x] Initialization and Configuration:
- [x] ITStatsAndScoresAccess.shared.configure(with configuration: ITConfiguration)
- [x] ITConfiguration(userId: String, language: String, country: String)

- [x] Delegates:
- [x] ITNavigationBridgeDelegate:
- [x] navigateTo(destinationDetails jsonString: String, navigationType: ITNavigationType)

- [x] ITFollowingAndRemindersDelegate:
- [x] getFollowingAndReminders(followingListJSON: @escaping (FollowingListJSONString) ->())
- [x] setReminderButtonTappedFor(fixtureId: String, sourceName: String?, setReminderTurnOn: @escaping (Bool)->())
- [x] setFollowButtonTappedFor(id: String, sourceName: String?, followType: ITFollowType, setFollowTurnOn: @escaping (Bool) -> ())

- [x] ITAnalyticsDelegate:
- [x] report(event: AnalyticsEvent, parameters: [String: Any])

- [x] Score Center:
- [x] presentScoresScreen(in viewController: UIViewController)

- [x] LiteFixture Page:
- [x] pushLiteFixtureScreen(externalId: String, selectedTab: LiteFixtureTab, in viewController: UIViewController? = nil)
- [x] presentLiteFixtureScreen(externalId: String, selectedTab: LiteFixtureTab, in viewController: UIViewController? = nil)
- [x] Stand alone Fixture Pages:
- [x] presentHead2HeadScreen(fixtureId: String, in viewController: UIViewController, contentHeight: @escaping (CGFloat) -> Void)
- [x] presentLineupsScreen(fixtureId: String, in viewController: UIViewController, contentHeight: @escaping (CGFloat) -> Void)
- [x] presentLiveUpdatesScreen(fixtureId: String, in viewController: UIViewController, contentHeight: @escaping (CGFloat) -> Void)
- [x] presentStatisticsScreen(fixtureId: String, in viewController: UIViewController, contentHeight: @escaping (CGFloat) -> Void)
- [x] Stand alone Fixture Pages - UIView versions:
- [x] presentHead2HeadScreen(fixtureId: String, in viewController: UIViewController, contentHeight: @escaping (CGFloat) -> Void)
- [x] getUIViewForLineupsScreen(fixtureId: String, contentHeight: @escaping (CGFloat) -> Void) -> UIView
- [x] getUIViewForLiveUpdatesScreen(fixtureId: String, contentHeight: @escaping (CGFloat) -> Void) -> UIView
- [x] getUIViewForStatisticsScreen(fixtureId: String, contentHeight: @escaping (CGFloat) -> Void) -> UIView

- [x] LiteCompetition Page:
- [x] pushLiteCompetitionScreen(externalId: String, selectedTab: LiteCompetitionInfo, in viewController: UIViewController? = nil)
- [x] presentLiteCompetitionScreen(externalId: String, selectedTab: LiteCompetitionInfo, in viewController: UIViewController? = nil)
- [x] Stand alone Competition Pages:
- [x] presentCompetitionMatchesScreen(competitionId: String, competitionSeasonId: String? = nil, in viewController: UIViewController, contentHeight: @escaping (CGFloat)
- [x] presentCompetitionTableScreen(competitionId: String, competitionSeasonId: String? = nil, in viewController: UIViewController, contentHeight: @escaping (CGFloat) -> Void)
- [x] presentCompetitionLeagueStatsScreen(competitionId: String, competitionSeasonId: String? = nil, in viewController: UIViewController, contentHeight: @escaping (CGFloat) -> Void)
- [x] presentCompetitionPlayersStatsScreen(competitionId: String, competitionSeasonId: String? = nil, in viewController: UIViewController, contentHeight: @escaping (CGFloat) -> Void)
- [x] Stand alone Competition Pages - UIView versions:
- [x] getUIViewForCompetitionMatchesScreen(competitionId: String, competitionSeasonId: String? = nil, contentHeight: @escaping (CGFloat) -> Void) -> UIView
- [x] getUIViewForCompetitionTableScreen(competitionId: String, competitionSeasonId: String? = nil, contentHeight: @escaping (CGFloat) -> Void) -> UIView
- [x] getUIViewForCompetitionLeagueStatsScreen(competitionId: String, competitionSeasonId: String? = nil, contentHeight: @escaping (CGFloat) -> Void) -> UIView
- [x] getUIViewForCompetitionPlayersStatsScreen(competitionId: String, competitionSeasonId: String? = nil, contentHeight: @escaping (CGFloat) -> Void) -> UIView

- [x] Stand alone Team Pages:
- [x] pushLiteTeamScreen(externalId: String, selectedTab: LiteTeamInfo, in viewController: UIViewController? = nil)
- [x] presentLiteTeamScreen(externalId: String, selectedTab: LiteTeamInfo, in viewController: UIViewController? = nil)
- [x] presentTeamMatchesScreen(competitionId: String, in viewController: UIViewController, contentHeight: @escaping (CGFloat) -> Void)
- [x] presentTeamOverviewScreen(competitionId: String, in viewController: UIViewController, contentHeight: @escaping (CGFloat) -> Void)
- [x] presentTeamTableScreen(competitionId: String, in viewController: UIViewController, contentHeight: @escaping (CGFloat) -> Void)
- [x] presentTeamSquadScreen(competitionId: String, in viewController: UIViewController, contentHeight: @escaping (CGFloat) -> Void)
- [x] presentTeamStatsTeamScreen(competitionId: String, in viewController: UIViewController, contentHeight: @escaping (CGFloat) -> Void)
- [x] presentTeamPlayersStatsScreen(competitionId: String, in viewController: UIViewController, contentHeight: @escaping (CGFloat) -> Void)
- [x] Stand alone Team Pages - UIView versions:
- [x] getUIViewForTeamMatchesScreen(competitionId: String, contentHeight: @escaping (CGFloat) -> Void) -> UIView
- [x] getUIViewForTeamOverviewScreen(competitionId: String, contentHeight: @escaping (CGFloat) -> Void) -> UIView
- [x] getUIViewForTeamTableScreen(competitionId: String, contentHeight: @escaping (CGFloat) -> Void) -> UIView
- [x] getUIViewForTeamSquadScreen(competitionId: String, contentHeight: @escaping (CGFloat) -> Void) -> UIView
- [x] getUIViewForTeamStatsTeamScreen(competitionId: String, contentHeight: @escaping (CGFloat) -> Void) -> UIView
- [x] getUIViewForTeamPlayersStatsScreen(competitionId: String, contentHeight: @escaping (CGFloat) -> Void) -> UIView


```
public enum ITNavigationType: String {
    case fixture
    case competition
    case contestant //Team
    
    var jsonParameterKey: String {
        switch self {
        case .fixture: return "fixtureId"
        case .competition: return "competitionId"
        case .contestant: return "contestantId"
        }
    }
}
```

```
public enum ITFollowType: String {
    case competition
    case contestant //Team
}
```

## Known Issues
- [x] None

## Dependencies and ThirdParty sdks/libraries/frameworks
- [x] MQTT-NIO. https://swiftpackageindex.com/sroebert/mqtt-nio
- [x] Mixpanel. https://github.com/mixpanel/mixpanel-swift

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
- Dependency Rule -> Up to Next Major \<major.minor.patch> (example: 0.1.85)
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
        
        // Add delegates:
        ITStatsAndScoresAccess.shared.followingAndRemindersDelegate = itFollowingAndRemindersManager
        ITStatsAndScoresAccess.shared.navigationDelegate = itNavigationBridgeManager
        ITStatsAndScoresAccess.shared.analyticsDelegate = itAnalytics
        
        return true
    }
}

// Recommend to make separate classes to conform to the delegates: 

import ITStatsAndScores

class ITNavigationBridgeManager: ITNavigationBridgeDelegate {
    
    func navigateTo(destinationDetails jsonString: String, navigationType: ITStatsAndScores.ITNavigationType) {
        // print(jsonString)
        // Perform app navigation
    }
}

struct ITFollowingAndRemindersManager: ITFollowingAndRemindersDelegate {
    
    func getFollowingAndReminders(followingListJSON: @escaping (ITStatsAndScores.FollowingListJSONString) -> ()) {
        let jsonString = "" // Provide appropriate JSON String (See example file FollowingList.json)
        // print(jsonString)
        followingListJSON(jsonString)
    }
    
    func setReminderButtonTappedFor(fixtureId: String, setReminderTurnOn: @escaping (Bool) -> ()) {
        // Do what you need and then either
        setReminderTurnOn(true) // OR setReminderTurnOn(false)
    }
    
    func setFollowButtonTappedFor(id: String, followType: ITStatsAndScores.ITFollowType, setFollowTurnOn: @escaping (Bool) -> ()) {
        // Do what you need and then either
        setFollowTurnOn(true) // OR setFollowTurnOn(false)
    }
}

struct ITAnalyticsManager: ITAnalyticsDelegate {
    
    func report(event: ITStatsAndScores.AnalyticsEvent, parameters: [String : Any]) {
        // To log in Firebase Analytics
        //FBAnalyticsService.logEvent(event.rawValue, parameters: parameters)
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

        ITStatsAndScoresAccess.shared.presentScoresScreen(in: self)
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
        
        // Add delegates:
        ITStatsAndScoresAccess.shared.followingAndRemindersDelegate = itFollowingAndRemindersManager
        ITStatsAndScoresAccess.shared.navigationDelegate = itNavigationBridgeManager
        ITStatsAndScoresAccess.shared.analyticsDelegate = itAnalytics
    }
    
    var body: some Scene {
        WindowGroup {
            MainTabView().preferredColorScheme(.dark) // Forcing dark mode
        }
    }
}
```
- Then in the (Navigation/Tab) View you wish to present - (Provide a ViewController)
```

import SwiftUI
import ITStatsAndScores

struct MainTabView: View {
    var body: some View {
        ITStatsAndScoresAccess.shared.presentScoresScreenView(in: statsAndScoresVC)
    }
}

import UIKit
import ITStatsAndScores

let statsAndScoresVC = StatsAndScoresViewController()

class StatsAndScoresViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()

        ITStatsAndScoresAccess.shared.presentScoresScreen(in: self)
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

## Implementation of single - Stand alone Competition screens
- presentCompetitionMatchesScreen, presentCompetitionTableScreen, presentCompetitionLeagueStatsScreen, presentCompetitionPlayersStatsScreen.
- It is a similar process to present a single stand alone Competition screen as it is for presentScoresScreen 
- You must provide a real competitionId in the method, 
- You may provide a competitionSeasonId to load a specific season of the competition, Here is an example implementation of one of the screens In UIKit:
```
import UIKit
import ITStatsAndScores

class CompetitionMatchesViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()

        ITStatsAndScoresAccess.shared.presentCompetitionMatchesScreen(competitionId: "someId", competitionSeasonId: nil, in viewController: UIViewController, contentHeight: @escaping (CGFloat)
    }
}
```

## Implementation of single - Stand alone Team screens
- presentTeamMatchesScreen, presentTeamOverviewScreen, getUIViewForTeamTableScreen, presentTeamSquadScreen, presentTeamStatsTeamScreen, presentTeamPlayersStatsScreen.
- It is a similar process to present a single stand alone Competition screen as it is for presentScoresScreen 
- You must provide a real contestantId in the method, Here is an example implementation of one of the screens In UIKit:
```
import UIKit
import ITStatsAndScores

class CompetitionMatchesViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()

        ITStatsAndScoresAccess.shared.presentTeamMatchesScreen(contestantId: String, in viewController: UIViewController, contentHeight: @escaping (CGFloat) -> Void)
    }
}
```
