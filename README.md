<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Form Validation Project</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
  <style>
    body {
      background-color: #f8f9fa;
    }
    .container {
      max-width: 500px;
      margin-top: 50px;
      padding: 20px;
      background: white;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
  </style>
</head>
<body>
  <div class="container">
    <h2 class="mb-4 text-center">Registration Form</h2>
    <form id="myForm">
      <div class="mb-3">
        <label for="fullname" class="form-label">Full Name</label>
        <input type="text" class="form-control" id="fullname" required />
      </div>
      <div class="mb-3">
        <label for="email" class="form-label">Email ID</label>
        <input type="email" class="form-control" id="email" required />
      </div>
      <div class="mb-3">
        <label for="phone" class="form-label">Phone Number</label>
        <input type="text" class="form-control" id="phone" required />
      </div>
      <div class="mb-3">
        <label for="password" class="form-label">Password</label>
        <input type="password" class="form-control" id="password" required />
      </div>
      <div class="mb-3">
        <label for="confirmPassword" class="form-label">Confirm Password</label>
        <input type="password" class="form-control" id="confirmPassword" required />
      </div>
      <div id="error" class="text-danger mb-3"></div>
      <button type="submit" class="btn btn-primary w-100">Submit</button>
    </form>
  </div>

  <script>
    document.getElementById("myForm").addEventListener("submit", function (e) {
      e.preventDefault();

      const name = document.getElementById("fullname").value.trim();
      const email = document.getElementById("email").value.trim();
      const phone = document.getElementById("phone").value.trim();
      const password = document.getElementById("password").value;
      const confirmPassword = document.getElementById("confirmPassword").value;
      const errorDiv = document.getElementById("error");

      errorDiv.textContent = "";

      if (name.length < 5) {
        errorDiv.textContent = "Name must be at least 5 characters long.";
        return;
      }

      if (!email.includes("@")) {
        errorDiv.textContent = "Enter a valid email.";
        return;
      }

      if (phone.length !== 10 || phone === "123456789" || isNaN(phone)) {
        errorDiv.textContent = "Enter a valid 10-digit phone number.";
        return;
      }

      if (
        password.length < 8 ||
        password.toLowerCase() === "password" ||
        password.toLowerCase() === name.toLowerCase()
      ) {
        errorDiv.textContent = "Password is not strong enough.";
        return;
      }

      if (password !== confirmPassword) {
        errorDiv.textContent = "Passwords do not match.";
        return;
      }

      alert("Form submitted successfully!");
      this.reset();
    });
  </script>
</body>
</html>
