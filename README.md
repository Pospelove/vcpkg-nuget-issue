# vcpkg-nuget-issue

This repository was created to reproduce [microsoft/vcpkg#19038](https://github.com/microsoft/vcpkg/issues/19038)

## Details

There is a manifest file `vcpkg.json`. It contains two dependencies: `cpp-httplib` and `sqlite3`. 

There is also a GitHub workflow `.github/workflows/test.yml` based on [this example](https://github.com/microsoft/vcpkg/blob/f7c83acf486c572d7b1ebe5894dc83bca4f5faef/docs/users/binarycaching.md#github-packages). Full logs can be found [here](https://github.com/Pospelove/vcpkg-nuget-issue/runs/3149229829?check_suite_focus=true).

Everything works as expected for `cpp-httplib`:

```
Attempting to build package from 'x64-linux.nuspec'.
Successfully created package '/home/runner/work/vcpkg-nuget-issue/vcpkg-nuget-issue/vcpkg/buildtrees/cpp-httplib_x64-linux.0.9.1-vcpkg75a5a75aebe464e42595b35e450f69d866da94003d82be7308582c636b32b929.nupkg'.
Uploading binaries for cpp-httplib:x64-linux to NuGet source GitHub.
...
...
...
Your package was pushed.
```

However uploading `sqlite3` to NuGet fails:

```
Uploading binaries for sqlite3:x64-linux to NuGet source GitHub.
...
...
...
An error was encountered when fetching 'PUT https://nuget.pkg.github.com/skyrim-multiplayer/'. The request will now be retried.
An error occurred while sending the request.
  The server returned an invalid or unrecognized response.
  PUT https://nuget.pkg.github.com/skyrim-multiplayer/
An error occurred while sending the request.
  The server returned an invalid or unrecognized response.
Pushing NuGet to GitHub failed. Use --debug for more information.
```