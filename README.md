
This project is an example of a collection of
FTC OpModes that builds with the library implementation
of Qualcomm's ftc_app found here

  https://github.com/cmacfarl/ftc_app
  
It includes the ftc_app library via a change to the 
settings.gradle and build.gradle file.

Add the following to settings.gradle:

    include ':FtcLib'

    project(':FtcLib').projectDir = 
            new File(settingsDir, '../ftc_lib/ftc_app/FtcRobotController')

and the following to build.gradle:

    repositories {
        flatDir {
            dirs '../../ftc_lib/ftc_app/FtcRobotController/libs'
        }
    }

    dependencies {
        compile project(':FtcLib')
        compile 'com.android.support:appcompat-v7:22.1.1'
    }

The path to the ftp_app directory is relative you where this project 
is stored.  If you clone this repository you will need to change
those relative directories appropriately.

The ftc_app library looks in a resource file for the
list of OpModes to register.

For example:

    <?xml version="1.0" encoding="utf-8"?>
    <resources>
        <string name="op_mode_classpath">team25.testbot</string>
        <string-array
            name="op_mode_list">
                <item>NullOp</item>
        </string-array>
    </resources>

Replace the classpath with a path to your project, and add
any number of <item> elements with the names of your OpMode classes.
