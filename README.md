# Sentry.io for nativescript

This plugin uses sentry-android and sentry-cocoa to catch native errors/stack traces and send them to a sentry server.

**NOTE:** If you have a **native exeption** and the app exits the plugin will save the log and send it in the **next app startup**, this is how the native plugins are implemented and it is expected behavior

## Installation

```javascript
tns plugin add nativescript-sentry.io
```

## Usage

### Without Angular
```typescript
import { Sentry } from 'nativescript-sentry.io';
const dsn = 'https://<key>:<secret>@host/<project>';
Sentry.init(dsn);
```
### With Angular
```typescript
import { SentryModule } from 'nativescript-sentry.io/angular';

NgModule({
  ...
  imports: [
       SentryModule.forRoot({dsn: 'https://<key>:<secret>@host/<project>'})
  ],

```

**Note:** this plugin adds a custom ErrorHandler and automatically provides it

## API

### Init Sentry

`Sentry.init(dsn: string, options: SentryOptions)`

### Capture Exception

`Sentry.captureException(exeption: Error, options: SentryOptions)`

Example:
```typescript
try {
    throw 'try catch Exception example'
} catch(error) {
    Sentry.captureException(error, {});
}
```

### Capture Message

`Sentry.captureMessage(message: string, options: SentryOptions)`

### Capture BreadCrumb

`Sentry.captureBreadcrumb(breadcrumb:SentryBreadcrumb)`

### Set Current user

`Sentry.setContextUser(user: SentryUser)`

### Context Tags

`Sentry.setContextTags(tags: any)`

### Context Extra

`Sentry.setContextExtra(extra: any)`

### Clear context

`Sentry.clearContext()``



