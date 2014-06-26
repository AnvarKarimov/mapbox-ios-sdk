# Releasing

1. Choose a version number per [Semantic Versioning](http://semver.org/). 
1. If appropriate, update `screenshot.png` in the `packaging` branch. 
1. Switch to `release` at a point where the release code is ready to go. 
1. Update `Mapbox.podspec` with the version and any other necessary changes. 
    - The local spec should reference `:branch => 'release'`, not a tag. 
    - Be sure to lint the spec with `pod spec lint`. 
1. Update `CHANGELOG.md` with change notes for the version. 
1. Update `README.markdown` as appropriate. Note that it references the screenshot mentioned above. 
1. Create a tag with the version in `release` and push the tag. 
1. Update the website docs in the `mb-pages` branch as appropriate. Be sure to update `version` in `_config.mb-pages.yml`. These docs might also reference the screenshot if it was updated above, so be sure to check context. 
1. Release on CocoaPods: 
    - Switch to the `packaging` branch. 
    - Run `git submodule update` to bring the CocoaPods working copy up to date. 
    - Run `cd CocoaPods` and ensure that you are on an up-to-date `master` branch. 
    - Copy `Mapbox.podspec` from `release` into a new folder in `./Mapbox/x.y.z` according to the version. 
        - The remote spec should reference `:tag => m.version.to_s`, not a branch. 
        - Be sure to again lint the spec with `pod spec lint`. 
    - Add the new folder and file and commit it to CocoaPods to publish the release. 
