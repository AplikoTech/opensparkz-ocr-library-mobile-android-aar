# OS-Secure-Card-Capture-Component-Android
Keep the OSCardCapture-release.aar file in app/libs folder.

and now open app level build.gradle file and add following line

    dependencies {
       implementation files('libs/OSCardCapture-release.aar')
    }

After that sync the project and its done.


1. 	Implementation
 
Add the following code in your design XML:

    <com.opensparkz.oscardcapture.OSCardCapture
        android:id="@+id/cardCaptureComponent"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>
 
 
Create an instance of cardCaptureComponent:

    Val cardCaptureComponent = findViewById(R.id.cardCaptureComponent)
 
Enable Default loader(Optional):

    cardCaptureComponent?.enableDefaultLoader()
 
Configure API environment(Optional), available options are `TEST`, `PRODAU` & `PRODUS`, default `TEST`:

    cardCaptureComponent?.environment(“TEST”)
 
Register Card:
//Show your loader, if SDK default loader is not enabled

    cardCaptureComponent?.registerCard(accessToken, this)
    
2nd parameter is a result response listener
 
Override listener methods:

    override fun onSuccess(code: Int, message: String?, data: JSONObject?) {
    //Dismiss your loader is used
    // code- a value from API response 0 means success else we have some errors
    //messages- response message
    // data- contains values in response of register card sample data
    {
            "cardToken": "9efeb2fe-7af8-4dc2-8d30-c173554",
            "cardScheme": null,
            "cardId": "xxxx-xxxx",
            "referenceId": null,
            "expiry": "0224"
        }

    }

    override fun onFailure(code: Int, message: String?) {
    //Dismiss your loader is used
    // code- code except 0
    //messages- error message
    }

 
Customisation in com.opensparkz.oscardcapture.OSCardCapture View Change text label color

    app:defaultTextColor="#777676"
 
Change card background color

    app:backgroundColor="#fff"
 
Change border color of card & expiry edittext is in focus

    app:activeBorderColor="#AA3C3C"
 
Change border color of Complete component, Card edittext & expiry edittext view

    app:defaultBorderColor="#000"
 
Change text color of card and expiry edit text view

    app:defaultEditTextColor="#777676"
 
Change color of error message below card and expiry edit text view

    app:errorTextColor="#AA3C3C"
 
Change the font family for texts

    android:fontFamily="@font/your_font"/>
    
