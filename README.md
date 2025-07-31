<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>动态爱心</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f0f0f0;
        }

        .heart {
            width: 100px;
            height: 100px;
            background-color: red;
            position: relative;
            transform: rotate(-45deg);
            animation: pulse 1.5s infinite;
        }

        .heart:before, .heart:after {
            content: "";
            position: absolute;
            width: 100px;
            height: 100px;
            background-color: red;
            border-radius: 50%;
        }

        .heart:before {
            left: 50px;
            top: 0;
        }

        .heart:after {
            top: 50px;
            left: 0;
        }

        @keyframes pulse {
            0% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.2);
            }
            100% {
                transform: scale(1);
            }
        }
    </style>
</head>
<body>
    <div class="heart"></div>
</body>
</html>
