# Android_Application_Example

Application class is a base class of Android app containing components like Activities and Services. Application or its sub classes are instantiated before all the activities or any other application objects have been created in Android app.

## 1- Create new class and extnd Application:
```Java
import android.app.Application;

public class App extends Application {
}
```

## 2- To implement singleton instansing, use this way:
```Java
import android.app.Application;

public class App extends Application {
    private static App sInstance;

    @Override
    public void onCreate() {
        super.onCreate();
        sInstance = this;
    }

    public static App getInstance() {
        return sInstance;
    }
}
```

## 3- Use from App class instans instead of ApplicationContext in other classes:
```Java
Toast.makeText(App.getInstance().getApplicationContext(), "Some error text", Toast.LENGTH_SHORT).show();
...
App.getInstance().startActivity(intent);
...
SharedPreferences sharedPref = App.getInstance().getSharedPreferences(App.getInstance().getString(R.string.some_name), Context.MODE_PRIVATE);
```

# We can declare some other method or properties in App class ang use in other classes:
```Java
import android.app.Application;

public class App extends Application {
    private static App sInstance;
    private static String name = "Test Name";

    @Override
    public void onCreate() {
        super.onCreate();
        sInstance = this;
    }

    public static App getInstance() {
        return sInstance;
    }
    
    public static String getName() {
        return name;
    }
}
```
