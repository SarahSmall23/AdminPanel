<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Admin Dashboard | UMP Online Student Market</title>
    <link rel="stylesheet" href="my styles.css">
   
    <style>
        :root {
            --primary-color: #2c3e50;
            --secondary-color: #3498db;
            --accent-color: #e74c3c;
            --light-color: #ecf0f1;
            --dark-color: #2c3e50;
            --success-color: #27ae60;
            --warning-color: #f39c12;
            --sidebar-width: 250px;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Roboto', sans-serif;
            background-color: #f5f7fa;
            color: #333;
            display: flex;
            min-height: 100vh;
        }
        
        /* Sidebar Styles */
        .sidebar {
            width: var(--sidebar-width);
            background-color: var(--primary-color);
            color: white;
            padding: 20px 0;
            height: 100vh;
            position: fixed;
            transition: all 0.3s;
        }
        
        .sidebar-header {
            padding: 0 20px 20px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .sidebar-header h3 {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .sidebar-menu {
            padding: 20px 0;
        }
        
        .menu-item {
            padding: 12px 20px;
            display: flex;
            align-items: center;
            gap: 10px;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .menu-item:hover, .menu-item.active {
            background-color: rgba(255, 255, 255, 0.1);
        }
        
        .menu-item i {
            width: 20px;
            text-align: center;
        }
        
        /* Main Content Styles */
        .main-content {
            flex: 1;
            margin-left: var(--sidebar-width);
            padding: 20px;
        }
        
        .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px 20px;
            background-color: white;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            border-radius: 8px;
            margin-bottom: 20px;
        }
        
        .user-info {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .user-avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background-color: var(--secondary-color);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
        }
        
        /* Dashboard Cards */
        .dashboard-cards {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .card {
            background-color: white;
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
            transition: transform 0.3s;
        }
        
        .card:hover {
            transform: translateY(-5px);
        }
        
        .card-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }
        
        .card-icon {
            width: 40px;
            height: 40px;
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
        }
        
        .card-icon.sales {
            background-color: var(--secondary-color);
        }
        
        .card-icon.users {
            background-color: var(--success-color);
        }
        
        .card-icon.orders {
            background-color: var(--warning-color);
        }
        
        .card-icon.revenue {
            background-color: var(--accent-color);
        }
        
        .card-value {
            font-size: 24px;
            font-weight: 700;
            margin: 10px 0;
        }
        
        .card-footer {
            font-size: 14px;
            color: #777;
        }
        
        /* Tables */
        .table-container {
            background-color: white;
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
            margin-bottom: 30px;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
        }
        
        th, td {
            padding: 12px 15px;
            text-align: left;
            border-bottom: 1px solid #eee;
        }
        
        th {
            background-color: #f8f9fa;
            font-weight: 500;
        }
        
        tr:hover {
            background-color: #f8f9fa;
        }
        
        .btn {
            padding: 8px 12px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 14px;
            transition: all 0.3s;
        }
        
        .btn-primary {
            background-color: var(--secondary-color);
            color: white;
        }
        
        .btn-danger {
            background-color: var(--accent-color);
            color: white;
        }
        
        .btn-success {
            background-color: var(--success-color);
            color: white;
        }
        
        .btn-warning {
            background-color: var(--warning-color);
            color: white;
        }
        
        .btn-sm {
            padding: 5px 10px;
            font-size: 12px;
        }
        
        .status-badge {
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 500;
        }
        
        .status-active {
            background-color: #d4edda;
            color: #155724;
        }
        
        .status-pending {
            background-color: #fff3cd;
            color: #856404;
        }
        
        .status-inactive {
            background-color: #f8d7da;
            color: #721c24;
        }
        
        /* Charts Container */
        .charts-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .chart-card {
            background-color: white;
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
        }
        
        .chart-header {
            margin-bottom: 20px;
        }
        
        /* Footer */
        .footer {
            text-align: center;
            padding: 20px;
            color: #777;
            font-size: 14px;
        }
        
        /* Responsive */
        @media (max-width: 992px) {
            .sidebar {
                width: 70px;
                overflow: hidden;
            }
            
            .sidebar-header h3 span, .menu-item span {
                display: none;
            }
            
            .sidebar-header h3 {
                justify-content: center;
            }
            
            .menu-item {
                justify-content: center;
            }
            
            .main-content {
                margin-left: 70px;
            }
        }
        
        @media (max-width: 768px) {
            .dashboard-cards {
                grid-template-columns: 1fr 1fr;
            }
            
            .charts-container {
                grid-template-columns: 1fr;
            }
        }
        
        @media (max-width: 576px) {
            .dashboard-cards {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- Sidebar -->
    <div class="sidebar">
        <div class="sidebar-header">
            <h3><i class="fas fa-store"></i> <span>UMP Market</span></h3>
        </div>
        <div class="sidebar-menu">
            <div class="menu-item active">
                <i class="fas fa-tachometer-alt"></i>
                <span>Dashboard</span>
            </div>
            <div class="menu-item">
                <i class="fas fa-users"></i>
                <span>Users</span>
            </div>
            <div class="menu-item">
                <i class="fas fa-user-tie"></i>
                <span>Vendors</span>
            </div>
            <div class="menu-item">
                <i class="fas fa-shopping-cart"></i>
                <span>Products</span>
            </div>
            <div class="menu-item">
                <i class="fas fa-receipt"></i>
                <span>Orders</span>
            </div>
            <div class="menu-item">
                <i class="fas fa-chart-line"></i>
                <span>Analytics</span>
            </div>
            <div class="menu-item">
                <i class="fas fa-cog"></i>
                <span>Settings</span>
            </div>
        </div>
    </div>

    <!-- Main Content -->
    <div class="main-content">
        <div class="header">
            <h2>Admin Dashboard</h2>
            <div class="user-info">
                <div class="user-avatar">AD</div>
                <span>Admin User</span>
                <i class="fas fa-chevron-down"></i>
            </div>
        </div>

        <!-- Dashboard Cards -->
        <div class="dashboard-cards">
            <div class="card">
                <div class="card-header">
                    <h3>Total Sales</h3>
                    <div class="card-icon sales">
                        <i class="fas fa-rand-sign"></i>
                    </div>
                </div>
                <div class="card-value">R700,000</div>
                <div class="card-footer">+12% from last month</div>
            </div>
            
            <div class="card">
                <div class="card-header">
                    <h3>Active Users</h3>
                    <div class="card-icon users">
                        <i class="fas fa-users"></i>
                    </div>
                </div>
                <div class="card-value">400</div>
                <div class="card-footer">+25 new this week</div>
            </div>
            
            <div class="card">
                <div class="card-header">
                    <h3>Total Orders</h3>
                    <div class="card-icon orders">
                        <i class="fas fa-shopping-cart"></i>
                    </div>
                </div>
                <div class="card-value">1,250</div>
                <div class="card-footer">5 pending fulfillment</div>
            </div>
            
            <div class="card">
                <div class="card-header">
                    <h3>Monthly Revenue</h3>
                    <div class="card-icon revenue">
                        <i class="fas fa-chart-line"></i>
                    </div>
                </div>
                <div class="card-value">R120,000</div>
                <div class="card-footer">Projected: R150,000</div>
            </div>
        </div>

        <!-- Charts -->
        <div class="charts-container">
            <div class="chart-card">
                <div class="chart-header">
                    <h3>Sales Overview</h3>
                </div>
                <div class="chart-placeholder" style="height: 300px; background-color: #f8f9fa; display: flex; align-items: center; justify-content: center; color: #999;">
                    [Sales Chart Would Appear Here]
                </div>
            </div>
            
            <div class="chart-card">
                <div class="chart-header">
                    <h3>User Growth</h3>
                </div>
                <div class="chart-placeholder" style="height: 300px; background-color: #f8f9fa; display: flex; align-items: center; justify-content: center; color: #999;">
                    [User Growth Chart Would Appear Here]
                </div>
            </div>
        </div>

        <!-- User Management -->
        <div class="table-container">
            <h2>User Management</h2>
            <p>Manage all registered users of the platform</p>
            
            <div style="margin: 15px 0; display: flex; justify-content: space-between;">
                <div>
                    <input type="text" placeholder="Search users..." style="padding: 8px; border: 1px solid #ddd; border-radius: 4px; width: 250px;">
                </div>
                <div>
                    <button class="btn btn-primary"><i class="fas fa-plus"></i> Add User</button>
                    <button class="btn"><i class="fas fa-filter"></i> Filter</button>
                    <button class="btn"><i class="fas fa-download"></i> Export</button>
                </div>
            </div>
            
            <table>
                <thead>
                    <tr>
                        <th>ID</th>
                        <th>User</th>
                        <th>Email</th>
                        <th>Role</th>
                        <th>Status</th>
                        <th>Joined</th>
                        <th>Actions</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>#1001</td>
                        <td>Sarah Small</td>
                        <td>sarashawty75@icloud.com</td>
                        <td>Student</td>
                        <td><span class="status-badge status-active">Active</span></td>
                        <td>2025-01-15</td>
                        <td>
                            <button class="btn btn-primary btn-sm"><i class="fas fa-edit"></i></button>
                            <button class="btn btn-danger btn-sm"><i class="fas fa-trash"></i></button>
                        </td>
                    </tr>
                    <tr>
                        <td>#1002</td>
                        <td>Truelly</td>
                        <td>Truelly dibakwane@ump.ac.za</td>
                        <td>Vendor</td>
                        <td><span class="status-badge status-pending">Pending</span></td>
                        <td>2025-02-20</td>
                        <td>
                            <button class="btn btn-primary btn-sm"><i class="fas fa-edit"></i></button>
                            <button class="btn btn-success btn-sm"><i class="fas fa-check"></i></button>
                            <button class="btn btn-danger btn-sm"><i class="fas fa-trash"></i></button>
                        </td>
                    </tr>
                    <tr>
                        <td>#1003</td>
                        <td>Annetha Uyanda</td>
                        <td>AnnethaUyanda@ump.ac.za</td>
                        <td>Admin</td>
                        <td><span class="status-badge status-active">Active</span></td>
                        <td>2024-11-05</td>
                        <td>
                            <button class="btn btn-primary btn-sm"><i class="fas fa-edit"></i></button>
                            <button class="btn btn-danger btn-sm"><i class="fas fa-trash"></i></button>
                        </td>
                    </tr>
                </tbody>
            </table>
            
            <div style="margin-top: 15px; display: flex; justify-content: space-between; align-items: center;">
                <div>Showing 1 to 3 of 400 entries</div>
                <div>
                    <button class="btn">Previous</button>
                    <button class="btn btn-primary">1</button>
                    <button class="btn">2</button>
                    <button class="btn">3</button>
                    <button class="btn">Next</button>
                </div>
            </div>
        </div>

        <!-- Vendor Management -->
        <div class="table-container">
            <h2>Vendor Management</h2>
            <p>Approve or reject vendor applications and manage existing vendors</p>
            
            <table>
                <thead>
                    <tr>
                        <th>ID</th>
                        <th>Business Name</th>
                        <th>Owner</th>
                        <th>Email</th>
                        <th>Status</th>
                        <th>Products</th>
                        <th>Rating</th>
                        <th>Actions</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>#V2001</td>
                        <td>Campus Books</td>
                        <td>Pilot</td>
                        <td>Pilot@campusbooks.co.za</td>
                        <td><span class="status-badge status-active">Approved</span></td>
                        <td>45</td>
                        <td>4.8 <i class="fas fa-star" style="color: var(--warning-color);"></i></td>
                        <td>
                            <button class="btn btn-primary btn-sm"><i class="fas fa-eye"></i></button>
                            <button class="btn btn-warning btn-sm"><i class="fas fa-ban"></i></button>
                        </td>
                    </tr>
                    <tr>
                        <td>#V2002</td>
                        <td>Student Eats</td>
                        <td>Stuart</td>
                        <td>Stuart@studenteats.co.za</td>
                        <td><span class="status-badge status-pending">Pending</span></td>
                        <td>-</td>
                        <td>-</td>
                        <td>
                            <button class="btn btn-success btn-sm"><i class="fas fa-check"></i></button>
                            <button class="btn btn-danger btn-sm"><i class="fas fa-times"></i></button>
                            <button class="btn btn-primary btn-sm"><i class="fas fa-eye"></i></button>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>

        <!-- Recent Activity -->
        <div class="table-container">
            <h2>Recent Activity</h2>
            <p>Latest actions and events on the platform</p>
            
            <div style="display: flex; gap: 15px; margin-bottom: 15px;">
                <button class="btn btn-primary">All Activity</button>
                <button class="btn">User Actions</button>
                <button class="btn">System Events</button>
                <button class="btn">Transactions</button>
            </div>
            
            <div style="border-left: 2px solid #eee; padding-left: 20px;">
                <div style="display: flex; gap: 15px; padding: 10px 0; border-bottom: 1px solid #f5f5f5;">
                    <div style="width: 40px; height: 40px; background-color: #e3f2fd; border-radius: 50%; display: flex; align-items: center; justify-content: center;">
                        <i class="fas fa-user" style="color: var(--secondary-color);"></i>
                    </div>
                    <div>
                        <div><strong>Sarah Small</strong> registered a new account</div>
                        <div style="font-size: 12px; color: #777;">2 hours ago</div>
                    </div>
                </div>
                
                <div style="display: flex; gap: 15px; padding: 10px 0; border-bottom: 1px solid #f5f5f5;">
                    <div style="width: 40px; height: 40px; background-color: #e8f5e9; border-radius: 50%; display: flex; align-items: center; justify-content: center;">
                        <i class="fas fa-shopping-cart" style="color: var(--success-color);"></i>
                    </div>
                    <div>
                        <div>New order <strong>#ORD-45678</strong> placed by AnnethaUyanda</div>
                        <div style="font-size: 12px; color: #777;">5 hours ago</div>
                    </div>
                </div>
                
                <div style="display: flex; gap: 15px; padding: 10px 0;">
                    <div style="width: 40px; height: 40px; background-color: #fff3e0; border-radius: 50%; display: flex; align-items: center; justify-content: center;">
                        <i class="fas fa-exclamation-triangle" style="color: var(--warning-color);"></i>
                    </div>
                    <div>
                        <div>System alert: <strong>Low inventory</strong> for product "Calculus Textbook"</div>
                        <div style="font-size: 12px; color: #777;">1 day ago</div>
                    </div>
                </div>
            </div>
        </div>

        <div class="footer">
            <p>© 2025 UMP Online Student Market. All Rights Reserved. | Version 2.1.0</p>
        </div>
    </div>

    <script>
        // This would be replaced with actual JavaScript functionality
        console.log("Admin panel loaded");
    </script>
</body>
</html>
