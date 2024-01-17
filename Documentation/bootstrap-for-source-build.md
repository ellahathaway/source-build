# Bootstrap SDK for a Source-Build Build

## Step 1: Download the Source-Build SDK

Navigate to the artifacts for a clean SB build of the VMR. Obtain the appropriate SDK(s) from these artifacts.

The current SB build requires 4 artifacts:
- CentOS8_Stream_Online_MSFT sdk
- CentOS8_Stream_Online_MSFT artifacts
- Alpine3.19 sdk
- Alpine 3.19 artifacts

> The necessary artifacts will change depending on the required Stage 2 builds. That is, since the Stage 2 build consumes the Stage 2 artifacts, it is necessary to upload the corresponding Stage 1 artifacts for every Stage 2 build.
> Currently. the VMR has 2 Stage 2 legs: CentOS_Stream8 and Alpine3.19. As a result, we must upload the SDK and artifacts for both OSes.


## Step 2: Upload artifacts to blob storage

Using Azure Storage explorer, upload the artifacts to our blob storage.

## Step 3: Update global.json with MSFT SDK version

Navigate to [installer/src/SourceBuild/content/global.json](https://github.com/dotnet/installer/blob/main/src/SourceBuild/content/global.json) and update the dotnet version with the latest version as found at https://github.com/dotnet/installer?tab=readme-ov-file#table

## Step 4: Update Version.Props

Nagivate to [installer/src/SourceBuild/content/eng/Version.Props](https://github.com/dotnet/installer/blob/main/src/SourceBuild/content/eng/Versions.props) and update `PrivateSourceBuiltSdkVersion` and `PrivateSourceBuiltArtifactsVersion` with the versions of the SDK and artifacts you pulled downloaded in Step 1. These should both be the same version.

## Step 5: Open a PR with your changes

Open a PR with these changes and include @dotnet/source-build-internal as a code reviewer.
