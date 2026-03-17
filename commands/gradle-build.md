---
name: gradle-build
description: Fix Gradle build errors in Android and Kotlin Multiplatform projects.
user_invocable: true
---

# Gradle Build Fix

Fix Gradle build errors in Android and Kotlin Multiplatform (KMP) projects.

## Build Configuration Detection

| Project Type | Build Command |
|--------------|---------------|
| KMP | `./gradlew composeApp:compileKotlinMetadata` |
| Android | `./gradlew app:compileDebugKotlin` |

## Fix Process

1. **Parse and Group Errors**
   - Separate Kotlin compilation errors from Gradle configuration errors
   - Group by module

2. **Fix Loop**
   - Read file with error
   - Diagnose common issues
   - Apply minimal fix
   - Verify with rebuild

3. **Guardrails**
   - Stop if fix introduces more errors
   - Stop if same error persists after 3 attempts
   - Stop if requires major structural changes

## Common Fixes

| Issue | Fix |
|-------|-----|
| Unresolved reference in commonMain | Check dependencies in `commonMain.dependencies {}` |
| Expect/actual mismatch | Add `actual` implementation per platform |
| Compose compiler version mismatch | Align with Kotlin version in `libs.versions.toml` |
| Duplicate class | Check conflicting dependencies with `./gradlew dependencies` |

## Summary Report

Report fixed errors, remaining errors, and next steps.
