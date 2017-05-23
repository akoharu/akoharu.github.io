---
layout: post
title: "Angular 4 forms : Template Driven Forms"
quote : Template Driven Forms.
date: "2017-04-10 23:27:57 +0700"
---

Angular 4 forms can be implemented using two ways. Template driven and model driven. I will show you how to work with forms in angular 4 using template driven approach.

# Create an initial HTML form template

{% highlight ruby %}
<form #loginForm="ngForm" (ngSubmit)="onLogin(loginForm.value)" *ngIf="!auth.loggedIn()">
    <div class="card card-login card-hidden">
        <div class="card-header text-center" data-background-color="rose">
            <h4 class="card-title">Login</h4>
        </div>
        <div class="card-content">
            <div class="input-group">
                <span class="input-group-addon">
                                                <i class="material-icons">fingerprint</i>
                                            </span>
                <div class="form-group label-floating">
                    <label class="control-label">ID</label>
                    <input type="text" class="form-control" name="idUser" ngModel>
                </div>
            </div>
            <div class="input-group">
                <span class="input-group-addon">
                                                <i class="material-icons">lock_outline</i>
                                            </span>
                <div class="form-group label-floating">
                    <label class="control-label">Password</label>
                    <input type="password" class="form-control" name="password" ngModel>
                </div>
            </div>
        </div>
        <div class="footer text-center">
            <button type="submit" class="btn btn-rose btn-simple btn-wd btn-lg">Login</button>
        </div>
    </div>
</form>
{% endhighlight %}

<blockquote>You need one more addition to display the data. Declare a template variable for the form. Add the form tag with #loginForm="ngForm".
<br><br>
<b>Add ngModel directive</b> <br>
The NgForm directive supplements the form element with additional features. It holds the controls you created for the elements with an <b>ngModel directive</b> and name attribute, and monitors their properties, including their validity. It also has its own valid property which is true only if every contained control is valid.
</blockquote>

# Function for (ngSubmit)

{% highlight ruby %}
  onLogin(credentials){
    console.log(credentials)
  }
{% endhighlight %}

<blockquote>
Dont forget to to import <b>FormsModule</b> in app.module.ts 
</blockquote>
