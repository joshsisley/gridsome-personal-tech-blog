---
title: A Quick Introduction to Observables in Angular
tags: Angular, Programming, RxJS, JavaScript
category: Angular
excerpt: Angular uses observables extensively in both the event system and the HTTP service. This means that it is essential for you to understand how and when to use observables in your Angular project.
created: 2021-02-08
image: ./images/angular_intro.png
image_caption: 
author: author1
---

# What are Observables?

Observables provide support for data sharing between publishers and subscribers in an Angular application. Angular uses observables extensively in both the event system and the HTTP service. This means that it is essential for you to understand how and when to use observables in your Angular project.

**Observables are lazy**
    -  You could think of lazy observables as newsletters. For each subscriber a new newsletter is created. They are then only sent to the people who subscribed, and not to anyone else.


**Observables can have multiple values over time**
    - If you keep that subscription to the newsletter open, you will keep getting a new one every once and a while until you unsubscribe. The sender is the one who decides when you get it but all you have to do is just wait until it comes.

If you come from the world of promises the concept of having multiple values over time is a key difference as promises always return only one value. Another important concept and key difference is that observables are cancelable. If you don’t want to get that newsletter anymore, you can simply unsubscribe. With promises this is different, you can’t cancel a promise. If the promise is handed to you, then the process that will produce the promise’s resolution is already underway. Wrapping your head around observables can be challenging at first, therefore I will do my best to try and simplify it with a basic example below.


# Observables in HTTP Requests

One of the first places that you will encounter the use of Observables in Angular is going to be when setting up an HTTP request. So lets take a look at an example:

&nbsp;


```ts
import { Observable } from "rxjs/Rx"
import { Injectable } from "@angular/core"
import { Http, Response } from "@angular/http"

@Injectable()
export class UserService {

    constructor(
        public http: Http
    ) {}

    fetchUsers() {
        return this.http.get("/api/users").map((res: Response) => res.json())
    }
}
```

&nbsp;

The above code represents a **`Service`** in Angular that will make an HTTP call to get the users from your API endpoint. The **`fetchUsers()`** method is going to end up returning an observable that the component will then be able to subscribe to in order to receive the data. Below are two examples of how we could go about subscribing to the above services' method and displaying the user list:


&nbsp;


### Option 1
```ts
import { Component } from "@angular/core"
import { UserService } from "../services/user.service"

@Component({
    selector: "user-list",
    templateUrl:  "./user-list.component.html",
})

export class UserList {

    public users = []

    constructor(
        private userService: UserService,
    ) {}

    // Make a call to fetch the users on init of the component
    // We manually subscribe to the user service method and set the users
    // in our callback
    ngOnInit() {
        this.userService.fetchUsers().subscribe(users => {
            this.users = users
        })
    }
}
```

In the HTML it would then look like this:
```html
<ul class="user__list" *ngIf="users.length">
    <li class="user" *ngFor="let user of users">
        {{ user.name }}
    </li>
</ul>
```


This example is pretty straight forward but requires you to manually subscribe to the returned **`Observable`** from the service. In the next example, I will show you how we can go about using the observable without having to manually subscribe.

&nbsp;
     

### Option 2
```ts
import { Component } from "@angular/core"
import { Observable } from "rxjs/Rx"
import { UserService } from "../services/user.service"

@Component({
    selector: "user-list",
    templateUrl:  "./user-list.component.html",
})

export class UserList {

    public users$: Observable<any[]>

    constructor(
        private client: HttpClient,
    ) {}

    // The fetchUsers method returns an observable
    // which we then assign to the users$ property of our class
    public ngOnInit() {
        this.users$ = this.client.fetchUsers()
    }
}
```

The HTML would then look like this:
```html
<!-- Check if the user list exists and if the length is gt 0 -->
<ul class="user__list" *ngIf="(users$ | async).length">
    <li class="user" *ngFor="let user of users$ | async">
        {{ user.name }}
    </li>
</ul>
```

The one big difference that you will notice with this example is that inside of the HTML you will see the **`async`** pipe. So what does the async pipe do exactly? The async pipe will subscribe to an **Observable** and return the latest value it has emitted. In our example, that would mean that the **`users$`** observable will return the latest list of users which we can then loop through and display to the user. This is all done without having to ever manually subscribe in our component.


# Conclusion

This post should hopefully have given you a little bit better understanding of how a basic Observable works. The next step in understanding Observables in Angular, is to dive into the power of RxJS and all the helper functions that it provides. There is so much more to learn when it comes to Observables and using RxJS in Angular. In future articles I will start to go over more complex examples of using RxJS as well as creating your own observables. Until then, I encourage you to keep reading more about the basics of Observables and practicing some of these basic concepts in your projects.


&nbsp;

