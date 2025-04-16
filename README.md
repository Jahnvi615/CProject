<div class="container">
    <div class="sidebar">
      <div>
        <h2>Dashboard</h2>
        <ul>
          <li class="active">Home <span class="badge">4</span></li>
          <li>Messages <span class="badge">3</span></li>
          <li>Tasks</li>
          <li>Analytics</li>
          <li>Users</li>
          <li>Settings</li>
        </ul>
      </div>
      <div class="logout">
        <p>Logout</p>
      </div>
    </div>
  
    <div class="main-content">
      <div class="header">
        <h1>Welcome back!</h1>
        <div class="user-info">Jahnvi Goyal</div>
      </div>
  
      <div class="cards">
        <div class="card">
          <h3>Revenue</h3>
          <p>$12,000</p>
          <span class="positive">+8.2%</span>
        </div>
        <div class="card">
          <h3>Orders</h3>
          <p>540</p>
          <span class="negative">-3.1%</span>
        </div>
        <div class="card">
          <h3>Visitors</h3>
          <p>1,230</p>
          <span class="positive">+5.6%</span>
        </div>
      </div>
  
      <div class="grid">
        <div class="card">
          <h3>Earnings</h3>
          <p class="earnings">This Month<br><strong>$9,800</strong></p>
        </div>
        <div class="card social-activity">
          <h3>Social Activity</h3>
          <ul>
            <li>Instagram <span class="amount">$1,200</span></li>
            <li>Facebook <span class="amount">$950</span></li>
            <li>Twitter <span class="amount">$800</span></li>
            <li>LinkedIn <span class="amount">$700</span></li>
          </ul>
        </div>
      </div>
    </div>
  </div>
  *****************************************************************************************************************
body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background-color: #f8f9fd;
    margin: 0;
    padding: 0;
  }
  
  .container {
    display: flex;
    height: 100vh;
  }
  
  .sidebar {
    width: 240px;
    background-color: #0e1e46;
    color: white;
    padding: 30px 20px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }
  
  .sidebar h2 {
    font-size: 24px;
    margin-bottom: 30px;
  }
  
  .sidebar ul {
    list-style-type: none;
    padding: 0;
    margin: 0;
  }
  
  .sidebar li {
    margin: 15px 0;
    cursor: pointer;
    font-size: 16px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    color: #cfd7f2;
  }
  
  .sidebar li.active, .sidebar li:hover {
    color: white;
    font-weight: bold;
  }
  
  .badge {
    background-color: red;
    color: white;
    border-radius: 50%;
    padding: 2px 8px;
    font-size: 12px;
  }
  
  .logout {
    margin-top: auto;
    color: #a0b3d2;
  }
  
  .main-content {
    flex: 1;
    padding: 30px;
    overflow-y: auto;
    background: linear-gradient(to bottom right, #f1f4ff, #ffffff);
  }
  
  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 30px;
  }
  
  .header h1 {
    font-size: 26px;
    font-weight: 600;
  }
  
  .user-info {
    font-size: 16px;
    color: #555;
  }
  
  .cards {
    display: flex;
    gap: 20px;
    margin-bottom: 30px;
  }
  
  .card {
    background: white;
    padding: 20px;
    border-radius: 12px;
    box-shadow: 0 2px 8px rgba(0,0,0,0.05);
    flex: 1;
    min-width: 180px;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
  }

  
  
  .card:hover {
    transform: translateY(-5px);
    box-shadow: 0 4px 16px rgba(0,0,0,0.1);
  }
  
  .card h3 {
    font-size: 16px;
    margin-bottom: 10px;
  }
  
  .card p {
    font-size: 20px;
    font-weight: bold;
    margin-bottom: 5px;
  }
  
  .card span {
    font-size: 14px;
  }
  
  .positive {
    color: green;
  }
  
  .negative {
    color: red;
  }
  
  .grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
    margin-bottom: 30px;
  }
  
  .earnings {
    font-size: 14px;
  }
  
  .earnings strong {
    font-size: 20px;
    color: #000;
  }
  
  .social-activity .card {
    min-height: 250px;
  }
  
  ul {
    list-style: none;
    padding-left: 0;
  }
  
  ul li {
    margin-bottom: 10px;
    font-size: 14px;
  }
  
  .amount {
    float: right;
    font-weight: bold;
  }
  
  @media (max-width: 768px) {
    .container {
      flex-direction: column;
    }
  
    .sidebar {
      width: 100%;
      flex-direction: row;
      flex-wrap: wrap;
    }
  
    .main-content {
      padding: 15px;
    }
  
    .cards {
      flex-direction: column;
    }
  }
  *******************************************************************************************
// dashboard1.component.ts
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-dashboard1',
  templateUrl: './dashboard1.component.html',
  styleUrls: ['./dashboard1.component.css']
})
export class Dashboard1Component implements OnInit {
  currentDate = '27 Mar, 2020 - 27 Apr, 2020';
  userName = 'Jonathan';

  devices = [
    { name: 'Mobile', value: 875, change: '+26.2%', positive: true },
    { name: 'PC', value: 675, change: '+8.2%', positive: true },
    { name: 'Microsoft Xbox One', value: 411, change: '-2.6%', positive: false },
    { name: 'Sony PlayStation 4', value: 300, change: '+3.1%', positive: true }
  ];

  nationality = [
    { region: 'North America', percent: 50 },
    { region: 'Europe', percent: 30 },
    { region: 'Asia', percent: 15 },
    { region: 'Australia', percent: 5 }
  ];

  usersByAge = [
    { ageRange: '10 - 40', percent: 60 },
    { ageRange: '40 - 65', percent: 40 }
  ];

  adRequest = {
    amount: '$12,500',
    dates: ['21/04', '22/04', '23/04', '24/04'],
    values: [5000, 9000, 10000, 12500]
  };

  socialMedia = [
    { platform: 'Facebook', icon: 'fab fa-facebook', percent: 42 },
    { platform: 'Twitter', icon: 'fab fa-twitter', percent: 20 },
    { platform: 'Youtube', icon: 'fab fa-youtube', percent: 20 }
  ];

  activity = [
    { message: '230 new users have played Ludo World' },
    { message: 'Several users have commented on your post about Grand Theft Auto V.' },
    { message: '1,200 new users subscribed to the CD PROJEKT RED channel' }
  ];

  adUsers = [
    { name: 'Joe Morassi', role: 'Marketing specialist', amount: '$2,500' },
    { name: 'Miranda Kress', role: 'Marketing manager', amount: '$1,830' },
    { name: 'Simon Trainor', role: 'Junior marketing specialist', amount: '$1,050' },
    { name: 'Josh White', role: 'Marketing manager', amount: '$995' }
  ];

  constructor() {}

  ngOnInit(): void {}
}
