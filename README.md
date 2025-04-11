# WindowsMauiUnpackagedSKGLViewError
Reproduction for SKGLView crash on Windows in .NET MAUI when built unpackaged

## Unpackaged (Not Working)

1. Delete `bin` and `obj` folders.
2. Change WindowsPackageType to `None` in the .csproj file.
3. Build using 'dotnet build -f:net9.0-windows10.0.19041.0 -c:Debug --no-incremental'
4. Start the app by clicking on the exe in bin\Debug\net9.0-windows10.0.19041.0\win10-x64\WindowsMauiUnpackagedSKGLViewError.exe
5. App opens as a default MAUI App
6. Press Click me button. It tries to open now also GLPage with SKGLView
7. App crashes in an exception logged by Event Viewer (in Windows Logs\Application) at SkiaSharp.Views.GlesInterop.Egl.eglGetPlatformDisplayEXT(UInt32, IntPtr, Int32[]); this exception is identified by SentrySDK as System.Exception with message 'Failed to get EGL display'
8. If you remove SKGLView from GLPage.xaml, and repeat the process from (1), GLPage opens successfully

## Packaged (Working)

1. Delete `bin` and `obj` folders.
2. Change WindowsPackageType to `MSIX` in the .csproj file.
3. Build using 'dotnet build -f:net9.0-windows10.0.19041.0 -c:Debug --no-incremental'
4. Start the app from Visual Studio using **Windows Packaged MSIX** launch profile.
5. App opens as a default MAUI App
6. Press Click me button. It tries to open now also GLPage with SKGLView
7. App works.