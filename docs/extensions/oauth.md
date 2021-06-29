---
layout: default
title: OAuth
parent: Extensions
nav_order: 3
---

# OAuth
From your extension you can use the OAuth protocol to contact an application server.

## Configure extension
If your extension need to use an OAuth application you have to set it up in the manifest file. (see [Manifest](manifest.md#oauth))

Then the user who will install you app will have the capability to define which application (declare on its platform) he want to use.

## Recieved selected application
In your Content & your Settings components you'll be able to retrieve the application set by the customer administrator via props sent by Lumapps to your extension.
You'll recieved the OAuth application ID inside the globalValue property :

```javascript
interface WidgetProps {
    globalValue?: {
        oauthApplicationId: string
    };
    ...
}
```


## OAuth with SDK
To contact the server application from your extension you'll have to use the LumApps Javascript SDK.


## Contact

If you are interrested in, you can register to be part of the Lumapps Marketplace program 
<form onSubmit="submitForm()">
    <script>
    function submitForm() {
        alert('test');
    }
    </script>
    <div>
        <label for="first_name">First Name</label>
        <input type="text" name="first_name">
        <label for="last_name">Last Name</label>
        <input type="text" name="last_name">
    </div>
    <div>
        <label for="email">Email</label>
        <input type="text" name="test">
    </div>
    <div>
        <label for="company_name">Company Name</label>
        <input type="text" name="company_name">
    </div>
    <div>
        <button>Submit</button>
    </div>
</form>