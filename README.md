# TrueFace Web Liveness SDK (Public Distribution)

This repository distributes the public binaries and release assets for the TrueFace Web Liveness SDK via the jsDelivr CDN.

## Integration

Include the CSS stylesheet and script file directly in your HTML document:

```html
<!-- Include TrueFace Liveness CSS -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/trueface-dev/web-artifact@v1.0.0/trueface-web-sdk.css">

<!-- Include TrueFace Liveness JS -->
<script src="https://cdn.jsdelivr.net/gh/trueface-dev/web-artifact@v1.0.0/trueface-web-sdk.js"></script>
```

> [!NOTE]
> Replace `@v1.0.0` with the specific version tag you are targeting, or omit it to target the latest release (e.g. `web-artifact@latest/...` - though version pinning is recommended for production environments).

## Usage

Create a container element in your HTML page to mount the camera preview:

```html
<div id="livenessContainer" style="width: 100%; max-width: 500px; height: 600px;"></div>
```

Run the liveness check sequence programmatically in JavaScript:

```html
<script>
  async function runVerification() {
    const container = document.getElementById('livenessContainer');
    
    // Initialize the SDK configuration
    const tf = new TrueFaceLiveness({
      backendBaseUrl: 'https://api.trueface.dev',
      publicKey: 'pk_test_YOUR_PUBLISHABLE_KEY',
      verificationId: 'ca93f062-7c46-43b1-be08-5136fc02e83b',
      clientSecret: 'vs_THE_SESSION_CLIENT_SECRET'
    });

    try {
      // Start the biometric check sequence
      const result = await tf.start(container);
      
      console.log('Verification status:', result.status);     // e.g. "approved", "rejected"
      console.log('Verification decision:', result.decision); // e.g. "approved", "rejected", null
    } catch (err) {
      console.error('Liveness check session failed:', err);
    }
  }
</script>
```
