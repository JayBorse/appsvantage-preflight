# AppsVantage Preflight 🚀
> **Apple App Store Pre-Flight Guideline & Compliance Auditor, Privacy Manifest Generator, and Model Context Protocol (MCP) AI Agent Server.**

Audit iOS applications, Xcode projects, and compiled `.ipa` archives against Apple App Store Review Guidelines *before* submitting to TestFlight or App Store Review.

[![npm version](https://img.shields.io/npm/v/appsvantage-preflight.svg)](https://www.npmjs.com/package/appsvantage-preflight)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

---

## ⚡ Quick Start

Run a full audit instantly with zero installation (your first audit is 100% free!):

```bash
# Audit an iOS project folder (reads Info.plist, Podfile.lock, Package.resolved)
npx appsvantage-preflight ./ios

# Audit a compiled .ipa archive
npx appsvantage-preflight ./build/MyApp.ipa

# Strict CI/CD build gate (fails with exit code 1 if critical blockers detected)
npx appsvantage-preflight ./ios --fail-on-critical
```

---

## 🎟️ Pricing & License Activation

AppsVantage Preflight is designed for indie developers and production engineering teams:

| Tier | Price | What's Included |
|---|---|---|
| **Free Trial** | **$0** | 1 comprehensive pre-flight scan of any iOS project or .ipa |
| **App Launch Pass** | **$19.99** (one-time) | 90 days of unlimited audits for 1 app, CI/CD gating, privacy manifests |
| **Agency Monthly** | **$49.99/mo** | Unlimited audits across up to 10 apps, team sharing, priority support |

### Activating Your License
Once purchased at [https://www.appsvantage.com/preflight](https://www.appsvantage.com/preflight), pass your key via CLI or environment variable:

```bash
# Pass via CLI flag
npx appsvantage-preflight ./ios --key YOUR_LICENSE_KEY

# Or export as environment variable
export APPSVANTAGE_LICENSE_KEY=YOUR_LICENSE_KEY
npx appsvantage-preflight ./ios
```

---

## 🤖 Model Context Protocol (MCP) Agent Server

Integrate preflight auditing directly into **Cursor**, **Windsurf**, or **Claude Code**:

### Add to Cursor (`~/.cursor/mcp.json`) or Claude Desktop:
```json
{
  "mcpServers": {
    "appsvantage": {
      "command": "npx",
      "args": ["appsvantage-preflight", "mcp"],
      "env": {
        "APPSVANTAGE_LICENSE_KEY": "YOUR_LICENSE_KEY"
      }
    }
  }
}
```

### Autonomous AI Agent Capabilities:
- `appsvantage_audit`: Deep compliance audit of local Xcode projects or `.ipa` packages.
- `appsvantage_generate_privacy_manifest`: Writes a valid Apple `PrivacyInfo.xcprivacy` XML manifest.
- `appsvantage_decode_rejection`: Diagnoses rejection text, produces a Resolution Center appeal letter, and provides an AI fix prompt.

---

## 🛠️ CLI Commands & Options

```bash
USAGE:
  appsvantage-preflight [target-path] [options]
  appsvantage-preflight mcp

COMMANDS:
  mcp                     Launch Model Context Protocol (MCP) server over stdio.

ARGUMENTS:
  target-path             Path to an .ipa file, Info.plist, or Xcode project directory.
                          Defaults to current directory (.) if omitted.

OPTIONS:
  -k, --key <key>         AppsVantage license key or account email.
  --json                  Output audit report as raw JSON (for CI/CD pipelines).
  --fail-on-critical      Exit with code 1 if critical submission blockers are detected.
  --generate-xcprivacy    Generate a valid Apple PrivacyInfo.xcprivacy file.
  --decode-rejection      Decode Apple Review rejection text and generate appeal letter.
  -v, --version           Print tool version.
  -h, --help              Show help screen.

ENVIRONMENT VARIABLES:
  APPSVANTAGE_LICENSE_KEY AppsVantage license key or account email.
```

---

## 🔍 What AppsVantage Preflight Checks

1. **Apple May 2024 Privacy Manifest Mandate**:
   - Audits third-party SDKs against Apple's mandatory SDK list.
   - Verifies framework-level `PrivacyInfo.xcprivacy` and Required Reason API declarations.
   - Cross-checks tracking SDKs against declared `NSPrivacyTracking`.
2. **Provisioning Profiles & Entitlements**:
   - Flags development builds (`get-task-allow: true`) or Ad-Hoc profiles that cause App Store rejection.
   - Verifies In-App Purchase, Push Notification, and Sign in with Apple capabilities.
3. **App Transport Security (ATS)**:
   - Identifies insecure HTTP exceptions and legacy `UIWebView` usage.
4. **Purpose Strings & Permissions**:
   - Verifies usage descriptions (`NSCameraUsageDescription`, `NSLocationWhenInUseUsageDescription`, etc.).
5. **Leak & Secret Scanner**:
   - Flags local development endpoints (`localhost`, `127.0.0.1`, `.local`) in production configs.

---

## 🌐 Web Platform & Deep Analytics

Need competitor intelligence, paywall benchmarks, or certified PDF audit reports?
Visit [https://www.appsvantage.com](https://www.appsvantage.com).

---

## 📄 License

MIT © [AppsVantage](https://www.appsvantage.com)
