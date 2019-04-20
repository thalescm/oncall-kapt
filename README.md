# Onecall Kapt

This simple project aims to test kotlin cli to make kapt to run all phases toghether with compilation by using `aptMode=compile` as an argument to kapt.

Right now this isn't working on the kapt side.
If you **remove** lines 76 to 93 fron `build-project`, that all works fine (but the kapt won't be run).


## Project structure.

Project is composed of a and annotation class, on `kotlinannotation` folder, and an annotation processor that will process that annotation, on `kotlinap` folder.

`kotlinannotation` project is run with normal kotlin compilation (no kapt is necessary).
`kottlinap` project uses [auto-service](https://github.com/google/auto/tree/master/service) lib to be made an annotation processor, so it needs kapt in order to work right (without kapt, the META-INF/servives/javax.annotation.processing.Processor file is not created).

## Running

`./build-project` is all you have to do.

Output will be generated on `out` folder.

## Validating

unzip `out/kotlinap/kotlinap.jar` and check if `META-INF/servives/javax.annotation.processing.Processor` file exists