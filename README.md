# osTicket Installation and Configuration Guide

## Introduction

This document outlines the step-by-step process for installing and configuring osTicket, an open-source support ticket system. This guide will help users set up osTicket on a local server using XAMPP, providing a robust solution for managing customer support requests.

## Prerequisites

- A computer running Windows.
- XAMPP installed (Download from [Apache Friends](https://www.apachefriends.org/index.html)).
- A web browser (e.g., Chrome, Firefox).

## Step 1: Download and Install XAMPP

1. Go to the [XAMPP download page](https://www.apachefriends.org/index.html).
2. Download the XAMPP installer for Windows.
3. Run the installer and follow the on-screen instructions to install XAMPP.
4. Once installed, open the XAMPP Control Panel.

## Step 2: Download osTicket

1. Go to the [osTicket download page](https://osticket.com/download).
2. Download the latest stable version of osTicket.
3. Extract the downloaded file to a folder on your computer.

## Step 3: Set Up osTicket

### Move osTicket Files

1. Navigate to the extracted osTicket files.
2. Copy the contents of the `upload` folder.
3. Paste the copied files into the `C:\xampp1\htdocs\osticket` directory.

### Configure Apache

1. Open the XAMPP Control Panel.
2. Start the Apache service.

### Create MySQL Database

1. Start the MySQL service from the XAMPP Control Panel.
2. Click on the "Admin" button next to MySQL to open phpMyAdmin.
3. In phpMyAdmin, click on "Databases".
4. Create a new database named `osticket_db`.

### Create a MySQL User

1. In phpMyAdmin, click on the "User Accounts" tab.
2. Click on "Add user account".
3. Enter the following details:
   - Username: `osticket_user`
   - Host: `localhost`
   - Password: `your_password`
4. Under "Database for user", select "Create database with same name and grant all privileges".
5. Click "Go" to create the user.

### Configure osTicket

1. Open your web browser and go to `http://localhost/osticket/setup/`.
2. Follow the on-screen instructions to configure osTicket.
   - Database settings:
     - MySQL Hostname: `localhost`
     - Database Name: `osticket_db`
     - Database User: `osticket_user`
     - Database Password: `your_password`
3. Rename `include/ost-sampleconfig.php` to `include/ost-config.php`.
4. Click "Install Now".

### Post-Installation Steps

1. Change permission of `include/ost-config.php` to remove write access:
   - Open Command Prompt as an administrator.
   - Run: `icacls C:\xampp1\htdocs\osticket\include\ost-config.php /reset`
2. Navigate to the osTicket admin panel at `http://localhost/osticket/scp`.
