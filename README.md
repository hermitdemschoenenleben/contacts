<p align="center"><br><img src="https://user-images.githubusercontent.com/236501/85893648-1c92e880-b7a8-11ea-926d-95355b8175c7.png" width="128" height="128" /></p>

<h3 align="center">Contacts</h3>
<p align="center"><strong><code>@capacitor-community/contacts</code></strong></p>
<p align="center">
  Capacitor community plugin for fetching contacts.
</p>

<p align="center">
  <img src="https://img.shields.io/maintenance/yes/2021?style=flat-square" />
  <a href="https://github.com/capacitor-community/contacts/actions?query=workflow%3A%22Test+and+Build+Plugin%22"><img src="https://img.shields.io/github/workflow/status/capacitor-community/contacts/Test%20and%20Build%20Plugin?style=flat-square" /></a>
  <a href="https://www.npmjs.com/package/@capacitor-community/contacts"><img src="https://img.shields.io/npm/l/@capacitor-community/contacts?style=flat-square" /></a>
  <br>
  <a href="https://www.npmjs.com/package/@capacitor-community/contacts"><img src="https://img.shields.io/npm/dw/@capacitor-community/contacts?style=flat-square" /></a>
  <a href="https://www.npmjs.com/package/@capacitor-community/contacts"><img src="https://img.shields.io/npm/v/@capacitor-community/contacts?style=flat-square" /></a>
</p>

## Maintainers

| Maintainer                           | GitHub                                                                                       | Social                       | Sponsoring Company |
| ------------------------------------ | -------------------------------------------------------------------------------------------- | ---------------------------- | ------------------ |
| Jonathan Gerber / Byrds & Bytes GmbH | [idrimi](https://github.com/idrimi) / [Byrds & Bytes GmbH](https://github.com/byrdsandbytes) | [byrds.ch](https://byrds.ch) | Byrds & Bytes GmbH |

Maintenance Status: Actively Maintained

## Demo

You can find a working Ionic App using the Byrds' Capacitor Contacts plugin here:
https://github.com/byrdsandbytes/capContactsDemo

## Prerequisites

Setup your project with Capacitor. For details check here: https://capacitorjs.com

```sh
cd my-app
npm install --save @capacitor/core @capacitor/cli
```

Initialize Capacitor

```sh
npx cap init
```

Add the platforms you want to use.

```sh
npx cap add android
npx cap add ios
npx cap add electron
```

## Installation

Install:

```sh
npm i --save @capacitor-community/contacts

# or yarn
yarn add @capacitor-community/contacts

# or pnpm
pnpm add @capacitor-community/contacts
```

Sync:

```sh
npx cap sync
```

### iOS

For iOS you need to set a usage description in your info.plist file. (Privacy Setting)
Open xCode search for your info.plist file and press the tiny "+". Add the following entry:

```
Privacy - Contacts Usage Description
```

Give it a value like:

```
"We need access to your contacts in order to do something."
```

### Android Notes

For Android you have to add the permissions in your AndroidManifest.xml. Add the following permissions before the closing of the "manifest" tag.

```xml
<uses-permission android:name="android.permission.READ_CONTACTS" />
<uses-permission android:name="android.permission.WRITE_CONTACTS"/>
```

Next import the capContacts class to your MainActivity

```java
// Initializes the Bridge
this.init(savedInstanceState, new ArrayList<Class<? extends Plugin>>() {{
  // Additional plugins you've installed go here
  // Ex: add(TotallyAwesomePlugin.class);
  add(Contacts.class);
}});
```

Make sure to import it properly as well.

```java
import ch.byrds.capacitor.contacts.Contacts;
```

**NOTE**: On Android you have to ask for permission first, before you can fetch the contacts. Use the `getPermissions()` method before you try to fetch contacts using `getContacts()`.

## Usage / Examples

You have the following Methods available:

```ts
export interface ContactsPlugin {
  getPermissions(): Promise<PermissionStatus>;
  getContacts(): Promise<{contacts: Contact[]}>;
  saveContact(contact: NewContact): Promise<void>;
}
```

If you're considering to use this plugin you most likely want to retrieve contacts a users contacts:

Import the Plugin in your TS file:

```ts
import { Contacts } from '@capacitor-community/contacts'
```

Next use it and console log the result:

```ts
Contacts.getContacts().then(result => {
    console.log(result);
    for (const contact of result.contacts) {
        console.log(contact);
    }
});

```

That's it. Do Whatever you want with the retrieved contacts.

If you're trying to build something like "contacts matching" based on phone numbers, recommends using google [libphonenumber](https://www.npmjs.com/package/google-libphonenumber) based library [awesome-phonenumber](https://www.npmjs.com/package/awesome-phonenumber).

In order to match them properly you need to format them before you can match or store them properly.

### Interfaces

```ts
export interface PermissionStatus {
  granted: boolean;
}

export interface Contact {
  contactId: string;
  displayName?: string;
  phoneNumbers: PhoneNumber[];
  emails: EmailAddress[];
  photoThumbnail?: string;
  organizationName?: string;
  organizationRole?: string;
  birthday?: string;
}

export interface PhoneNumber {
  label?: string;
  number?: string;
}

export interface EmailAddress {
  label?: string;
  address?: string;
}
```

## Built With

- Swift 5
- Java
- Angular
- Capacitor

## Authors

- Jonathan Gerber ([idrimi](https://github.com/idrimi))

## License

MIT

## Contributors

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tr>
    <td align="center"><a href="https://github.com/Idrimi"><img src="https://avatars0.githubusercontent.com/u/24573405?v=4?s=100" width="100px;" alt=""/><br /><sub><b>idrimi</b></sub></a><br /><a href="https://github.com/capacitor-community/contacts/commits?author=Idrimi" title="Code">💻</a></td>
    <td align="center"><a href="https://github.com/tafelnl"><img src="https://avatars2.githubusercontent.com/u/35837839?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Tafel</b></sub></a><br /><a href="https://github.com/capacitor-community/contacts/commits?author=tafelnl" title="Code">💻</a></td>
    <td align="center"><a href="http://ionicframework.com/"><img src="https://avatars3.githubusercontent.com/u/11214?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Max Lynch</b></sub></a><br /><a href="https://github.com/capacitor-community/contacts/commits?author=mlynch" title="Documentation">📖</a> <a href="#eventOrganizing-mlynch" title="Event Organizing">📋</a></td>
    <td align="center"><a href="https://github.com/david-garzon-adl"><img src="https://avatars0.githubusercontent.com/u/45822796?v=4?s=100" width="100px;" alt=""/><br /><sub><b>David Javier Garzon Carrillo</b></sub></a><br /><a href="https://github.com/capacitor-community/contacts/commits?author=david-garzon-adl" title="Code">💻</a></td>
    <td align="center"><a href="https://github.com/vhinic"><img src="https://avatars.githubusercontent.com/u/244439?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Vladimir Hinić</b></sub></a><br /><a href="https://github.com/capacitor-community/contacts/commits?author=vhinic" title="Code">💻</a></td>
    <td align="center"><a href="https://t.me/reslear"><img src="https://avatars.githubusercontent.com/u/12596485?v=4?s=100" width="100px;" alt=""/><br /><sub><b>reslear</b></sub></a><br /><a href="https://github.com/capacitor-community/contacts/commits?author=reslear" title="Documentation">📖</a></td>
    <td align="center"><a href="https://marvin.digital/"><img src="https://avatars.githubusercontent.com/u/11534760?v=4?s=100" width="100px;" alt=""/><br /><sub><b>Marvin Heilemann</b></sub></a><br /><a href="https://github.com/capacitor-community/contacts/commits?author=muuvmuuv" title="Code">💻</a> <a href="https://github.com/capacitor-community/contacts/commits?author=muuvmuuv" title="Documentation">📖</a></td>
  </tr>
</table>

<!-- markdownlint-restore -->
<!-- markdownlint-enable -->
<!-- prettier-ignore-end -->
<!-- ALL-CONTRIBUTORS-LIST:END -->

## API

<docgen-index>

* [`getPermissions()`](#getpermissions)
* [`getContacts()`](#getcontacts)
* [`saveContact(...)`](#savecontact)
* [Interfaces](#interfaces)
* [Enums](#enums)

</docgen-index>

<docgen-api>
<!--Update the source file JSDoc comments and rerun docgen to update the docs below-->

### getPermissions()

```typescript
getPermissions() => Promise<PermissionStatus>
```

**Returns:** <code>Promise&lt;<a href="#permissionstatus">PermissionStatus</a>&gt;</code>

--------------------


### getContacts()

```typescript
getContacts() => Promise<{ contacts: Contact[]; }>
```

**Returns:** <code>Promise&lt;{ contacts: Contact[]; }&gt;</code>

--------------------


### saveContact(...)

```typescript
saveContact(contact: NewContact) => Promise<void>
```

| Param         | Type                                              |
| ------------- | ------------------------------------------------- |
| **`contact`** | <code><a href="#newcontact">NewContact</a></code> |

--------------------


### Interfaces


#### PermissionStatus

| Prop           | Type                                                                                                                      |
| -------------- | ------------------------------------------------------------------------------------------------------------------------- |
| **`onchange`** | <code>((this: <a href="#permissionstatus">PermissionStatus</a>, ev: <a href="#event">Event</a>) =&gt; any) \| null</code> |
| **`state`**    | <code>"denied" \| "granted" \| "prompt"</code>                                                                            |

| Method                  | Signature                                                                                                                                                                                                                                                       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **addEventListener**    | &lt;K extends "change"&gt;(type: K, listener: (this: <a href="#permissionstatus">PermissionStatus</a>, ev: PermissionStatusEventMap[K]) =&gt; any, options?: boolean \| <a href="#addeventlisteneroptions">AddEventListenerOptions</a> \| undefined) =&gt; void | Appends an event listener for events whose type attribute value is type. The callback argument sets the callback that will be invoked when the event is dispatched. The options argument sets listener-specific options. For compatibility this can be a boolean, in which case the method behaves exactly as if the value was specified as options's capture. When set to true, options's capture prevents callback from being invoked when the event's eventPhase attribute value is BUBBLING_PHASE. When false (or not present), callback will not be invoked when event's eventPhase attribute value is CAPTURING_PHASE. Either way, callback will be invoked if event's eventPhase attribute value is AT_TARGET. When set to true, options's passive indicates that the callback will not cancel the event by invoking preventDefault(). This is used to enable performance optimizations described in § 2.8 Observing event listeners. When set to true, options's once indicates that the callback will only be invoked once after which the event listener will be removed. The event listener is appended to target's event listener list and is not appended if it has the same type, callback, and capture. |
| **addEventListener**    | (type: string, listener: EventListenerOrEventListenerObject, options?: boolean \| <a href="#addeventlisteneroptions">AddEventListenerOptions</a> \| undefined) =&gt; void                                                                                       | Appends an event listener for events whose type attribute value is type. The callback argument sets the callback that will be invoked when the event is dispatched. The options argument sets listener-specific options. For compatibility this can be a boolean, in which case the method behaves exactly as if the value was specified as options's capture. When set to true, options's capture prevents callback from being invoked when the event's eventPhase attribute value is BUBBLING_PHASE. When false (or not present), callback will not be invoked when event's eventPhase attribute value is CAPTURING_PHASE. Either way, callback will be invoked if event's eventPhase attribute value is AT_TARGET. When set to true, options's passive indicates that the callback will not cancel the event by invoking preventDefault(). This is used to enable performance optimizations described in § 2.8 Observing event listeners. When set to true, options's once indicates that the callback will only be invoked once after which the event listener will be removed. The event listener is appended to target's event listener list and is not appended if it has the same type, callback, and capture. |
| **removeEventListener** | &lt;K extends "change"&gt;(type: K, listener: (this: <a href="#permissionstatus">PermissionStatus</a>, ev: PermissionStatusEventMap[K]) =&gt; any, options?: boolean \| <a href="#eventlisteneroptions">EventListenerOptions</a> \| undefined) =&gt; void       | Removes the event listener in target's event listener list with the same type, callback, and options.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| **removeEventListener** | (type: string, listener: EventListenerOrEventListenerObject, options?: boolean \| <a href="#eventlisteneroptions">EventListenerOptions</a> \| undefined) =&gt; void                                                                                             | Removes the event listener in target's event listener list with the same type, callback, and options.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |


#### PermissionStatusEventMap

| Prop           | Type                                    |
| -------------- | --------------------------------------- |
| **`"change"`** | <code><a href="#event">Event</a></code> |


#### Event

An event which takes place in the DOM.

| Prop                   | Type                                                        | Description                                                                                                                                                                                                                                                |
| ---------------------- | ----------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **`bubbles`**          | <code>boolean</code>                                        | Returns true or false depending on how event was initialized. True if event goes through its target's ancestors in reverse tree order, and false otherwise.                                                                                                |
| **`cancelBubble`**     | <code>boolean</code>                                        |                                                                                                                                                                                                                                                            |
| **`cancelable`**       | <code>boolean</code>                                        | Returns true or false depending on how event was initialized. Its return value does not always carry meaning, but true can indicate that part of the operation during which event was dispatched, can be canceled by invoking the preventDefault() method. |
| **`composed`**         | <code>boolean</code>                                        | Returns true or false depending on how event was initialized. True if event invokes listeners past a ShadowRoot node that is the root of its target, and false otherwise.                                                                                  |
| **`currentTarget`**    | <code><a href="#eventtarget">EventTarget</a> \| null</code> | Returns the object whose event listener's callback is currently being invoked.                                                                                                                                                                             |
| **`defaultPrevented`** | <code>boolean</code>                                        | Returns true if preventDefault() was invoked successfully to indicate cancelation, and false otherwise.                                                                                                                                                    |
| **`eventPhase`**       | <code>number</code>                                         | Returns the event's phase, which is one of NONE, CAPTURING_PHASE, AT_TARGET, and BUBBLING_PHASE.                                                                                                                                                           |
| **`isTrusted`**        | <code>boolean</code>                                        | Returns true if event was dispatched by the user agent, and false otherwise.                                                                                                                                                                               |
| **`returnValue`**      | <code>boolean</code>                                        |                                                                                                                                                                                                                                                            |
| **`srcElement`**       | <code><a href="#eventtarget">EventTarget</a> \| null</code> |                                                                                                                                                                                                                                                            |
| **`target`**           | <code><a href="#eventtarget">EventTarget</a> \| null</code> | Returns the object to which event is dispatched (its target).                                                                                                                                                                                              |
| **`timeStamp`**        | <code>number</code>                                         | Returns the event's timestamp as the number of milliseconds measured relative to the time origin.                                                                                                                                                          |
| **`type`**             | <code>string</code>                                         | Returns the type of event, e.g. "click", "hashchange", or "submit".                                                                                                                                                                                        |
| **`AT_TARGET`**        | <code>number</code>                                         |                                                                                                                                                                                                                                                            |
| **`BUBBLING_PHASE`**   | <code>number</code>                                         |                                                                                                                                                                                                                                                            |
| **`CAPTURING_PHASE`**  | <code>number</code>                                         |                                                                                                                                                                                                                                                            |
| **`NONE`**             | <code>number</code>                                         |                                                                                                                                                                                                                                                            |

| Method                       | Signature                                                                                    | Description                                                                                                                                                                                                                             |
| ---------------------------- | -------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **composedPath**             | () =&gt; EventTarget[]                                                                       | Returns the invocation target objects of event's path (objects on which listeners will be invoked), except for any nodes in shadow trees of which the shadow root's mode is "closed" that are not reachable from event's currentTarget. |
| **initEvent**                | (type: string, bubbles?: boolean \| undefined, cancelable?: boolean \| undefined) =&gt; void |                                                                                                                                                                                                                                         |
| **preventDefault**           | () =&gt; void                                                                                | If invoked when the cancelable attribute value is true, and while executing a listener for the event with passive set to false, signals to the operation that caused event to be dispatched that it needs to be canceled.               |
| **stopImmediatePropagation** | () =&gt; void                                                                                | Invoking this method prevents event from reaching any registered event listeners after the current one finishes running and, when dispatched in a tree, also prevents event from reaching any other objects.                            |
| **stopPropagation**          | () =&gt; void                                                                                | When dispatched in a tree, invoking this method prevents event from reaching any objects other than the current object.                                                                                                                 |


#### EventTarget

<a href="#eventtarget">EventTarget</a> is a DOM interface implemented by objects that can receive events and may have listeners for them.

| Method                  | Signature                                                                                                                                                                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **addEventListener**    | (type: string, listener: EventListenerOrEventListenerObject \| null, options?: boolean \| <a href="#addeventlisteneroptions">AddEventListenerOptions</a> \| undefined) =&gt; void | Appends an event listener for events whose type attribute value is type. The callback argument sets the callback that will be invoked when the event is dispatched. The options argument sets listener-specific options. For compatibility this can be a boolean, in which case the method behaves exactly as if the value was specified as options's capture. When set to true, options's capture prevents callback from being invoked when the event's eventPhase attribute value is BUBBLING_PHASE. When false (or not present), callback will not be invoked when event's eventPhase attribute value is CAPTURING_PHASE. Either way, callback will be invoked if event's eventPhase attribute value is AT_TARGET. When set to true, options's passive indicates that the callback will not cancel the event by invoking preventDefault(). This is used to enable performance optimizations described in § 2.8 Observing event listeners. When set to true, options's once indicates that the callback will only be invoked once after which the event listener will be removed. The event listener is appended to target's event listener list and is not appended if it has the same type, callback, and capture. |
| **dispatchEvent**       | (event: <a href="#event">Event</a>) =&gt; boolean                                                                                                                                 | Dispatches a synthetic event event to target and returns true if either event's cancelable attribute value is false or its preventDefault() method was not invoked, and false otherwise.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| **removeEventListener** | (type: string, callback: EventListenerOrEventListenerObject \| null, options?: boolean \| <a href="#eventlisteneroptions">EventListenerOptions</a> \| undefined) =&gt; void       | Removes the event listener in target's event listener list with the same type, callback, and options.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |


#### AddEventListenerOptions

| Prop          | Type                 |
| ------------- | -------------------- |
| **`once`**    | <code>boolean</code> |
| **`passive`** | <code>boolean</code> |


#### EventListenerOptions

| Prop          | Type                 |
| ------------- | -------------------- |
| **`capture`** | <code>boolean</code> |


#### Contact

| Prop                   | Type                        |
| ---------------------- | --------------------------- |
| **`contactId`**        | <code>string</code>         |
| **`displayName`**      | <code>string</code>         |
| **`phoneNumbers`**     | <code>PhoneNumber[]</code>  |
| **`emails`**           | <code>EmailAddress[]</code> |
| **`photoThumbnail`**   | <code>string</code>         |
| **`organizationName`** | <code>string</code>         |
| **`organizationRole`** | <code>string</code>         |
| **`birthday`**         | <code>string</code>         |
| **`whatsapp`**         | <code>string</code>         |


#### PhoneNumber

| Prop         | Type                |
| ------------ | ------------------- |
| **`label`**  | <code>string</code> |
| **`number`** | <code>string</code> |


#### EmailAddress

| Prop          | Type                |
| ------------- | ------------------- |
| **`label`**   | <code>string</code> |
| **`address`** | <code>string</code> |


#### NewContact

New contact schema.

| Prop                   | Type                                                | Description  |
| ---------------------- | --------------------------------------------------- | ------------ |
| **`contactType`**      | <code><a href="#contacttype">ContactType</a></code> |              |
| **`namePrefix`**       | <code>string</code>                                 |              |
| **`givenName`**        | <code>string</code>                                 |              |
| **`middleName`**       | <code>string</code>                                 |              |
| **`familyName`**       | <code>string</code>                                 |              |
| **`nameSuffix`**       | <code>string</code>                                 |              |
| **`nickname`**         | <code>string</code>                                 |              |
| **`jobTitle`**         | <code>string</code>                                 |              |
| **`departmentName`**   | <code>string</code>                                 |              |
| **`organizationName`** | <code>string</code>                                 |              |
| **`postalAddresses`**  | <code>PostalAddress[]</code>                        |              |
| **`emailAddresses`**   | <code>EmailAddress[]</code>                         |              |
| **`urlAddresses`**     | <code>UrlAddress[]</code>                           |              |
| **`phoneNumbers`**     | <code>PhoneNumber[]</code>                          |              |
| **`birthday`**         | <code>string</code>                                 |              |
| **`note`**             | <code>string</code>                                 |              |
| **`socialProfiles`**   | <code>SocialProfile[]</code>                        |              |
| **`image`**            | <code>string</code>                                 | Base64 image |


#### PostalAddress

| Prop          | Type                                                                                                    |
| ------------- | ------------------------------------------------------------------------------------------------------- |
| **`label`**   | <code>string</code>                                                                                     |
| **`address`** | <code>{ street?: string; city?: string; state?: string; postalCode?: string; country?: string; }</code> |


#### UrlAddress

| Prop        | Type                |
| ----------- | ------------------- |
| **`label`** | <code>string</code> |
| **`url`**   | <code>string</code> |


#### SocialProfile

| Prop          | Type                                                                      |
| ------------- | ------------------------------------------------------------------------- |
| **`label`**   | <code>string</code>                                                       |
| **`profile`** | <code>{ username?: string; service?: string; urlString?: string; }</code> |


### Enums


#### ContactType

| Members            |
| ------------------ |
| **`Person`**       |
| **`Organization`** |

</docgen-api>
