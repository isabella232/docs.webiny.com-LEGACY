# Input

![](/assets/Input.png)

<img src="/assets/Input.png" style="width: 100%"/>

## Implementation

To create a new `Input` component initialize the component via `Ui.Input`.

```html
<Ui.Input
        placeholder="Enter your email"
        label="Email"
        name="email"
        validate="required,email"
        tooltip="Your email address"
        info="Info text for your input fields"
        description="This is your user account email"/>
```

### Parameters

| Name | Description | Type | Default |
| --- | --- | --- | --- |
| delay |  | number | 400 |
| description |  | object | null |
| hideAnimation |  | object | {"translateY":0,"opacity":0,"duration":225} |
| info |  | object | null |
| label |  | object | null |
| onChange |  | object | null |
| onEnter |  | object | null |
| onKeyDown |  | object | null |
| onKeyUp |  | object | null |
| placeholder |  | object | null |
| readOnly |  | boolean | false |
| renderer |  | function | callable |
| showAnimation |  | object | {"translateY":50,"opacity":1,"duration":225} |
| showValidationIcon |  | boolean | true |
| showValidationMessage |  | boolean | true |
| type |  | string | text |
| value |  | object | null |
| valueLink |  | object | null |

