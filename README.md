<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>高级动态爱心</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: #f3f3f3;
            overflow: hidden;
        }

        .heart {
            width: 100px;
            height: 100px;
            background: linear-gradient(45deg, #ff0066, #ff6600);
            position: relative;
            transform: rotate(-45deg);
            animation: heartbeat 1.5s ease-in-out infinite, pulse 1.5s ease-in-out infinite;
        }

        .heart:before, .heart:after {
            content: "";
            position: absolute;
            width: 100px;
            height: 100px;
            background: linear-gradient(45deg, #ff0066, #ff6600);
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

        @keyframes heartbeat {
            0% {
                transform: rotate(-45deg) scale(1);
            }
            25% {
                transform: rotate(-45deg) scale(1.2);
            }
            50% {
                transform: rotate(-45deg) scale(1);
            }
            75% {
                transform: rotate(-45deg) scale(1.2);
            }
            100% {
                transform: rotate(-45deg) scale(1);
            }
        }

        @keyframes pulse {
            0% {
                transform: rotate(-45deg) scale(1);
            }
            50% {
                transform: rotate(-45deg) scale(1.1);
            }
            100% {
                transform: rotate(-45deg) scale(1);
            }
        }

        /* 鼠标悬停时的效果 */
        .heart:hover {
            animation: none;
            transform: rotate(-45deg) scale(1.5);
            filter: brightness(1.2);
        }
    </style>
</head>
<body>
    <div class="heart"></div>
</body>
</html>
