Source: [https://developer.apple.com/documentation/metal/managing-your-metal-app-window-in-ipados?language=objc](<https://developer.apple.com/documentation/metal/managing-your-metal-app-window-in-ipados?language=objc>)

<a id="managing-your-metal-app-window-in-ipados"></a>

# Managing your Metal app window in iPadOS

Set up a window that handles dynamically resizing your Metal content.

<a id="discussion"></a>

## Discussion

A scene represents a single instance of your app’s UI. You can choose
whether people can create multiple scenes for your app. Typically, Metal
apps and games support only one scene because they need priority access to the
available resources on a device. On iPadOS 26 and later, people can always
resize your app’s scenes if they have enabled multitasking.

Apps that don’t adopt the scene-based life cycle log a warning at startup
on iOS 26 and iPadOS 26 and must be updated. In the next major release, the
scene-based life cycle is required when building with the latest SDK.

> Important: Because
> <doc://com.apple.documentation/documentation/BundleResources/Information-Property-List/UIRequiresFullScreen>
> is deprecated, you can no longer opt out of iPad multitasking and dynamic resizing.

For more information on migrating your iPad app, see
<doc://com.apple.documentation/documentation/Technotes/tn3192-Migrating-your-app-from-the-deprecated-UIRequiresFullScreen-key>
and <doc://com.apple.documentation/documentation/Technotes/tn3187-Migrating-to-the-UIKit-scene-based-life-cycle>.

<a id="create-the-window"></a>

## Create the window

Manage windows on iPad by using <doc://com.apple.documentation/documentation/UIKit/UIWindowScene>
for UIKit and <doc://com.apple.documentation/documentation/SwiftUI/Scene> for
SwiftUI. To configure a <doc://com.apple.documentation/documentation/UIKit/UIWindow>
under a scene you assign a content view controller and embed your Metal view inside
the controller.

To configure scene support for your Metal project:

1. Open the Xcode project.
2. Select the project in the Project navigator.
3. Select the app target.
4. Navigate to the General tab.
5. In the Deployment Info section, select “Scene manifest”.
6. Add the <doc://com.apple.documentation/documentation/BundleResources/Information-Property-List/UIApplicationSceneManifest> key if it doesn’t already exist.
7. Configure the dictionary value for your project.

```json
<key>UIApplicationSceneManifest</key>
<dict>
    <key>UIApplicationSupportsMultipleScenes</key>
    <false/> 
    <key>UISceneConfigurations</key>
    <dict>
        <key>UIWindowSceneSessionRoleApplication</key>
        <array>
            <dict>
                <key>UISceneConfigurationName</key>
                <string>Default Configuration</string>
                <key>MyCustomSceneDelegateClass</key>
                <string>SceneDelegate</string>
                <key>UISceneStoryboardFile</key>
                <string>Main</string> 
                <key>UISceneClassName</key>
                <string>UIWindowScene</string> 
            </dict>
        </array>
    </dict>
</dict>
```

To provide dynamic scene configurations for complex scenes that require fine-grained
control, implement
<doc://com.apple.documentation/documentation/UIKit/UIApplicationDelegate/application(_:configurationForConnecting:options:)>
for UIKit and <doc://com.apple.documentation/documentation/SwiftUI/UIApplicationDelegateAdaptor>
for apps that uses the SwiftUI life cycle. This allows for providing dynamic
scene configurations:

```objc
- (UISceneConfiguration *)application:(UIApplication *)application 
                          configurationForConnectingSceneSession:(UISceneSession *)connectingSceneSession 
                          options:(UISceneConnectionOptions *)options {
                          
    // Each scene configuration has a unique, app-specific configuration 
    // name that you use to identify the scene. The configuration
    // name corresponds to entries in the `Info.plist` scene manifest.
    NSString *configurationName;

    // An activity type distinguishes which scene to create.
    NSString *activityType = options.userActivities.allObjects.firstObject.activityType;

    if ([activityType isEqualToString:@"com.apple.gallery.openInspector"]) {
        // Create a photo inspector window scene.
        configurationName = @"Inspector Configuration";
    } else {
        // Create a default gallery window scene.
        configurationName = @"Default Configuration";
    }

    return [[UISceneConfiguration alloc] initWithName: configurationName
                                         sessionRole: connectingSceneSession.role];
}

// The system calls this delegate when a person dismisses a scene 
// session, like when closing a window.
// 
// If the system ends a session while the app wasn't running, it 
// calls application(_:didDiscardSceneSessions:) shortly after 
// calling `application(_:didFinishLaunchingWithOptions:)`.
// 
// Use this method to release scene-specific resources for the 
// scene, as they won't return.
- (void)application:(UIApplication *)application 
        didDiscardSceneSessions:(NSSet<UISceneSession *> *)sceneSessions {
        
}
```

For more information on dynamic configuration, see
<doc://com.apple.documentation/documentation/Technotes/tn3187-Migrating-to-the-UIKit-scene-based-life-cycle>. For more information on adding scene support to your app, see
<doc://com.apple.documentation/documentation/UIKit/specifying-the-scenes-your-app-supports>.

<a id="choose-the-content-size-and-style-of-your-window"></a>

## Choose the content size and style of your window

After adding scene support, configure the initial size and style of your window’s
scenes. When your app creates or restores an instance of your user interface,
the system calls
<doc://com.apple.documentation/documentation/UIKit/UISceneDelegate/scene(_:willConnectTo:options:)>.
This delegate method provides a window scene that you use to configure size
contraints and style. For Metal apps and games, this is typically a single scene.

Use <doc://com.apple.documentation/documentation/UIKit/UISceneSizeRestrictions>
to constrain the minimum size you want, and to handle aspect ratio changes:

```objc
- (void)scene:(UIScene *)scene
        willConnectToSession:(UISceneSession *)session
        options:(UISceneConnectionOptions *)connectionOptions {

    UIWindowScene *windowScene = (UIWindowScene *)scene;
    if (![windowScene isKindOfClass:[UIWindowScene class]]) {
      return;
    }

    windowScene.sizeRestrictions.minimumSize = CGSizeMake(640.0,
                                                          windowScene.sizeRestrictions.minimumSize.height);
}        
```

In SwiftUI, use the
<doc://com.apple.documentation/documentation/SwiftUI/Scene/windowResizability(_:)>
modifier to allow your scene’s content to provide sizing information:

```swift
@main
struct MyApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
               .frame(minWidth: 640, minHeight: 360)
        }
        .windowResizability(.contentMinSize)
    }
}
```

To get the display scale, access
<doc://com.apple.documentation/documentation/UIKit/UITraitCollection/displayScale>
from <doc://com.apple.documentation/documentation/UIKit/UITraitCollection> and
perform necessary updates in
<doc://com.apple.documentation/documentation/UIKit/UIViewController/viewIsAppearing(_:)>.
To calculate the pixel values you use for updating the size of [`MTLDrawable`](https://developer.apple.com/documentation/Metal/MTLDrawable),
multiply the view’s frame and the
<doc://com.apple.documentation/documentation/QuartzCore/CALayer/contentsScale>
of your <doc://com.apple.documentation/documentation/QuartzCore/CAMetalLayer>:

```objc
CAMetalLayer *metalLayer = (CAMetalLayer *)self.view.layer;
if (![metalLayer isKindOfClass:[CAMetalLayer class]]) {
    return;
}
// Get the scale that matches the window's display scale.
CGFloat screenScale = metalLayer.contentsScale;

// Calculate the drawable size in pixels.
CGSize sizeInPixels = CGSizeMake(self.view.frame.size.width * screenScale,
                                 self.view.frame.size.height * screenScale);
metalLayer.drawableSize = sizeInPixels;
```

When a person resizes a window, it’s possible that the Metal view only renders
to a portion of the window. In this case, add a launch screen with a black
background color to letterbox the presentation, then configure the content
gravity property for your view so drawable content scales uniformly.

![A screenshot of the Xcode information property list file that shows metadata](<managing-your-metal-app-window-in-ipados/e9eb7b153cfaf45f83c26aac.png>)

```objc
- (void)viewDidLoad {
    [super viewDidLoad];

    CAMetalLayer *metalLayer = (CAMetalLayer *)self.view.layer;
    if (![metalLayer isKindOfClass:[CAMetalLayer class]]) {
        return;
    }

    metalLayer.opaque = YES;
    metalLayer.backgroundColor = [UIColor blackColor].CGColor;
    
    // For a game, set the content gravity so the aspect ratio of your
    // drawable scene scales uniformly to avoid squishing your content.
    metalLayer.contentsGravity = kCAGravityResizeAspect;
}
```

<a id="handle-window-resizing"></a>

## Handle window resizing

When resizing a window, the system sets
<doc://com.apple.documentation/documentation/UIKit/UIWindowScene/Geometry/isInteractivelyResizing>
and calls the scene delegate <doc://com.apple.documentation/documentation/UIKit/UIWindowSceneDelegate/windowScene(_:didUpdateEffectiveGeometry:)>
to allow for an app to handle window size changes. When a window resizes, continue
rendering at the existing render target size until a person stops resizing the
window, at which point you can update the new render target size. Don’t query the
window size while a person is resizing a window. Instead, track the state in your
renderer and then perform the necessary render size update when the person
finishes resizing the window. For more information on responding to scene size changes, see
<doc://com.apple.documentation/documentation/Technotes/tn3187-Migrating-to-the-UIKit-scene-based-life-cycle>.

If you use <doc://com.apple.documentation/documentation/MetalKit>, your app
receives the
<doc://com.apple.documentation/documentation/MetalKit/MTKViewDelegate/mtkView(_:drawableSizeWillChange:)>
delegate view callback:

```objc
- (void)mtkView:(nonnull MTKView *)view 
        drawableSizeWillChange:(CGSize)size {
        
    /// Your code that responds to drawable size or orientation changes.

    /// Update the projection matrix with the new aspect size.
    float aspect = size.width / (float)size.height;
    _projectionMatrix = matrix_perspective_right_hand(65.0f * (M_PI / 180.0f), 
                                                      aspect, 
                                                      0.1f, 
                                                      100.0f);
}

matrix_float4x4 matrix_perspective_right_hand(float fovyRadians, 
                                              float aspect, 
                                              float nearZ, 
                                              float farZ) {
    float ys = 1 / tanf(fovyRadians * 0.5);
    float xs = ys / aspect;
    float zs = farZ / (nearZ - farZ);

    return (matrix_float4x4) {{
        { xs,   0,          0,  0 },    // Column 0
        {  0,  ys,          0,  0 },    // Column 1
        {  0,   0,         zs, -1 },    // Column 2
        {  0,   0, nearZ * zs,  0 }     // Column 3
    }};
}
```

Your <doc://com.apple.documentation/documentation/QuartzCore/CAMetalLayer>
views receive a <doc://com.apple.documentation/documentation/UIKit/UIView> life
cycle call to <doc://com.apple.documentation/documentation/UIKit/UIView/layoutSubviews()> and related property updates —
<doc://com.apple.documentation/documentation/UIKit/UIView/contentScaleFactor>,
<doc://com.apple.documentation/documentation/UIKit/UIView/frame>,
and <doc://com.apple.documentation/documentation/UIKit/UIView/bounds>. Use the
related properties to update the [`MTLDrawable`](https://developer.apple.com/documentation/Metal/MTLDrawable) size by getting the window scene’s
<doc://com.apple.documentation/documentation/UIKit/UICoordinateSpace/bounds> from
<doc://com.apple.documentation/documentation/UIKit/UIWindowScene/Geometry/coordinateSpace>
and multiplying it by the <doc://com.apple.documentation/documentation/QuartzCore/CALayer/contentsScale>
of your <doc://com.apple.documentation/documentation/QuartzCore/CAMetalLayer>:

```objc
- (void)resizeDrawable:(CGFloat)scaleFactor
{
    CGSize newSize = self.bounds.size;
    newSize.width *= scaleFactor;
    newSize.height *= scaleFactor;

    if(newSize.width <= 0 || newSize.width <= 0)
    {
        return;
    }

    if(_metalLayer) {
        if(newSize.width == _metalLayer.drawableSize.width &&
           newSize.height == _metalLayer.drawableSize.height)
        {
            return;
        }

        _metalLayer.drawableSize = newSize;
    } 

    [_delegate drawableResize:newSize];
}
```

<a id="handle-moving-a-window-between-displays"></a>

## Handle moving a window between displays

In iPad, you use <doc://com.apple.documentation/documentation/UIKit/UITraitCollection>
to assist with providing a flexible windowing environment that allows your app
to render and move windows between multiple displays. To eliminate the need to
manually register for trait changes, use
<doc://com.apple.documentation/documentation/UIKit/automatic-trait-tracking> to
observe the values you need from your specific views. In some cases, you might use
<doc://com.apple.documentation/documentation/UIKit/UIScreen> to access a trait
that <doc://com.apple.documentation/documentation/UIKit/UITraitCollection> doesn’t
provide, like <doc://com.apple.documentation/documentation/UIKit/UIScreen/nativeScale>.

When your app’s scene geometry changes — like when moving between screens —
the <doc://com.apple.documentation/documentation/UIKit/UIWindowSceneDelegate> calls the
<doc://com.apple.documentation/documentation/UIKit/UIWindowSceneDelegate/windowScene(_:didUpdateEffectiveGeometry:)>
method to inspect the window geometry and perform necessary updates:

```objc
- (void)windowScene:(UIWindowScene *)windowScene
        didUpdateEffectiveGeometry:(UIWindowSceneGeometry *)previousGeometry {

    UIWindowSceneGeometry *geometry = windowScene.effectiveGeometry;
    CGSize sceneSize = geometry.coordinateSpace.bounds.size;

    // Perform necessary updates after the scene geometry changes.
    if (!CGSizeEqualToSize(sceneSize, self.previousSceneSize)) {
        self.previousSceneSize = sceneSize;
    }
}
```

For more information on supporting multiple displays in iPadOS, see
<doc://com.apple.documentation/documentation/UIKit/presenting-content-on-a-connected-display>.
For more information on managing your Metal app window in macOS, see [Managing your game window for Metal in macOS](./managing-your-game-window-for-metal-in-macos-0050b14332.md).

<a id="lock-interface-orientation-for-device-rotation"></a>

## Lock interface orientation for device rotation

Some Metal apps and games might need to lock the interface orientation so the
screen geometry remains locked when a person rotates the device. To lock the
orientation, call
<doc://com.apple.documentation/documentation/UIKit/UIViewController/setNeedsUpdateOfPrefersInterfaceOrientationLocked()>
in your view controller and check whether the interface is already locked
with the `previousEffectiveGeometry` parameter of
<doc://com.apple.documentation/documentation/UIKit/UIWindowSceneDelegate/windowScene(_:didUpdateEffectiveGeometry:)>:

```objc
- (void)windowScene:(UIWindowScene *)windowScene
        didUpdateEffectiveGeometry:(UIWindowSceneGeometry *)previousGeometry {

    BOOL wasLocked = previousGeometry.interfaceOrientationLocked;
    BOOL isLocked = windowScene.effectiveGeometry.interfaceOrientationLocked;

    if (wasLocked != isLocked) {
        [self.myGameInstance pauseIfNeededWithIsInterfaceOrientationLocked: isLocked];
    }
}
```

For more information on locking your app’s orientation, see
<doc://com.apple.documentation/documentation/Technotes/tn3192-Migrating-your-app-from-the-deprecated-UIRequiresFullScreen-key>.

---

Copyright © 2026 Apple Inc. All rights reserved. | [Terms of Use](https://www.apple.com/legal/internet-services/terms/site.html) | [Privacy Policy](https://www.apple.com/privacy/privacy-policy)
