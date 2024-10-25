
mkdir ~/bin

curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo

chmod a+x ~/bin/repo

_____________________________
```
export ANDROID_HOME=/home/joimar/Android/Sdk
export PATH=$ANDROID_HOME/platform-tools:$ANDROID_HOME/tools:$PATH
```

______________________________________________________________

Olhe as builds em https://source.android.com/docs/setup/reference/build-numbers?hl=pt-br



repo init -u https://android.googlesource.com/platform/manifest -b android-12.1.0_r27



export ANDROID_HOME=/home/joimar/Android/Sdk