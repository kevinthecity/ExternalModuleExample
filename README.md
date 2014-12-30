# ExternalModuleExample

Example of how to have an external project as a dependency. The key piece to pay attention to here is the top level [settings.gradle](https://github.com/kevinthecity/ExternalModuleExample/blob/master/settings.gradle) and the app modules [build.gradle](https://github.com/kevinthecity/ExternalModuleExample/blob/master/app/build.gradle#L25) file. This project requires the [ExoPlayer](https://github.com/google/ExoPlayer) library for demonstration purposes.

## settings.gradle
In `settings.gradle` you will see a reference to include the external module into your project. 
```
include '../ExoPlayer/:library'
```
This is a relative path, so for this example, the [ExoPlayer](https://github.com/google/ExoPlayer) library needs to exist in a folder at the same level as this project. The `:library` it is referencing is a module within that ExoPlayer project. Thats important because there could be multiple modules, and you would need to include them separately if you wanted them all.

## build.gradle
In `app/build.gradle` you will see a reference in the dependencies to compile the project.
```
dependencies {
    ...
    compile project(':../ExoPlayer/:library')
}
```

This ensures that the external project is compiled and that the code is useable within your own project.
