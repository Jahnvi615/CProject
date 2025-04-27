<div class="container-fluid d-flex vh-100">
  <!-- Left section for image/logo -->
  <div class="col-md-6 p-0 d-flex flex-column bg-right s">
    <div class="d-flex flex-column justify-content-center align-items-center flex-grow-1">
      <img src="/assests/img/logo.png" alt="Logo" class="logo" style="height:100px;" />
      <p class="text-center cname fw-bold" style="font-size: 45px; color:white;">
        Safe<span style="color: orange;">Guard</span>
      </p>
    </div>
    <p class="text-light text-center mb-3">&copy; 2025 SafeGuard. All rights reserved.</p>
  </div>

  <!-- Right section for forms -->
  <div class="col-md-6 d-flex flex-column justify-content-center align-items-center bg-light">
    <!-- Login Form -->
    <div *ngIf="!isSignup" class="text-center w-75">
      <h1 class="mb-4 fw-bold">Login</h1>

      <div class="input-group mb-1">
        <span class="input-group-text"><i class="fa fa-user"></i></span>
        <input type="text" class="form-control" placeholder="Username" required minlength="3" maxlength="20" pattern="[a-zA-Z0-9]+" [(ngModel)]="username" name="loginUsername" #loginUsername="ngModel" />
      </div>
      <div *ngIf="loginUsername.invalid && loginUsername.touched" class="text-danger mb-2 text-start small">
        <div *ngIf="loginUsername.errors?.['required']">Username is required.</div>
        <div *ngIf="loginUsername.errors?.['minlength']">Username must be at least 3 characters.</div>
        <div *ngIf="loginUsername.errors?.['maxlength']">Username cannot exceed 20 characters.</div>
        <div *ngIf="loginUsername.errors?.['pattern']">Username must be alphanumeric only.</div>
      </div>

      <div class="input-group mb-1">
        <span class="input-group-text"><i class="fa fa-lock"></i></span>
        <input type="password" class="form-control" placeholder="Password" required minlength="6" [(ngModel)]="password" name="loginPassword" #loginPassword="ngModel" />
      </div>
      <div *ngIf="loginPassword.invalid && loginPassword.touched" class="text-danger mb-2 text-start small">
        <div *ngIf="loginPassword.errors?.['required']">Password is required.</div>
        <div *ngIf="loginPassword.errors?.['minlength']">Password must be at least 6 characters.</div>
      </div>

      <div class="form-check mb-3 ms-2">
        <input class="form-check-input" type="checkbox" id="underwriterCheckbox" [(ngModel)]="isUnderwriter" name="isUnderwriter" />
        <label class="form-check-label" for="underwriterCheckbox">
          Log in as Underwriter
        </label>
      </div>

      <div *ngIf="isUnderwriter" class="mb-3">
        <input
          type="password"
          id="underwriterKey"
          class="form-control"
          [(ngModel)]="underwriterKey"
          name="underwriterKey"
          required
          minlength="6"
          placeholder="Enter key"
        />
      </div>

      <a>
        <button class="btn btn-login w-100 fw-bold mb-3" (click)="login()">Login</button>
      </a>

      <!-- Show login error message -->
      <p *ngIf="loginErrorMessage" class="text-danger small text-center mb-3">{{ loginErrorMessage }}</p>

      <p class="fs-6 d-flex justify-content-center align-items-center gap-2">
        Don't have an account?
        <button class="btn btn-register p-0 fw-bold" (click)="toggleSignup()">Register</button>
      </p>

      <div class="mt-4">
        <a href="#contact" class="btn btn-link text-decoration-underline">Support</a>
        <a href="/" class="btn btn-link text-decoration-underline">About</a>
      </div>
    </div>

    <!-- Signup Form -->
    <div *ngIf="isSignup" class="text-center w-75">
      <h1 class="mb-4 fw-bold">Sign Up</h1>

      <div class="input-group mb-1">
        <span class="input-group-text"><i class="fa fa-user"></i></span>
        <input type="text" class="form-control" placeholder="Username" required minlength="3" maxlength="20" pattern="[a-zA-Z0-9]+" [(ngModel)]="username" name="signupUsername" #signupUsername="ngModel" />
      </div>
      <div *ngIf="signupUsername.invalid && signupUsername.touched" class="text-danger mb-2 text-start small">
        <div *ngIf="signupUsername.errors?.['required']">Username is required.</div>
        <div *ngIf="signupUsername.errors?.['minlength']">Username must be at least 3 characters.</div>
        <div *ngIf="signupUsername.errors?.['maxlength']">Username cannot exceed 20 characters.</div>
        <div *ngIf="signupUsername.errors?.['pattern']">Username must be alphanumeric only.</div>
      </div>

      <div class="input-group mb-1">
        <span class="input-group-text"><i class="fa fa-envelope"></i></span>
        <input
          type="email"
          class="form-control"
          placeholder="Email"
          required
          [(ngModel)]="email"
          name="signupEmail"
          #signupEmail="ngModel"
          pattern="^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$"
        />
      </div>
      <div *ngIf="signupEmail.invalid && signupEmail.touched" class="text-danger mb-2 text-start small">
        <div *ngIf="signupEmail.errors?.['required']">Email is required.</div>
        <div *ngIf="signupEmail.errors?.['email']">Enter a valid email address.</div>
        <div *ngIf="signupEmail.errors?.['pattern']">Enter a valid email format.</div>
      </div>
      

      <div class="input-group mb-1">
        <span class="input-group-text"><i class="fa fa-lock"></i></span>
        <input type="password" class="form-control" placeholder="Password" required minlength="6" [(ngModel)]="password" name="signupPassword" #signupPassword="ngModel" />
      </div>
      <div *ngIf="signupPassword.invalid && signupPassword.touched" class="text-danger mb-2 text-start small">
        <div *ngIf="signupPassword.errors?.['required']">Password is required.</div>
        <div *ngIf="signupPassword.errors?.['minlength']">Password must be at least 6 characters.</div>
      </div>

      <div class="form-check mb-3 ms-2">
        <input
          class="form-check-input"
          type="checkbox"
          id="underwriterCheckbox"
          [(ngModel)]="isUnderwriter"
          name="isUnderwriter"
        />
        <label class="form-check-label" for="underwriterCheckbox">
          Sign in as Underwriter
        </label>
      </div>

      <div *ngIf="isUnderwriter" class="mb-3">
        <input
          type="password"
          id="underwriterKey"
          class="form-control"
          [(ngModel)]="underwriterKey"
          name="underwriterKey"
          placeholder="Enter key"
        />
      </div>

      <a>
        <button class="btn btn-signup w-100 fw-bold mb-3" (click)="signup()">Sign Up</button>
      </a>

      <!-- Show signup error message -->
      <p *ngIf="signupErrorMessage" class="text-danger small text-center mb-3">{{ signupErrorMessage }}</p>

      <p class="fs-6 d-flex justify-content-center align-items-center gap-2">
        Already have an account?
        <button class="btn btn-register p-0 fw-bold" (click)="toggleSignup()">Login</button>
      </p>

      <div class="mt-4">
        <a href="#contact" class="btn btn-link text-decoration-underline">Support</a>
        <a href="/" class="btn btn-link text-decoration-underline">About</a>
      </div>
    </div>
  </div>
</div>
***********************************************************************************************************************************************************************************************************
import { Component } from '@angular/core';
import { CommonModule } from '@angular/common';
import { FormsModule } from '@angular/forms';
import { Router } from '@angular/router';
import { RouterOutlet } from '@angular/router';
import { RouterLink } from '@angular/router';
import { AuthService } from '../Service/auth-service.service';

@Component({
  selector: 'app-login-signup',
  imports: [RouterOutlet, CommonModule, FormsModule, RouterLink],
  templateUrl: './login-signup.component.html',
  styleUrls: ['./login-signup.component.css']
})
export class LoginSignupComponent {
  constructor(private router: Router, private authservice: AuthService) {}

  isSignup = false;
  fullName: string = '';
  email: string = '';
  username: string = '';
  password: string = '';
  isUnderwriter: boolean = false;
  underwriterKey: string = '';
  
  // Error messages
  loginErrorMessage: string = '';
  signupErrorMessage: string = '';

  toggleSignup() {
    this.isSignup = !this.isSignup;
  }

  signup() {
    this.signupErrorMessage = ''; // Reset error message
    if (!this.username || !this.email || !this.password) {
      this.signupErrorMessage = 'Please fill in all the required fields.';
      return;
    }

    enum Role {
      User,
      Underwriter
    }

    const user = {
      username: this.username,
      password: this.password,
      role: Role.User,
      email: this.email,
      key: 'sdfghjk'
    };

    if (this.isUnderwriter) {
      user.role = Role.Underwriter;
      user.key = this.underwriterKey;
    }

    try {
      console.log(user);
      this.authservice.Register(user).subscribe(d => {
        console.log(d);
        this.isSignup = false;
        this.username = '';
        this.email = '';
        this.password = '';
        this.underwriterKey = '';
      });
    } catch (error) {
      console.log(error);
    }
  }

  login() {
    this.loginErrorMessage = ''; // Reset error message
    if (!this.username || !this.password) {
      this.loginErrorMessage = 'Please enter both username and password.';
      return;
    }

    enum Role {
      User,
      Underwriter
    }

    const user = {
      username: this.username,
      password: this.password,
      role: Role.User,
      email: 'sdfgh',
      key: 'sdfghjk'
    };

    if (this.isUnderwriter) {
      user.role = Role.Underwriter;
      user.key = this.underwriterKey;
    }

    try {
      console.log(user);
      this.authservice.Login(user).subscribe(d => {
        console.log(d);
        this.isSignup = false;
        this.username = '';
        this.password = '';
        this.underwriterKey = '';

        if (this.isUnderwriter) {
          this.router.navigate(['/underwriter']); // Redirect for underwriter
        } else {
          this.router.navigate(['/dashboard']); // Default redirect
        }
      });
    } catch (error) {
      this.loginErrorMessage = 'Login failed. Please try again.';
    }
  }
}
