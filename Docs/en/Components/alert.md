# Alert

![](/Images/Components/Alert/Screen Shot 2016-05-16 at 22.05.48.png)

## Implementation
To create a new `Alert` component intialize the component via `Ui.Alert`.

```html
<Ui.Alert title="Well done!">
You successfully read this important alert message.
</Ui.Alert>
```

### Parameters
| Name | Description | Type | Default |
| -- | -- | -- | -- |
| title | Alert title - the bit shown in bold | string |  |
| type | Can be `success`, `info`, `warning` or `error`  | string | `info` |
| icon | By default it matches the `type` value  | string | `info` |
| close | Show the close button - the "x" at the right hand side   | boolean | true |
