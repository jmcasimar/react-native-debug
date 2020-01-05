# react-native-debug

A continuación se enlistan los problemas que se han presentado en algún proyecto de react-native y cómo solucionarlo:

1- Problemas para compilar HRSL. Por algún motivo alguna dependencia crea conflictos para compilar el proyecto, las dependencias que presentaron problemas que requieren acciones adicionales al comando npm install -s <package> fueron:
* react-native-camera: Después de instalarlo fue necesario ligar manualmente el paquete con el proyecto siguiente los pasos recomendados en el siguiente link https://github.com/react-native-community/react-native-camera/blob/master/docs/installation.md. Es importante prestar especial atención a la versión de react-native para ligarlo automáticamente, en caso de no saber cual utilizar ligarlo el paquete manualmente.
* react-native-html-to-pdf: Después de instalarlo fue necesario ligar manualmente el paquete con el proyecto siguiendo los pasos recomendados en el siguiente link https://www.npmjs.com/package/react-native-html-to-pdf. Preste especial atención en la línea que solicita añadir "compile project..." se debe reemplazar compila por implementation dado que compile está obsoleto en la documentación de react-native. Así como eliminar u omitir la línea que dice "new MainReactPackage(),"
* react-native-print: Después de instalarlo fue necesario ligar manualmente el paquete con el proyecto siguiendo los pasos recomendados en el siguiente link https://www.npmjs.com/package/react-native-print. Preste especial atención en la línea que solicita añadir "compile project..." se debe reemplazar compila por implementation dado que compile está obsoleto en la documentación de react-native. Así como eliminar u omitir la línea que dice "new MainReactPackage(),"
* react-native-svg: Después de instalarlo fue necesario ligar manualmente el paquete con el proyecto siguiendo los pasos recomendados en el siguiente link https://github.com/react-native-community/react-native-svg#notice.

2- En caso de que obtengas el siguiente error:
Execution failed for task ':app:transformDexArchiveWithExternalLibsDexMergerForDebug'.
> com.android.builder.dexing.DexArchiveMergerException: Error while merging dex archives:
  The number of method references in a .dex file cannot exceed 64K.
  Learn how to resolve this issue at https://developer.android.com/tools/building/multidex.html
Debes habilitar multidex siguiendo los pasos del siguiente link https://developer.android.com/studio/build/multidex
Presta especial atención en la versión de Android para la cual estás trabajando, por lo general Android ^5.0. Si la versión que estás utilizando es mayor a esa lo único que debes hacer es cambiar en tu android/buidle.gradle la siguiente línea:
minSdkVersion = 21 o cualquier numero mayor a 21

3- Después de instalar todas las dependencias y ligarlas manualmente, fue necesario quitar las líneas añadidas en el archivo android/settings.gradle y MainApplication.java puesto que Android estaba creando el link duplicado.

4- El componente createStackNavigator fue movido de react-navigation a react-navigation-stack para resolver el error es necesario "npm install -i react-navigation-stack", cambiar la línea donde se importa el componente en el archivo src/navigator.js

5- El componente createDrawerNavigator fue movido de react-navigation a react-navigation-drawer para resolver el error es necesario "npm install -i react-navigation-drawer", cambiar la línea donde se importa el componente en el archivo src/navigator.js

5- Además fue necesario instalar "npm install -i react-native-reanimated", "npm install -i react-native-screens" y "npm install --s @react-native-community/masked-view"
