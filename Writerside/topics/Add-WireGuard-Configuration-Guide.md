# Add WireGuard Configuration

To add a new WireGuard Configuration, simply click the big "+" button on the top right of the Home page

![add-configuration-button.png](../images/user-guides/add-configuration-button.png)

Then you will see a form, with the following fields need to input. Specifications came from [Some Unofficial WireGuard Documentation](https://github.com/pirate/wireguard-docs)

- **Name**
  - This will be the name of your WireGuard Configuration, the rules are following:
    1. Can't use existing WireGuard configuration's name
    2. Must match the regex `^[a-zA-Z0-9_=+.-]{1,15}$`
- **Private Key & Public Key**
  - Both keys are pre-generated. If you wish to use your own key pair, simply **paste** your Private Key into the input, and it will generate the Public Key automatically.
  - To re-generate a key pair, simply click the blue refresh button on the right of Private Key input.
