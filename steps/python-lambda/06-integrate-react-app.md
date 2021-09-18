# Integrate React app

Return to the root folder of the project where `amplify init` was executed.

Install `aws-amplify`

```shell
npm i aws-amplify
```

To configure the React app to use AMplify, add the following to `index.js` after `import reportWebVitals from './reportWebVitals';`

```javascript
import { Amplify } from 'aws-amplify'
import config from './aws-exports'

Amplify.configure(config)
```

Next we will use `aws-amplify` to invoke the API with a GET request. Open `App.js` and replace the content in the file with the code below.

```javascript
import {useEffect} from 'react'
import { API } from 'aws-amplify'

function App(){
  useEffect(() => {
  const getData = async () => {
    const data = await API.get('carApi', '/car')
    console.log(data)
  }
  getData()
  })
  
return <div></div>
}

export default App;

```
The above imports `API` from `aws-amplify` to invoke the API endpoint that is referenced in `carAPI`.

Lets deploy the React app locally and test on the browser.

```shell
npm run start
```

Check the console in the browser for the log printed with the items. In this case it will be empty since there are no cars stored in DynamoDB. Let's change that.

Replace `const data = await API.get('carApi', '/car')` with the following code to test POST request to the API.

```javascript
    const data = await API.post('carApi', '/car', {
      body: {
        name: 'Ford Mustang',
        year: '2021',
        link: 'https://www.ford.com/cmslibs/content/dam/vdm_ford/live/en_us/ford/nameplate/mustang/2021/collections/3_2/21_FRD_MUST_Mach1_wdmp_200510_01894_167.jpg/_jcr_content/renditions/cq5dam.web.1280.1280.jpeg'
      }
    })
```
Deploy the React app locally.

```shell
npm run start
```
Check the console in the browser and there should be a log entry saying `item created`.

Replace the POST request with the previous GET request and run `npm run start` to see the new item fetched.


## Conclusion

We have completed the steps on how to deploy Python based lambda functions. Head back to the main page [here](../../README.md) to continue with the rest of the workshop.