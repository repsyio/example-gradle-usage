# AGENTS.md

Sample that consumes a library (`io.repsy.example:gradle-deploy:1.0`) from a Repsy Maven repository with Gradle.

Sibling samples: `example-gradle-deploy`, `example-gradle-usage`, `example-maven-deploy`, `example-maven-usage`
(the `*-usage` samples consume what the matching `*-deploy` sample publishes, group `io.repsy.example`, version 1.0).
They back articles on https://docs.repsy.io; they are not Repsy product code, so the Repsy Jira and PR rules do not apply.

## Layout
- `build.gradle`: adds the Repsy repository (`repsyUrl`, `repsyUsername`, `repsyPassword` properties) and the dependency `compile 'io.repsy.example:gradle-deploy:1.0'`.
- `src/main/java/io/repsy/example/gradle_usage/Main.java`: the program. `gradlew`: wrapper (Gradle 9.8.2).

## Commands
- Build: `./gradlew build`; resolving the dependency needs the Repsy properties and the deploy sample already published (credentials; do not run unasked). No tests or CI.
- Known issue: `build.gradle` still uses the removed `compile` configuration, so `./gradlew build` fails on Gradle 9.8.2 until it is changed to `implementation`.

## Conventions
- Default branch `master`. Few commits; titles are short free-form sentences, no ticket prefix; squash merges add ` (#N)`.
- `.github/dependabot.yml` exists (Dependabot only, no CI).
- Keep the sample minimal and in line with the docs article linked in `README.md`.
- Never put real credentials or a real username in the files; the Repsy URL and credentials are placeholders or properties.
