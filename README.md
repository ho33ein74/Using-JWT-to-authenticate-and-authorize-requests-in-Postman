# Using-JWT-to-authenticate-and-authorize-requests-in-Postman

Choose the edit option on the collection and write the following code into the "pre-request scripts":
![Screenshot__12_](/uploads/-/system/personal_snippet/13/09a74b6348e86d8c0600865f5dd972b1/Screenshot__12_.png)
```
let email  = pm.variables.get("email");
let password = pm.variables.get("password");
let baseUrl = pm.variables.get("baseUrl");
pm.sendRequest({
      url:  baseUrl+`/sso/token/`,
      method: 'POST',
      header: {
        'Accept': 'application/json',
        'Content-Type': 'application/x-www-form-urlencoded'
      },
      body: {
          mode: 'urlencoded',
          urlencoded: [
            {key: "email", value: email},
            {key: "password", value: password}
        ]
      }
  }, function (err, res) {
        pm.globals.set("token", res.json().token);
  });
```
![Screenshot__13_](/uploads/-/system/personal_snippet/13/9b783276ab9ad23881141b35dae521c1/Screenshot__13_.png)

In the variables tab, define the parameters as shown in the image below
![Screenshot__15_](/uploads/-/system/personal_snippet/13/d5adc075a3294eeb28f4e429e053203b/Screenshot__15_.png)

In the final step, make the following settings
![Screenshot__14_](/uploads/-/system/personal_snippet/13/f99bed1ab07342c3437858ec5d81fdd4/Screenshot__14_.png)
