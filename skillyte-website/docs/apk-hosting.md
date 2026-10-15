# Hosting the Android APK

The APK is **not stored in this repository**. It is about 110 MB, which is over GitHub's 100 MB limit for files in a repo. It is hosted on Amazon S3, and the "Download APK" button on the home page links to it:

`https://skillyte-prod.s3.ap-south-1.amazonaws.com/resources/Skillyte_v1.0.17_118_12_10_2026_17_25.apk`

## Publish a new version

1. Upload the new APK to S3 and make sure it is publicly readable (see the checklist below).
2. In `index.html` (section `#android-apk`) update the download link, version, size, "Updated" date and SHA-256 checksum.
3. Commit and deploy the site.

Make the checksum with `shasum -a 256 <file>` (macOS/Linux) or `certutil -hashfile <file> SHA256` (Windows).

## S3 checklist

- **Make only the APK public, not the whole bucket.** `skillyte-prod` is the production bucket and may hold user data. Prefer a separate bucket (for example `skillyte-public-downloads`) or a bucket policy that allows public `s3:GetObject` only on the download path. Keep S3 "Block Public Access" on for everything else.
- Set the object's **Content-Type** to `application/vnd.android.package-archive`.
- Consider putting **CloudFront** in front of the bucket. It is faster for visitors and cheaper than serving 110 MB files directly from S3.
- Test the link in a private browser window while signed out of AWS.
- Always sign releases with the same keystore, or Android will refuse to update an installed app.

## Current release

- Package: `com.skillyte.app`
- Version: 1.0.17 (build 118)
- Minimum Android: 7.0 (API 24)
- SHA-256: `461a6d21cc77c5e37d6fe09ccfe50d240ee57037f6d0ddc8820f6894e3d5355b`
