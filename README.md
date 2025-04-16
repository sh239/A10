<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Cookie</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            padding: 40px;
            background-color: #f0f8ff;
        }
        h1 {
            color: #333;
        }
        #cookieValue {
            margin-top: 20px;
            font-weight: bold;
            color: green;
        }
    </style>
</head>
<body>

<h1>Welcome to the Cookie Page</h1>
<p>This page sets a cookie and shows its value when you reload the page.</p>

<div id="cookieValue"></div>

<script>
    function setCookie(name, value, days) {
        const expires = new Date(Date.now() + days * 864e5).toUTCString();
        document.cookie = name + '=' + encodeURIComponent(value) + '; expires=' + expires + '; path=/';
    }

    function getCookie(name) {
        return document.cookie.split('; ').reduce((r, v) => {
            const parts = v.split('=');
            return parts[0] === name ? decodeURIComponent(parts[1]) : r
        }, '');
    }

    let username = getCookie("username");

    if (!username) {
        username = prompt("Welcome! Please enter your name:");
        if (username) {
            setCookie("username", username, 7);
        }
    }

    document.getElementById("cookieValue").textContent =
        username ? `Your saved name is: ${username}` : "No cookie was set.";
</script>

</body>
</html>
