# TrueFace Web Liveness SDK

Standalone native JavaScript/HTML5 SDK for integrating secure biometric liveness check in web applications.

## Integration

Include the CSS and script files directly in your HTML header:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/trueface-dev/web-artifact@v0.1.0/trueface-web-sdk.css">
<script src="https://cdn.jsdelivr.net/gh/trueface-dev/web-artifact@v0.1.0/trueface-web-sdk.js"></script>
```

## Usage

Mount the camera preview element and execute the liveness check sequence programmatically:

```html
<div id="livenessContainer"></div>

<script>
  async function runVerification() {
    const container = document.getElementById('livenessContainer');
    
    const tf = new TrueFaceLiveness({
      backendBaseUrl: 'https://api.trueface.dev',
      publicKey: 'pk_test_SFJdgYdzDh84SO2jKDwL6qTxQINZCOi6',
      verificationId: 'ca93f062-7c46-43b1-be08-5136fc02e83b',
      clientSecret: 'vs_4f4PZPic2lkqlY8UEgFcQHLdrMdaY3VM'
    });

    try {
      const result = await tf.start(container);
      console.log('Verification status:', result.status);
      console.log('Verification decision:', result.decision);
    } catch (err) {
      console.error('Liveness session failed:', err);
    }
  }
</script>
```
