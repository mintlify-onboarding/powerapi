---
title: Introduction
---

Users are able to embed any page of our business [application](https://app.powerapi.com) into their application. For this example we will embed the [/business/basic-information](https://app.powerapi.com/business/basic-information) page.

When embedding any page, by default the user will be taken to the login page to sign-in if they are not already authenticated. To have the user be instantly logged in you can include the users access token in the URL. The access token can be found in the [Authentication](/docs/authentication.mdx) section.

The resulting URL should look like this:

```url
https://app.powerapi.com/business/basic-information?access_token=ca5b04d6e3531570cfd6cf2ea947a2dab9be88...
```

### Examples

Once you have generated the URL as shown above you can embed the SDK into your application using an `iframe`.

```html title="Example: Javascript"
<iframe
  title="PowerAPI"
  src="https://app.powerapi.com/business/basic-information?access_token=<token>&hide_header=true&hide_navigation=true"
/>
```

```tsx title="Example: React Dynamic"
type PowerAPIProps = {
  page: string;
  showHeader?: boolean;
  showNavigation?: boolean;
};

export const PowerAPI = ({
  page,
  showHeader,
  showNavigation,
}: PowerAPIProps) => {
  const url = new URL(page, BASE_URL);
  url.searchParams.append("access_token", TOKEN);
  url.searchParams.append("hide_header", String(!showHeader));
  url.searchParams.append("hide_navigation", String(!showNavigation));

  return <iframe title="PowerAPI" src={url.toString()}></iframe>;
};

// <PowerAPI page="/">
```
