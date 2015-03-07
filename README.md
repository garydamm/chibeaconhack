# chibeaconhack
Simplest Gimbal Integration Example on iOS.

```objective-c
#import <Gimbal/Gimbal.h>
#import "AppDelegate.h"

@interface AppDelegate () <GMBLPlaceManagerDelegate>
@property (nonatomic) GMBLPlaceManager *placeManager;
@end

@implementation AppDelegate

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    
    [Gimbal setAPIKey:@"YOUR-APIKEY-HERE" options:nil];
    
    self.placeManager = [GMBLPlaceManager new];
    self.placeManager.delegate = self;
    [GMBLPlaceManager startMonitoring];
    
    [GMBLCommunicationManager startReceivingCommunications];

    return YES;
}

- (void)placeManager:(GMBLPlaceManager *)manager didBeginVisit:(GMBLVisit *)visit
{
    NSLog(@"Arrive %@", [visit.place description]);
}

- (void)placeManager:(GMBLPlaceManager *)manager didEndVisit:(GMBLVisit *)visit
{
    NSLog(@"Depart %@", [visit.place description]);
}

@end
```
