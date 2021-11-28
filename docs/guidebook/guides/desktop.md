---
title: "Swipechain Desktop Wallet v2.x.x"
---

# Desktop Wallet

<!-- ![Swipechain Desktop](./assets/desktop/banner.png) -->

[![Build Status](https://badgen.now.sh/circleci/github/SwipeChain/swipechain-desktop-wallet)](https://circleci.com/gh/SwipeChain/swipechain-desktop-wallet)
[![Latest Version](https://badgen.now.sh/github/release/SwipeChain/desktop-wallet)](https://github.com/SwipeChain/desktop-wallet/releases)
[![License: MIT](https://badgen.now.sh/badge/license/MIT/green)](https://opensource.org/licenses/MIT)

## Download

[Latest Release](https://github.com/SwipeChain/swipechain-desktop/releases)

## Installing via Package Managers

### Arch Linux

Install via [AUR](https://aur.archlinux.org/packages/swipechain-desktop):

> Manjaro

```shell
pamac build swipechain-desktop
```

### Mac OS X

Install via [Homebrew](https://brew.sh/):

```shell
brew cask install swipechain-desktop-wallet
```

## Translations

Translations are part of our [Swipechain Development and Security Bounty Program](https://blog.swipechain.org/swipechain-development-and-security-bounty-program-a95122d06879).

Full translations are considered to be `Tier 3`, while grammar fixes, typos, etc. are considered to be `Tier 6`.

<details>
<summary>
  <h4>Full translations should involve 5 tasks</h4>
</summary>

- Create a pull request for the language you are going to translate. If you have doubts about something, use English to explain them.
- Translate the textual content of the application, using the [English language file](https://github.com/SwipeChain/desktop-wallet/blob/develop/src/renderer/i18n/locales/en-US.js) as the reference. To do that, a new file, with the language locale code should be created. The name of the file should be a valid [RFC 5646](https://tools.ietf.org/html/rfc5646) and should be located at `src/renderer/i18n/locales/LANGUAGE.js`. Thanks to [vue-i18n-extract](https://github.com/pixari/vue-i18n-extract), it is possible to execute `yarn i18n src/renderer/i18n/locales/LANGUAGE.js` to find suggestions of missing translations.
- Add the language to the [English language file](https://github.com/SwipeChain/desktop-wallet/blob/develop/src/renderer/i18n/locales/en-US.js) at the `LANGUAGES` key.
- Update the [date and time formats file](https://github.com/SwipeChain/desktop-wallet/blob/develop/src/renderer/i18n/date-time-formats.js) to include the short and long format that are used commonly by native speakers.
- Update the [number formats file](https://github.com/SwipeChain/desktop-wallet/blob/develop/src/renderer/i18n/number-formats.js) to include the preferred way of displaying currencies used commonly by native speakers.
- Add the language at the `I18N.enabledLocales` array at the [main configuration file](https://github.com/SwipeChain/desktop-wallet/blob/develop/config/index.js). This step is necessary to make the language would not be available.
- Execute the application. Go to the [ development section](https://github.com/SwipeChain/desktop-wallet#development) to learn how to install the requirements and execute it.

</details>

## Development

### Requirements

#### Ubuntu

In Ubuntu the development files of `libudev` are necessary:

```
sudo apt-get install libudev-dev libusb-1.0-0-dev
```

#### Windows

- Python 2.7
- Visual Studio 2017

#### Node 12

To download, head over to [here](https://nodejs.org/en/) and download Node 12.

If you already have npm installed, you can run

```
npm install -g n
sudo n 12
```

#### Yarn

Install the Yarn dependency manager

```
npm install -g yarn
```

### Commands

<details>
<summary>
  <h4>List of commands</h4>
</summary>

```bash
# Install Dependencies
yarn install

# Execute the application. Making changes in the code, updates the application (hot reloading).
yarn dev

# Lint all JS/Vue files in `src` and `__tests__`
yarn lint

# Lint, and fix, all JS/Vue files in `src` and `__tests__`
yarn lint:fix

# Check That All Dependencies Are Used
yarn depcheck

# Collect the Code and Produce a Compressed File
yarn pack

# Build Electron Application for Production (Current OS)
yarn build

# Build Electron Application for Production (Windows)
yarn build:win

# Build Electron Application for Production (Mac)
yarn build:mac

# Build Electron Application for Production (Linux)
yarn build:linux

# Run Unit and End-to-End Tests
yarn test

# Run Unit Tests
yarn test:unit

# Run Unit Tests and Generate and Display the Coverage Report
yarn test:unit:coverage

# Run Unit Tests and Watch for Changes to Re-Run the Tests
yarn test:unit:watch

# Run end-to-end tests, without building the application
yarn test:e2e

# Build the Application and Run End-to-End Tests
yarn test:e2e:full

# List What Translations Are Missing or Unused on a Specific Language. It Could Capture Suggestions That Are Not Accurate
yarn i18n 'src/renderer/i18n/locales/LANGUAGE.js'

# List What English Messages Are Missing or Unused (English Is the Default Language)
yarn i18n:en-US

# List What Translations Are Missing or Unused on Every Language
yarn i18n:all
```

</details>

## Plugins

You can find a plugin template [here](https://github.com/swipechain-ecosystem-desktop-plugins/template) which will help get you started.

### File Structure

All plugins require at least the following files in order to work: 

- package.json
- src/index.js

### Installation

Plugins are to be installed inside of the `~/.swipechain-desktop/plugins` folder.

**Note: If running in development mode, the path used is `~/.swipechain-desktop/plugins-dev`.**

### Permissions

You also have the option of using the following permissions:

<details>
<summary>
  <h4>Accessibility permissions</h4>
</summary>

#### COMPONENTS
Load in custom components.

To be used in combination with other permissions:

- ROUTES
- MENU_ITEMS
- AVATARS
- WALLET_TABS

#### ROUTES

Loads additional routes into the Desktop Wallet.

To be used in combination with other permissions:

- COMPONENTS
- MENU_ITEMS

#### MENU_ITEMS

Loads custom menu items into the Desktop Wallet for the sidebar.

To be used in combination with other permissions:

- ROUTES (required)
- COMPONENTS

#### AVATARS

Plugin contains custom components.

Can be used in combination with the COMPONENTS permission.

#### PUBLIC

Allow access to Font Awesome components.

#### THEMES

Allow additional custom themes for the Desktop Wallet.

#### WALLET_TABS

Allow showing an additional tab/page on the Wallet screen.

Can be used in combination with the COMPONENTS permission.

#### UI_COMPONENTS

Allow access to the standard Desktop Wallet components used throughout the wallet. This gives plugins the ability to look and feel like they are a part of the application.

Allows access to all of the Button components:

- ButtonClipboard
- ButtonClose
- ButtonGeneric
- ButtonLayout
- ButtonLetter
- ButtonModal
- ButtonReload
- ButtonSwitch

Allows access to all of the Collapse components:

- Collapse
- CollapseAccordion

Allows access to all of the Input components:

- InputAddress
- InputCurrency
- InputDelegate
- InputFee
- InputField
- InputLanguage
- InputPassword
- InputSelect
- InputSwitch
- InputText

Allows access to all of the ListDivided components:

- ListDivided
- ListDividedItem

Allows access to the Loader component:

- Loader

Allows access to all of the Menu components:

- MenuDropdown
- MenuDropdownAlternativeHandler
- MenuDropdownHandler
- MenuDropdownItem
- MenuNavigation
- MenuNavigationItem
- MenuOptions
- MenuOptionsItem
- MenuStep
- MenuStepItem
- MenuTab
- MenuTabItem

Allows access to the TableWrapper component:

- TableWrapper

#### WEBFRAME

Allow showing remote URL pages within a frame. For example, showing the explorer within a page on the Desktop Wallet:

- WebFrame

</details>

<details>
<summary>
  <h4>Wallet API permissions</h4>
</summary>

#### ALERTS

Allow access to the Desktop Wallet alerts. For example, they could be used for notifications.

**`walletApi.alert.error(...)`**

Trigger an error notification alert.

**`walletApi.alert.success(...)`**

Trigger a success notification alert.

**`walletApi.alert.info(...)`**

Trigger an info notification alert.

**`walletApi.alert.warn(...)`**

Trigger a warn notification alert.

#### AUDIO

Allow access to play audio from within the Desktop Wallet. For example, they could be used as an announcement for a new transaction.

**`AudioContext`**

#### EVENTS

Allow access to the Desktop Wallet events. For example, an event is triggered every time a new transaction is received.

**`walletApi.eventBus.on(event, callback)`**

Used to listen for an event.

**`walletApi.eventBus.off(event, callback)`**

Used to disable listening for an event.

#### HTTP

Allow performing external web requests. E.g. accessing the API of a third-party provider. 

**Note: This relies on a whitelist being provided within the `package.json` file**

**`walletApi.http.get(url, opts)`**

Perform a GET request.

**`walletApi.http.post(url, opts)`**

Perform a POST request.

#### MESSAGING

Allow WebFrame to have access to a one-way messaging system. E.g. trigger a plugin change when a button is pressed on an external page inside the WebFrame component.

Run `sendToHost(event, data)` from within a WebFrame to trigger a messaging event.

**`walletApi.messages.on(action, eventCallback)`**

Listen for a message from within the WebFrame.

**`walletApi.messages.clear()`**

Clear all messaging events.

#### PEER_CURRENT

Allows access to the currently connected peer. E.g. to fetch additional data from the network.

**`walletApi.peers.current.get(url, timeout = 3000)`**

Perform a GET request on the network.

**`walletApi.peers.current.post(url, timeout = 3000)`**

Perform a POST request on the network.

#### PROFILE_ALL

Get all available profiles. E.g. to provide a list of wallets for the user to choose from which could be network independent.

**`walletApi.profiles.all`**

#### PROFILE_CURRENT

Get the currently active profile. E.g. to provide a list of wallets for the user to choose from.

**`walletApi.profiles.getCurrent()`**

#### PUBLIC

Allow access to the current route, including being able to navigate.

**`walletApi.route.get()`**

Get the current route.

**`walletApi.route.goTo()`**

Navigate to a new route.

#### STORAGE

Allow storing data within the Desktop Wallet, using a key-value pair.

**`walletApi.storage.get(key, global = false)`**

Get a single value from the store based on key. If `global` is `true`, it will fetch the data stored globally in the wallet.

**`walletApi.storage.set(key, value, global = false)`**

Set a value in the store. If `global` is `true`, it will globally store the data in the wallet.

**`walletApi.storage.getOptions()`**

Get all values from the store for the plugin.

#### TIMERS

Allows initiating and dealing with timers from inside a plugin.

**`walletApi.timers.setInterval(method, interval, ...args)`**

Start interval timer to run every `interval` milliseconds.

**`walletApi.timers.setTimeout(method, interval, ...args)`**

Start timeout timer to run once after `interval` milliseconds.

**`walletApi.timers.clearInterval(id)`**

Clear interval timer created using `setInterval`.

**`walletApi.timers.clearTimeout(id)`**

Clear timeout timer created using `setTimeout`.

**`walletApi.timers.intervals`**

Get a list of intervals which are active.

**`walletApi.timers.timeouts`**

Get a list of timeouts which are active.

#### WEBSOCKET

Allows initiating and dealing with websockets from inside a plugin.

**`walletApi.websocket.clear()`**

Clear existing websockets.

**`walletApi.websocket.on(action, eventCallback)`**

Create new websocket event.

**`walletApi.websocket.close()`**

Close an open websocket.

**`walletApi.websocket.destroy()`**

Close an open websocket and clear all active events.

**`walletApi.websocket.send(data)`**

Send data across the websocket.

**`walletApi.websocket.isConnecting()`**

Get whether the websocket is currently connecting.

**`walletApi.websocket.isDestroyed()`**

Get whether the websocket is uninitiated or destroyed.

**`walletApi.websocket.isOpen()`**

Get whether the websocket is open.

**`walletApi.websocket.isClosing()`**

Get whether the websocket is in the process of closing.

**`walletApi.websocket.isClosed()`**

Get whether the websocket is closed.

**`walletApi.websocket.binaryType`**

Get or set the binary type for the websocket.

</details>

## Security

If you discover a security vulnerability within this project, please send an e-mail to security@swipechain.org. All security vulnerabilities will be promptly addressed.

## Credits

- [Alex Barnsley](https://github.com/alexbarnsley)
- [Michel Kraaijeveld](https://github.com/ItsANameToo)
- [Lúcio Rubens](https://github.com/luciorubeens)

## License

[MIT](LICENSE) © [Swipechain](https://swipechain.org)
