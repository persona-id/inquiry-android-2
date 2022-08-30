# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project
adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [v2.2.34] - 2022-08-30

### Fixed

- Fixed a crash when custom text attributes are set on the overlay hint of the government ID capture screen.

## [v2.2.33] - 2022-08-30

### Fixed

- Fixed a bug where background images and colors wouldn't stretch to fill the screen.

## [v2.2.32] - 2022-08-29

### Changed

- Autosubmit confirmation code after it has been typed in.
- Confirmation code fields now paste properly and align with expected behavior when deleting and changing numbers.
- Give a default margin of 24dp to footers

### Fixed

- Fixed a crash related to lottie.
- Fixed text layouts when the device is set to render large font sizes for accessibility.
- Fixed a bug that caused inquiries which contained back-to-back combined steps of the same type to hang.

## [v2.2.31] - 2022-08-22

### Added

- Added the ability to render the government id select screen as a more granularly configurable page type
- Added the ability to style processing screen text elements via the server

### Fixed

- Fix a bug where text fields will not retain their state on activity recreate.
- Fix a bug where cursor will jump to the front in text fields on text input.

### Changed
- Downgrade dependency on bouncy castle from jdk18on to jdk15to18.

## [v2.2.30] - 2022-08-15

### Fixed

- Workaround an Android 12 bugs where requesting permissions can cause a memory leak.
- Fix a crash that would occur when a selfie/government id flow is launched on a device has no cameras.

### Changed

- Keep screen on on camera capture screens.
- Default assets for government id, selfie, and document processing animations have been updated.
- Permission request popup has been moved for the government ID step. It was moved from the ID select screen to the camera capture screen.

## [v2.2.29] - 2022-07-29

### Added

- Added the ability to control page level vertical alignment via the server.
- Added the ability to style buttons on the government id capture page via the server.

### Fixed

- Fixed an animation bug on small screens on the review captured image screen.
- Swapped the order of the buttons on the permission request bottom sheet to be consistent with Android standards.
- Fixed an issue where you couldn't resume inquiries created in sandbox mode and have the pass/fail toggle show up.

## [v2.2.28] - 2022-07-19

### Fixed

- Fixed a bug where buttons were not being properly aligned when a loading indicator is built into the button.

## [v2.2.27] - 2022-07-18

### Added

- Support configuration to skip the instructions screen for selfie capture.

### Fixed

- Fixed a bug where the government ID step will send the wrong parameters to the server in certain edge cases.

## [v2.2.26] - 2022-07-08

### Added

- Added the following theme property:
  - `personaInitialLoadingBackgroundDrawable`
- Added animations when transitioning between screens

### Changed

- Improve barcode scanning to detect barcodes faster
- Removed loading screens when navigating back
- Update dependencies

## [v2.2.25] - 2022-06-27

### Changed

- When transitioning to the next step, show a progress bar embedded into the action button as opposed to showing a full screen progress bar.

### Fixed

- Fix a crash for the document select step when a selected document cannot be opened.
- Fix a bug that caused the government ID step to upload one more photo than necessary.
- Made lottie animation loading more resilient.

## [v2.2.24] - 2022-06-15

### Fixed

- Confirm back press when users press the back button on transition/load screens.
- Disable submit button on document select screen if no documents are selected.
- Show an icon for PDF documents selected for the document verification step.

### Added

- Added a hint shadow that indicates when there is more content to be scrolled.
- Added the app set ID to request headers (https://developer.android.com/training/articles/app-set-id)

### Changed

- Match camera feed edge radius and hint box radius to the radius of the capture feed border.
- Updated the implementation of government id auto capture to allow server configurability.
- Update dependencies
- Limit polling for inquiry status update to 90 seconds. Previously there was no time limit.
- Update the network write timeout to 1 minute. Previously this was 10 seconds.

## [v2.2.23] - 2022-05-24

### Added

- Added support for the following `InquiryField` types: `date`, `datetime`, `float`

### Changed

- Change the government ID select screen to be configurable by the server
- Update dependencies
- Depend on Kotlin 1.6.10

## [v2.2.22] - 2022-05-20

### Fixed

- Disable back action for government id flows without a back step
- Improve handling of network errors

## [v2.2.21] - 2022-05-16

### Changed

- Make the number of images captured for the government id step configurable by the server
- Make the manual capture button delay for the government id step configurable by the server
- Update the image shown when there was an error verifying the back side of a government id

## [v2.2.20] - 2022-05-06

### Changed

- Allow users to retry navigating between certain steps on recoverable network errors
- Allow users to retry uploading government id/document files
- Improve network calls so they are more resilient
- Selfie biometric consent has moved to appear above the agreement button to ensure users have read the full consent text before continuing.
- Update dependency of Coil from 0.12.0 to 2.0.0-rc03

### Fixed

- Display errors on input fields when there is a user input error
- Fix flickering of image/document previews in rare cases.

## [v2.2.19] - 2022-04-29

### Fixed

- Fix the resolution of font names when loading custom font families in texts

## [v2.2.18] - 2022-04-27

### Changed

- Handle more types of network errors

## [v2.2.17] - 2022-04-22

### Changed

- Make the clickable area of the back and close button slightly bigger

### Fixed

- Fix a race condition crash on the inquiry success screen

## [v2.2.16] - 2022-04-20

### Added
- Added the ability to render markdown on selfie step disclosure text

## [v2.2.15] - 2022-04-13

### Removed

- The following string resources have been removed, their values are now supplied by the server:
  - `pi2_selfie_hold_still`

## [v2.2.14] - 2022-04-04

### Added

- Added the following style attribute: `personaCenterAlignRemoteAsset`

### Fixed

- Handle 404s more gracefully

## [v2.2.13] - 2022-03-30

### Changed

- Skip government ID select screen if only one ID class is available
- The loading icon for initial inquiry load has been changed to a neutral grey spinner 

### Fixed

- Allow for server-defined images to have nullable widths/heights without crashing

## [v2.2.12] - 2022-03-24

### Changed

- Selfie manual capture button for the center pose now triggers a capture immediately for behavior
  consistency. Previously it would trigger a countdown instead.

### Fixed

- Show users the manual capture button immediately if auto capture cannot be performed on the device
- Recover from camera related errors more gracefully, allow users to retake photos on error

## [v2.2.11] - 2022-03-22

### Changed

- Government id list items now use `textAppearanceListItem` instead of `textAppearanceSubtitle1`
- Selfie capture animations are now customizable via `personaSelfieLookLeftLottieRaw` and
  `personaSelfieLookRightLottieRaw`
- When a static image (drawable) is set instead of a Lottie animation via
  `personaSelfieLookLeftDrawable` and `personaSelfieLookRightDrawable`, the animation will not play.
  Instead, the given static image will be used instead.

### Fixed

- Respect the values of `personaSelfieLookLeftDrawable` and `personaSelfieLookRightDrawable`
- Prevent buttons from overlapping with UI elements on government ID flow

## [v2.2.10] - 2022-03-16

### Changed

- Various animations and drawables are more themeable

**UI UPDATES: SELFIE CAMERA CAPTURE SCREEN**

We’ve made updates to the selfie verification flow to help reduce blurry and repeat pose captures.
You’ll notice the following changes to the selfie verification flow:

- New selfie animation includes an arrow that points users in the direction they should look for
  left and right pose capture.

- Auto-capture is delayed for left and right pose until each animation plays. In addition, user will
  be able to clearly preview selfie during capture (blur overlay removed).

If you have any questions about these changes, please reach out to your CSM.

### Fixed

- Reduce flickering due to re-layouts during first render pass
- Title/body text fields can now honor `android:textAlignment` properly
- Improve government ID capture's user experience on lower end devices; make UI more responsive
- Improve the capture speed of government ID auto capture and manual capture

## [v2.2.9] - 2022-03-07

### Added

- Show a (hide-able) cancel "X" on every non-loading screen to match iOS and web
- Added support for upload option with government id verification

### Changed

- Buttons on government id review screen will flow vertically when text is more than one line
- Update the cancel sheet's copy

### Fixed

- Fix compatibility issues with Lottie 5.0+
- Fix layout on government id select screen when no back button is shown
- Fix back button on government id review screen

## [v2.2.8] - 2022-02-24

### Added

- Added support for custom government id scanning lottie animation
- Added support for custom selfie look left and look right drawable

## [v2.2.7] - 2022-02-22

### Added

- Added support for custom government id overlays and hint animations

### Fixed

- Allow "center-only" selfie experiences to pass
- Fixed crash in government id

## [v2.2.6] - 2022-02-16

### Added

- Various theme attributes have been added

### Changed

- Default alignment of ui step screens
- Country select now presents a bottom sheet instead of a dropdown

## [v2.2.5] - 2022-02-11

### Added

- Auto-capture for center pose selfies
- Support for additional government IDs
  - Citizenship Certificate
  - Consular ID
  - Foreigner ID
  - Health Insurance Card
  - Long Term Pass
  - National Bureau of Investigation Certificate
  - Permanant Account Number card (SSN)

### Changed

- Autofocus first input field on page load
- Only allow digits (0-9) in day/month input fields

## [v2.2.4] - 2022-02-04

### Added

- Added support for custom Selfie animation on selfie start view with
  - Lottie file `personaInquirySelfieLottieRaw`
  - Size between 0.0 and 1.0 for `personaInquirySelfieLottieWidthPercent`
- Added support for additional ID types

### Removed

- The following string resources have been removed, their values are now supplied by the server:
  - `persona_selfie_persona_governmentid_submitting_title`
  - `persona_selfie_persona_governmentid_submitting_body`
  - `selfie_hint_center`
  - `selfie_hint_look_left`
  - `selfie_hint_look_right`
  - `governmentid_idlabel_dl`
  - `governmentid_idlabel_id`
  - `governmentid_idlabel_keyp`
  - `governmentid_idlabel_mid`
  - `governmentid_idlabel_myn`
  - `governmentid_idlabel_nric`
  - `governmentid_idlabel_ofw`
  - `governmentid_idlabel_pp`
  - `governmentid_idlabel_ppc`
  - `governmentid_idlabel_pr`
  - `governmentid_idlabel_rp`
  - `governmentid_idlabel_sp`
  - `governmentid_idlabel_sss`
  - `governmentid_idlabel_umid`
  - `governmentid_idlabel_pid`
  - `governmentid_idlabel_vid`
  - `governmentid_idlabel_visa`
  - `governmentid_idlabel_wp`

## [v2.2.3] - 2022-02-03

### Fixed

- Use styles that are night-mode friendly for chevrons and arrows

## [v2.2.2] - 2022-02-01

### Added

- Support SVGs from the server

### Fixed

- Enable haptic feedback on older versions of Android
- Address resource contention that stopped the camera after many usages

## [v2.2.1] - 2022-01-28

### Added

- Show the countdown on the overlay

### Changed

- Change selfie capture to be more strict, surface errors to users
- Depend on Kotlin 1.5.31
- Update resources to prevent name collisions with the v1.x SDK

## [v2.2.0] - 2022-01-25

### Breaking

- `com.withpersona.sdk` has been changed to `com.withpersona.sdk2` everywhere

## [v2.1.3] - 2022-01-24

### Added

- Support for server driven localizations in selfie templates

### Changed

- Cancel modal now uses `textAppearanceHeadline6` and `textAppearanceSubtitle1`

### Removed

- The following string resources have been removed:
  - `persona_selfie_start_title`
  - `persona_selfie_start_body`
  - `persona_selfie_start_button`

## [v2.1.2] - 2022-01-18

### Added

- Support for more server driven localizations on government ID templates
- Support more components for form templates
- Added address auto complete on address fields
- Improve auto capture to take better pictures

### Changed

- Update dependencies
- Various bug fixes

## [v2.1.1] - 2021-12-13

### Added

- Allow multiple documents to be added on the same step
- Support for server driven localizations in government ID templates

### Changed

- Update dependencies

### Removed

- The following string resources have been removed:
  - `persona_governmentid_start_title`
  - `persona_governmentid_start_body`
  - `persona_governmentid_failed_title`
  - `persona_governmentid_submitting_title`
  - `persona_governmentid_submitting_body`

## [v2.1.0] - 2021-11-18

### Added

- Support completing an Inquiry flow without showing a completion screen

### Changed

- Redesign Government ID capture screens
- Secondary buttons are now outlined
- Update dependencies

### Fixed

- Remove Snackbar usage in Sandbox which older versions of AGP strips out
- Use the Material UI background for `materialButtonStyle` and `materialButtonStyleSecondary`

## [v2.0.3] - 2021-10-20

### Fixed

- Return an error when the SDK is launched without internet
- Return session when canceling from document upload step

## [v2.0.2] - 2021-10-13

### Added

- Support document upload step
- Forward along server errors on the Inquiry creation step
- Return error if using an incompatible template ID

### Fixed

- Starting an Inquiry by Inquiry Template Version has been fixed
- Removed loading indicator blip after selfie and document verifications
- Re-add Field population on client-side Inquiry creation

### Changed

- Update dependencies

## [v2.0.1] - 2021-08-26

### Added

- Support the Keypass ID and Visa government ID types
- Show a cancel confirmation pop-up

### Fixed

- `InquiryField.Unknown` return the name of the unknown type instead of just "unknown"

### Changed

- Footer now has a thin line on top of it

## [v2.0.0] - 2021-08-05

### Added

- Support AndroidX's `registerForActivityResult` for interacting with the Inquiry
- `Cancel` response now returns the `sessionToken` so the Inquiry flow can be resumed

### Changed

- `Success` and `Failure` callbacks are now represented by `Complete` with a status of `completed`
  or `failed` (though can be customizable in the future)
- Support Inquiry templates prefixed with `itmpl_` instead of `tmpl_`
- `Attributes` returned in the `Success` response are now in the `Complete`'s `fields` response

### Deprecated

- Recommend moving off `Inquiry#onActivityResult` and onto AndroidX's `registerForActivityResult`

### Removed

- `Relationships` and the containing list of `Verification` no longer exists
