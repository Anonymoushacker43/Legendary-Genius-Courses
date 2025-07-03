<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GP Learning Platform</title>
    <style>
        /* --- Basic Reset and Body Styles --- */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', 'Roboto', 'Helvetica Neue', sans-serif;
            background-color: #0d0d0d;
            color: #ffffff;
            padding-bottom: 20px;
        }

        /* --- Header Section --- */
        .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 15px;
            background: linear-gradient(to right, #330000, #1a1a1a);
            border-bottom: 2px solid #ff0000;
        }

        .header-text h1 {
            font-size: 24px;
            font-weight: bold;
            text-transform: uppercase;
        }

        .header-text h1 .highlight {
            color: #00ff00;
        }
        
        .header-text p {
            font-size: 14px;
            color: #cccccc;
            text-transform: uppercase;
        }

        .logo-container {
            position: relative;
        }

        .logo {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            background: #111;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 32px;
            font-weight: bold;
            color: #fff;
            position: relative;
            z-index: 2;
            border: 3px solid;
            border-image: conic-gradient(from 180deg, #8A2BE2, #4B0082, #0000FF, #00BFFF, #8A2BE2) 1;
            box-shadow: 0 0 15px #8A2BE2, 0 0 25px #0000FF;
        }

        .live-tag {
            position: absolute;
            top: -5px;
            right: -10px;
            background-color: #ff0000;
            color: white;
            padding: 3px 8px;
            border-radius: 5px;
            font-size: 10px;
            font-weight: bold;
            z-index: 3;
        }

        /* --- Ad Placeholder --- */
        .ad-placeholder {
            background-color: #222;
            border: 2px dashed #555;
            color: #888;
            text-align: center;
            display: flex;
            justify-content: center;
            align-items: center;
            margin: 15px 10px;
            min-height: 50px;
            border-radius: 8px;
            font-weight: bold;
        }

        /* --- Main Grid for Courses --- */
        .course-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 10px;
            padding: 0 10px; /* Adjusted padding */
        }

        .course-card {
            background-color: #000000;
            border: 2px solid #00ff00;
            border-radius: 8px;
            padding: 15px 5px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
            text-decoration: none;
            color: #ffffff;
            aspect-ratio: 1 / 1;
            cursor: pointer;
            transition: transform 0.2s ease, box-shadow 0.2s ease;
        }

        .course-card:hover {
            transform: scale(1.05);
            box-shadow: 0 0 15px #00ff00;
        }
        
        .course-card.alt-color {
            border-color: #ffff00;
        }

        .course-card.alt-color:hover {
            box-shadow: 0 0 15px #ffff00;
        }

        .card-icon {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            border: 2px solid #00ff00;
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 8px;
        }
        
        .course-card.alt-color .card-icon {
            border-color: #ffff00;
        }

        .card-icon svg {
            width: 20px;
            height: 20px;
            fill: #ffffff;
        }

        .course-card .card-title {
            font-size: 13px;
            font-weight: 600;
            line-height: 1.2;
        }

        /* --- Payment Modal Styles (UNCHANGED) --- */
        .payment-modal {
            display: none; position: fixed; z-index: 1000; left: 0; top: 0; width: 100%; height: 100%; overflow: auto; background-color: rgba(0, 0, 0, 0.9); justify-content: center; align-items: center;
        }
        .modal-content {
            background-color: #1a1a1a; margin: auto; padding: 20px; border: 2px solid #00ff00; border-radius: 10px; width: 95%; max-width: 400px; position: relative; box-shadow: 0 0 25px #00ff0033;
        }
        .close-button {
            color: #aaa; position: absolute; top: 5px; right: 15px; font-size: 28px; font-weight: bold; cursor: pointer;
        }
        .close-button:hover, .close-button:focus { color: white; }
        .modal-header h2 { color: #00ff00; margin-bottom: 5px; }
        .modal-header p { font-size: 18px; margin-bottom: 20px; }
        .payment-details h3 { color: #ffff00; margin-top: 15px; margin-bottom: 10px; border-bottom: 1px solid #ffff0055; padding-bottom: 5px; }
        .payment-info { background: #222; padding: 10px; border-radius: 5px; margin-bottom: 5px; }
        .payment-info p { margin: 0; font-size: 14px; }
        .payment-info .label { font-weight: bold; color: #ccc; }
        .info-line { display: flex; justify-content: space-between; align-items: center; }
        .copy-btn { background: #00ff00; color: #000; border: none; padding: 4px 8px; font-size: 12px; border-radius: 4px; cursor: pointer; font-weight: bold; }
        .copy-btn.alt { background: #ffff00; }
        .user-form { margin-top: 25px; }
        .user-form input { width: 100%; padding: 12px; margin-bottom: 15px; border-radius: 5px; border: 1px solid #555; background-color: #333; color: #fff; font-size: 16px; }
        .submit-btn { width: 100%; padding: 12px; background: #00ff00; color: #000; border: none; border-radius: 5px; font-size: 18px; font-weight: bold; cursor: pointer; transition: background-color 0.3s; }
        .submit-btn:hover { background-color: #00aa00; }

    </style>
</head>
<body>

    <header class="header">
        <div class="header-text">
            <h1>GP <span class="highlight">Learning</span></h1>
            <p>Many More Courses Available</p>
        </div>
        <div class="logo-container">
            <div class="live-tag">LIVE</div>
            <div class="logo">GP</div>
        </div>
    </header>

    <!-- Ad Placeholder 1 -->
    <div class="ad-placeholder">
        <p>Ad Banner Area (320x50)</p>
    </div>

    <main>
        <div class="course-grid">
            <!-- Row 1 -->
            <a class="course-card" data-course-name="Web Dev Course" data-course-price="Rs. 1500">
                <div class="card-icon"><svg viewBox="0 0 24 24"><path d="M9.4 16.6L4.8 12l4.6-4.6L8 6l-6 6 6 6 1.4-1.4zm5.2 0l4.6-4.6-4.6-4.6L16 6l6 6-6 6-1.4-1.4z"/></svg></div><span class="card-title">Web Dev Course</span>
            </a>
            <a class="course-card" data-course-name="App Dev Tools" data-course-price="Rs. 2000">
                <div class="card-icon"><svg viewBox="0 0 24 24"><path d="M15.5 1h-8C6.12 1 5 2.12 5 3.5v17C5 21.88 6.12 23 7.5 23h8c1.38 0 2.5-1.12 2.5-2.5v-17C18 2.12 16.88 1 15.5 1zm-4 21c-.83 0-1.5-.67-1.5-1.5s.67-1.5 1.5-1.5 1.5.67 1.5 1.5-.67 1.5-1.5 1.5zm4.5-4H7V4h9v14z"/></svg></div><span class="card-title">App Dev Tools</span>
            </a>
            <a class="course-card" data-course-name="Ethical Security" data-course-price="Rs. 2500">
                <div class="card-icon"><svg viewBox="0 0 24 24"><path d="M12 1L3 5v6c0 5.55 3.84 10.74 9 12 5.16-1.26 9-6.45 9-12V5l-9-4zm-1 6h2v2h-2V7zm0 4h2v6h-2v-6z"/></svg></div><span class="card-title">Ethical Security</span>
            </a>
            
            <!-- Row 2 -->
            <a class="course-card alt-color" data-course-name="Data Science" data-course-price="Rs. 3000">
                <div class="card-icon"><svg viewBox="0 0 24 24"><path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/></svg></div><span class="card-title">Data Science</span>
            </a>
            <a class="course-card alt-color" data-course-name="Cloud Basics" data-course-price="Rs. 1000">
                <div class="card-icon"><svg viewBox="0 0 24 24"><path d="M19.35 10.04C18.67 6.59 15.64 4 12 4 9.11 4 6.6 5.64 5.35 8.04 2.34 8.36 0 10.91 0 14c0 3.31 2.69 6 6 6h13c2.76 0 5-2.24 5-5 0-2.64-2.05-4.78-4.65-4.96z"/></svg></div><span class="card-title">Cloud Basics</span>
            </a>
            <a class="course-card alt-color" data-course-name="UI/UX Design" data-course-price="Rs. 1800">
                <div class="card-icon"><svg viewBox="0 0 24 24"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-1 17.93c-3.95-.49-7-3.85-7-7.93 0-.62.08-1.21.21-1.79L9 15v1c0 1.1.9 2 2 2v1.93zm6.9-2.54c-.26-.81-1-1.39-1.9-1.39h-1v-3c0-.55-.45-1-1-1H8v-2h2c.55 0 1-.45 1-1V7h2c1.1 0 2-.9 2-2v-.41c2.93 1.19 5 4.06 5 7.41 0 2.08-.8 3.97-2.1 5.39z"/></svg></div><span class="card-title">UI/UX Design</span>
            </a>

            <!-- Row 3 (New Courses) -->
            <a class="course-card" data-course-name="Email Marketing" data-course-price="Rs. 900">
                <div class="card-icon"><svg viewBox="0 0 24 24"><path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 14H4V8l8 5 8-5v10zm-8-7L4 6h16l-8 5z"/></svg></div><span class="card-title">Email Marketing</span>
            </a>
            <a class="course-card" data-course-name="SEO Mastery" data-course-price="Rs. 2200">
                <div class="card-icon"><svg viewBox="0 0 24 24"><path d="M15.5 14h-.79l-.28-.27A6.471 6.471 0 0 0 16 9.5 6.5 6.5 0 1 0 9.5 16c1.61 0 3.09-.59 4.23-1.57l.27.28v.79l5 4.99L20.49 19l-4.99-5zm-6 0C7.01 14 5 11.99 5 9.5S7.01 5 9.5 5 14 7.01 14 9.5 11.99 14 9.5 14z"/></svg></div><span class="card-title">SEO Mastery</span>
            </a>
            <a class="course-card" data-course-name="Video Editing" data-course-price="Rs. 2800">
                <div class="card-icon"><svg viewBox="0 0 24 24"><path d="M10 16.5l6-4.5-6-4.5v9zM12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8z"/></svg></div><span class="card-title">Video Editing</span>
            </a>

            <!-- Row 4 (New Courses) -->
             <a class="course-card alt-color" data-course-name="Graphic Design" data-course-price="Rs. 1700">
                <div class="card-icon"><svg viewBox="0 0 24 24"><path d="M3 17.25V21h3.75L17.81 9.94l-3.75-3.75L3 17.25zM20.71 7.04c.39-.39.39-1.02 0-1.41l-2.34-2.34c-.39-.39-1.02-.39-1.41 0l-1.83 1.83 3.75 3.75 1.83-1.83z"/></svg></div><span class="card-title">Graphic Design</span>
            </a>
            <a class="course-card alt-color" data-course-name="Social Media" data-course-price="Rs. 1200">
                <div class="card-icon"><svg viewBox="0 0 24 24"><path d="M16 11c1.66 0 2.99-1.34 2.99-3S17.66 5 16 5c-1.66 0-3 1.34-3 3s1.34 3 3 3zm-8 0c1.66 0 2.99-1.34 2.99-3S9.66 5 8 5C6.34 5 5 6.34 5 8s1.34 3 3 3zm0 2c-2.33 0-7 1.17-7 3.5V19h14v-2.5c0-2.33-4.67-3.5-7-3.5zm8 0c-.29 0-.62.02-.97.05 1.16.84 1.97 1.97 1.97 3.45V19h6v-2.5c0-2.33-4.67-3.5-7-3.5z"/></svg></div><span class="card-title">Social Media</span>
            </a>
            <a class="course-card alt-color" data-course-name="Python Basics" data-course-price="Rs. 3500">
                <div class="card-icon"><svg viewBox="0 0 24 24"><path d="M9.4 16.6L4.8 12l4.6-4.6L8 6l-6 6 6 6 1.4-1.4zm5.2 0l4.6-4.6-4.6-4.6L16 6l6 6-6 6-1.4-1.4z"/></svg></div><span class="card-title">Python Basics</span>
            </a>
        </div>
    </main>

    <!-- Ad Placeholder 2 -->
    <div class="ad-placeholder" style="min-height: 90px; margin-top: 20px;">
        <p>Large Ad Area (300x90)</p>
    </div>

    <!-- The Payment Modal (UNCHANGED) -->
    <div id="paymentModal" class="payment-modal">
        <div class="modal-content">
            <span class="close-button">×</span>
            <div class="modal-header">
                <h2>Purchase Course</h2>
                <p><span id="modal-course-name">Course Name</span> - <strong id="modal-course-price">Price</strong></p>
            </div>
            <div class="payment-details">
                <h3>JazzCash</h3>
                <div class="payment-info">
                    <p><span class="label">Name:</span> Bibi Razia</p>
                    <div class="info-line">
                         <p><span class="label">Number:</span> <span id="jazzcash-number">03052010757</span></p>
                         <button class="copy-btn" onclick="copyToClipboard('jazzcash-number', this)">Copy</button>
                    </div>
                </div>
                <h3>Easypaisa</h3>
                <div class="payment-info">
                    <p><span class="label">Name:</span> Bibi razia</p>
                    <div class="info-line">
                        <p><span class="label">Number:</span> <span id="easypaisa-number">03473945995</span></p>
                        <button class="copy-btn" onclick="copyToClipboard('easypaisa-number', this)">Copy</button>
                    </div>
                </div>
                <h3>Crypto Address</h3>
                <div class="payment-info">
                    <p><span class="label">Bitcoin (BTC):</span></p>
                    <div class="info-line">
                        <p style="word-break: break-all; font-size: 12px;" id="btc-address">1A1DhHUghwcx8SJu3qZ32gHFfXTNz9v2jr</p>
                        <button class="copy-btn alt" onclick="copyToClipboard('btc-address', this)">Copy</button>
                    </div>
                </div>
                 <div class="payment-info">
                    <p><span class="label">Tether (USDT TRC20):</span></p>
                    <div class="info-line">
                         <p style="word-break: break-all; font-size: 12px;" id="usdt-address">TKBFxayCBW4U3CA5VoywYCexwMoxMJm3AX</p>
                         <button class="copy-btn alt" onclick="copyToClipboard('usdt-address', this)">Copy</button>
                    </div>
                </div>
            </div>
            <form class="user-form" id="payment-form">
                <p style="font-size:14px; margin-bottom:15px; text-align:center;">After payment, enter your details below and submit.</p>
                <input type="email" id="user-email" placeholder="Enter Your Email" required>
                <input type="text" id="transaction-id" placeholder="Enter Transaction ID / TXID" required>
                <button type="submit" class="submit-btn">Submit Details</button>
            </form>
        </div>
    </div>

<script>
    // --- JAVASCRIPT FOR MODAL FUNCTIONALITY (UNCHANGED) ---
    const modal = document.getElementById("paymentModal");
    const modalCourseName = document.getElementById("modal-course-name");
    const modalCoursePrice = document.getElementById("modal-course-price");
    const closeButton = document.querySelector(".close-button");
    const courseCards = document.querySelectorAll(".course-card");
    const paymentForm = document.getElementById("payment-form");

    courseCards.forEach(card => {
        card.addEventListener("click", function() {
            const courseName = this.dataset.courseName;
            const coursePrice = this.dataset.coursePrice;
            modalCourseName.textContent = courseName;
            modalCoursePrice.textContent = coursePrice;
            modal.style.display = "flex";
        });
    });

    function closeModal() {
        modal.style.display = "none";
    }

    closeButton.addEventListener("click", closeModal);

    window.addEventListener("click", function(event) {
        if (event.target == modal) {
            closeModal();
        }
    });

    function copyToClipboard(elementId, button) {
        const textToCopy = document.getElementById(elementId).innerText;
        navigator.clipboard.writeText(textToCopy).then(() => {
            const originalText = button.innerText;
            button.innerText = "Copied!";
            setTimeout(() => {
                button.innerText = originalText;
            }, 1500);
        }).catch(err => {
            console.error('Failed to copy: ', err);
        });
    }

    paymentForm.addEventListener('submit', function(event) {
        event.preventDefault(); 
        const email = document.getElementById('user-email').value;
        const txId = document.getElementById('transaction-id').value;
        if (email && txId) {
            alert("Thank You!\nYour details have been submitted.\nWe will verify your payment and contact you at: " + email);
            paymentForm.reset();
            closeModal();
        } else {
            alert("Please fill in both your email and the transaction ID.");
        }
    });
</script>

</body>
</html>
