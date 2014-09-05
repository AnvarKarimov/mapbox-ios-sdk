# Releasing

1. Choose a version number per [Semantic Versioning](http://semver.org/). 
1. If appropriate, update `screenshot.png` in the `packaging` branch. 
1. Switch to `release` at a point where the release code is ready to go. 
1. Update `CHANGELOG.md` with change notes for the version. 
1. Update `README.markdown` as appropriate. Note that it references the screenshot mentioned above. 
1. Update `Mapbox.podspec` with the version and any other necessary changes. 
    - The local spec should reference the version above, not a branch. 
    - Be sure to lint the spec with `pod spec lint`. 
1. Create a tag with the version in `release` and push the tag. 
1. Update the website docs in the `mb-pages` branch as appropriate. Be sure to update `version` in `_config.yml` and `_config.mb-pages.yml`. These docs might also reference the screenshot if it was updated above, so be sure to check context. 
1. Release on CocoaPods via `pod trunk push`. 
1. Switch to `packaging` and copy aside the `package.sh` script. 
1. Switch back to `release`, copy in `package.sh`, and run it. 
1. Zip up the product in `./dist` and upload to [S3](http://mapbox-ios-sdk.s3.amazonaws.com/index.html). 
