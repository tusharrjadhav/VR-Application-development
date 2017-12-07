# VR-Application-development
Summary how to create VR Application for Android

**Supported VR platform**
-	Cardboard
-	Almost any smartphone on Android or iOS
-	Daydream
-	Pixel, Pixel XL, Galaxy S8, ZenFone AR, etc. Daydream ready phone

**SDKs**
-	Unity
-	Android/NDK
-	iOS
-	Unreal (game engine)

**Requirement**

-*Hardware*
       -	Daydream: Daydream-ready phone and a Daydream View.
       -	Cardboard: Android device running Android 4.4 ‘KitKat’ (API 19) or higher and a Cardboard viewer.
-*Software*
       -	Android Studio version 2.3.3 or higher.
       -	Android SDK 7.1.1 ‘Nougat’ (API 25) or higher.
       -	Google VR SDK for Android version 1.80.0 or higher.

Supported Formats
Image Specifications
-	png, jpeg, or gif. recommend use jpeg for improved compression.
-	Image dimensions should be powers of two (e.g. 2048 or 4096).
-	Mono images should be 2:1 aspect ratio (e.g. 4096 x 2048).
-	Stereo images should be 1:1 aspect ratio (e.g. 4096 x 4096).
-	Image need to be equirectangular format.
Video specifications
-	mp4s encoded with h264.
-	Mono videos should be 2:1 aspect ratio.
-	Stereo videos should be 1:1 aspect ratio.
-	For maximum compatibility and quality. Provide both a monoscopic 1920x1080 video and a stereo video at 2048x2048 or higher.

How to Use

def vrVersion= “1.80.0”
       dependencies{
       compile ‘com.android.support:appcompat-v7:26.0.0’
       compile ‘com.android.support:design:26.0.0’
       compile “com.google.vr:sdk-base:$vrVersion”
       compile “com.google.vr:sdk-audio:$vrVersion”
       compile “com.google.vr:sdk-common:$vrVersion”
       compile “com.google.vr:sdk-commonwidget:$vrVersion”
       compile “com.google.vr:sdk-panowidget:$vrVersion”
       compile “com.google.vr:sdk-videowidget:$vrVersion”
       }

VrPanoramaView
Since the image is large we load it asynchronously. (AsyncTask, RxJava, etc.)
Load image from:
-	asset
-	file system (png, jpeg, gif)
-	URL
-	anything can convert to Bitmap

vrVideoView.loadVideoFromAsset(filename,videoOptions);
vrVideoView.loadVideo(uri,videoOptions);

VrPanoramaView.Options
-	TYPE_MONO — single equirectangular panorama.
-	TYPE_STEREO_OVER_UNDER — two vertically-stacked equirectangular panoramaspanoramas.

VrVideoView 
Load video form:
-	asset
-	file system (mp4, webm, ogg, aac.)
-	MPEG-DASH format (Dynamic Adaptive Streaming over HTTP wiki) (support from v1.40.0)
-	HTTP Live Streaming (HLS wiki) format (ts, m3u8)

VrVideoView.loadVideo(Uri uri, VrVideoView.Options options)
      
VrVideoView.loadVideoFromAsset(String s, VrVideoView.Options options)

VrVideoView.Options
inputFormat
-	FORMAT_DEFAULT — In a standalone, non-streaming format using container formats such as mp4, webm, ogg, aac.
-	FORMAT_DASH — MPEG-DASH format. (a kind of adaptive bitrate streaming)
-	FORMAT_HLS — HTTP Live Streaming (HLS) format.
inputType
-	TYPE_MONO — single equirectangular panorama.
-	TYPE_STEREO_OVER_UNDER — two vertically-stacked equirectangular panoramas.

View Lifecycle
@Override
public void onPause(){
       super.onPause();
       panoWidgetView.pauseRendering();
       videoWidgetView.pauseRendering();
       }
@Override
public void onResume(){
       super.onResume();
       panoWidgetView.resumeRendering();
       videoWidgetView.resumeRendering();
       }
@Override
public void onDestroy(){
       super.onDestroy();
       panoWidgetView.shutdown();
       videoWidgetView.shutdown();
       }

RajawaliVR
Rajawali is a 3D engine for Android based on OpenGL ES 2.0/3.0.  RajawaliVR integrates the Rajawali 3D framework with the Google Cardboard SDK v0.6.0.
RajawaliVR used to be a separate module and now is moved to the main Rajawali repository on Github.

We can create VR app using Unity and Unreal. We need to create/import 3D model animate them and moment algorithms that make them hard to implement and Most important they are game engines and as Application developer we are also want to access to API and Libs provided by Android. With Unity & Unreal we lost the access to these.

OpenGL is standard when doing native mobile development. OpenGL the graphics lib and for animating and movement of the any object on screen we can use Rajawali lib.

Unity

Build virtual reality applications for Android and iOS using Unity and the Google VR SDK.
Unity's native integration with Google VR makes it easy to build Android applications for Daydream and Cardboard. The Google VR SDK for Unity provides additional features like spatialized audio, Daydream controller support, utilities and samples.
Using the native integration requires Unity 5.6 or newer.

Unity provide Unity IDE and MonoDevelop. Monodevelop is a development IDE for writing your code in C#, JS, and Boo. 

Unreal
Build mobile VR applications in Unreal using the Google VR Plugin. Unreal Engine natively supports creating Daydream and Cardboard applications.
Google has made significant improvements to Unreal Engine integration that will help developers build better production-quality Daydream apps. The latest version introduces Daydream controller support in the editor, a neck model, new rendering optimizations, and much more.
Unreal Engine 4 provides two toolsets for programmers which can also be used in tandem to accelerate development workflows. New gameplay classes, Slate and Canvas user interface elements, and editor functionality can be written with C++, and all changes will be reflected in Unreal Editor after compiling with either Visual Studio or XCode. The Blueprints visual scripting system is a robust tool which enables classes to be created in-editor through wiring together function blocks and property references.
C++ classes can be used as a base for Blueprint classes, and in this way programmers can set up fundamental gameplay classes that are then sub-classed and iterated on by level designers.

Read about creating Daydream applications in Unreal.



Reference
Google VR https://developers.google.com/vr
Google VR for Android https://developers.google.com/vr/android
VR View sample code https://developers.google.com/vr/android/samples/vrview
googlevr/gvr-android-sdk https://github.com/googlevr/gvr-android-sdk
Rajawali https://github.com/Rajawali/Rajawali






