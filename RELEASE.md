# Release Notes

Use this checklist before publishing a GitHub release.

## Before Release

- Confirm `src/DelimPlot.App/DelimPlot.App.csproj` version fields are set to the release version.
- Refresh screenshots in `screenshots/`.
- Verify sample files in `samples/` load and plot correctly.
- Run a Release build.
- Publish the Windows standalone executable.
- Test opening a `.delimplot` file with `DelimPlot.exe`.

## Build Commands

```powershell
dotnet build DelimPlot.sln --configuration Release
```

```powershell
dotnet publish src\DelimPlot.App\DelimPlot.App.csproj --configuration Release --runtime win-x64 --self-contained true -p:PublishSingleFile=true -p:PublishReadyToRun=false -p:IncludeNativeLibrariesForSelfExtract=true -o artifacts\win-x64
New-Item -ItemType Directory -Force -Path artifacts\release | Out-Null
Copy-Item artifacts\win-x64\DelimPlot.exe artifacts\release\DelimPlot-0.1.0-win-x64.exe -Force
Copy-Item artifacts\win-x64\DelimPlot.exe artifacts\release\DelimPlot-latest-win-x64.exe -Force
```

## Release Artifact

This release currently publishes Windows x64 only.

Attach these files to the GitHub release:

```text
artifacts\release\DelimPlot-0.1.0-win-x64.exe
artifacts\release\DelimPlot-latest-win-x64.exe
```

## Suggested Tag

```text
v0.1.0
```
