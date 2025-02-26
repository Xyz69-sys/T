<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TechNova Solutions - Sign Up</title>
    <style>
        /* General page styling */
        body {
            font-family: Arial, sans-serif;
            background: #f7f7f7;
            margin: 0;
            padding: 0;
        }

        /* Main container */
        .container {
            width: 100%;
            max-width: 600px;
            margin: 50px auto;
            padding: 20px;
            background-color: #ffffff;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            border-radius: 8px;
        }

        /* Heading */
        h2 {
            text-align: center;
            color: #333;
            font-size: 30px;
            margin-bottom: 30px;
        }

        /* Form input styles */
        .form-group {
            margin-bottom: 20px;
        }

        label {
            display: block;
            font-weight: bold;
            color: #555;
        }

        input[type="text"], input[type="email"], input[type="password"], input[type="tel"], input[type="date"] {
            width: 100%;
            padding: 12px;
            border: 2px solid #ddd;
            border-radius: 6px;
            font-size: 16px;
            background-color: #f9f9f9;
        }

        input[type="text"]:focus, input[type="email"]:focus, input[type="password"]:focus, input[type="tel"]:focus, input[type="date"]:focus {
            border-color: #4CAF50;
            background-color: #fff;
        }

        .error {
            color: red;
            font-size: 14px;
        }

        .submit-btn {
            width: 100%;
            padding: 15px;
            background-color: #4CAF50;
            color: white;
            font-size: 18px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            transition: 0.3s;
        }

        .submit-btn:hover {
            background-color: #45a049;
        }

        /* Gender radio button styling */
        .gender-group {
            display: flex;
            align-items: center;
            margin-top: 10px;
        }

        .gender-group label {
            margin-right: 15px;
            font-weight: normal;
        }

        /* Thank you message */
        .thank-you-message {
            text-align: center;
            font-size: 24px;
            font-weight: bold;
            color: red;
            margin-top: 50px;
        }

        /* Responsiveness */
        @media (max-width: 768px) {
            .container {
                padding: 15px;
            }

            h2 {
                font-size: 24px;
            }
        }
    </style>
</head>
<body>

    <div class="container">
        <h2>Sign Up for TechNova Solutions</h2>
        <form id="signup-form" onsubmit="return validateForm()">
            <!-- Full Name -->
            <div class="form-group">
                <label for="full-name">Full Name:</label>
                <input type="text" id="full-name" name="full-name" placeholder="Enter your full name" required>
                <div id="name-error" class="error"></div>
            </div>

            <!-- Email -->
            <div class="form-group">
                <label for="email">Email:</label>
                <input type="email" id="email" name="email" placeholder="Enter your email" required>
                <div id="email-error" class="error"></div>
            </div>

            <!-- Phone -->
            <div class="form-group">
                <label for="phone">Phone Number:</label>
                <input type="tel" id="phone" name="phone" placeholder="Enter your phone number" required>
                <div id="phone-error" class="error"></div>
            </div>

            <!-- Date of Birth -->
            <div class="form-group">
                <label for="dob">Date of Birth:</label>
                <input type="date" id="dob" name="dob" required>
                <div id="dob-error" class="error"></div>
            </div>

            <!-- Address -->
            <div class="form-group">
                <label for="address">Address:</label>
                <input type="text" id="address" name="address" placeholder="Enter your address" required>
                <div id="address-error" class="error"></div>
            </div>

            <!-- Password -->
            <div class="form-group">
                <label for="password">Password:</label>
                <input type="password" id="password" name="password" placeholder="Create a password" required>
                <div id="password-error" class="error"></div>
            </div>

            <!-- Confirm Password -->
            <div class="form-group">
                <label for="confirm-password">Confirm Password:</label>
                <input type="password" id="confirm-password" name="confirm-password" placeholder="Confirm your password" required>
                <div id="confirm-password-error" class="error"></div>
            </div>

            <!-- Gender Selection -->
            <div class="form-group">
                <label>Gender:</label>
                <div class="gender-group">
                    <input type="radio" id="male" name="gender" value="male" required>
                    <label for="male">Male</label>

                    <input type="radio" id="female" name="gender" value="female" required>
                    <label for="female">Female</label>
                </div>
                <div id="gender-error" class="error"></div>
            </div>

            <!-- Submit Button -->
            <button type="submit" class="submit-btn">Sign Up</button>
        </form>
    </div>

    <!-- Thank you message (hidden by default) -->
    <div class="thank-you-message" id="thank-you-message" style="display:none;">
        Thank You for Signing Up!
    </div>

    <script>
        function validateForm() {
            let isValid = true;

            // Clear previous errors
            document.getElementById("name-error").innerHTML = "";
            document.getElementById("email-error").innerHTML = "";
            document.getElementById("phone-error").innerHTML = "";
            document.getElementById("dob-error").innerHTML = "";
            document.getElementById("address-error").innerHTML = "";
            document.getElementById("password-error").innerHTML = "";
            document.getElementById("confirm-password-error").innerHTML = "";
            document.getElementById("gender-error").innerHTML = "";

            // Full Name validation
            const name = document.getElementById("full-name").value;
            if (name.trim() === "") {
                document.getElementById("name-error").innerHTML = "Full name is required.";
                isValid = false;
            }

            // Email validation
            const email = document.getElementById("email").value;
            const emailPattern = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,6}$/;
            if (!emailPattern.test(email)) {
                document.getElementById("email-error").innerHTML = "Please enter a valid email.";
                isValid = false;
            }

            // Phone validation
            const phone = document.getElementById("phone").value;
            const phonePattern = /^[0-9]{10}$/;
            if (!phonePattern.test(phone)) {
                document.getElementById("phone-error").innerHTML = "Please enter a valid phone number (10 digits).";
                isValid = false;
            }

            // Date of Birth validation
            const dob = document.getElementById("dob").value;
            if (dob === "") {
                document.getElementById("dob-error").innerHTML = "Date of birth is required.";
                isValid = false;
            }

            // Address validation
            const address = document.getElementById("address").value;
            if (address.trim() === "") {
                document.getElementById("address-error").innerHTML = "Address is required.";
                isValid = false;
            }

            // Password validation
            const password = document.getElementById("password").value;
            if (password.length < 6) {
                document.getElementById("password-error").innerHTML = "Password must be at least 6 characters.";
                isValid = false;
            }

            // Confirm Password validation
            const confirmPassword = document.getElementById("confirm-password").value;
            if (password !== confirmPassword) {
                document.getElementById("confirm-password-error").innerHTML = "Passwords do not match.";
                isValid = false;
            }

            // Gender validation
            const gender = document.querySelector('input[name="gender"]:checked');
            if (!gender) {
                document.getElementById("gender-error").innerHTML = "Please select a gender.";
                isValid = false;
            }

            // Show the thank you message on success
            if (isValid) {
                // Hide the form and show the thank you message
                document.querySelector("form").style.display = "none";
                document.getElementById("thank-you-message").style.display = "block";
            }

            return false; // Prevent form submission for client-side validation
        }
    </script>

</body>
</html>

