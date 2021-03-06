L710/d2vzw Build Instructions
=======================
http://wiki.cyanogenmod.org/w/Build_for_d2vzw
```
mkdir -p android/CM11
cd android/CM11
repo init -u git://github.com/CyanogenMod/android.git -b cm-11.0
```

Modify your `.repo/local_manifest/roomservice.xml` as follows:

```xml
<?xml version="1.0" encoding="UTF-8"?>
  <manifest>
    <project name="Hrubak/d2vzw-tools.git" path="d2vzw-tools" remote="github" revision="cm-11.0" />
    <project name="TheMuppets/proprietary_vendor_samsung" path="vendor/samsung" revision="cm-11.0" />
    <project name="CyanogenMod/android_device_samsung_d2vzw" path="device/samsung/d2vzw" remote="github" />
    <project name="CyanogenMod/android_device_samsung_qcom-common" path="device/samsung/qcom-common" remote="github" />
    <project name="CyanogenMod/android_device_samsung_msm8960-common" path="device/samsung/msm8960-common" />
    <project name="CyanogenMod/android_device_samsung_d2-common" path="device/samsung/d2-common" remote="github" />
    <project name="CyanogenMod/android_kernel_samsung_d2" path="kernel/samsung/d2" remote="github" />
    <project name="CyanogenMod/android_hardware_samsung" path="hardware/samsung" remote="github" />
  </manifest>
```

```
repo sync
vendor/cm/get-prebuilts
```

Auto Apply Patches
==================
This script will remove any topic branches named auto, then apply all patches under topic branch auto.

```
d2vzw-tools/apply.sh
```
Usage: 
```
repo start auto 'path'                            #start a new branch 'auto' and set the path to your project
echo "say something about the patch"              #echo something
cdv 'same path ^'                                 #cd to the project path
git reset --hard                                  #make the project clean
git fetch, git revert, git something put it here  #add you cherry-picks, reverts, etc here
cdb                                               #cd back to working_dir
```

Build
=====
```
. build/envsetup.sh && brunch d2vzw
```
