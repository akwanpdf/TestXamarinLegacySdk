# TestXamarinLegacySdk
**Purpose:** to show that when building an Android app that uses a Microsoft.NET.Sdk binding lib in terminal, a NuGet package is created. Meanwhile, when building an app that uses a Xamarin.Legacy.Sdk binding lib in terminal, no NuGet package is created. For both binding libs, GeneratePackageOnBuild is already set to true.

Projects:
1. JavaBinding: a binding library that uses Xamarin.Legacy.Sdk to target NET6 and MonoAndroid11.0
2. NET6JavaBinding: a binding library that uses Microsoft.NET.Sdk to target NET6
3. UseJavaBinding: an app that uses JavaBinding. 
4. UseNET6JavaBinding: an app that uses NET6JavaBinding. 

For context, the projects were created using Microsoft.Android.Templates::31.0.101-preview.10.59.

## Prerequisites
- .NET SDK version 6.0.100
- Visual Studio Community 2022 for Mac Preview, Version 17.0 Preview (17.0 build 4729)
- macOS Big Sur Version 11.6

## Directions
1. Download the repo.
2. Open terminal. In `JavaBinding/` folder, run `dotnet restore`.
3. In `UseJavaBinding/` folder, run `dotnet build`.
4. Observe that no `.nupkg` is created in the build output. Alternatively, check by opening the Finder app and searching for `.nupkg` in the `JavaBinding` folder (if there is one, its "Date Modified" time will not be the current time).
5. In `UseNET6JavaBinding` folder, run `dotnet build`.
6. Observe that a `.nupkg` is created in the build output (for example, this line may show up in the build output: `Successfully created package '<pathToRepo>/NET6JavaBinding/bin/Debug/NET6JavaBinding.1.0.0.nupkg'.`). Alternatively, check by opening the Finder app and searching for `.nupkg` in the `NET6JavaBinding` folder (its "Date Modified" time will be around the current time). 
