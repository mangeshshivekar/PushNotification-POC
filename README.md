# Push Notification for React Web App-POC

Push Notifications help user to recieve notifications on the web application.

**User will be able to see notifications for latest offers
**also regarding the order status.**

This POC will take the user enagement to the next level.

**It will reduce the users application journey.**

The solution is like a client server application.

1. Client contionously listens to the notifications sent by the server.
2. For Demo purpose we have chosen Firebase Cloud Messaging (FCM) service as a server to send the notifications.


**The implementation includes below steps**

**Server side steps:

### Step 1: Navigate to https://console.firebase.google.com/.

### Step 2: Create a firebase account using organisation's google ID.

### Step 3: Click on Add Project and enter a project name.

### Step 4: Uncheck google analytics and click on continue.

### Step 5: Click on Web icon </> to register a web application.

### Step 6: click on register,Copy and paste these scripts into the bottom of your <body> tag, but before you use any Firebase services.

### Step 7:The configuration is a JSON object required on the client side for connecting to the server and receiving the messages.


** Client Side steps for a React web Application.

### Step 1: Create a React web application using below link or follow the steps on an existing web application

			https://reactjs.org/docs/getting-started.html

### Step 2: Install firebase dependency by npm install firebase.

### Step 3: Create firebase.js at src level as below.
			import firebase from 'firebase'

			const firebaseConfig = {
				apiKey: "AIzaSyDlNZoBrYNHU6qMSVUjuUq_RebjRNOx8Dk",
				authDomain: "hcl-push-notification.firebaseapp.com",
				databaseURL: "https://hcl-push-notification.firebaseio.com",
				projectId: "hcl-push-notification",
				storageBucket: "hcl-push-notification.appspot.com",
				messagingSenderId: "235955423939",
				appId: "1:235955423939:web:eabce9351db1bcc3cbb076"
			};
			// Initialize Firebase
			firebase.initializeApp(firebaseConfig);


			export default firebase;

### Step 4: Create firebase-messaging-sw.js at the src/public level as below.

			importScripts('https://www.gstatic.com/firebasejs/7.14.2/firebase-app.js');
			importScripts('https://www.gstatic.com/firebasejs/7.14.2/firebase-messaging.js');

			const config = {
				apiKey: "AIzaSyDlNZoBrYNHU6qMSVUjuUq_RebjRNOx8Dk",
				authDomain: "hcl-push-notification.firebaseapp.com",
				databaseURL: "https://hcl-push-notification.firebaseio.com",
				projectId: "hcl-push-notification",
				storageBucket: "hcl-push-notification.appspot.com",
				messagingSenderId: "235955423939",
				appId: "1:235955423939:web:eabce9351db1bcc3cbb076"
			};

			firebase.initializeApp(config);
			const messaging = firebase.messaging();

### Step 5: Import and create firebase instance in App.js 
		
			import firebase from './firebase'



			function App() {
			  React.useEffect(()=>{
				let messaging = firebase.messaging();
				debugger
				  messaging.requestPermission().then(() => {
					return messaging.getToken()
				  }).then(token => {
					console.log('Token : ', token)
				  }).catch(() => {
					console.log('error');
				  })
				},[]);

### Step 6: load the application in the browser.

### Step 7:When the application loads, the Step 5 returns us  a token which can be used to recieve notification on that device.


*** Actual working POC.

1. In the firebase project click on Cloud Messaging Service.

2. Click on send sample message.

3. Enter the message title and description.

4. Click on send.

You will receive notification on the web application.

*** please note user should set the browser to accept notifications else it will not work.

