# eSpeak NG Java Editor
__This is an eSpeakNG Editor rewritten in Java.__

![Screenshot](/docs/images/screenshot.png)

This editor is not production ready yet!
For latest development news look at [commits](https://github.com/valdisvi/espeak-ng-jeditor/commits/master) and [changelog](CHANGELOG.md). 
For production purposes you can use older snapshot of [espeak-ng-editor](https://github.com/valdisvi/espeak-ng-espeakedit)!

##Building

### espeak-ng
_eSpeakNG Java Editor relies on libraries of eSpeakNG, which have to be recompiled with custom settings._
Clone [eSpeakNG](https://github.com/espeak-ng/espeak-ng/) project and [solve dependencies](https://github.com/espeak-ng/espeak-ng/#dependencies):

(To be sure) install additional packages:

```
sudo apt-get install libwxgtk3.0 libportaudio2 sox libwxgtk3.0-dev libportaudio-dev
```

When invoke building of `espeak-ng` project add additional `-fPIC` flags to compiler, e.g. by compiling in following way:


```
./autogen.sh
CFLAGS='-fPIC' ./configure --prefix=/usr
make -B
```

### espeak-ng-jeditor
Clone [espeak-ng-jeditor](https://github.com/valdisvi/espeak-ng-jeditor) project.
_Note that `espeak-ng` and `espeak-ng-jeditor` projects should be subfolders of common folder!_

Compile customized shared library by executing Bash script in `espeak-ng-jeditor` project folder:

```
./updateJNIchanges.sh
```
To rebuild Java classes, run Maven task:

```
mvn compile
```
## Documentation

* [General Editor info](docs/editor.md)
* [User interface](docs/editor_if.md)
* [All other documents](docs/)

## Licence

This software is licenced under [GNU Lesser General Public License](https://spdx.org/licenses/LGPL-3.0.html)

## TODOs
**Project design**
- [ ] Implement JNI to espeak-ng API to save phoneme data
- [ ] implement JNI to espeak-ng API to translate text and show speech intonation
- [ ] Set up `pom.xml` file for Maven to allow building single, executable *.jar file with included *.so (shared library) file.
- [ ] Improve support for different GUI languages using Java *.properties files

**Editor GUI**

- [ ] Need to calculate rms and left panel's bottom part with correct values
- [ ] Implement "Amplitude frame" in bottom left corner
- [ ] Implement scrollbar for list of phoneme frames
- [ ] Implement listeners for all menu items and all buttons
- [ ] Make Fourier in text panel

