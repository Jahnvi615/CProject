<div class="pricing-container">
    <h2>Pricing</h2>
    <p class="sub-text">
      Sign-up in less than 30 seconds. Try out our 7 days risk free trial. <br />
      Upgrade at anytime, no questions, no hassle.
    </p>
    <button class="popular-btn">Popular Plan</button>


      

  
    <div class="plan-cards">
      <div class="card" *ngFor="let plan of plans" [ngClass]="{ 'highlighted': plan.type === 'Standard' }">
        <h3>{{ plan.type }}</h3>
        <h1><span class="dollar">$</span>{{ plan.price }}<span class="duration">/mo</span></h1>
        <ul>
          <li *ngFor="let feature of plan.features">✔ {{ feature }}</li>
        </ul>
        <div class="btn-group">
          <button class="view-btn" (click)="openPopup(plan)">View Details</button>
         <button class="add-btn"(click)=" openTermsPopup()">Add</button>
        </div>
      </div>
    </div>
  
    <div class="popup" [class.show]="showPopup">
      <div class="popup-content">
        <h3>{{ selectedPlan?.type }} Plan Details</h3>
        <ul>
          <li *ngFor="let feature of selectedPlan?.features">✔ {{ feature }}</li>
        </ul>
        <button class="close-btn" (click)="closePopup()">Close</button>
      </div>
    </div>
  </div>
  
  <div
  class="floating-cart"
  id="draggable-cart"
  (mousedown)="startDrag($event)"
>
  <h4>Premium Summary</h4>
  <p>Selected Plan: <strong>Standard</strong></p>
  <p>Price: <strong>$99/mo</strong></p>
  <button class="checkout-btn">Proceed</button>
</div>


<div class="terms-popup" *ngIf="showPopup">
  <div class="popup-box">
    <h2><i class="fab fa-twitter"></i> Twitter Terms of Service</h2>

    <div class="terms-content">
      <p><strong>If you live in the United States,</strong> the Twitter User Agreement comprises these 
        <a href="#">Terms of Service</a>, our <a href="#">Privacy Policy</a>, the <a href="#">Twitter Rules</a> and all incorporated policies.
      </p>
      <p><strong>If you live in the European Union or otherwise outside the United States,</strong> the Twitter User Agreement comprises these 
        <a href="#">Terms of Service</a>, our <a href="#">Privacy Policy</a>, the <a href="#">Twitter Rules</a> and all incorporated policies.
      </p>

      <h3>Terms of Services</h3>
      <p><strong>If you live in the United States</strong></p>
      <p>These Terms of Service govern your access to and use of our services, including websites, apps, emails, notifications, and more...</p>

      <h4>1. Who May Use the Services</h4>
      <p>You may use the Services only if you agree to form a binding contract...</p>
    </div>

    <div class="terms-actions">
      <label class="agree-checkbox">
        <input type="checkbox" [(ngModel)]="agreedToTerms" />
        I agree to the Terms
      </label>
      <div class="button-group">
        <button (click)="downloadQuote()">Download</button>
        <button (click)="confirmDecline()">Decline</button>
        <button [disabled]="!agreedToTerms" (click)="acceptTerms()">Accept</button>
      </div>
    </div>
  </div>
</div>




.pricing-container {
    padding: 2rem;
    text-align: center;
    background: white;
    position: relative;
  }
  
  h2 {
    color: #7a5af8;
    font-size: 2rem;
    font-weight: bold;
  }
  
  .sub-text {
    font-size: 0.9rem;
    color: #777;
    margin: 0.5rem 0 1rem;
  }
  
  .popular-btn {
    background: #7a5af8;
    color: white;
    border: none;
    padding: 0.5rem 1.2rem;
    border-radius: 8px;
    margin-bottom: 1.5rem;
    font-weight: bold;
  }
  
  .plan-cards {
    display: flex;
    gap: 1.5rem;
    justify-content: center;
    flex-wrap: wrap;
  }
  
  .card {
    background: #f9f9f9;
    padding: 1.5rem;
    border-radius: 16px;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
    width: 280px;
    transition: 0.3s ease;
  }
  
  .card.highlighted {
    border: 2px solid #7a5af8;
    background: white;
  }
  
  .card h3 {
    font-size: 1.2rem;
    margin-bottom: 0.5rem;
  }
  
  .card h1 {
    font-size: 2rem;
    margin: 0.5rem 0;
  }
  
  .card .dollar {
    font-size: 1.5rem;
  }
  
  .card .duration {
    font-size: 1rem;
    color: #888;
  }
  .card:hover
  {
    border: 2px solid #7a5af8;
    background: white;
    width: 350px;
  }
  .card ul {
    list-style: none;
    padding: 0;
    margin: 1rem 0;
    text-align: left;
  }
  
  .card ul li {
    margin-bottom: 0.5rem;
    font-size: 0.9rem;
    color: #333;
  }
  
  .btn-group {
    display: flex;
    justify-content: space-between;
  }
  
  .view-btn,
  .add-btn {
    padding: 0.5rem 0.8rem;
    border: none;
    border-radius: 8px;
    font-weight: bold;
    cursor: pointer;
    flex: 1;
    margin: 0 0.25rem;
  }
  
  .view-btn {
    background: #e0e0ff;
    color: #7a5af8;
  }
  
  .add-btn {
    background: #7a5af8;
    color: white;
  }
  
  .popup {
    position: fixed;
    top: 0;
    left: -100%;
    width: 280px;
    height: 100%;
    background: white;
    box-shadow: 4px 0 10px rgba(0, 0, 0, 0.15);
    transition: left 0.4s ease;
    z-index: 1000;
    padding: 1.5rem;
  }
  
  .popup.show {
    left: 0;
  }
  
  .popup-content h3 {
    font-size: 1.2rem;
    margin-bottom: 1rem;
    color: #7a5af8;
  }
  
  .popup-content ul {
    list-style: none;
    padding-left: 0;
    text-align: left;
  }
  
  .popup-content li {
    margin-bottom: 0.5rem;
  }
  
  .close-btn {
    background: #ff4b5c;
    color: white;
    border: none;
    padding: 0.5rem 1rem;
    margin-top: 1rem;
    border-radius: 8px;
    cursor: pointer;
  }
  
  @media (max-width: 768px) {
    .plan-cards {
      flex-direction: column;
      align-items: center;
    }
  
    .card {
      width: 90%;
    }
  
    .popup {
      width: 100%;
    }
  }

  .floating-cart {
  position: fixed;
  top: 150px;
  right: 30px;
  width: 220px;
  background: #fff;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
  border-radius: 12px;
  padding: 16px;
  z-index: 999;
  transition: all 0.01s ease-in-out;
}

.floating-cart h4 {
  font-size: 18px;
  margin-bottom: 10px;
  color: #333;
}

.floating-cart p {
  font-size: 14px;
  margin: 6px 0;
  color: #444;
}

.checkout-btn {
  width: 100%;
  padding: 8px;
  background-color: #6c63ff;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
}

.checkout-btn:hover {
  background-color: #574be9;
}

.floating-cart {
    position: fixed;
    top: 100px;
    right: 30px;
    width: 220px;
    background: #b6b4da;
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
    border-radius: 12px;
    padding: 16px;
    z-index: 999;
    cursor: move;
    user-select: none;
  }
  
  .floating-cart h4 {
    font-size: 18px;
    margin-bottom: 10px;
    color: #333;
  }
  
  .floating-cart p {
    font-size: 14px;
    margin: 6px 0;
    color: #444;
  }
  
  .checkout-btn {
    width: 100%;
    padding: 8px;
    background-color: #6c63ff;
    color: white;
    border: none;
    border-radius: 8px;
    cursor: pointer;
  }
  
  .checkout-btn:hover {
    background-color: #574be9;
  }
  
 /* Pop up  */
 .terms-popup {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  z-index: 9999;
  display: flex;
  justify-content: center;
  align-items: center;
}

.popup-box {
  background: white;
  width: 90%;
  max-width: 700px;
  border-radius: 12px;
  padding: 20px 30px;
  box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
  font-family: 'Segoe UI', sans-serif;
}

.popup-box h2 {
  font-size: 20px;
  color: #1da1f2;
  display: flex;
  align-items: center;
  gap: 8px;
}

.terms-content {
  max-height: 300px;
  overflow-y: auto;
  padding: 15px 0;
  color: #555;
}

.terms-content h3,
.terms-content h4 {
  margin-top: 20px;
  color: #1da1f2;
}

.terms-content a {
  color: #1da1f2;
  text-decoration: none;
}

.agree-checkbox {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 15px;
  font-size: 14px;
}

.terms-actions {
  margin-top: 20px;
}

.button-group {
  display: flex;
  gap: 10px;
  justify-content: flex-end;
}

.button-group button {
  padding: 8px 18px;
  border: none;
  border-radius: 20px;
  cursor: pointer;
  font-weight: 500;
  font-size: 14px;
}

.button-group button:nth-child(1) {
  background: #e8f4fd;
  color: #1da1f2;
}

.button-group button:nth-child(2) {
  background: #fbeaea;
  color: #d93025;
}

.button-group button:nth-child(3) {
  background: #1da1f2;
  color: white;
}

.button-group button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}







import { CommonModule } from '@angular/common';
import { Component } from '@angular/core';
import { FormsModule } from '@angular/forms';

@Component({
  selector: 'app-plan',
  imports:[CommonModule, FormsModule],
  templateUrl: './plan.component.html',
  styleUrls: ['./plan.component.css']
})
export class PlanComponent {
  plans = [
    {
      type: 'Free',
      price: 0,
      features: ['Up to 100 emails per day', 'Unlimited contacts']
    },
    {
      type: 'Standard',
      price: 99,
      features: ['Up to 100,000 emails per day', 'No daily limits', 'Email support']
    },
    {
      type: 'Enterprise',
      price: 399,
      features: ['Up to 1,000,000 emails per day', 'Marketing automation', 'Landing pages', 'Telephone support']
    }
  ];

  showPopup = false;
  selectedPlan: any = null;

  openPopup(plan: any) {
    this.selectedPlan = plan;
    this.showPopup = true;
  }

  closePopup() {
    this.showPopup = false;
  }

  dragging = false;
offsetX = 0;
offsetY = 0;

startDrag(event: MouseEvent) {
  this.dragging = true;
  this.offsetX = event.clientX - (event.target as HTMLElement).getBoundingClientRect().left;
  this.offsetY = event.clientY - (event.target as HTMLElement).getBoundingClientRect().top;

  document.addEventListener('mousemove', this.drag);
  document.addEventListener('mouseup', this.stopDrag);
}

drag = (event: MouseEvent) => {
  if (this.dragging) {
    const cart = document.getElementById('draggable-cart')!;
    cart.style.left = `${event.clientX - this.offsetX}px`;
    cart.style.top = `${event.clientY - this.offsetY}px`;
    cart.style.right = 'auto'; // override fixed right
  }
};

stopDrag = () => {
  this.dragging = false;
  document.removeEventListener('mousemove', this.drag);
  document.removeEventListener('mouseup', this.stopDrag);
};

showQuotePopup = false;

openQuotePopup(plan: any) {
  this.selectedPlan = plan;
  this.showQuotePopup = true;
}

closeQuotePopup() {
  this.showQuotePopup = false;
}


  agreedToTerms = false;
  showTermsPopup = false;

openTermsPopup() {
  this.showTermsPopup = true;
}

  downloadQuote() {
    // Logic to download the quote
    alert("Quote downloading...");
  }

  confirmDecline() {
    const confirmResult = confirm("Are you sure you want to decline?");
    if (confirmResult) {
      this.showPopup = false;
      setTimeout(() => alert("Your quote has been declined."), 300);
    }
  }

  acceptTerms() {
    if (this.agreedToTerms) {
      this.showPopup = false;
      alert("You have accepted the terms.");
    }
  }

}






----------------------------------------------------------------------------------------------------------------------------------------------------
.dashboard-container {
  display: flex;
  height: 100vh;
  overflow: hidden;
}

/* Sidebar */
.sidebar {
  width: 230px;
  background: #002b80;
  color: white;
  padding: 15px 10px;
  transition: all 0.4s ease;
  display: flex;
  flex-direction: column;
  position: relative;
}

.sidebar.collapsed {
  width: 60px;
}

.sidebar .icon {
  cursor: pointer;
  font-size: 22px;
}

.menu {
  list-style: none;
  padding: 0;
}

.menu li {
  margin-top:30px;
  padding: 12px 10px;
  display: flex;
  align-items: center;
  gap: 10px;
  cursor: pointer;
  transition: background 0.3s ease;
}

.menu li:hover {
  background-color: rgba(255, 255, 255, 0.1);
}

.menu span {
  transition: opacity 0.3s ease;
}

.sidebar.collapsed .menu span {
  display: none;
}

/* User Footer Fixed */
.sidebar-footer {
  position: sticky;
  bottom: 0;
  background: #001f5c;
  padding: 12px 10px;
  color: white;
  border-top: 1px solid rgba(255, 255, 255, 0.2);
}

.sidebar-footer .username {
  font-size: 14px;
}

.sidebar-footer .logout {
  font-size: 13px;
}



  
  /* Main Content */
  .main-content {
    flex-grow: 1;
    background: #f4f4f4;
  }
  
  /* Navbar */
  .navbar {
    display: flex;
    justify-content: space-between;
    background: #002b80;
    padding: 10px;
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
    align-items: center;
    color: white;
  }
  
  .navbar input {
    flex-grow: 1;
    margin-right: 20px;
    padding: 8px;
  }
  
  .fa-solid {
    height: 20px;
    width: 20px;
  }
  
  /* User Info */
  .user-info {
    display: flex;
    align-items: center; /* Vertically aligns icon and text */
    gap: 10px; /* Spacing between elements */
  }
  
  .user-dropdown {
    display: flex; /* Inline display for icon and username */
    align-items: center; /* Centers icon and username vertically */
    position: relative;
    gap: 5px; /* Adjust spacing between icon and username */
  }
  
  .profile-icon {
    font-size: 30px;
    cursor: pointer;
  }
  
  .user-name {
    font-weight: bold;
    cursor: pointer;
  }
  
  /* Dropdown Menu */
  .dropdown-menu {
    display: none;
    position: absolute;
    top: 100%; 
    right: 0;
    background-color: white;
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.2);
    border-radius: 5px;
    padding: 10px 0;
    list-style: none;
    z-index: 10;
    color: black;
    text-align: left;
    width: 150px;
  }
  
  .dropdown-menu li {
    padding: 10px;
    cursor: pointer;
  }
  
  .dropdown-menu li a {
    text-decoration: none;
    color: black;
  }
  
  .dropdown-menu li:hover {
    background-color: rgba(0, 43, 128, 0.1);
  }
  
  /* Show Dropdown on Hover */
  .user-dropdown:hover .dropdown-menu {
    display: block;
  }
  
  .btn {
    background-color: orange;
    color: white;
  }
  
  @media (max-width: 768px) {
    .sidebar {
      position: absolute;
      height: 100%;
    }
  
    .navbar {
      flex-direction: column;
    }
  }
  




<div class="dashboard-container d-flex">
  <!-- Sidebar -->
  <div [class.collapsed]="isCollapsed" class="sidebar d-flex flex-column">
    <!-- Top logo and toggle icon -->
    <div class="logo d-flex align-items-center justify-content-between">
      <div class="d-flex align-items-center">
        <i class="fas fa-bars-staggered icon me-2" (click)="toggleSidebar()"></i>
        <img *ngIf="!isCollapsed" src="/assests/img/logo1.jpg" alt="Logo" style="height:30px; width:45px;" />
        <span *ngIf="!isCollapsed" class="brand fs-5 fw-bold ms-2">
          Safe<span style="color:orange;">Guard</span>
        </span>
      </div>
    </div>

    <!-- Scrollable Menu -->
    <ul class="menu flex-grow-1 overflow-auto mt-3">
      <li><i class="fas fa-user"></i> <span *ngIf="!isCollapsed">Profile</span></li>
      <li><i class="fas fa-chart-line"></i> <span *ngIf="!isCollapsed">Flows</span></li>
      <li><i class="fas fa-calendar-check"></i> <span *ngIf="!isCollapsed">My Quotes</span></li>
    </ul>

    <!-- Bottom user profile -->
    <div class="sidebar-footer d-flex align-items-center ">
      <i class="fas fa-user-circle fs-4 ms-5"></i>
      <div *ngIf="!isCollapsed">
        <div class="username fw-bold">{{ username }}</div>
        <div class="logout text-danger" style="cursor:pointer;" (click)="logout()">Logout</div>
      </div>
    </div>
  </div>

  



  <!-- Main Content -->
  <div class="main-content">
    <!-- Navbar -->
    <div class="navbar">
      <h3 class="pe-3">SafeGuard</h3>
      <input type="text" placeholder="Search by Quote Policy Number..." />
      <div class="user-info">
        <i class="fa-solid fa-bell"></i>
        <div class="user-dropdown">
          <i class="fas fa-user-circle profile-icon"></i>
          <span class="user-name">{{ username }}</span>
          <!-- Dropdown menu -->
          <ul class="dropdown-menu">
            <li><a routerLink="/about">About</a></li>
            <li><a routerLink="/profile">Profile</a></li>
            <li><a routerLink="/settings">Settings</a></li>
            <li><a href="#" (click)="logout()">Log Out</a></li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</div>















import { Component } from '@angular/core';
import { CommonModule } from '@angular/common';
import { SharedService } from '../shared.service';

@Component({
  selector: 'app-navbar',
  imports: [CommonModule],
  templateUrl: './navbar.component.html',
  styleUrls: ['./navbar.component.css'] // Fixed to 'styleUrls' (plural)
})
export class NavbarComponent {
  title = 'Capstone_Project';
  isCollapsed: boolean = true; // Sidebar state
  username: string = ''; // Dynamic username from the service

  constructor(private sharedService: SharedService) {
    // Subscribe to sidebar collapse/expand state from shared service
    this.sharedService.isCollapsed$.subscribe(value => {
      this.isCollapsed = value;
    });

    this.fetchUsername(); // Fetch the username on component initialization
  }

  toggleSidebar() {
    this.sharedService.toggleSidebar(); // Toggle the sidebar state
  }

  fetchUsername() {
    // Simulate fetching the username from a database or API
    this.username = 'Jahnvi Goyal'; // Replace with your actual service call
  }

  logout() {
    console.log('User logged out'); // Add actual logout logic here
  }
}











---------------------------------------------------------------------------------------------------
<!-- dashboard.component.html -->
<app-navbar></app-navbar>

<div class="dashboard" [ngClass]="{ 'collapsed': isCollapsed }">
  <h2>Quotes for 2025-Apr</h2>

  <div class="status-buttons">
    <button class="pending">Pending Request (0)</button>
    <button class="triggered">System Triggered (0)</button>
  </div>

  <div class="stats">
    <div class="stat-box">
      <h3>0</h3>
      <a [routerLink]="['/forms']">Get Quote</a>
    </div>
    <div class="stat-box">
      <h3><i class="fa fa-user"></i></h3>
      <p>Total Quotes</p>
    </div>
    <div class="stat-box">
      <h3>3</h3>
      <p>Previous Quotes</p>
    </div>
  </div>

  <app-footer></app-footer>
</div>



/* Base Container */
.dashboard-container {
    display: flex;
    height: 100vh;
    overflow: hidden;
  }
  
  /* Sidebar */
  .sidebar {
    width: 230px;
    background: #002b80;
    color: white;
    padding: 15px 10px;
    transition: all 0.4s ease;
    display: flex;
    flex-direction: column;
    position: relative;
  }
  
  .sidebar.collapsed {
    width: 60px;
  }
  
  .sidebar .icon {
    cursor: pointer;
    font-size: 22px;
    margin-bottom: 10px;
  }
  
  .menu {
    list-style: none;
    padding: 0;
  }
  
  .menu li {
    padding: 12px 10px;
    display: flex;
    align-items: center;
    gap: 10px;
    cursor: pointer;
  }
  
  .menu span {
    transition: opacity 0.3s ease;
  }
  
  .sidebar.collapsed .menu span {
    display: none;
  }
  
  .sidebar-footer {
    position: sticky;
    bottom: 0;
    background: #001f5c;
    padding: 12px 10px;
    color: white;
    border-top: 1px solid rgba(255, 255, 255, 0.2);
  }
  
  /* Main Content */
  .main-content {
    flex-grow: 1;
    background: #f4f4f4;
  }
  
  /* Navbar */
  .navbar {
    display: flex;
    justify-content: space-between;
    background: #002b80;
    padding: 10px;
    color: white;
    align-items: center;
  }
  
  .navbar input {
    flex-grow: 1;
    margin-right: 20px;
    padding: 8px;
  }
  
  .user-info {
    display: flex;
    align-items: center;
    gap: 10px;
  }
  
  .user-dropdown {
    position: relative;
    display: flex;
    align-items: center;
    gap: 5px;
  }
  
  .profile-icon {
    font-size: 30px;
    cursor: pointer;
  }
  
  .user-name {
    font-weight: bold;
    cursor: pointer;
  }
  
  .dropdown-menu {
    display: none;
    position: absolute;
    top: 100%;
    right: 0;
    background-color: white;
    color: black;
    width: 150px;
    border-radius: 5px;
    list-style: none;
    padding: 10px 0;
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.2);
    z-index: 100;
  }
  
  .dropdown-menu li {
    padding: 10px;
    cursor: pointer;
  }
  
  .dropdown-menu li:hover {
    background: rgba(0, 43, 128, 0.1);
  }
  
  .user-dropdown:hover .dropdown-menu {
    display: block;
  }
  
  /* Dashboard Panel */
  .dashboard {
    position: absolute;
    top: 60px; /* height of navbar */
    left: 230px; /* width of expanded sidebar */
    width: calc(100% - 230px);
    padding: 20px;
    transition: all 0.3s ease;
    box-sizing: border-box;
  }
  
  .dashboard.collapsed {
    left: 100px; /* 60px sidebar + 40px buffer */
    width: calc(100% - 100px);
  }
  
  .dashboard h2 {
    margin-top: 10px;
    padding-left: 10px;
  }
  
  .status-buttons {
    display: flex;
    gap: 10px;
    padding-left: 10px;
  }
  
  .pending,
  .triggered {
    background: orange;
    border: none;
    padding: 8px 14px;
    color: white;
    border-radius: 5px;
    margin-top: 15px;
    font-weight: bold;
    cursor: pointer;
  }
  
  .stats {
    display: flex;
    gap: 20px;
    margin-top: 40px;
    flex-wrap: wrap;
  }
  
  .stat-box {
    background: white;
    padding: 30px;
    border-radius: 10px;
    text-align: center;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
    flex: 1 1 30%;
    min-width: 220px;
  }
  
  .stat-box h3 {
    margin-bottom: 10px;
    font-size: 28px;
  }
  
  .stat-box p {
    font-size: 16px;
    color: #333;
  }
  
  /* Responsive */
  @media (max-width: 768px) {
    .sidebar {
      position: absolute;
      height: 100%;
    }
  
    .navbar {
      flex-direction: column;
    }
  
    .dashboard,
    .dashboard.collapsed {
      left: 100px;
      width: calc(100% - 100px);
    }
  
    .stat-box {
      flex: 1 1 100%;
    }
  }
  










import { Component } from '@angular/core';
import { CommonModule } from '@angular/common';
import { NavbarComponent } from '../navbar/navbar.component';
import { RouterLink } from '@angular/router';
import { SharedService } from '../shared.service';
import { FooterComponent } from '../footer/footer.component';
 
@Component({
  selector: 'app-dashboard',
  imports: [CommonModule,NavbarComponent,RouterLink, FooterComponent],
  templateUrl: './dashboard.component.html',
  styleUrl: './dashboard.component.css'
})
export class DashboardComponent {
  isCollapsed: boolean = true;
 
  constructor(private sharedService: SharedService) {
    // Subscribe to changes in the isCollapsed property
    this.sharedService.isCollapsed$.subscribe(value => {
      this.isCollapsed = value;
    });
  }
}






----------------------------------------------------------------------------------------

<div class="container-fluid d-flex vh-100">
  <!-- Left section for image/logo -->
  <div class="col-md-6 p-0 d-flex flex-column bg-right s">
    <div class="d-flex flex-column justify-content-center align-items-center flex-grow-1">
      <img src="/assests/img/logo13.jpg" alt="Logo" class="logo" style="height:140px;" />
      <p class="text-center fw-bold" style="font-size: 45px; color:white;">
        Safe<span style="color: rgb(234, 111, 49);">Guard</span>
      </p>
    </div>
    <p class="text-light text-center mb-3">&copy; 2025 SafeGuard. All rights reserved.</p>
  </div>

  <!-- Right section for forms -->
  <div class="col-md-6 d-flex flex-column justify-content-center align-items-center bg-light">
    <!-- Login Form -->
    <div *ngIf="!isSignup" class="text-center w-75">
      <h1 class="mb-4 fw-bold">Login</h1>
      <div class="input-group mb-3">
        <span class="input-group-text"><i class="fa fa-user"></i></span>
        <input type="text" class="form-control" placeholder="Username" [(ngModel)]="username" />
      </div>
      <div class="input-group mb-3">
        <span class="input-group-text"><i class="fa fa-lock"></i></span>
        <input type="password" class="form-control" placeholder="Password" [(ngModel)]="password" />
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
          placeholder="Enter key"
        />
      </div>
      
      <a [routerLink]="['/dashboard']">
        <button class="btn btn-login w-100 fw-bold mb-3" (click)="login()">Login</button>
      </a>
      <p class="fs-6 d-flex justify-content-center align-items-center gap-2">
        Don't have an account?
        <button class="btn btn-register p-0 fw-bold" (click)="toggleSignup()">Register</button>
      </p>
      <div class="mt-4">
        <a href="/support" class="btn btn-link text-decoration-underline">Support</a>
        <a href="/about" class="btn btn-link text-decoration-underline">About</a>
      </div>
    </div>
    <!-- Signup Form -->
    <div *ngIf="isSignup" class="text-center w-75">
      <h1 class="mb-4 fw-bold">Sign Up</h1>
      <div class="input-group mb-3">
        <span class="input-group-text"><i class="fa fa-user"></i></span>
        <input type="text" class="form-control" placeholder="Full Name" [(ngModel)]="fullName" />
      </div>
      <div class="input-group mb-3">
        <span class="input-group-text"><i class="fa fa-envelope"></i></span>
        <input type="email" class="form-control" placeholder="Email" [(ngModel)]="email" />
      </div>
      <div class="input-group mb-3">
        <span class="input-group-text"><i class="fa fa-lock"></i></span>
        <input type="password" class="form-control" placeholder="Password" [(ngModel)]="password" />
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
      <a [routerLink]="['/dashboard']">
        <button class="btn btn-signup w-100 fw-bold mb-3" (click)="signup()">Sign Up</button>
      </a>
      <p class="fs-6 d-flex justify-content-center align-items-center gap-2">
        Already have an account?
        <button class="btn btn-register p-0 fw-bold"(click)="toggleSignup()">Login</button>
      </p>
      <div class="mt-4">
        <a href="/support" class="btn btn-link  text-decoration-underline">Support</a>
        <a href="/about" class="btn btn-link  text-decoration-underline">About</a>
      </div>
    </div>
  </div>
</div>










/* Left Section Styling */
.logo-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  flex-grow: 1;
}

.bg-right {
  background-color: #002b80;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
}

.text-light {
  color: white;
  font-size: 14px;
  margin-bottom: 15px;
}

/* Right Section Styling */
.input-group-text {
  border: none;
}

.form-control:focus {
  border-color: black;
  box-shadow: none;
}

.btn-login {
  background-color: orange;
  color: white;
  /* text-decoration: underline; */
}

.btn-login:hover {
  color: white;
  text-decoration: underline;
  background-color: orange;
}

.btn-signup {
  background-color: orange;
  color: white;
  
}

.btn-signup:hover {
  color: white;
  text-decoration: underline;
  background-color: orange;
}

.btn-register {
  color: black;
  text-decoration: underline;
}

.btn-register:hover {
  color: black;
  text-decoration: underline;
}

.btn-link {
  color: #002b80;
  
}

.btn-link:hover {
  color: orange;
  
}
.form-check {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 15px;
  color: #333;
}

.form-check-input {
  width: 18px;
  height: 18px;
  cursor: pointer;
}

.form-check-label {
  cursor: pointer;
}

input[type="password"] {
  max-width: 300px;
}








import { Component } from '@angular/core';
import { CommonModule } from '@angular/common';
import { FormsModule } from '@angular/forms';
import { Router } from '@angular/router';
import { RouterOutlet } from '@angular/router';
import { RouterLink } from '@angular/router';

 
@Component({
  selector: 'app-login-signup',
  imports: [RouterOutlet, CommonModule, FormsModule, RouterLink],
  templateUrl: './login-signup.component.html',
  styleUrls: ['./login-signup.component.css']
})
export class LoginSignupComponent {
  constructor(private router: Router) {}
  isSignup = false;
  fullName: string = '';
  email: string = '';
  username: string = '';
  password: string = '';
  isUnderwriter: boolean = false;
  underwriterKey: string = '';

  

 
  toggleSignup() {
    this.isSignup = !this.isSignup; 
  }
 
  signup() {
    console.log(`Sign Up: ${this.fullName}, ${this.email}, ${this.password}`);
  }
 
  login() {
    console.log(`Login: ${this.username}, ${this.password}`);
    
  }
}













