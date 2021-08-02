# Buildozer-Kivy-MacM1-Error
I'm currently trying to make my kivy app into an apk so I can run it on my phone. The tutorial I was using used buildozer and I did what it said. I then get the error `configure: error: Unexpected output of 'arch' on OSX` I think it's something to do with my Mac using the M1 chip. Just in case this might affect it, I'm using Pipenv for the app.

My Pipfile:
```
[[source]]
url = "https://pypi.org/simple"
verify_ssl = true
name = "pypi"

[packages]
kivy = {extras = ["base"], file = "https://github.com/kivy/kivy/archive/master.zip"}
buildozer = "*"

[dev-packages]

[requires]
python_version = "3.9"
```

Command Ran:

`buildozer -v android debug`

Edit:
I was able to get past this using rosetta in terminal. But now I have another error :p
I removed my spec file but you can still view it in the github.

My new error seems to be something with c++? The error logs mentions gcc a lot and pointer which I assume are from c++. I'm thinking I have the wrong version or a dependency that I don't have installed although I really have no clue.

Here's the error. Full error in github.
```
/Users/jaydenl/Dev/kivy/kvcalc/.buildozer/android/platform/build-armeabi-v7a/build/other_builds/hostpython3/desktop/hostpython3/Modules/posixmodule.c:9084:15: error: implicit declaration of function 'sendfile' is invalid in C99 [-Werror,-Wimplicit-function-declaration]
        ret = sendfile(in, out, offset, &sbytes, &sf, flags);
              ^
gcc -Wno-unused-result -Wsign-compare -Wunreachable-code -DNDEBUG -g -fwrapv -O3 -Wall    -std=c99 -Wextra -Wno-unused-result -Wno-unused-parameter -Wno-missing-field-initializers -Wstrict-prototypes -Werror=implicit-function-declaration  -I/Users/jaydenl/Dev/kivy/kvcalc/.buildozer/android/platform/build-armeabi-v7a/build/other_builds/hostpython3/desktop/hostpython3/Include/internal -IObjects -IInclude -IPython -I. -I/Users/jaydenl/Dev/kivy/kvcalc/.buildozer/android/platform/build-armeabi-v7a/build/other_builds/hostpython3/desktop/hostpython3/Include    -DPy_BUILD_CORE_BUILTIN  -c /Users/jaydenl/Dev/kivy/kvcalc/.buildozer/android/platform/build-armeabi-v7a/build/other_builds/hostpython3/desktop/hostpython3/Modules/_sre.c -o Modules/_sre.o
gcc -Wno-unused-result -Wsign-compare -Wunreachable-code -DNDEBUG -g -fwrapv -O3 -Wall    -std=c99 -Wextra -Wno-unused-result -Wno-unused-parameter -Wno-missing-field-initializers -Wstrict-prototypes -Werror=implicit-function-declaration  -I/Users/jaydenl/Dev/kivy/kvcalc/.buildozer/android/platform/build-armeabi-v7a/build/other_builds/hostpython3/desktop/hostpython3/Include/internal -IObjects -IInclude -IPython -I. -I/Users/jaydenl/Dev/kivy/kvcalc/.buildozer/android/platform/build-armeabi-v7a/build/other_builds/hostpython3/desktop/hostpython3/Include    -DPy_BUILD_CORE_BUILTIN  -c /Users/jaydenl/Dev/kivy/kvcalc/.buildozer/android/platform/build-armeabi-v7a/build/other_builds/hostpython3/desktop/hostpython3/Modules/_codecsmodule.c -o Modules/_codecsmodule.o
1 error generated.
make: *** [Modules/posixmodule.o] Error 1
make: *** Waiting for unfinished jobs....
1 warning generated.
```

