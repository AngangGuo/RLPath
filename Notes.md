# Design Notes

## Login
### Use Browser Chrome: Go to BlueIQ website
**Option**
```
Open: IfNotOpen
Window attach mode: Application instance
```
After I run `Login.xaml`, it opens Chrome browser, go to `https://example.com/Login.aspx` and logged in the website. 
The browser is left open in `https://example.com/Welcome.aspx` page.  

If I run this script again without close the first instance, it won't open another browser, nor go to the Login page,
but trys to find the `User Name` at the Welcome page and cause error: `Source: Type Into 'User Name'`

If you change the option to `Window attache mode: Single window`, the browswer popup window asking to save password will cause error:
`Message: The UI Element to be found does not belong to the target application that has 'Window attach mode' set to 'Single window'.`

**Fix 1:** Change the option to always open a new window(Prefer)
```
Open: Always
Window attach mode: Application instance
```

**Fix 2:** Add `Check App State` at the beginning to make sure it's in the Login page

### Verify Login
How to verify if I've logged in successfully?

1. Check URL: The URL should be changed to `https://example.com/Welcome.aspx` page
2. Checking menu items like `Audit`, `Job`, `Receiving`, etc.

Problem: What to do if verify failed?

### Possible Concurrent Issues
When checking login processing, after get the URL as Login.aspx and before processing the get message in login page, the browser may go to Welcome.aspx page already.
I use try..catch block and ignore the error, then try again. See Login.xaml for more details.

## Close Pallets
* Get the pallet id from Pallet Details section in the load information page will ensure that they are all valid pallet ids so that we can omit the need for the logic to check wrong pallet id
* Using filter to filtering out the pallet ids with empty site also eliminate some error logic
* 
