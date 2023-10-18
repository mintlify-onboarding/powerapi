---
title: Live Demos
hide_table_of_contents: true
---

For a live demo with a visual config editor see the [Config Creator](./config-creator) section.

## Basic using `token`

:::tip

The easiest way to get the token is to log in to the main [website](https://app.powerapi.com) and copy the `accessToken` cookie.

:::

```jsx live
function PowerAPI() {
  const PAGE = "/business/basic-information";
  const TOKEN = ""; // "ca5b04d6e3531570cfd6cf2ea947a2dab9be88...";

  const url = new URL(PAGE, POWERAPI_URL);
  url.searchParams.append("access_token", TOKEN);
  url.searchParams.append("hide_header", "true"); // hide the header
  url.searchParams.append("hide_navigation", "true"); // hide navigation
  url.searchParams.append("hide_tabs", "false"); // hide top-level tabs
  // url.searchParams.append("css", ""); // add custom css

  return !TOKEN ? (
    <div>A token is required to display the iframe</div>
  ) : (
    <iframe
      title="PowerAPI"
      src={url.toString()}
      width="100%"
      height={512}
    ></iframe>
  );
}
```

## Advanced using `email` and `password`

```jsx live
function PowerAPI() {
  const PAGE = "/business/basic-information";

  // add email and password to fetch token
  const EMAIL = "";
  const PASSWORD = "";
  // or set token here manually
  const [token, setToken] = useState("");

  const url = new URL(PAGE, POWERAPI_URL);
  url.searchParams.append("access_token", token);
  url.searchParams.append("hide_header", "true"); // hide the header
  url.searchParams.append("hide_navigation", "true"); // hide navigation
  url.searchParams.append("hide_tabs", "false"); // hide top-level tabs
  // url.searchParams.append("css", ""); // add custom css

  useEffect(() => {
    if (EMAIL && PASSWORD)
      fetch(`${BACKEND_URL}/oauth/token`, {
        method: "POST",
        headers: {
          "Content-Type": "application/vnd.api+json",
          Accept: "application/vnd.api+json",
        },
        body: JSON.stringify({
          scope: "trusted public",
          grant_type: "password",
          email: EMAIL,
          password: PASSWORD,
        }),
      }).then(async (res) => {
        setToken((await res.json()).access_token);
      });
  }, []);

  return !token ? (
    <div>A token is required to display the iframe</div>
  ) : (
    <iframe
      title="PowerAPI"
      src={url.toString()}
      width="100%"
      height={512}
    ></iframe>
  );
}
```
