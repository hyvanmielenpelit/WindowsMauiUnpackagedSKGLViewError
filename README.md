# WindowsMauiUnpackagedSKGLViewError
Reproduction for SKGLView crash on Windows in .NET MAUI when built unpackaged

1. Build using 'dotnet build .\WindowsMauiUnpackagedSKGLViewError.csproj -f:net9.0-windows10.0.19041.0 -c:Debug --no-incremental -p:WindowsPackageType=None'
2. Start the app by clicking on the exe in bin\Debug\net9.0-windows10.0.19041.0\win10-x64\WindowsMauiUnpackagedSKGLViewError.exe
3. App crashes in an exception logged by Event Viewer (in Windows Logs\Application)