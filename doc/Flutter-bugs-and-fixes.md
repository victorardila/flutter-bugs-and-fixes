# `Solución de Bugs de Flutter a partir de soluciones tecnicas`

<div style="display: flex; justify-content: space-between;">
    <img src="https://github.com/user-attachments/assets/ca42b94b-ff08-49ef-abd9-ac109ef58e80" alt="bug" width="100%" />
</div>

## `Documentacion`

Este README.md es para actualizar un proyecto Flutter que ha estado inactivo por un tiempo, especialmente si has cambiado de computadora o has actualizado tu entorno de desarrollo. De otra manera si por algun caso
las deendencias de flutter se han actualizado o si se ha cambiado la version del SDK de flutter o quizas desee cambiarlo.

### Problemas comunes:
- ### `Incompatibilidades de Gradle:` 
Flutter depende de Gradle para la construcción del proyecto. Si has actualizado Flutter, Gradle o tu sistema operativo, es posible que haya incompatibilidades entre las versiones que estén provocando errores.

- ### `Dependencias desactualizadas:` 
Los paquetes de las dependencias (por ejemplo, flutter pub upgrade) pueden no ser compatibles con las versiones más recientes del SDK de Flutter o con las versiones más recientes de otras bibliotecas.

- ### `Incompatibilidades del SDK de Flutter:` 
Si el SDK de Flutter con el que creaste el proyecto es más antiguo que la versión actual, podrías encontrar errores al intentar construir el proyecto con el SDK de Flutter actual.

### Nota: Sigue los pasos de acuerdo a los casos

Debe estar constantemente ejecutando los comandos base de flutter a nivel raiz de proyecto.

`Obtener informacion del proyecto como el SDK de flutter la version de java, version de flutter, etc.`

```sh(bash)
# Obtener informacion del desarrollo del proyecto
flutter doctor --verbose
```

### `ScreenShoot`

![Consola](https://github.com/user-attachments/assets/fa2ba3d6-4b80-49f8-8485-5a8186c3b273)

Aquie esta el resumen de la creacion del proyecto con todas sus especificaciones

`Reconstruccion rapida`

```sh(bash)
# Limpiar construcciones del proyecto
flutter clean
# Obtener las dependencias del pubspect
flutter pub get
# ejecutar el proyecto
flutter run
```

### 1. Desuso del proyecto por algun tiempo.

### `Descripcion`

Cuando se deja de ejecutar un proyecto y se deja en el vault del olvido este queda con su dependencias con las que se trabajo, lo que quiere decir que depsues de un tiempo esta versiones estaranen `deprecated`o obsoletas.
Si este es el caso debemos asegurarnos de ejecutar por consola a nivel raiz de proyecto esto:

```sh(bash)
flutter pub upgrade
```

- Deberia haber actualizado las dependencias a la versiones actuales de las mismas 

## `Si el paso anterior no solucionó`
### 2. Actualizar el SDK a la version estable oficialmente

En muchos casos los errores o bugs que se presentan se originan por la version del SDK quizas por su falta de compatibilidad con el entorno actual de las herramientas de dart

```sh(bash)
flutter channel
```

```sh(bash)
flutter channel stable
```

```sh(bash)
flutter upgrade
```

### `ScreenShoot`

![Consola](https://github.com/user-attachments/assets/0077ad05-ca07-4e7a-a4bd-33834b0e7eb4)

## `Si los pasos anteriores no funcionaron quiere decir que el error tiene una profundidad mayor`
Si por alguna razon se actualizo o actualizaste Android Studio entonces deberas actualizar la version del gradle por cada version de complemento

### 3. Manipular las versiones de Gradle y Kotlin a partir de esta tabla(Recomendado)
Para actualizar su version de gradle hay dos formas de actualizarlo manualmene(No recomendado) y por consola(Recomendado):

### `(Recomendado)`
A nivel de android del proyecto en la consola debe ejecutar este comando:
```sh
./gradlew wrapper --gradle-version=8.3
```

### `(No recomendado)`

Debes ir al archivo gradle-wrapper.properties dentro de la carpeta gradle dentro de wrapper
Proyecto>📂android>📂gradle>📂wrapper

```text
distribuciónBase= GRADLE_USER_HOME
distribuciónPath=wrapper/dists
zipStoreBase= GRADLE_USER_HOME
zipStorePath=wrapper/dists
# Cambiar la version del gradle en gardle-(version empleada).zip
distribuciónUrl=http://services.gradle.org/distributions/gradle-8.3-all.zip
```

### Sitio oficial: `https://developer.android.com/build/releases/gradle-plugin?hl=es-419`
