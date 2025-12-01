# GetCookies CMP - Google Tag Manager Template

A Google Tag Manager template for [GetCookies](https://getcookies.co), a Consent Management Platform (CMP) that helps make your use of cookies and online tracking compliant with GDPR, CCPA, and other privacy regulations.

## Features

- **Full Google Consent Mode v2 Support** - Sets default consent state before any tags fire
- **Real-time Consent Updates** - Instantly updates consent when users interact with the cookie banner
- **All Consent Types Supported**:
  - `ad_storage` - Advertising cookies
  - `ad_user_data` - User data for advertising
  - `ad_personalization` - Personalized advertising
  - `analytics_storage` - Analytics cookies
  - `functionality_storage` - Functionality cookies
  - `personalization_storage` - Personalization cookies
- **Consent Persistence** - Automatically restores consent from localStorage on return visits
- **URL Passthrough** - Preserves ad click information when cookies are denied
- **Ads Data Redaction** - Option to redact ad identifiers when consent is denied
- **Configurable Defaults** - Set default consent state per category

## Installation

### Step 1: Add the Template to GTM

1. In Google Tag Manager, go to **Templates** → **Tag Templates**
2. Click **New** and then click the three-dot menu → **Import**
3. Download the template from: `https://api.getcookies.co/api/v1/gtm-template/download`
4. Import the downloaded JSON file
5. Click **Save**

### Step 2: Create a GetCookies Tag

1. Go to **Tags** → **New**
2. Click **Tag Configuration** and select **GetCookies CMP**
3. Enter your **Domain ID** (find this in your [GetCookies dashboard](https://getcookies.co) under Domains → Widget Configuration)
4. Keep **Enable Google Consent Mode v2** checked (recommended)
5. Click **Triggering** and add **Consent Initialization - All Pages**
6. Save the tag

### Step 3: Configure Your Tracking Tags

For each tracking tag (Google Analytics, Google Ads, Meta Pixel, etc.):

1. Open the tag
2. Click **Advanced Settings** → **Consent Settings**
3. Select **Require additional consent for tag to fire**
4. Add the appropriate consent types:
   - Google Analytics: `analytics_storage`
   - Google Ads: `ad_storage`, `ad_user_data`, `ad_personalization`
   - Meta Pixel: `ad_storage`, `ad_user_data`, `ad_personalization`
5. Save the tag

### Step 4: Publish

Click **Submit** in the top right to publish your changes.

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| Domain ID | Your GetCookies domain identifier (required) | - |
| Enable Google Consent Mode v2 | Integrate with Google's consent API | `true` |
| Wait for update | Milliseconds to wait for consent before firing tags | `500` |
| Redact ads data | Redact ad identifiers when consent denied | `dynamic` |
| URL passthrough | Pass ad click info via URL when cookies denied | `true` |
| Default consent states | Initial consent state per category | All `denied` |

## How It Works

1. **On Page Load**: The template immediately sets all consent types to their default state (denied) before any other tags can fire
2. **Check for Existing Consent**: If the user has previously given consent, it's restored from localStorage
3. **Display Banner**: The GetCookies widget loads and displays the cookie consent banner
4. **User Interaction**: When the user accepts or customizes their consent, the template updates Google's consent state in real-time
5. **Tags Fire Accordingly**: Tags with consent requirements only fire if the appropriate consent has been granted

## Support

- **Documentation**: [https://getcookies.co/help/gtm-installation](https://getcookies.co/help/gtm-installation)
- **Support**: [https://getcookies.co/support](https://getcookies.co/support)
- **Issues**: Please report issues in this repository's [Issues](../../issues) section

## License

Licensed under the Apache License, Version 2.0. See [LICENSE](LICENSE) for details.

Copyright 2024 GetCookies
