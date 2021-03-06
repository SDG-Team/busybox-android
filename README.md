Busybox for Android the Easy Way (just a quick hack)
====================================================

This little package is designed to make your life easier if you are using
the shell under an Android device. It includes a full-fledged Busybox
environment that should make a fair replacement for the poor toolbox that
comes with Android by default.

You can install it in two ways: if you are compiling Android yourself, then
you can add this package to your repository and Busybox will replace the
default Toolbox whenever possible. If you already have a deployed (and
rooted!) Android device, you can deploy busybox on it.

Installing in your Android source tree
--------------------------------------
Simply add a 'local_manifest.xml' file (or edit the existing one) in the .repo
directory located at the root of your Android source tree with the following
lines:

    <?xml version="1.0" encoding="UTF-8"?>
    <manifest>
    <remote name="busybox-android"
            fetch="git://github.com/Gnurou/"/>
    <project path="busybox-android"
             name="busybox-android"
             remote="busybox-android"
             revision="master"/>
    </manifest>

Then run "repo sync" and build your images normally.

Installing on an already-deployed Android device
------------------------------------------------
Run the 'android-install.sh' script while your device is connected. This will
remount the system partition read-write, copy busybox, and make the appropriate
symlinks on your device. You will need adb in your path for this to work.

Misc
----
The files busybox-android.patch and busybox-android.config are a patch that
allows ash history to work on Android and the configuration used to build
Busybox, respectively. The busybox binary has been built statically against
glibc - unfortunately, it seems impossible to build it against Android NDK.

Non-executable .sh scripts are not meant to be run directly by the user.

Feedback & contact
------------------
Alexandre Courbot <acourbot@nvidia.com>

