{% extends "base.html" %}
{% load static %}
{% block head %}
<title>MediQ</title>

<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="MediQ connects you with healthcare resources and information, providing real-time updates on available beds and hospital resources.">

<meta property="og:title" content="MediQ">
<meta property="og:description" content="Connecting with Available Healthcare Resources and Information.">
<meta property="og:image" content="{% static 'images/og-image.jpg' %}">
<meta property="og:url" content="https://yourwebsite.com">
<meta property="og:type" content="website">

<meta name="theme-color" content="#007bff">
<link rel="stylesheet" href="{% static 'styles/your-custom-style.css' %}">
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">

<style>
:root {
    --primary-color: #7a15ff;
    --navbar-bg-color: #0080ff;
    --navbar-link-color: #000000; 
    --navbar-link-hover-color: #ffffff;
    --navbar-link-active-bg: #ff2dbc; 
    --button-bg-color: #ffffff;
    --button-text-color: #7a15ff;
    --button-hover-bg-color: #ff2dbc;
    --card-shadow: 0 4px 12px rgba(0, 0, 0, 0.15); 
    --heading-color: #000000;
    --text-color: #000000;
    --border-radius: 0px;
    --container-max-width: 1140px; 
}

body, h1, h2, h3, p, ul, li {
margin: 0;
padding: 0;
box-sizing: border-box;
}

body {
    display: flex;
    flex-direction: column;
    font-family: 'Roboto', sans-serif;
    line-height: 1.6;
    color: var(--text-color);
    background: url(https://i.redd.it/hxrfxy6aesja1.jpg) no-repeat center center fixed;
    background-size: cover;
    padding-bottom: 20px;
}

body::before {
content: '';
position: absolute;
top: 0;
left: 0;
width: 100%;
height: 100%;
background: inherit; 
z-index: -1; 
}
.main-content {
    flex: 1; /* Allow this area to grow and fill the available space */
    display: flex;
    flex-direction: column;
    position: relative;
    background-color: none;  /*The Damn Border*/
    padding: 10px;
    border: none;
    border-radius: var(--border-radius);
}

.navbar {
    background-color: var(--navbar-bg-color);
    margin-bottom: 20px;
    padding: 0 15px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.navbar-nav {
    display: flex;
    justify-content: space-around;
    margin: 0;
    padding: 0;
    width: 50%;
}

.navbar-nav .nav-item {
    margin: 0 15px;
}

.navbar-nav .nav-link {
    color: var(--navbar-link-color);
    transition: background-color 0.3s ease, color 0.3s ease;
    padding: 10px 20px;
    border-radius: var(--border-radius);
    font-weight: 600;
}

.navbar-nav .nav-link.active, .navbar-nav .nav-link.active:hover {
    color: #ffffff;
    background-color: var(--navbar-link-active-bg);
}

.navbar-nav .nav-link:hover {
    color: #ffffff;
    background-color: #ff2dbc;
}

.navbar-brand {
    display: flex;
    align-items: center;
    font-weight: 700;
}

.navbar-logo {
    height: 40px; /* Adjust the size as needed */
    margin-right: 10px; /* Space between logo and text */
}

@media (max-width: 768px) {
    .navbar-logo {
        height: 30px; /* Adjust for smaller screens */
    }
}

.hero-section {
    background-color: #000000; /* Changed from image background to black color */
    color: #ffffff;
    padding: 120px 20px;
    text-align: center;
    border: none;
    border-bottom: none; /* Removed the purple border */
}

.hero-section .hero-box {
    background-color: rgba(0, 0, 0, 0.5); /* Added slight background color to make text stand out */
    padding: 30px; /* Adjusted padding */
    border-radius: var(--border-radius);
}

.hero-section h1 {
    font-size: 4rem; 
    margin-bottom: 20px;
}

.hero-section p {
    font-size: 1.75rem; 
    margin-bottom: 30px;
}

.hero-section .btn-primary {
    background-color: var(--button-bg-color);
    color: var(--button-text-color);
    border: none;
    padding: 12px 24px; 
    font-size: 1.0rem; 
    border-radius: var(--border-radius);
    text-transform: uppercase;
    font-weight: 700;
    transition: background-color 0.3s ease, transform 0.3s ease;
}

.hero-section .btn-primary:hover {
    background-color: var(--button-hover-bg-color);
    transform: scale(1.05); 
}

.hero-box {
    background-color: rgb(0, 0, 0); 
    padding: 30px; 
    border-radius: 40px; 
    max-width: 680px; /* Limit the width of the box */
    margin: 0 auto; /* Center the box horizontally */
}

.features {
    padding: 60px 20px;
    background-color: #f7f7f7;
}

.features .card {
    border: none;
    border-radius: var(--border-radius);
    overflow: hidden;
    box-shadow: var(--card-shadow);
    transition: transform 0.3s ease, box-shadow 0.3s ease; /* Added transition */
    margin-top: 20px;
}

.features .card:hover {
    transform: translateY(-10px); /* Increased hover effect */
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3); /* Enhanced shadow on hover */
}

.features .card-img-top {
    height: 250px;
    object-fit: cover;
}

.dashboard-explorer {
    background-color: #f7f7f7; /* Light background color for the unified section */
    padding: 60px 20px;
}

.dashboard-explorer-card {
    background-color: #ffffff;
    padding: 20px;
    border-radius: 10px;
    box-shadow: var(--card-shadow);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin-top: 20px;
}

.dashboard-explorer-card:hover {
    transform: translateY(-10px);
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
}

.dashboard-explorer-card h3 {
    margin-bottom: 20px;
    font-size: 1.5rem;
}

.dashboard-explorer-card p {
    margin-bottom: 40px;
}

@media (max-width: 768px) {
    .dashboard-explorer-card {
        padding: 15px;
    }

    .dashboard-explorer-card h3 {
        font-size: 1.25rem;
    }

    .dashboard-explorer-card p {
        font-size: 0.875rem;
    }
}

.card-link {
    text-decoration: none; /* Remove underline from the link */
    color: inherit; /* Inherit color from parent element */
}

.card-link .card {
    transition: transform 0.3s ease, box-shadow 0.3s ease; /* Ensure smooth transitions */
}

.card-link .card:hover {
    transform: translateY(-8px); /* Hover effect */
    box-shadow: 0 6px 12px rgba(0, 0, 0, 0.2); /* Enhanced shadow on hover */
}

.contact {
    background: #f7f7f7;
    padding: 60px 20px;
    border-top: 0px solid #7a15ff;
    flex: 1; 
    display: flex;
    flex-direction: column;
    justify-content: center;
}

footer {
    background-color: #f7f7f7;
    padding: 20px 0;
    text-align: center;
}

.contact .form-group {
    margin-bottom: 1.5rem;
}

.contact .form-control {
    border-radius: 5px;
    border-color: #000000;
    box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.2);
    transition: border-color 0.3s ease, box-shadow 0.3s ease;
}

.contact .form-control:focus {
    border-color: var(--primary-color);
    box-shadow: 0 0 0 0.2rem rgba(180, 180, 180, 0.16); 
}

.contact-box { 
    background-color: #ffffff;
    padding: 30px;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    max-width: 600px; 
    margin: 0 auto; 
}

.contact .btn-primary {
    background-color: #4b3efe;
    border: none;
    color: #ffffff;
    text-transform: uppercase;
    font-weight: 700;
    transition: background-color 0.3s ease, transform 0.3s ease;
    padding: 5px 10px;
    border-radius: 5px;
}

.contact .btn-primary:hover {
    background-color: #2111ff; 
    transform: scale(1.05); 
}

.contact h2 {
    color: var(--heading-color);
    margin-bottom: 10px; 
    font-size: 2rem;
}

@media (max-width: 768px) {
    .hero-section h1 {
        font-size: 2.5rem; /* Responsive font size */
    }

    .hero-section p {
        font-size: 1rem; /* Responsive font size */
    }

    .hero-section .btn-primary {
        font-size: 1rem; /* Responsive font size */
    }
    }
</style>

{% endblock %}
{% block navbar %}

<nav class="navbar navbar-expand-lg navbar-light bg-light">
    <div class="container">
        <a class="navbar-brand" href="#"><img src="https://img.freepik.com/premium-vector/vector-illustration-heart-shape-drops-blood-symbol-limitless-healthcare-medical-treatment-conceptual-logo-use-medical-care-advertisement_570429-36243.jpg" alt="MediQ Logo" class="navbar-logo">MediQ</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
            <ul class="navbar-nav mx-auto">
                <li class="nav-item">
                    <a class="nav-link active" aria-current="page" href="">Home</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="{% url 'beds_avail:beds_avail_home' %}">Available Beds</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#">Hospital Login</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#">About</a>
                </li>
            </ul>
        </div>
    </div>
</nav>
{% endblock %}

{% block content %}

<!-- Hero Section -->
<div class="main-content">
    <header class="hero-section text-center text-light py-5">
        <div class="container">
            <div class="hero-box">
                <h1 class="display-4">- Welcome To MediQ -</h1>
                <p class="lead">Connecting with Available Healthcare Resources and Information</p>
                <a href="{% url 'beds_avail:beds_avail_home' %}" class="btn btn-primary btn-lg">Find Available Beds</a>
            </div>
        </div>
</header>

<!-- Explorer -->
<section class="dashboard-explorer py-5">
    <div class="container">
        <h2 class="text-center">- Explore -</h2>
        <div class="row text-center">
            <!-- Overview Block -->
            <div class="col-md-3 mb-4">
                <div class="dashboard-explorer-card">
                    <h3>Overview</h3>
                    <p>Get a quick overview of current statistics and important updates.</p>
                    <a href="#" class="btn btn-primary">View Details</a>
                </div>
            </div>
            <!-- Recent Activity Block -->
            <div class="col-md-3 mb-4">
                <div class="dashboard-explorer-card">
                    <h3>Recent Activity</h3>
                    <p>Track recent activity and updates in your area of interest.</p>
                    <a href="#" class="btn btn-primary">See Activity</a>
                </div>
            </div>
            <!-- Health Reports Block -->
            <div class="col-md-3 mb-4">
                <div class="dashboard-explorer-card">
                    <h3>Health Reports</h3>
                    <p>Generate and review detailed reports on various metrics.</p>
                    <a href="#" class="btn btn-primary">Generate Report</a>
                </div>
            </div>
            <!-- Patient Stories Block -->
            <div class="col-md-3 mb-4">
                <div class="dashboard-explorer-card">
                    <h3>Patient Stories</h3>
                    <p>Read stories from patients and healthcare professionals.</p>
                    <a href="#" class="btn btn-primary">Read Stories</a>
                </div>
            </div>
        </div>
    </div>
</section>

<!-- Features Section -->
    <section class="features py-5">
        <div class="container">
            <h2 class="text-center", style="color: #ff0000">- Emergency -</h2>
            <div class="row text-center">
                <div class="col-md-4 mb-4">
                    <div class="card">
                        <img src="https://img.freepik.com/premium-vector/drawing-pills-bottle-medicine_1095437-14454.jpg" class="card-img-top" alt="Feature 1">
                        <div class="card-body">
                            <h5 class="card-title">Medicines - Drugs</h5>
                            <p class="card-text">Get information on available medicines and drugs only minutes away.</p>
                        </div>
                    </div>
                </div>
                <div class="col-md-4 mb-4">
                    <a href="{% url 'beds_avail:beds_avail_home' %}" class="card-link">
                        <div class="card">
                            <img src="https://us.123rf.com/450wm/salapao2u/salapao2u1611/salapao2u161100105/66080920-hospital-bed-with-medical-equipments.jpg" class="card-img-top" alt="Feature 2">
                            <div class="card-body">
                                <h5 class="card-title">Beds - ERs</h5>
                                <p class="card-text">Find out the availability of beds in emergency rooms and hospitals nearby.</p>
                            </div>
                        </div>
                    </div></a>
                <div class="col-md-4 mb-4"> 
                    <div class="card">
                        <img src="https://static.vecteezy.com/system/resources/previews/034/217/887/non_2x/doctors-and-nurses-in-white-coat-with-stethoscope-group-of-hospital-medical-staff-standing-together-with-arms-crossed-free-vector.jpg" class="card-img-top" alt="Feature 3">
                        <div class="card-body">
                            <h5 class="card-title">Professionals</h5>
                            <p class="card-text">Connect with healthcare professionals and get expert advice.</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

<!-- Contact Section -->
    <section class="contact py-5">
        <div class="container">
            <h2 class="text-center">[ Contact Us ]</h2>
            <div class="contact-box">
                <form>
                    {% csrf_token %}
                    <div class="form-group">
                        <label for="name">Name</label>
                        <input type="text" class="form-control" id="name" placeholder="Your Name" required>
                    </div>
                    <div class="form-group">
                        <label for="email">Email Address</label>
                        <input type="email" class="form-control" id="email" placeholder="Your Email" required>
                    </div>
                    <div class="form-group">
                        <label for="message">Message</label>
                        <textarea class="form-control" id="message" rows="4" placeholder="Your Message"></textarea>
                    </div>
                    <button type="submit" class="btn btn-primary">Send Message</button>
                </form>
            </div>
        </div>
    </section>
    <footer class="text-center py-4">
        <div class="container">
            <p>&copy; 2024 MediQ. All Rights Reserved.</p>
        </div>
    </footer>
</div>

{% endblock %}
