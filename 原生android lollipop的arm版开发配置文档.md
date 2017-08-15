
### 同步lollipop代码并编译
```
repo init -u git://192.168.0.185/lollipop/platform/manifest.git -b multiwindow
repo sync

repo start multiwindow --all
repo forall -c 'git remote add devorg git://192.168.0.185/lollipop/$REPO_PROJECT.git $@'

source build/envsetup.sh
lunch aosp_x86_64-eng
make -j<NUM>

#在目录out/target/product/generic_x86_64生成镜像：system.img和userdata.img
```

### 下载SDK并创建5.1的emulator
  - SDK放置于服务器上，可scp下载至本地： scp lh@192.168.0.180:~/sdk/5.1.tar.gz ./
  - 创建模拟器：openthos
  - 推荐参数：Ｎexus10, Android5.1.1 , Intel Atom(x86_64). noSkin
  - 启动：`./emulator -avd openthos -system /path/to/system.img -data /patch/to/userdata.img`
  
### 查看log
   - platform-tools: 
   - adb logcat *:V >> DEBUG.log
   
