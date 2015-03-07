# chibeaconhack
Simplest Gimbal Integration Example on iOS.

'''objective-c
#import <Gimbal/Gimbal.h>
#import "AppDelegate.h"

@interface AppDelegate () <GMBLPlaceManagerDelegate>
@property (nonatomic) GMBLPlaceManager *placeManager;

@end

@implementation AppDelegate


- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    [Gimbal setAPIKey:@"0e49e70b-b864-4075-934b-353c5db5d04b" options:nil];
    
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
'''
