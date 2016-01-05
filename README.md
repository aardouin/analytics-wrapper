# AnalyticsWrapper
A multi analytics service wrapper

##Setup

Add `core` dependency, current version is `0.1`: 

```groovy
repositories {
    maven { url "https://jitpack.io" }
}
compile 'com.github.aardouin.analytics-wrapper:core:$version'
```


##Quick start guide

####Init AnalyticsManager 
It is advised to use AnalyticsManager as a singleton inside your application : 

```java
private static AnalyticsManager analyticsManagerInstance;
@Override
public void onCreate() {
    super.onCreate();
    analyticsManagerInstance = new AnalyticsManager();
}

public static AnalyticsManager getAnalyticsInstance(){
    return analyticsManagerInstance;
}
```


In order to add a new analytics provider, include it into gradle : 

```groovy
compile 'com.github.aardouin.analytics-wrapper:$provider:$version'
```

Add provider instance to using : 

```java
analyticsManagerInstance.addAnalytics("analyticsName",AbstractAnalytics analytics)
```

##Providers available
* [AT Internet](./atinternet/)
* [Google Analytics](./googleanalytics/)

##Simple events tracking

Tracking can be made for every analytics instance available to the manager or for a specific analytics instance : 

i.e : 

```java
analyticsManagerInstance.trackScreen("screenName");

analyticsManagerInstance.getAnalyticsInstance("specificAnalyticsName")
						.trackScreen("screenName");
```

Tracking method available are the following : 

```java
void trackScreen(String screenName);
void trackClickEvent(String eventName);
```
