# WindowsMauiUnpackagedSKGLViewError
Reproduction for SKGLView crash on Windows in .NET MAUI when built unpackaged

## Unpackaged (Not Working)

1. Delete `bin` and `obj` folders.
2. Build using 'dotnet build .\WindowsMauiUnpackagedSKGLViewError.csproj -f:net9.0-windows10.0.19041.0 -c:Debug --no-incremental'
3. Start the app by clicking on the exe in bin\Debug\net9.0-windows10.0.19041.0\win10-x64\WindowsMauiUnpackagedSKGLViewError.exe
4. App opens as a default MAUI App
5. Press Click me button. It tries to open now also GLPage with SKGLView
6. App crashes in an exception logged by Event Viewer (in Windows Logs\Application) at SkiaSharp.Views.GlesInterop.Egl.eglGetPlatformDisplayEXT(UInt32, IntPtr, Int32[]); this exception is identified by SentrySDK as System.Exception with message 'Failed to get EGL display'
7. If you remove SKGLView from GLPage.xaml, and repeat the process from (1), GLPage opens successfully

## Packaged (Working)

1. Delete `bin` and `obj` folders.
2. Build using 'dotnet build .\WindowsMauiUnpackagedSKGLViewError.csproj -f:net9.0-windows10.0.19041.0 -c:Debug --no-incremental'
3. Start the app from Visual Studio using **Windows Packaged MSIX** launch profile.
4. App opens as a default MAUI App
5. Press Click me button. It tries to open now also GLPage with SKGLView
6. App works.