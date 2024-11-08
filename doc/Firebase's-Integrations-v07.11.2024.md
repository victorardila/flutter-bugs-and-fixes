# Configuración de Firebase en una aplicación Flutter

Este documento detalla los pasos necesarios para configurar Firebase en una aplicación Flutter, incluyendo la instalación de las herramientas de línea de comandos, la configuración de la aplicación para utilizar Firebase, y la inicialización de Firebase en el proyecto.

## 1. Instalación de las herramientas de línea de comandos necesarias

Primero, instala el CLI (Command Line Interface) de Firebase, lo cual permitirá interactuar con Firebase desde la terminal. En Linux, usa el siguiente comando:

```bash
# Copiar código
curl -sL https://firebase.tools | bash
```

- Una vez instalada la CLI, inicia sesión en Firebase usando tu cuenta de Google. Para ello, ejecuta:

```bash
# Copiar código
firebase login
```

- Luego, instala el CLI de FlutterFire, que es una herramienta específica para conectar las aplicaciones de Flutter con Firebase:

```bash
# Copiar código
dart pub global activate flutterfire_cli
```

- ademas, agrega la variable `flutterfire` a las variables de entorno por ejemplo en linux:

```bash
# En bashrc o zshrc
nano ~/.bashrc
```

- Agrega $HOME/.pub-cache/bin al PATH: Desplázate al final del archivo y agrega esta línea:

```bash
# Copiar código
export PATH="$PATH:$HOME/.pub-cache/bin"
```

- Finalmente, comprueba que tengas una versionde flutterfire instalada

```bash
# Copiar código
flutterfire --version
```

## 2. Configuración de la aplicación Flutter para usar Firebase

Para conectar tu aplicación Flutter con Firebase, usa la herramienta flutterfire configure. Esto permitirá seleccionar las plataformas (iOS, Android, Web) que usará tu app y generará un archivo de configuración necesario para la conexión.

- Navega al directorio de tu proyecto de Flutter y ejecuta:

```bash
# Copiar código
flutterfire configure
```

### ¿Qué hace el flujo de trabajo flutterfire configure?

El comando flutterfire configure inicia un flujo de trabajo interactivo que:

Te permite seleccionar las plataformas que tu aplicación soportará, como iOS, Android y Web.
Crea nuevas aplicaciones de Firebase para cada plataforma seleccionada en tu proyecto Firebase.
Te da la opción de seleccionar un proyecto de Firebase existente o crear uno nuevo.
Si ya existen aplicaciones registradas en el proyecto Firebase seleccionado, intenta asociarlas con tu proyecto Flutter, basado en la configuración actual.
Genera un archivo de configuración llamado firebase_options.dart en el directorio lib/ de tu proyecto. Este archivo contiene las opciones de configuración necesarias para conectar la app con Firebase.
(Para las funcionalidades de Crashlytics o Performance Monitoring en Android) Añade los complementos de Gradle necesarios en tu proyecto Flutter.

## 3. Inicialización de Firebase en la aplicación
Una vez configurada la aplicación para Firebase, inicializa Firebase en el código de Flutter.

- Desde el directorio de tu proyecto de Flutter, añade el paquete principal de Firebase:

```bash
# Copiar código
flutter pub add firebase_core
```

- Asegúrate de que la configuración de Firebase esté actualizada ejecutando nuevamente el comando:

```bash
# Copiar código
flutterfire configure
```

- En el archivo principal de tu aplicación (lib/main.dart), importa el paquete firebase_core y el archivo de configuración generado (firebase_options.dart):

```dart
# Copiar código
import 'package:firebase_core/firebase_core.dart';
import 'firebase_options.dart';
```

- Antes de ejecutar tu aplicación, inicializa Firebase utilizando el objeto DefaultFirebaseOptions (exportado por el archivo de configuración):

```dart
# Copiar código
WidgetsFlutterBinding.ensureInitialized();
await Firebase.initializeApp(
  options: DefaultFirebaseOptions.currentPlatform,
);
runApp(const MyApp());
```

- Finalmente, compila tu aplicación para asegurarte de que la configuración esté funcionando correctamente:

```bash
Copiar código
flutter run
```

## Tutorial

```src
https://www.youtube.com/watch?v=Z_RQ29Blh08
```
