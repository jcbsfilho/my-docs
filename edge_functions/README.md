# Edge Functions

Azion Edge Functions allows you to create event-driven, serverless applications, at the edge of the network, closer to users.

With Edge Functions, you can perform serverless functions in response to events on edge nodes of our network with no need of having or managing servers.

Explore how to use and get the most out of Edge Functions as follows.

## About Edge Functions

### How it works

#### Basics

Step-by-step: creating an Edge Function

Edge Functions with multiple files

Activating your settings

## Related documentation

1. **About Edge Functions**

Here are some of the solutions provided by Azion Edge Functions.

You can use functions to handle HTTP in the following Request and Response phases:

- As soon as a user’s requests are received in the Edge Node (Viewer Request).
- Before the Azion Edge Node forwards the Request to the Origin (Origin Request).
- As soon as the Edge Node gets the response from the Origin (Origin Response).
- Before the Azion Edge Node forwards the response to the user (Viewer Response).

You can also generate responses without necessarily having to forward the request to the origin.

By using Edge Functions on your Edge Application, you can create a variety of solutions, for example:

- Inspect cookies to rewrite URLs to different versions of a site for A/B testing.
- Send different objects to your users based on the User-Agent header, which contains information about the device that submitted the request. For example, you can send images in different resolutions to users based on their devices.
- Inspect headers or authorized tokens, inserting a corresponding header and allowing access control before forwarding a request to the origin.
- Add, delete, and modify headers and rewrite the URL path to direct users to different cache objects.
- Generate new HTTP responses to do things like redirect unauthenticated users to login pages or create and deliver static webpages right from the edge.

See more ways of using Edge Functions in Guides.

2. **How it works**

You can create custom functions or use any of the existing ones provided by Azion, both for Edge Application and Edge Firewall.

The language currently supported by the platform is JavaScript.

Edge Functions run during the handling of the request and Azion Edge Computing Platform provides a Rules Engine model that can trigger the execution of the Edge Functions code according to the handling phases.

The language-specific Runtime provides a programming interface for interacting and manipulating Request and Response objects to implement the necessary logic.

When instantiating an edge function, you can enter parameters that will be passed on to the function, in JSON format, through arguments. You can also define and run tests online to validate its construction.

Edge Functions are performed directly on Azion Edge Infrastructure. To use them, they just need to be associated to a Behavior in the Rules Engine. Thus, when a request meets the criteria defined in the Rule Engine rules, the edge function will be triggered.

3. **Basics**

You can create Edge Functions and maintain a repository of functions that can be used in Edge Application or Edge Firewall. Consult the Runtime API according to the Runtime chosen for writing the edge function.

In addition to customizing your own functions, you can also choose from the ready-to-use ones provided by Azion or Independent Software Vendors (ISV). Browse the Azion Marketplace catalog on Real-Time Manager (RTM).

**JavaScript Runtime Environment**

By using the JavaScript Runtime Environment, Edge Functions written by the user go directly into effect without undergoing an internal review because the code runs on limited to isolated resources.

You can modify a function’s behavior without changing the code itself. This means you don’t need to hard-code the function. In the Arguments (Args) tab, you can insert JSON parameters by internal code functions. This format allows you to designate variable alternatives to your code that can contain details about a function and request.

Arguments are dynamic values that can change the Edge Functions running at the edge nodes.

You can use the same function in different Edge Applications.

For example, if you build an edge function with an argument that controls whether the code needs to send data to Amazon S3 bucket, and in a particular edge application you determine true, at the Functions Instance, in the Args, the function will generate a post for an S3 so the results of the request are kept.

Structure: arguments are always JSON structures that will be stored in a function configuration through the Args tab in the functions module.
Instantiating: in order to instantiate Args, use event.args.<ARG_CREATED>. By using this command you will be able to connect to the Args tab to your code. See our examples page.

**Edge Functions Instances**

According to its initiator type, before associating an execution trigger with Edge Function, it must be instantiated in Edge Application or Edge Firewall. With the Edge Functions module enabled, you can instantiate your edge functions for later use in a Rules Engine Rule, through the Functions tab.

Learn more about Edge Functions Instances in the Edge Application and Edge Firewall documentation.

**Edge Functions Metrics**

We provide real-time information about the performance of your Edge Functions through RTM.

To access the graphs, follow these steps:

1. Log in to Real-Time Manager.
2. Select Products menu > Real-Time Metrics.
3. Select the Edge Functions and the Time Range you want to analyze. Click on the Filter button.
4. You’ll get the total number of invocations per instance of Edge Functions from Edge Firewall, for example.

Read the Real-Time Metrics documentation to learn more about this product.

4. **Step-by-step: creating an Edge Function**

To see your Edge Function in effectively operation you just need to write, instantiate and associate it with a Behavior Run Function, using a Rule in the Rules Engine.

1. Log into the RTM. On the Products Menu, click on Edge Functions.
2. Click on Add Function to add a new Edge Function.
3. Name your function in the Edge Function Name field to be able to save your settings.
4. In Language, select JavaScript. Copy the following example to the Code tab field.

```javascript
async function handleRequest(request) {
  return new Response("Hello World!",
    {
        status:200
    })
}
addEventListener("fetch", event => {
  event.respondWith(handleRequest(event.request))
})
```

In the Function to run field, enter the name of the main function to run in the source code.
Select the Initiator Type, which refers to the type of module where the function will be instantiated and executed. In this example, it refers to Edge Application.
Click on Save to save your settings. You return to the Edge Functions home page, where you see your list of Edge Functions.
Then, access the Products menu, on the top left. Select an Edge Application from your list.
On the Main Settings tab, enable the Edge Functions module in the Edge Application Modules section.
On the Rules Engine tab, create or edit a Rule and in the Behavior section, in the Then field, select Run Function and associate it with the desired Edge Function.

Example of response when running the Behavior Run Function:

Hello World!

Use RTM to check on your metrics. For example, when you want to see the number of Invocations of Edge Functions instances.

Fields marked with an asterisk are required.

**Edge Functions with multiple files**

Edge Functions work with a single JavaScript (.js) file. In case your Edge Functions have more than one file or use JavaScript modules, you'll need to bundle those files.

One of the ways to proceed is to use Webpack, which allows you to bundle JavaScript files into a single file.

Only JavaScript files are supported.

We don't support Node/Deno API native, so your code must solve all dependencies.

Learn more about Azion's Runtime API.

**Example:**

If you have an Edge Function that has a module to fetch data:

The `index.js` has the event listener and imports modules.
The `modules` folder has all modules that are required by your function.
The `webpack.config.js` has the configuration of how to bundle your function.

**Requirements:**

- NodeJS.
- webpack-cli.

**Bundle and Upload:**

After you code your function, you need to bundle it using the following command:

```bash
webpack-cli --config webpack.config.js
```

It will generate a directory called dist with a single file called main.js. You need to copy the content of this file and paste it into the RTM.

File structure:

```bash
your_function/
    modules/
        data.js
    index.js
    webpack.config.js
```

Content:

index.js

```javascript

import fetchData from "./modules/data"

addEventListener("fetch", (event) => {
    event.respondWith(fetchData())
})

```


modules/data.js:

```javascript
async function fetchData() {
    let data = await fetch("https://httpbin.org/get?username=azionuser&name=Azion&last_login=2021-03-10")
    let json = await data.json()
    return new Response(JSON.stringify(json["args"]), {"status": 200})
}

export default fetchData

```

webpack.config.js:

The target must be "webworker" and the mode must be "production".

```javascript
module.exports = {
    target: "webworker",
    entry: "./index.js",
    mode: "production",
}
```
Generated file:

dist/main.js:

```javascript
(()=>{"use strict";addEventListener("fetch",(t=>{t.respondWith(async function(){let t=await fetch("https://httpbin.org/get?username=azionuser&name=Azion&last_login=2021-03-10"),e=await t.json();return new Response(JSON.stringify(e.args),{status:200})}())}))})();
```
Activating your Settings:

You will find the following buttons at the bottom of the screen:

Active: This option enables or disables your settings on the system.
Cancel: With this option, you return to the Edge Functions home page, discarding your edits.
Save: Once your selections are complete, click on Save to save your settings.
When you save your settings, you return to the Edge Functions home page, where you see your list of Edge Functions sorted by these options: name, language, initiator type, last editor, last modified, ref. count, and active. By clicking on the arrows on those tabs, you can also change how your list is displayed.

Related documentation:

Edge Functions Code Editor
Edge Functions and ChatGPT
Azion Preview Deployment
Edge Application — Edge Functions Instances
Edge Application — Rules Engine
Edge Firewall — Edge Functions Instances
Edge Firewall Rules Engine
Edge Functions — JavaScript Runtime APIs
Edge Functions — JavaScript Examples
Debugging
How to run edge functions inside your edge firewall
Edge Functions on Edge Firewall

