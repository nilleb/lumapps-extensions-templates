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

If you are interrested in, you can register to be part of the LumApps Marketplace program
<style>
.form {
    width        : 440px;
    height       : 520px;
    background   : #e6e6e6;
    border-radius: 8px;
    box-shadow   : 0 0 20px -10px #a9a9a9;
    margin       : calc(50vh - 220px) auto;
    padding      : 20px 30px;
    max-width    : calc(100vw - 40px);
    box-sizing   : border-box;
    font-family  : 'Montserrat', sans-serif;
    position     : relative;
    font-size    : 13px;
}

.form .lumapps-logo {
    width         : 24px;
    margin-right  : 12px;
}

.form h2 {
    margin        : 10px 0;
    padding-bottom: 10px;
    width         : 200px;
    color         : #1a1c40;
    border-bottom : 3px solid #1a1c40
}

.form input {
    width        : 100%;
    padding      : 10px;
    box-sizing   : border-box;
    background   : none;
    outline      : none;
    resize       : none;
    border       : 0;
    font-family  : 'Montserrat', sans-serif;
    transition   : all .3s;
    border-bottom: 2px solid #1a1c40;
}

.form input:focus-within {
    border-bottom: 2px solid #245be7;
}

.form ::placeholder {
    color: #1a1c40;
}

p:before {
    content  : attr(type);
    display  : block;
    margin   : 28px 0 0;
    font-size: 14px;
    color    : #1a1c40
}

.form button {
    float      : right;
    padding    : 12px 18px;
    margin     : 8px 0 0;
    font-family: 'Montserrat', sans-serif;
    border     : 0px solid #78788c;
    border-radius: 4px;
    background : 0;
    color      : #1a1c40;
    font-weight: bold;
    background-color: #ffcf1e;
    cursor     : pointer;
    transition : all .3s
}

.form button:hover {
    background: #1a1c40;
    color     : #fff
}

.form div {
    content      : 'Hi';
    position     : absolute;
    bottom       : -15px;
    right        : -20px;
    background   : #50505a;
    color        : #fff;
    width        : 320px;
    padding      : 16px 4px 16px 0;
    border-radius: 6px;
    font-size    : 13px;
    box-shadow   : 10px 10px 40px -14px #000
}

.form span {
    margin: 0 5px 0 15px
}
</style>

<script>
    function submitForm() {
        const form = document.querySelector('form[name="contact_form"]');
        const userName = form.elements['name'].value;
        const userEmail = form.elements['email'].value;
        const companyName = form.elements['company'].value;
        const companyWebsite = form.elements['companyWebsite'].value;
        const body = `A new MP Program request from ${userName} (${userEmail}) - ${companyName} (${companyWebsite})`;
        const bodyHtml = '<!DOCTYPE html>' +
            '<html lang="en" xmlns="http://www.w3.org/1999/xhtml" xmlns:o="urn:schemas-microsoft-com:office:office">' +
            '<head>' +
            '  <meta charset="utf-8">' +
            '  <meta name="viewport" content="width=device-width,initial-scale=1">' +
            '  <meta name="x-apple-disable-message-reformatting">' +
            '  <title></title>' +
            '  <!--[if mso]>' +
            '  <style>' +
            '    table {border-collapse:collapse;border-spacing:0;border:none;margin:0;}' +
            '    div, td {padding:0;}' +
            '    div {margin:0 !important;}' +
            '  </style>' +
            '  <noscript>' +
            '    <xml>' +
            '      <o:OfficeDocumentSettings>' +
            '        <o:PixelsPerInch>96</o:PixelsPerInch>' +
            '      </o:OfficeDocumentSettings>' +
            '    </xml>' +
            '  </noscript>' +
            '  <![endif]-->' +
            '  <style>' +
            '    table, td, div, h1, p {' +
            '      font-family: Arial, sans-serif;' +
            '    }' +
            '    @media screen and (max-width: 530px) {' +
            '      .unsub {' +
            '        display: block;' +
            '        padding: 8px;' +
            '        margin-top: 14px;' +
            '        border-radius: 6px;' +
            '        background-color: #555555;' +
            '        text-decoration: none !important;' +
            '        font-weight: bold;' +
            '      }' +
            '      .col-lge {' +
            '        max-width: 100% !important;' +
            '      }' +
            '    }' +
            '    @media screen and (min-width: 531px) {' +
            '      .col-sml {' +
            '        max-width: 27% !important;' +
            '      }' +
            '     .col-lge {' +
            '        max-width: 73% !important;' +
            '      }' +
            '    }' +
            '  </style>' +
            '</head>' +
            '<body style="margin:0;padding:0;word-spacing:normal;background-color:#f5f6fa;">' +
            '  <div role="article" aria-roledescription="email" lang="en" style="text-size-adjust:100%;-webkit-text-size-adjust:100%;-ms-text-size-adjust:100%;background-color:#f5f6fa;">' +
            '    <table role="presentation" style="width:100%;border:none;border-spacing:0;">' +
            '      <tr>' +
            '        <td align="center" style="padding:0;">' +
            '          <!--[if mso]>' +
            '          <table role="presentation" align="center" style="width:600px;">' +
            '          <tr>' +
            '          <td>' +
            '          <![endif]-->' +
            '          <table role="presentation" style="width:94%;max-width:600px;border:none;border-spacing:0;text-align:left;font-family:Arial,sans-serif;font-size:16px;line-height:22px;color:#363636;">' +
            '            <tr>' +
            '              <td style="padding:40px 30px 30px 30px;text-align:center;font-size:24px;font-weight:bold;">' +
            '                <a href="http://www.example.com/" style="text-decoration:none;"><img src="https://static.crozdesk.com/web_app_library/providers/logos/000/004/430/original/lumapps-1559230943-logo.png?1559230943" width="165" alt="Logo" style="width:80%;max-width:165px;height:auto;border:none;text-decoration:none;color:#ffffff;"></a>' +
            '              </td>' +
            '            </tr>' +
            '            <tr>' +
            '              <td style="padding:30px;background-color:#ffffff;">' +
            '                <h1 style="margin-top:0;margin-bottom:16px;font-size:26px;line-height:32px;font-weight:bold;letter-spacing:-0.02em;">New Marketplace program request</h1>' +
            '               <p style="margin:0;">A new request to join the LumApps Marketplace program hase been made.<br/>' +
            '                User requested an access : ' +
            '                <ul>' +
            '                    <li>' + userName + '</li>' +
            '                    <li>' + userEmail +'</li>' +
            '                    <li>' + companyName + '</li>' +
            '                    <li>' + companyWebsite + '</li>' +
            '                </ul>' +
            '                </p>' +
            '              </td>' +
            '            </tr>' +
            '            <tr>' +
            '              <td style="padding:30px;text-align:center;font-size:12px;background-color:#404040;color:#cccccc;">' +
            '                <p style="margin:0;font-size:14px;line-height:20px;">&reg; Lumapps, 2021<br>' +
            '              </td>' +
            '            </tr>' +
            '          </table>' +
            '          <!--[if mso]>' +
            '          </td>' +
            '          </tr>' +
            '          </table>' +
            '          <![endif]-->' +
            '        </td>' +
            '      </tr>' +
            '    </table>' +
            '  </div>' +
            '</body>' +
            '</html>';

        const email = 'gregory@lumapps.com'; 
        const subject = `Marketplace programm request - ${companyName}`;
        
        const mail = document.createElement("a");
        mail.target = "_blank";
        mail.href = `mailto:${email}?body=${encodeURIComponent(bodyHtml)}&subject=${encodeURIComponent(subject)}`;
        mail.click();
    }
</script>

<form class="form" name="contact_form" onSubmit="submitForm()">
    <h2><img class="lumapps-logo" src="https://static.crozdesk.com/web_app_library/providers/logos/000/004/430/original/lumapps-1559230943-logo.png?1559230943"/>CONTACT US</h2>
    <p type="Name:">
        <input placeholder="Write your name here.." name="name"/>
    </p>
    <p type="Email:">
        <input placeholder="Let us know how to contact you back.." name="email"/>
    </p>
    <p type="Company:">
        <input placeholder="Write your campany name here..." name="company"/>
    </p>
    <p type="Company website:">
        <input placeholder="Write your campany website URL name here..." name="companyWebsite"/>
    </p>
    <button type="submit">Submit</button>
</form>

<script>





</script>