<img src="https://cdn.jsdelivr.net/npm/@finsweet/cookie-consent@1/logo.svg" alt="Fs Cookie Consent" width="100%" />

<div align="center">
  <a href="https://www.npmjs.com/package/@finsweet/cookie-consent">
    <img src="https://badgen.net/npm/v/@finsweet/cookie-consent" alt="Version" />
  </a>
  <a href="https://www.npmjs.com/package/@finsweet/cookie-consent">
    <img src="https://badgen.net/badge/icon/typescript?icon=typescript&label" alt="Typescript" />
  </a>
  <a href="https://npmjs.org/package/@finsweet/cookie-consent">
    <img src="https://badgen.net/jsdelivr/hits/npm/@finsweet/cookie-consent" alt="JsDelivr Downloads" />
  </a>
  <a href="https://npmjs.org/package/@finsweet/cookie-consent">
    <img src="https://badgen.net/bundlephobia/minzip/@finsweet/cookie-consent" alt="Minizipped size" />
  </a>
</div>

# Cookie Consent for Webflow

Cookie consent solution built for Webflow websites. With this tool you can fully design and customize GPDR and CCPA compliant cookie consent banners using Webflow's Designer.

Table of contents:

1. [Getting Started](#getting-started)
2. [Components](#components)
   1. [Banner [Required]](#banner)
   2. [Manager [Optional]](#manager)
   3. [Preferences [Optional]](#preferences)
3. [Scripts](#scripts)
   1. [Categories](#categories)
   2. [Example](#example)
   3. [Using Google Tag Manager](#using-google-tag-manager)
   4. [&lt;noscript> tags](#noscript-tags)
4. [IFrames](#iframes)
   1. [Placeholder](#placeholder)
   2. [Example](#example-1)
5. [How it works](#how-it-works)
6. [Using Webflow Interactions](#using-webflow-interactions)
7. [Additional Options](#additional-options)
8. [Storing Consent Records](#storing-consent-records)
9. [Consent Variations](#consent-variations)
   1. [Opt-in [Recommended]](#opt-in-consent)
   2. [Opt-out [Not-Recommended]](#opt-out-consent)
   3. [Informational [Not-Recommended]](#informational-consent)
10. [Javascript API](#javascript-api)
11. [Important Notes](#important-notes)

## Getting Started

To get started with this product, you only need to:

1. Place the [components](#components) in all your project's pages, including all Collections, 404 and Search. Using [Webflow's Symbols](https://university.webflow.com/lesson/symbols) is strongly recommended to keep consistency across all the site.

2. Make sure all the [scripts](#scripts) are correctly set up.

3. Import our Fs Cookie Consent solution code immediately after the last [script](#scripts):

```html
<script async src="https://cdn.jsdelivr.net/npm/@finsweet/cookie-consent@1/fs-cc.js"></script>
```

You can modify some functionalities of the Fs Cookie Consent tool by adding custom attributes to the script tag. Check [Additional Options](#additional-options) for more info.

## Components

The solution consists of three different components:

1. [Banner [Required]](#banner)
2. [Manager [Optional]](#manager)
3. [Preferences [Optional]](#preferences)

### Banner

The Banner is the main component and the only one required to have on the page. It will be displayed to new users who haven't yet confirmed their allowance or denial of cookies.

#### How to set it up

Place any **_Div_** or **_Section_** on the page and give it a `fs-cc="banner"` attribute. Inside it, you can place the following components:

| Component                       | Required | Allowed Elements                                               | Attribute                  | Description                                                                                                                                                                                       |
| ------------------------------- | -------- | -------------------------------------------------------------- | -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Allow All Cookies               | Yes      | Button<br />Text Link<br />Link Block<br />Div<br />Text Block | `fs-cc="allow"`            | When clicked, all the cookies will be accepted and the banner will close.                                                                                                                         |
| Deny All Cookies                | No       | Button<br />Text Link<br />Link Block<br />Div<br />Text Block | `fs-cc="deny"`             | When clicked, all the cookies except the essential ones will be denied and the banner will close.                                                                                                 |
| Close                           | No       | Button<br />Text Link<br />Link Block<br />Div<br />Text Block | `fs-cc="close"`            | When clicked, the banner will just close without storing any consent from the user. The banner will keep displaying every time the page is refreshed until the user Allows or Denies the cookies. |
| Open Preferences                | No       | Button<br />Text Link<br />Link Block<br />Div<br />Text Block | `fs-cc="open-preferences"` | When clicked, the Preferences popup will open and the Banner will close.                                                                                                                          |
| Interaction Trigger             | No       | Div (must be set to `display: none`)                           | `fs-cc="interaction"`      | If this Div is placed inside the component, the script will use Webflow's Interactions to open/close it. Read [Using Webflow Interactions](#using-webflow-interactions) for more information.     |
| [Consents Form](#consents-form) | No       | Form                                                           | `None`                     | Within this form users can granulary choose what categories of cookies do they allow or deny. Read more at [Consents Form](#consents-form).                                                       |

Optionally, the `fs-cc="banner"` component accepts the following attributes:

| Attribute                       | Required | Description                                                                                                                                                                                                                                                                            |
| ------------------------------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `fs-cc-scroll="disable"`        | No       | If this attribute is set, scrolling will be disabled on the page when the component is displayed.                                                                                                                                                                                      |
| `fs-cc-display="PROPERTY_NAME"` | No       | If this attribute is set and no [interaction](#using-webflow-interactions) is used for displaying the component, the default fade animation will set this display property.<br />Avaiable properties are: `block`, `flex`, `grid`, `inline-block`, `inline`.<br /> Defaults to `flex`. |

### Manager

The Manager is an optional component that is always displayed on the page and lets the users open the [Preferences](#preferences) component at any moment to modify their Cookies consents.

#### How to set it up

Place any **_Div_** or **_Section_** on the page and give it a `fs-cc="manager"` attribute. Inside it, you can place the following components:

| Component           | Required | Allowed Elements                                               | Attribute                  | Description                                                                                                                                                                                   |
| ------------------- | -------- | -------------------------------------------------------------- | -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Open Preferences    | Yes      | Button<br />Text Link<br />Link Block<br />Div<br />Text Block | `fs-cc="open-preferences"` | When clicked, the Preferences popup will open.                                                                                                                                                |
| Interaction Trigger | No       | Div (must be set to `display: none`)                           | `fs-cc="interaction"`      | If this Div is placed inside the component, the script will use Webflow's Interactions to open/close it. Read [Using Webflow Interactions](#using-webflow-interactions) for more information. |

Optionally, the `fs-cc="manager"` component accepts the following attributes:

| Attribute                       | Required | Description                                                                                                                                                                                                                                                                            |
| ------------------------------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `fs-cc-display="PROPERTY_NAME"` | No       | If this attribute is set and no [interaction](#using-webflow-interactions) is used for displaying the component, the default fade animation will set this display property.<br />Avaiable properties are: `block`, `flex`, `grid`, `inline-block`, `inline`.<br /> Defaults to `flex`. |

### Preferences

The Preferences is an optional component that allows the users to manually decide what categories of Cookies do they allow or deny.

#### How to set it up

Place any **_Div_** or **_Section_** on the page and give it a `fs-cc="preferences"` attribute. Inside it, you can place the following components:

| Component                       | Required | Allowed Elements                                               | Attribute             | Description                                                                                                                                                                                                 |
| ------------------------------- | -------- | -------------------------------------------------------------- | --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Allow All Cookies               | No       | Button<br />Text Link<br />Link Block<br />Div<br />Text Block | `fs-cc="allow"`       | When clicked, all the cookies will be accepted and the banner will close.                                                                                                                                   |
| Deny All Cookies                | No       | Button<br />Text Link<br />Link Block<br />Div<br />Text Block | `fs-cc="deny"`        | When clicked, all the cookies except the essential ones will be denied and the banner will close.                                                                                                           |
| Close                           | No       | Button<br />Text Link<br />Link Block<br />Div<br />Text Block | `fs-cc="close"`       | When clicked, the popup will just close without storing any consent from the user. The [banner](#banner) will keep displaying every time the page is refreshed until the user Allows or Denies the cookies. |
| Interaction Trigger             | No       | Div (must be set to `display: none`)                           | `fs-cc="interaction"` | If this Div is placed inside the component, the script will use Webflow's Interactions to open/close it. Read [Using Webflow Interactions](#using-webflow-interactions) for more information.               |
| [Consents Form](#consents-form) | No       | Form                                                           | `None`                | Within this form users can granulary choose what categories of cookies do they allow or deny. Read more at [Consents Form](#consents-form).                                                                 |

Optionally, the `fs-cc="preferences"` component accepts the following attributes:

| Attribute                       | Required | Description                                                                                                                                                                                                                                                                            |
| ------------------------------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `fs-cc-scroll="disable"`        | No       | If this attribute is set, scrolling will be disabled on the page when the component is displayed.                                                                                                                                                                                      |
| `fs-cc-display="PROPERTY_NAME"` | No       | If this attribute is set and no [interaction](#using-webflow-interactions) is used for displaying the component, the default fade animation will set this display property.<br />Avaiable properties are: `block`, `flex`, `grid`, `inline-block`, `inline`.<br /> Defaults to `flex`. |

### Consents Form

Inside the [Banner](#banner) and the [Preferences][#preferences] components you can optionally add a form where users can granulary choose what categories of cookies do they allow or deny.

#### How to set it up

Place a **_Form_** with no attributes inside the component. Inside it, place the following elements:

| Element                | Required | Allowed Elements                                                                  | Attribute                                                         | Description                                                                                  |
| ---------------------- | -------- | --------------------------------------------------------------------------------- | ----------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| Marketing Toggle       | Yes      | Checkbox                                                                          | `fs-cc-checkbox="marketing"`                                      | When checked, users will allow all Cookies from the Marketing category.                      |
| Analytics Toggle       | Yes      | Checkbox                                                                          | `fs-cc-checkbox="analytics"`                                      | When checked, users will allow all Cookies from the Analytics category.                      |
| Personalization Toggle | Yes      | Checkbox                                                                          | `fs-cc-checkbox="personalization"`                                | When checked, users will allow all Cookies from the Personalization category.                |
| Save Preferences       | Yes      | Submit Button<br />Button<br />Text Link<br />Link Block<br />Div<br />Text Block | `fs-cc="submit"` (Not required if the element is a Submit Button) | When clicked, the new preferences from the user will be stored and the component will close. |

## Scripts

To avoid any third party script that uses cookies to be loaded when the page loads, you must include the following attribute to all of them:

```html
type="fs-cc"
```

Adding this attribute will prevent the browsers from being able to parse the Javascript inside it, thus giving our Fs Cookie Consent solution the control over when the scripts will run.

Additionally, you can give the scripts the following attribute to categorize them:

```html
fs-cc-categories="CATEGORY_NAME, CATEGORY_NAME, CATEGORY_NAME"
```

Continue reading the [categories](#categories) section for more information.

### Categories

By adding a `fs-cc-categories` attribute to the script, users will be able to granulary select what cookie categories do they allow when using the [Preferences](#preferences) component.

| Name                | Attribute                            | Description                                                                                                                                                               |
| ------------------- | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **essential**       | `fs-cc-categories="essential"`       | Required to enable basic website functionality. This category cannot be denied by the user.                                                                               |
| **marketing**       | `fs-cc-categories="marketing"`       | Used to deliver advertising that is more relevant to the user and his/her interests.                                                                                      |
| **analytics**       | `fs-cc-categories="analytics"`       | These cookies help the website operator understand how its website performs, how visitors interact with the site, and whether there may be technical issues.              |
| **personalization** | `fs-cc-categories="personalization"` | These cookies allow the website to remember choices the users make (such as user name, language, or the region they are in) and provide enhanced, more personal features. |

You can set more than one category to a script by comma separating them. Example: `fs-cc-category="marketing, analytics"`

### Example

**Example:** Google Analytics:

<!-- prettier-ignore-start -->
```html
<!-- Global site tag (gtag.js) - Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX" type="fs-cc" fs-cc-categories="analytics"></script>
<script type="fs-cc" fs-cc-categories="analytics">
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'G-XXXXXXXXXX');
</script>
```
<!-- prettier-ignore-end -->

### Using Google Tag Manager

If your website uses Google Tag Manager to dynamically load third party scripts, you <ins>**must not**</ins> set the GTM script to `type="fs-cc"`. Instead, you should load it as usual.

Our Fs Cookie Consent solution pushes the following events to the `dataLayer` when the correspondent category is consented by the user:

- `essential-activated`
- `marketing-activated`
- `analytics-activated`
- `personalization-activated`
- `uncategorized-activated`

You can use these events as [Custom event triggers](https://support.google.com/tagmanager/answer/7679219?hl=en) for loading your third party scripts after the user has explicitly given his/her consent.

### &lt;noscript> tags

The `<noscript>` tags are specifically designed to run when a user has Javascript disabled on the browser. This means that our Fs Cookie Consent cannot interact with them (as it's a Javascript based solution).

To be fully compliant, **make sure to remove any `<noscript>` tags included in your third party scripts.**

**Example:** Facebook Pixel.

<!-- prettier-ignore-start -->
```html
<!-- Facebook Pixel Code -->
<script>
    !function(f,b,e,v,n,t,s)
    {if(f.fbq)return;n=f.fbq=function(){n.callMethod?
    n.callMethod.apply(n,arguments):n.queue.push(arguments)};
    if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
    n.queue=[];t=b.createElement(e);t.async=!0;
    t.src=v;s=b.getElementsByTagName(e)[0];
    s.parentNode.insertBefore(t,s)}(window, document,'script',
    'https://connect.facebook.net/en_US/fbevents.js');
    fbq('init', '{your-pixel-id-goes-here}');
    fbq('track', 'PageView');
</script>
<noscript>
    <img height="1" width="1" style="display:none"
         src="https://www.facebook.com/tr?id={your-pixel-id-goes-here}&ev=PageView&noscript=1"/>
</noscript>
<!-- End Facebook Pixel Code -->
```
<!-- prettier-ignore-end -->

As you can see, Facebook includes a `<noscript>` tag in the tracking pixel to be able to track users with disabled Javascript.

A correct implementation of the Facebook Pixel would look like this:

<!-- prettier-ignore-start -->
```html
<!-- Facebook Pixel Code. Proper attributes have been added. -->
<script type="fs-cc" fs-cc-categories="marketing">
    !function(f,b,e,v,n,t,s)
    {if(f.fbq)return;n=f.fbq=function(){n.callMethod?
    n.callMethod.apply(n,arguments):n.queue.push(arguments)};
    if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
    n.queue=[];t=b.createElement(e);t.async=!0;
    t.src=v;s=b.getElementsByTagName(e)[0];
    s.parentNode.insertBefore(t,s)}(window, document,'script',
    'https://connect.facebook.net/en_US/fbevents.js');
    fbq('init', '{your-pixel-id-goes-here}');
    fbq('track', 'PageView');
</script>
<!-- End Facebook Pixel Code. The <noscript> tag has been removed -->
```
<!-- prettier-ignore-end -->

## IFrames

Same as the scripts, `<iframe>` elements can be prevented from loading on the page until the user gives his correspondent consents.

To set them up, replace the `src` attribute of the iFrame for:

```html
fs-cc-src="SOURCE_HERE"
```

Additionally, you can categorize it like the [scripts](#categories):

```html
fs-cc-categories="CATEGORY_NAME, CATEGORY_NAME, CATEGORY_NAME"
```

### Placeholder

While the `<iframe>` is not loaded, you might want to display a placeholder element instead.

If you set the following attribute to the `<iframe>`:

```html
fs-cc-placeholder="ELEMENT_SELECTOR"
```

The matching element will be hidden once the iFrame is correctly loaded. The selector can be any valid CSS selector, like an `#id`, a `.class` or an `[attribute]`.

### Example

```html
<iframe
  fs-cc-src="https://www.finsweet.com/"
  fs-cc-placeholder="#iframe-placeholder"
  width="100%"
  height="100%"
></iframe>
```

## How it works

1. The Fs Cookie Consent script checks if the user has given consent to load the cookies. If not, the [Banner](#banner) is displayed asking for it.
2. After the user has given his/her consent, our solution loads the consented categories' scripts.
3. If the user changes his [preferences](#preferences) at any time, our script erases all the cookies from his browser (except the HttpOnly ones, see [Important Notes](#important-notes) to read more) and re-runs only the correspondent scripts.
4. The library is disabled if the visitor is a Crawling Bot to prevent indexing its content or if the visitor has DoNotTrack activated.

## Using Webflow Interactions

By default, our Fs Cookie Consent script will apply a `fade-in` and `fade-out` animation to the components when showing/hiding them. Optionally, you can use Webflow Interactions to create your own custom animations.

To do so, place a hidden **_Div_** (set to `display: none`) inside the component with the `fs-cc="interaction"` attribute. Then, bind a [Mouse click (tap)](https://webflow.com/interactions-animations) interaction to it:

- `On 1st click` will be used to display the component. Make sure the component is set to `display: none` as the initial state.
- `On 2nd click` will be used to hide the component.

**Important**: Only set the interaction to the trigger! Do not bind this interaction to any other element (like the buttons), our Fs Cookie Consent script will programatically click this hidden **_Div_** when needed and fire the correspondent interaction.

## Additional Options

You can modify some of the behaviors of our Fs Cookie Consent tool by adding attributes to the main `<script>` tag.

| Attribute                        | Required | Description                                                                                                                                                                                                                                                                                                                                                       |
| -------------------------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `fs-cc-mode="opt-in"`            | No       | **Selected by default**. Only the essential cookies are be loaded by default. Users are able to Allow or Deny the use of cookies. If allowed, cookies will start loading on the pages. More info at [Opt-in Consent](#opt-in-consent).                                                                                                                            |
| `fs-cc-mode="opt-out"`           | No       | All cookies are be loaded by default even without the user's consent. Users are still able to Allow or Deny the use of cookies. If denied, cookies will stop loading on the pages. More info at [Opt-out Consent](#opt-out-consent).                                                                                                                              |
| `fs-cc-mode="informational"`     | No       | The banner becomes informational only, considering that the user has already granted his consent thus allowing all cookies to be loaded by default. More info at [Informational Consent](#informational-consent).                                                                                                                                                 |
| `fs-cc-expires="NUMBER_OF_DAYS"` | No       | By default, the user's consent is stored for 120 days. You can change this expiry time with this attribute. Example for a 30 day duration: `fs-cc-expires="30"`.                                                                                                                                                                                                  |
| `fs-cc-endpoint="URL"`           | No       | The library will send POST requests to this endpoint with the new consents. More info at [Storing Consent Records](#storing-consent-records).                                                                                                                                                                                                                     |
| `fs-cc-source="URL"`             | No       | If set, the components (Banner, Manager and Preferences) will be fetched from the specified URL and rendered to the current page.<br />This way, you won't have to manually place them into each single page of the website.<br />Accepts both absolute URLs (`fs-cc-source="https://example.com/components"`) and relative paths (`fs-cc-source="/components"`). |
| `fs-cc-domain="DOMAIN_NAME"`     | No       | If set, it allows to modify the domain target when storing the Consents Cookie in the user's browser.                                                                                                                                                                                                                                                             |

### Example

Example setting up Fs Cookie Consent in **Opt-out mode** and storing the user's consent for **60 days**:

<!-- prettier-ignore-start -->
```html
<script async src="https://cdn.jsdelivr.net/npm/@finsweet/cookie-consent@1/fs-cc.js" fs-cc-mode="opt-out" fs-cc-expires="60"></script>
```
<!-- prettier-ignore-end -->

## Storing Consent Records

Because consent under the GDPR is such an important issue, it’s mandatory to keep clear records and be able to demonstrate that the user has given consent. That's why our library offers the option of sending the consents to an API endpoint, so you can store them in your database.

If the `fs-cc-endpoint` attribute [is set](#additional-options), the library will make a POST request to the endpoint every time a user allow /denies / updates his consent.
The request is done with the following payload:

```typescript
interface CookieConsentPayload {
  id: string; // UUID for the consent
  url: string; // Origin URL
  action: string; // Action performed by the user: allow, deny or submit
  userAgent: string; // User Agent of the user's browser
  bannerText: string; // The text that is displayed in the Banner component
  consents: {
    uncategorized: boolean;
    essential: boolean;
    personalization: boolean;
    analytics: boolean;
    marketing: boolean;
  };
}
```

You can use it for storing the record to your own database.

Make sure you also store the following information for GDPR compliance:

| Property      | Description                                                                |
| ------------- | -------------------------------------------------------------------------- |
| Anonymized IP | The user's IP with the last digit replaced with a 0 to maintain anonymity. |
| Timestamp     | The date and time when you store the consent.                              |

For how long? Nobody knows exactly, but many consider that 2 years is a safe bet.

## Javascript API

You can use the Fs Cookie Consent Javascript API to further extend its functionalities.
You can safely access the library instance via:

```javascript
window.FsCC = window.FsCC || [];
window.FsCC.push((FsCC) => {
  // FsCC is ready
  const consents = FsCC.store.getConsents();
  console.log("The user's consents are: ", consents);
});
```

### Store

The Store manages all the important states in the application. You can access the Store object at:

<!-- prettier-ignore-start -->
```javascript
FsCC.store
```
<!-- prettier-ignore-end -->

Inside it, there are some methods and properties that you can access.

#### Properties

| Property       | Value                                  | Description                                                                          |
| -------------- | -------------------------------------- | ------------------------------------------------------------------------------------ |
| `cookieMaxAge` | Number                                 | Sets how long will the user's consent will persist.                                  |
| `mode`         | `informational`, `opt-in` or `opt-out` | Current mode. See [Additional Options](#additional-options) to see how to change it. |
| `scripts`      | Object                                 | All the scripts that have the `type="fs-cc"` attribute, classified by category.      |

#### Methods

```typescript
FsCC.store.userHasConfirmed = () => boolean; // Returns if the user has previously confirmed his allowance / denial of cookies
FsCC.store.getConsents = () => Consents; // Returns the current stored consents, classified by category
FsCC.store.getBannerText = () => string | null | undefined; // Returns the stored text of the banner
FsCC.store.storeScript = (scriptData: ScriptData) => void; // Stores an additional script
FsCC.store.storeIFrame = (iFrameData: IFrameData) => void; // Stores an additional iFrame
FsCC.store.getStoredElements = () => (ScriptData | IFrameData)[]; // Returns the stored scripts and iFrames
```

### Consent Controller

The Consent Controller runs all the logic behind the scenes. You can access the Consent Controller object at:

<!-- prettier-ignore-start -->
```javascript
FsCC.consentController
```
<!-- prettier-ignore-end -->

#### Methods

```typescript
FsCC.consentController.updateConsents = (consents: Partial<Consents>) => void; // Stores new consents from the users and applies them to the corrsepondent scripts.
```

#### Events

```typescript
FsCC.consentController.on('updateconsents', (consents: Partial<Consents>) => {
  console.log('The following consents were updated:', consents);
});
```

### Banner

You can access the Banner object at:

<!-- prettier-ignore-start -->
```javascript
FsCC.banner
```
<!-- prettier-ignore-end -->

#### Properties

| Property | Value   | Description                                   |
| -------- | ------- | --------------------------------------------- |
| `ready`  | Boolean | Tells if the component was correctly mounted. |
| `isOpen` | Boolean | Tells if the component is open / closed.      |

#### Methods

```typescript
FsCC.banner.open = () => void; // Opens the banner.
FsCC.banner.close = () => void; // Closes the banner.
```

#### Events

```typescript
FsCC.banner.on('ready', (element: HTMLElement) => console.log('The component was correctly mounted!'));
FsCC.banner.on('allow', () => console.log('An Allow all Cookies button was clicked.'));
FsCC.banner.on('deny', () => console.log('A Deny all Cookies button was clicked.'));
FsCC.banner.on('openpreferences', () => console.log('An Open Preferences button was clicked.'));
FsCC.banner.on('close', () => console.log('The component was closed!.'));
FsCC.banner.on('updateconsents', (consents: Partial<Consents>) => {
  console.log('The following consents were updated:', consents);
});
```

### Manager

You can access the Manager object at:

<!-- prettier-ignore-start -->
```javascript
FsCC.manager
```
<!-- prettier-ignore-end -->

#### Properties

| Property | Value   | Description                                   |
| -------- | ------- | --------------------------------------------- |
| `ready`  | Boolean | Tells if the component was correctly mounted. |
| `isOpen` | Boolean | Tells if the component is open / closed.      |

#### Methods

```typescript
FsCC.manager.open = () => void; // Opens the manager.
FsCC.manager.close = () => void; // Closes the manager.
```

#### Events

```typescript
FsCC.manager.on('ready', (element: HTMLElement) => console.log('The component was correctly mounted!'));
FsCC.manager.on('allow', () => console.log('An Allow all Cookies button was clicked.'));
FsCC.manager.on('deny', () => console.log('A Deny all Cookies button was clicked.'));
FsCC.manager.on('openpreferences', () => console.log('An Open Preferences button was clicked.'));
FsCC.manager.on('close', () => console.log('The component was closed!.'));
```

### Preferences

You can access the Preferences object at:

<!-- prettier-ignore-start -->
```javascript
FsCC.preferences
```
<!-- prettier-ignore-end -->

#### Properties

| Property | Value   | Description                                   |
| -------- | ------- | --------------------------------------------- |
| `ready`  | Boolean | Tells if the component was correctly mounted. |
| `isOpen` | Boolean | Tells if the component is open / closed.      |

#### Methods

```typescript
FsCC.preferences.open = () => void; // Opens the preferences.
FsCC.preferences.close = () => void; // Closes the preferences.
```

#### Events

```typescript
FsCC.preferences.on('ready', (element: HTMLElement) => console.log('The component was correctly mounted!'));
FsCC.preferences.on('allow', () => console.log('An Allow all Cookies button was clicked.'));
FsCC.preferences.on('deny', () => console.log('A Deny all Cookies button was clicked.'));
FsCC.preferences.on('openpreferences', () => console.log('An Open Preferences button was clicked.'));
FsCC.preferences.on('close', () => console.log('The component was closed!.'));
FsCC.preferences.on('updateconsents', (consents: Partial<Consents>) => {
  console.log('The following consents were updated:', consents);
});
```

## Consent Variations

There are three different ways of asking for consent to the users:

1. [Opt-in [Recommended]](#opt-in-consent)
2. [Opt-out [Not-Recommended]](#opt-out-consent)
3. [Informational [Not-Recommended]](#informational-consent)

### Opt-in Consent

Cookies won't be loaded unless the user explicitly accepts them. This solution is the only GDPR and CCPA compliant one.

To build this consent variation, make sure [all the scripts are properly set up](#scripts) and that the users can Accept and Deny all the cookies.

### Opt-out Consent

Cookies are loaded without the consent from the user unless he explicitly rejects them. This solution is not GDPR nor CCPA compliant and we strongly advise against it, as we cannot guarantee all cookies will be removed after the user denies them (read [Important Notes](#important-notes) for further information).

To build this consent variation do not set the scripts to `type="fs-cc"` as your priority is to load them before asking for the user's consent. If the user denies them, the cookies will be removed from his/her browser.

### Informational Consent

Users are just informed about the use of cookies on the site and do not have the option of rejecting them. This solution is valid for some countries but it's not GDPR nor CCPA compliant.

To build this consent, you just need to add the [Banner](#component) with an `Allow All Cookies` button.

## Important Notes

### Legal compliance of this tool

Although our tool prevents third party scripts from being loaded unless the user explicitly allows them, and removes the correspondent cookies if the user decides not to allow them anymore, we cannot guarantee the removal of all cookies.

**Why?** Some third party providers set `HttpOnly` cookies to the user's browser, which cannot be deleted using Javascript, thus preventing tools like ours from removing them.

This is not a problem for 99% of the use cases, as your website will still be GDPR and CCPA compliant. But if you have specific legal compliance needs, we strongly advise seeking legal advice to make sure our Cookie Consent solution fits your project.

### Legal

All content on this repository, as well as content throughout [Finsweet's](https://www.finsweet.com/) websites, platforms, services, or softwares, nor any portion thereof constitutes actual legal or regulatory advice, opinion, or recommendation by [Finsweet](https://www.finsweet.com/).

We are providing this free library to help you comply with cookie consent laws. If legal assistance is required, contact a lawyer.

THE SOFTWARE IS PROVIDED **_“AS IS”_**, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
