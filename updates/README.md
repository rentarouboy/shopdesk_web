# ShopDesk cross-platform update feed

Stable releases are published in this repository without changing its website. Application source, licensing credentials, private keys and customer data are not uploaded.

Both ShopDesk clients read https://api.github.com/repos/rentarouboy/shopdesk_web/releases/latest and then the asset shopdesk-release.json. Drafts and prereleases are excluded. Tags use shopdesk-vMAJOR.MINOR.PATCH.

Required assets for every version:

- ShopDesk-vMAJOR.MINOR.PATCH-Windows-Setup.exe
- ShopDesk-vMAJOR.MINOR.PATCH-Windows-Portable.exe
- ShopDesk-vMAJOR.MINOR.PATCH-Android.apk
- shopdesk-release.json
- SHA256SUMS.txt

The schemaVersion 1 manifest contains version, ISO releasedAt, plain-text notes, windows.setup, windows.portable and android.apk. Each artifact contains its exact name and HTTPS GitHub release-download url, lowercase sha256 and integer bytes. The tag, version, platform names, sizes and checksums must all agree.

To publish future versions: build and validate both existing ShopDesk projects, retain Windows app identity and the Android package/signing identity, create a new draft release, upload all three final binaries plus manifest/checksums, verify uploaded hashes, then publish the complete release as latest. Keep all historical releases. The feed URL remains unchanged.

Windows verifies the setup download before the user opens the Windows installer. Android verifies the APK and uses the system package installer, including install-apps permission when required. Updates never move business data or change the licensing service. Neither client offers a downgrade.
