# WindowsMauiUnpackagedSKGLViewError
Reproduction for SKGLView crash on Windows in .NET MAUI when built unpackaged

1. Build using 'dotnet build .\WindowsMauiUnpackagedSKGLViewError.csproj -f:net9.0-windows10.0.19041.0 -c:Debug --no-incremental -p:WindowsPackageType=None'
2. Start the app by clicking on the exe in bin\Debug\net9.0-windows10.0.19041.0\win10-x64\WindowsMauiUnpackagedSKGLViewError.exe
3. App opens as a default MAUI App
4. Press Click me button. It tries to open now also GLPage with SKGLView
5. App crashes in an exception logged by Event Viewer (in Windows Logs\Application) at SkiaSharp.Views.GlesInterop.Egl.eglGetPlatformDisplayEXT(UInt32, IntPtr, Int32[]); this exception is identified by SentrySDK as System.Exception with message 'Failed to get EGL display'
6. If you remove SKGLView from GLPage.xaml, and repeat the process from (1), GLPage opens successfully
7. If you keep the SKGLView and build a packaged version by omitting '-p:WindowsPackageType=None' and start the app from Visual Studio, GLPage opens successfully
