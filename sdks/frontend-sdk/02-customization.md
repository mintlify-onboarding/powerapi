---
title: Customizing the UI
---

You can customize what the iframe display through several methods to tailor the experience to your needs.

## Embedding a specific page

Embedding a page is easy just find the page you want to embed on our application and copy the URL. There are a variety of options to configure the look of the page which are described later on.

## Embedding a specific tab

Some pages on our application have multiple top-level tabs, such as the dashboard, you can embed a specific tab by including the `?tab=<id>` query parameter. This is automatically added to the URL when switching between the tabs. Note that the default tab does not add anything to URL as it is not needed.

For example, to embed the "Online Presence" tab on the dashboard, you would use `/?tab=presence`.
Additionally, you may want the hide the tab switcher which can be done by added `hide_tabs` to the URL.

```url test title="Embedding presence tab without tabs" className=wrap
https://app.powerapi.com/?access_token=my_token&tab=presence&hide_tabs
```

For a completely seamless experience, you can also hide the header and navigation.

```url title="Embedding presence tab without tabs, header or navigation" className=wrap
https://app.powerapi.com/?access_token=my_token&tab=presence&hide_tabs&hide_header&hide_navigation
```

## Hiding parts of the UI

The frontend allows you to hide parts of the UI by passing a query parameters in the URL. The following query parameters are available:

| Parameter         | Description                                              |
| ----------------- | -------------------------------------------------------- |
| `hide_header`     | Hides the header of the page.                            |
| `hide_navigation` | Hides the sidebar of the page.                           |
| `hide_tabs`       | Hides the top-level tabs of the page.                    |
| `css`             | Injects custom CSS ([more info](./03-injecting-css.mdx)) |

```url title="Hiding the navigation and header" className=wrap
https://app.powerapi.com/business/basic-information?access_token=my_token&hide_header=true&hide_navigation=true
```
