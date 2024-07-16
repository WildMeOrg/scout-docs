# Code Contribition Guideline

## Best Practices
* DRY Principle: Do Not Repeat Yourself. Avoid code duplication by reusing components, functions, and styles. This not only minimizes the codebase but also simplifies maintenance and updates.
* If you are adding code that will be custom to a single platform, the feature needs to be approved by the Wild Me team. If approved, add all custom code in a block at the bottom of the page to prevent merge conflicts.

## Dependencies
We use dependabot for dependency management; however, due to inconsistencies in semantic versioning and behavioral changes in packages supporting machine learning, we do system testing for all PRs suggested by dependabot. If you want to update or add a new dependency, contact the Wild Me team to discuss the changes before submitting a PR. 

## In-line styling
Generally speaking, we want to avoid in-line styling to allow for greater consistency and understandability. If you have concerns with what theme styling to use, check the theme figma.

## Internationalization
All Wild Me tools are intended for an international audience, so we want to provide translated versions. An active goal for 2024 is to get ensure that all product copy has been internationalized according to the following standard.

At present, in Wildbook, all copy except for site name, notification messages, and species names are wrapped and localized to 4 languages: english, french, spanish, and italian.

## EXIF data handling
EXIF data is notoriously inconsistent between different cameras. Unless we want to provide an entire suite of EXIF management tools (we do not), we must make assumptions about the data coming in, prepare for those assumptions to be wrong, and fail gracefully. Any development focused on EXIF data management should catch exceptions for the following cases:
* data is missing
* data is in the wrong format
* data is data is of the wrong type
* any additional cases defined in the ticket
