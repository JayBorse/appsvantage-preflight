---
name: appsvantage-preflight
description: Apple App Store pre-flight guideline auditor, May 2024 Privacy Manifest generator, and rejection decoder for iOS developers.
license: MIT
metadata:
  author: AppsVantage
---

# AppsVantage Preflight Skill

Autonomous Apple App Store guideline compliance auditor, Privacy Manifest generator, and rejection decoder.

## When to activate
- When auditing an iOS app, Xcode project, or .ipa archive before submitting to App Store Review or TestFlight.
- When generating an official, valid Apple \`PrivacyInfo.xcprivacy\` file.
- When diagnosing Apple App Review rejections and drafting Resolution Center appeal letters.

## Commands & Capabilities
1. **Audit Project**:
   \`\`\`bash
   npx -y appsvantage-preflight ./ios --fail-on-critical
   \`\`\`
2. **Generate Privacy Manifest**:
   \`\`\`bash
   npx -y appsvantage-preflight --generate-xcprivacy
   \`\`\`
3. **Decode Rejection**:
   \`\`\`bash
   npx -y appsvantage-preflight --decode-rejection "<raw rejection text>"
   \`\`\`
