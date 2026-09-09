# AppsVantage Preflight 🚀
> **Apple App Store Pre-Flight Guideline & Compliance Auditor, Privacy Manifest Generator, and Model Context Protocol (MCP) AI Agent Server.**

Audit iOS applications, Xcode projects, and compiled `.ipa` archives against Apple App Store Review Guidelines *before* submitting to TestFlight or App Store Review.

[![npm version](https://img.shields.io/npm/v/appsvantage-preflight.svg)](https://www.npmjs.com/package/appsvantage-preflight)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

---

## ⚡ Quick Start

Run an audit instantly with zero installation:

```bash
# Audit an iOS project folder (reads Info.plist, Podfile.lock, Package.resolved)
npx appsvantage-preflight ./ios

# Audit a compiled .ipa archive
npx appsvantage-preflight ./build/MyApp.ipa

# Strict CI/CD build gate (fails with exit code 1 if critical blockers detected)
npx appsvantage-preflight ./ios --fail-on-critical
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
      "args": ["appsvantage-preflight", "mcp"]
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
  --json                  Output audit report as raw JSON (for CI/CD pipelines).
  --fail-on-critical      Exit with code 1 if critical submission blockers are detected.
  --generate-xcprivacy    Generate a valid Apple PrivacyInfo.xcprivacy file.
  --decode-rejection      Decode Apple Review rejection text and generate appeal letter.
  -v, --version           Print tool version.
  -h, --help              Show help screen.
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
Visit [AppsVantage Web Portal](https://appsvantage.com).

---

## 📄 License

MIT © [AppsVantage](https://appsvantage.com)
