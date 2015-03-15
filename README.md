## JEB App
The project provides an OS X app bundle for the JEB decompiler. It does NOT contain the JEB itself. Before using it, you may need to get a copy of the JEB from PNF Software: [https://www.pnfsoftware.com/]().

### How to Use
__Step 1.__ Clone this project to your Mac

__Step 2.__ Link to your copy of JEB

For example, if your JEB is placed at `~/bin/jeb` directory, execute:

  ```
  $ ln -s ~/bin/jeb JEB.app/Contents/Resources/Java
  ```

__Step 3.__ Config Java runtime version

Java 6 user can do nothing. If you are using Java 7, 

  ```
  $ vim JEB.app/Contents/Info.plist
  ```

Then change value of the key `JVMVersion` from `1.6+` to `1.7+`.

__Step 4.__ (_Optional_) Customize JVM options

These options are defined by the key `VMOptions` in the `JEB.app/Contents/Info.plist` file. 

__Step 5.__ (_Optional_) Customize the icon

Place your favorite icon (in Apple's .icns format) to `JEB.app/Contents/Resources/jeb.icns`. The default icon is converted from the newest official one (which is ugly indeed). An old official icon is also privided as `jeb_old.icns` in the same directory for your convenience. Note that after JEB launched, its icon on the docker will still changed to the official embedded one. You can hacks the `$JEB_ROOT/bin/jeb.jar` by yourself (hint: change PNG files in `assets` directory).

__Step 6.__ Copy the `JEB.app` to your `/Applications/` and enjoy it.

### Tested Environments
* OS X 10.9 Mavericks
* Java 6 (1.6.0 65)
* JEB 1.5.201410220 and JEB 1.5.201502120

### Known Issues
* You can't open two or more instances of the JEB only through clicking the app icon -- please use traditional command line instead. 
* Update checking may be skipped -- please use traditional way to check for updates. 

### Security/Privacy Concerns
The `JEB.app/Contents/MacOS/JavaApplicationStub` file is directly copied from `/System/Library/Frameworks/JavaVM.framework/Versions/Current/Resources/MacOS/JavaApplicationStub` in OS X 10.9.5 without any change. SHA-1 is `8dd8cbdd290e6e7506bb5b5203cf8cf6d1a27ad9`. 
