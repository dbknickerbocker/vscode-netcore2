"IntelliSense" Error in VS Code w/ ASP.NET Core 2.0
===================================================

VS Code's "IntelliSense" reports errors when authoring an ASP.NET Core 2.0 application on Windows, targeting .NET Framework 4.7 (full-framework, not .NET Core), with a runtime identifier of `win7-x64`.  The errors seems to persist even if targeting .NET 4.6.1 or 4.6.2, and even without a runtime identifier specified.

The IntelliSense errors follow this format:
```
The type '<TYPE>' is defined in an assembly that is not referenced. You must add a reference to assembly 'netstandard, Version=2.0.0.0, Culture=neutral, PublicKeyToken=cc7b13ffcd2dd51'. [<PROJECT_NAME>]
```

Error screenshots, when mousing over red squigglies
------
![IDisposable](https://github.com/dsteinweg/vscode-netcore2/raw/master/wwwroot/img/IDisposable.png)

![Object](https://github.com/dsteinweg/vscode-netcore2/raw/master/wwwroot/img/Object.png)

Environment
-----------
OS: `Windows 7 Enterprise SP1 x64`

VS Code version: `1.15.1`

OmniSharp (ms-vscode.csharp) version: `1.12.1`

`dotnet --info` output:
```
.NET Command Line Tools (2.0.0)

Product Information:
 Version:            2.0.0
 Commit SHA-1 hash:  cdcd1928c9

Runtime Environment:
 OS Name:     Windows
 OS Version:  6.1.7601
 OS Platform: Windows
 RID:         win7-x64
 Base Path:   C:\Program Files\dotnet\sdk\2.0.0\

Microsoft .NET Core Shared Framework Host

  Version  : 2.0.0
  Build    : e8b8861ac7faf042c87a5c2f9f2d04c98b69f28d
```

Restoring, building, and running from command line works fine:
```PowerShell
C:\github\vscode-netcore2 [master +7 ~0 -0 !]> dotnet restore
  Restore completed in 32.05 ms for C:\github\vscode-netcore2\vscode-netcore2.csproj.

C:\github\vscode-netcore2 [master +7 ~0 -0 !]> dotnet build
Microsoft (R) Build Engine version 15.3.409.57025 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  vscode-netcore2 -> C:\github\vscode-netcore2\bin\Debug\net47\win7-x64\vscode-netcore2.exe

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:04.58

C:\github\vscode-netcore2 [master +8 ~0 -0 !]> dotnet run
Hosting environment: Development
Content root path: C:\github\vscode-netcore2
Now listening on: http://localhost:5000
Application started. Press Ctrl+C to shut down.
info: Microsoft.AspNetCore.Hosting.Internal.WebHost[1]
      Request starting HTTP/1.1 GET http://localhost:5000/
info: Microsoft.AspNetCore.Hosting.Internal.WebHost[2]
      Request finished in 66.0619ms 200
```