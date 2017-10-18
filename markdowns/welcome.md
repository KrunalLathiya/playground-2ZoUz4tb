# Angular Form Validation Example Tutorial!
Angular is a platform that makes it easy to build applications with the web. Angular combines declarative templates, dependency injection, an end to end tooling, and integrated best practices to solve development challenges. User actions such as clicking a link, pushing a button, and entering text raise DOM events. Forms are the mainstay of business applications. You use forms to log in, submit a help request, place an order, book a flight, schedule a meeting, and perform countless other data-entry tasks. Improve overall data quality by validating user input for accuracy and completeness.

The source code for this template is on [GitHub](https://github.com/KrunalLathiya/playground-2ZoUz4tb), please feel free to come up with proposals to improve it.

# Step 1: Make one Angular Project.
Install Angular globally by the following command.
```javascript
npm install -g @angular/cli
```
After that, type the following command to make a project.
```javascript
ng new ngValidation
```
Create some files and also install all the dependencies related project.

Next, go to the project root and type the following command to start the server and open the project.
```
cd my-app
ng serve --open
```

# Step 2: Make one form inside app.component.html

We are going to create a form with one input for just basic understanding for Angular Forms.

First, we need to include Reactive Form in <b>app.module.ts</b> file.
```javascript
// app.module.ts

import { ReactiveFormsModule } from '@angular/forms';

imports: [
    BrowserModule, ReactiveFormsModule
  ],
```
Now, we need to write the code to display the form.
```javascript
<!--The whole content below can be removed with the new code.-->
<div style="text-align:center">
  <h1>
    Welcome to {{title}}!!
  </h1>
  <form [formGroup]="angForm" novalidate>
        <div class="form-group">
          <label class="center-block">Name:
            <input class="form-control" formControlName="name">
          </label>
        </div>
        <div *ngIf="angForm.controls['name'].invalid && (angForm.controls['name'].dirty || angForm.controls['name'].touched)" class="alert alert-danger">
            <div *ngIf="angForm.controls['name'].errors.required">
            Name is required.
          </div>
        </div>
  </form>
<p>Form value: {{ angForm.value | json }}</p>
<p>Form status: {{ angForm.status | json }}</p>
</div>
```
Also, we need to update the <b>app.component.ts</b> file.
```javascript
// app.component.ts

import { Component } from '@angular/core';
import { FormGroup,  FormBuilder,  Validators } from '@angular/forms';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'Angular Form Validation Tutorial';
   angForm: FormGroup;
   constructor(private fb: FormBuilder) {
    this.createForm();
  }
   createForm() {
    this.angForm = this.fb.group({
       name: ['', Validators.required ]
    });
  }
}
```
I am going to explain how it is working so bear with me.

# Step 3: Explanation
There are two types of forms in Angular.
1. Template Driven Forms
2. Reactive Forms

## Template Driven Forms
In this kind of form, we can write the forms in <b>Angular template</b> syntax with form syntax directives.

Following are the steps to build template driven forms.

1. Create the component that controls the form.
2. Create a template with the initial form layout.
3. Bind data properties to each form control using the two-way data-binding syntax.
4. Add an attribute to each form-input control.
5. Add custom CSS to provide visual feedback.
6. Show and hide validation-error messages.
7. Handle form submission with ngSubmit.
8. Disable the form’s Submit button until the form is valid.

## Reactive Forms
<b>We have used Reactive Forms in our example in this article. </b>
Reactive forms is an Angular technique for creating forms in a reactive style. Angular reactive forms facilitate a reactive style of programming that favors explicit management of the data flowing between a non-UI data model (typically retrieved from a server) and a UI-oriented form model that retains the states and values of the HTML controls on the screen. Reactive forms offer the ease of using reactive patterns, testing, and validation.

## Example

```javascript
// app.component.ts

import { Component } from '@angular/core';
import { FormGroup,  FormBuilder,  Validators } from '@angular/forms';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'Angular Form Validation Tutorial';
   angForm: FormGroup;
   constructor(private fb: FormBuilder) {
    this.createForm();
  }
   createForm() {
    this.angForm = this.fb.group({
       name: ['', Validators.required ]
    });
  }
}
```
First, we need to import some of the modules from the @angular/forms.
1. FormGroup
2. FormBuilder
3. Validators
Also, we need have imported <b>ReactiveFormsModule</b> in <b>app.module.ts</b> file.
Then, we have taken <b>heroForm</b> of the type of <b>FormGroup</b>.
```javascript
// app.component.ts

constructor(private fb: FormBuilder) {
    this.createForm();
}
```

We have used form builder to handle all the validation. So in that constructor, we are creating a form with the validation rules.
```javascript
// app.component.ts

createForm() {
  this.angForm = this.fb.group({
       name: ['', Validators.required ]
  });
}
```
In this code, I have assigned the Validation rules to the Form Object.
```javascript
<form [formGroup]="angForm" novalidate>
        <div class="form-group">
          <label class="center-block">Name:
            <input class="form-control" formControlName="name">
          </label>
        </div>
        <div *ngIf="angForm.controls['name'].invalid && (angForm.controls['name'].dirty || angForm.controls['name'].touched)" class="alert alert-danger">
            <div *ngIf="angForm.controls['name'].errors.required">
            Name is required.
          </div>
        </div>
  </form>
<p>Form value: {{ angForm.value | json }}</p>
<p>Form status: {{ angForm.status | json }}</p>
```
In this HTML code, I have assigned the global form group object called angForm. This is the top-level object.

All the inner form controls are like the children to them. We can also access its values.

I have used the conditional statement, if a user has touched the input field but not enter the values then, it displays the message. If user blurs the input field without any values then also it gives an error message.

@[Angular Validation Tutorial]({"stubs": ["src/app/app.module.ts", "src/app/app.component.ts", "src/app/app.component.html", "src/index.html"], "command": "./run.sh"})