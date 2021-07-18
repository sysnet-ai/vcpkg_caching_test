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
- Encountered: Does full build.
- However, at the end it still sees the objects in the cache.
```
Post job cleanup.
Save vcpkg and its artifacts to cache
  Cache hit occurred on the cache key 'localGitId=-574880384-args=42-os=1553167195-appendedKey=411780070-triplet=1258145250', saving cache is skipped.
⏱ elapsed: 0.090 seconds
run-vcpkg post action execution succeeded
```
### Third Run
- Upgraded to v7 as per recommendation and removed stale path from the action
- Ran with overlay-triplet
- Encountered: Does full build
```
Post job cleanup.
Save vcpkg and its artifacts to cache
  Caching paths: 'D:\a\vcpkg_caching_test\vcpkg_caching_test\vcpkg,!D:\a\vcpkg_caching_test\vcpkg_caching_test\vcpkg\packages,!D:\a\vcpkg_caching_test\vcpkg_caching_test\vcpkg\buildtrees,!D:\a\vcpkg_caching_test\vcpkg_caching_test\vcpkg\downloads,D:\a\vcpkg_caching_test\vcpkg_caching_test/vcpkg_installed'
  Running save-cache with key 'localGitId=-574880384-args=42-os=1553167250-imageVer=-2107296685-appendedKey=411780070-triplet=1258145250' ...
  C:\Windows\System32\tar.exe -z -cf cache.tgz -P -C D:/a/vcpkg_caching_test/vcpkg_caching_test --files-from manifest.txt
  Cache saved successfully
⏱ elapsed: 146.174 seconds
```

### Fourth Run
