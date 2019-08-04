# Prerequisites
## Tools
* [Download and install NodeJS](https://nodejs.org/) - LTS recommended
* Open a terminal and run `npm install -g @angular/cli` to install Angular CLI globally
* Install Firebase CLI globsllx using `npm install -g firebase-tools`
* Run `firebase login` to connect your account to the Firebase CLI. This will allow you to easily deploy your application in the future.


## Firebase
* [Create a new Firebase Project](https://console.firebase.google.com/)
* In your Firebase console, setup Authentication, Hosting and Database in preferred region
* Copy the Firebase config values (Project Settings -> Your apps -> Firebase SDK snippet) into `/src/environments/environment.ts`. It should look like this:

```javascript
export const environment = {
  production: false,
  firebase: {
    apiKey: '<your-key>',
    authDomain: '<your-project-authdomain>',
    databaseURL: '<your-database-URL>',
    projectId: '<your-project-id>',
    storageBucket: '<your-storage-bucket>',
    messagingSenderId: '<your-messaging-sender-id>'
  }
};
```


# Quick Demo Setup
## Local Setup
* In the project folder (where package.json is located), run `npm install` to install all dependencies
* After initialisation, run `npm run start` to run the project locally
## Firebase
* To connect the project to your Firebase project, run `firebase init` 
* You'll probably want Firestore + Hosting as features
* Select your previously created project as default
* Set 'dist' as your public directory (important as angular builds into 'dist')
* If you set up everything correctly, you can now easily build & deploy your application to Firebase using `npm run deploy`




# New project setup (Full)
* Run `ng new awesome-project` to create your new project
* Run `npm install firebase @angular/fire --save` to install Firebase and AngularFire
* In your `/src/app/app.module.ts`, initialize AngularFire import required modules.



```javascript
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { AppComponent } from './app.component';
import { AngularFireModule } from '@angular/fire';
import { AngularFirestoreModule } from '@angular/fire/firestore';
import { AngularFireStorageModule } from '@angular/fire/storage';
import { AngularFireAuthModule } from '@angular/fire/auth';
import { environment } from '../environments/environment';

@NgModule({
  imports: [
    BrowserModule,
    AngularFireModule.initializeApp(environment.firebase), // imports firebase/app needed for everything
    AngularFirestoreModule, // imports firebase/firestore, only needed for database features
    AngularFireAuthModule, // imports firebase/auth, only needed for auth features,
    AngularFireStorageModule // imports firebase/storage only needed for storage features
  ],
  declarations: [ AppComponent ],
  bootstrap: [ AppComponent ]
})
export class AppModule {}
```




# Further Reading
[AngularFire Setup](https://github.com/angular/angularfire2/blob/master/docs/install-and-setup.md)

[Deploying Angular App to Firebase](https://scotch.io/tutorials/deploying-an-angular-cli-app-to-production-with-firebase)

