# **Recovery**
A crash recovery framework!

----

[ ![Download](https://api.bintray.com/packages/sunzxyong/maven/Recovery/images/download.svg) ](https://bintray.com/sunzxyong/maven/Recovery/_latestVersion)[![License](https://img.shields.io/hexpm/l/plug.svg)](https://github.com/Sunzxyong/Recovery/blob/master/LICENSE)

[中文文档](https://github.com/Sunzxyong/Recovery/blob/master/README-Chinese.md)

# **Introduce**

[Blog Introduce](http://zhengxiaoyong.me/2016/09/05/Android%E8%BF%90%E8%A1%8C%E6%97%B6Crash%E8%87%AA%E5%8A%A8%E6%81%A2%E5%A4%8D%E6%A1%86%E6%9E%B6-Recovery)

“Recovery” can help you to automatic processing app crash at run time.It provides the following functions

* Automatic recovery activity stack and data.
* Support to recover the top activity
* To view and save of crash info.
* Restart and clear the cache.
* Twice failed to recover in a minute, will no longer to recover but to restart

# **Art**
![recovery](http://7xswxf.com2.z0.glb.qiniucdn.com/blog/Recovery.png)

# **Usage**
## **Reference**
**Gradle**

```
		compile 'com.zxy.android:recovery:0.0.3'
```

**Maven**

```
		<dependency>
  			<groupId>com.zxy.android</groupId>
  			<artifactId>recovery</artifactId>
  			<version>0.0.3</version>
  			<type>pom</type>
		</dependency>
```
## **Init**
In a custom Application performs initialization

```java
        Recovery.getInstance()
                .debug(true)
                .recoverInBackground(false)
                .recoverStack(true)
                .mainPage(MainActivity.class)
                .callback(new MyCrashCallback())
                .init(this);
```

## **Arguments**

| Argument | Type | Function |
| :-: | :-: | :-: |
| debug | boolean | Whether to open the debug mode |
| recoverInBackgroud | boolean | When the App in the background, whether to restore the stack  |
| recoverStack | boolean | Whether to restore the activity stack,else to restore the top activity |
| mainPage | Class<? extends Activity> | The back page |
| callback | RecoveryCallback | Crash info callback |

## **Callback**

```
public interface RecoveryCallback {

    void stackTrace(String stackTrace);

    void cause(String cause);

    void exception(String throwExceptionType, String throwClassName, String throwMethodName, int throwLineNumber);
}
```

## **Custom Theme**

Rewrite in your styles file：

```
    <color name="recoveryColorPrimary">#F44336</color>
    <color name="recoveryColorPrimaryDark">#D32F2F</color>
    <color name="recoveryColorAccent">#BDBDBD</color>
    <color name="recoveryTextColor">#FFFFFF</color>
```
## **Crash File Path**
> {SDCard Dir}/Android/data/{packageName}/files/recovery_crash/

# **LICENSE**

```
   Copyright 2016 zhengxiaoyong

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
```

