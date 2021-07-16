# vcpkg_caching_test
Test repository to showcase Vcpkg Action Caching Issues

### First Run (Basic Setup):
- Runs with overlay-triplet.
- Expected: full run since it is the first time, and caches.
- Encountered: full run, cache message is successful:
```
Post job cleanup.
Save vcpkg and its artifacts to cache
  Caching paths: 'D:\a\vcpkg_caching_test\vcpkg_caching_test\vcpkg,!D:\a\vcpkg_caching_test\vcpkg_caching_test\vcpkg\packages,!D:\a\vcpkg_caching_test\vcpkg_caching_test\vcpkg\buildtrees,!D:\a\vcpkg_caching_test\vcpkg_caching_test\vcpkg\downloads,D:\a\vcpkg_caching_test\vcpkg_caching_test/clients/cpp/vcpkg_installed'
  Running save-cache with key 'localGitId=-574880384-args=42-os=1553167195-appendedKey=411780070-triplet=1258145250' ...
  C:\Windows\System32\tar.exe -z -cf cache.tgz -P -C D:/a/vcpkg_caching_test/vcpkg_caching_test --files-from manifest.txt
```

### Second Run
- Runs with overlay-triplet.
- Expected: Cached fast run since it should pick the results of previous build 
- Encountered: ...
