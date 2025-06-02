<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Simple Web App</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header>
    <h1>Welcome to My Web App</h1>
  </header>
  <main>
    <p id="greeting">Click the button below to see a message!</p>
    <button id="showMessageBtn">Show Message</button>
    <p id="result"></p>
  </main>
  <footer>
    <p>&copy; 2025 Simple Web App</p>
  </footer>
  <script>
    // Example for testing in GitHub Actions
    document.getElementById("showMessageBtn").addEventListener("click", function() {
        const testMessage = "GitHub Actions Test Passed!";
        document.get ElementById("result").innerText = testMessage;
        console.log(testMessage);
    });
  </script>
</body>
</html>