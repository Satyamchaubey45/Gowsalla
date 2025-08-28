<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>गौ माता रक्षा - पंचायत गौशाला योजना</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/qrcode@1.5.3/build/qrcode.min.js"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Noto+Sans+Devanagari:wght@300;400;500;600;700;800&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body { 
            font-family: 'Noto Sans Devanagari', sans-serif; 
            overflow-x: hidden;
        }
        
        /* Advanced Gradients */
        .gradient-bg { 
            background: linear-gradient(135deg, #ff9a56 0%, #ff6b35 50%, #ff4757 100%);
            position: relative;
        }
        .gradient-bg::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(45deg, transparent 30%, rgba(255,255,255,0.1) 50%, transparent 70%);
            animation: shimmer 3s infinite;
        }
        
        .admin-bg { 
            background: linear-gradient(135deg, #667eea 0%, #764ba2 50%, #8b5cf6 100%);
            position: relative;
        }
        .admin-bg::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(45deg, transparent 30%, rgba(255,255,255,0.1) 50%, transparent 70%);
            animation: shimmer 4s infinite;
        }
        
        .user-bg { 
            background: linear-gradient(135deg, #4facfe 0%, #00f2fe 50%, #0ea5e9 100%);
            position: relative;
        }
        .user-bg::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(45deg, transparent 30%, rgba(255,255,255,0.1) 50%, transparent 70%);
            animation: shimmer 3.5s infinite;
        }
        
        /* Advanced Card Animations */
        .card-hover { 
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            position: relative;
            overflow: hidden;
        }
        .card-hover::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: left 0.5s;
        }
        .card-hover:hover::before {
            left: 100%;
        }
        .card-hover:hover { 
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 25px 50px rgba(0,0,0,0.15);
        }
        
        /* Button Animations */
        .amount-btn { 
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            position: relative;
            overflow: hidden;
        }
        .amount-btn::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            background: rgba(255,255,255,0.3);
            border-radius: 50%;
            transform: translate(-50%, -50%);
            transition: width 0.3s, height 0.3s;
        }
        .amount-btn:hover::before {
            width: 300px;
            height: 300px;
        }
        .amount-btn:hover { 
            transform: scale(1.08) rotate(2deg);
            box-shadow: 0 10px 25px rgba(0,0,0,0.2);
        }
        .amount-btn.selected { 
            background: linear-gradient(135deg, #10b981, #059669) !important; 
            color: white !important; 
            transform: scale(1.08);
            box-shadow: 0 10px 25px rgba(16, 185, 129, 0.4);
        }
        
        /* Hero Section with Particles */
        .hero-section { 
            background: linear-gradient(135deg, rgba(255,154,86,0.95) 0%, rgba(255,107,53,0.95) 50%, rgba(255,71,87,0.95) 100%);
            position: relative;
            overflow: hidden;
        }
        .hero-section::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-image: 
                radial-gradient(circle at 20% 80%, rgba(255,255,255,0.1) 2px, transparent 2px),
                radial-gradient(circle at 80% 20%, rgba(255,255,255,0.1) 2px, transparent 2px),
                radial-gradient(circle at 40% 40%, rgba(255,255,255,0.05) 1px, transparent 1px);
            background-size: 100px 100px, 150px 150px, 80px 80px;
            animation: float 20s infinite linear;
        }
        
        /* Advanced Activity Animation */
        .activity-item {
            animation: slideInBounce 0.6s cubic-bezier(0.68, -0.55, 0.265, 1.55);
            transform-origin: left center;
        }
        
        /* Payment Method Buttons */
        .payment-method-btn { 
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            position: relative;
            overflow: hidden;
        }
        .payment-method-btn::after {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            transition: left 0.5s;
        }
        .payment-method-btn:hover::after {
            left: 100%;
        }
        .payment-method-btn:hover { 
            transform: scale(1.05) translateY(-2px);
            box-shadow: 0 8px 20px rgba(0,0,0,0.15);
        }
        .payment-method-btn.selected { 
            background: linear-gradient(135deg, #3b82f6, #1d4ed8) !important; 
            color: white !important; 
            transform: scale(1.05);
            box-shadow: 0 8px 20px rgba(59, 130, 246, 0.4);
        }
        
        /* Feed Type Buttons */
        .feed-type-btn { 
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            position: relative;
            overflow: hidden;
        }
        .feed-type-btn:hover { 
            transform: scale(1.05) translateY(-2px);
            box-shadow: 0 8px 20px rgba(0,0,0,0.15);
        }
        .feed-type-btn.selected { 
            background: linear-gradient(135deg, #10b981, #059669) !important; 
            color: white !important; 
            transform: scale(1.05);
            box-shadow: 0 8px 20px rgba(16, 185, 129, 0.4);
        }
        
        /* QR Code Container */
        .qr-container {
            background: linear-gradient(135deg, #f8fafc 0%, #e2e8f0 100%);
            border: 2px solid #e2e8f0;
            position: relative;
        }
        
        /* Modal Animations */
        .modal-enter {
            animation: modalEnter 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }
        .modal-exit {
            animation: modalExit 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        /* Stats Counter Animation */
        .stat-number {
            animation: countUp 1s ease-out;
        }
        
        /* Loading Animation */
        .loading-spinner {
            width: 40px;
            height: 40px;
            border: 4px solid #f3f4f6;
            border-top: 4px solid #3b82f6;
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }
        
        /* Floating Elements */
        .float-element {
            animation: float 6s ease-in-out infinite;
        }
        
        /* Keyframes */
        @keyframes shimmer {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(100%); }
        }
        
        @keyframes slideInBounce {
            0% { 
                opacity: 0; 
                transform: translateX(-50px) scale(0.8); 
            }
            60% { 
                opacity: 1; 
                transform: translateX(10px) scale(1.05); 
            }
            100% { 
                opacity: 1; 
                transform: translateX(0) scale(1); 
            }
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0px) translateX(0px); }
            25% { transform: translateY(-10px) translateX(5px); }
            50% { transform: translateY(0px) translateX(10px); }
            75% { transform: translateY(-5px) translateX(5px); }
        }
        
        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }
        
        @keyframes rotate {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        @keyframes modalEnter {
            0% { 
                opacity: 0; 
                transform: scale(0.8) translateY(-50px); 
            }
            100% { 
                opacity: 1; 
                transform: scale(1) translateY(0); 
            }
        }
        
        @keyframes modalExit {
            0% { 
                opacity: 1; 
                transform: scale(1) translateY(0); 
            }
            100% { 
                opacity: 0; 
                transform: scale(0.8) translateY(-50px); 
            }
        }
        
        @keyframes countUp {
            0% { 
                opacity: 0; 
                transform: translateY(20px); 
            }
            100% { 
                opacity: 1; 
                transform: translateY(0); 
            }
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        /* Glassmorphism Effect */
        .glass {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        /* Neon Glow Effect */
        .neon-glow {
            box-shadow: 0 0 20px rgba(59, 130, 246, 0.5);
            animation: neonPulse 2s infinite alternate;
        }
        
        @keyframes neonPulse {
            0% { box-shadow: 0 0 20px rgba(59, 130, 246, 0.5); }
            100% { box-shadow: 0 0 30px rgba(59, 130, 246, 0.8); }
        }
        
        /* Responsive Improvements */
        @media (max-width: 768px) {
            .card-hover:hover {
                transform: translateY(-5px) scale(1.01);
            }
            .amount-btn:hover {
                transform: scale(1.03);
            }
        }
    </style>
</head>
<body class="bg-gradient-to-br from-orange-50 to-yellow-50 min-h-screen">
    <!-- Main Home Page -->
    <div id="homePage" class="min-h-screen">
        <!-- Header -->
        <header class="bg-white shadow-lg relative">
            <div class="container mx-auto px-4 py-4">
                <div class="flex items-center justify-between">
                    <div class="flex items-center space-x-3">
                        <div class="text-3xl md:text-4xl">🐄</div>
                        <div>
                            <h1 class="text-lg md:text-2xl font-bold text-gray-800">गौ माता रक्षा योजना</h1>
                            <p class="text-xs md:text-sm text-gray-600">पंचायत गौशाला सेवा</p>
                        </div>
                    </div>
                    
                    <!-- Mobile Menu Button -->
                    <button type="button" onclick="toggleMobileMenu()" class="md:hidden flex flex-col space-y-1 p-2 cursor-pointer">
                        <div class="w-6 h-0.5 bg-gray-600"></div>
                        <div class="w-6 h-0.5 bg-gray-600"></div>
                        <div class="w-6 h-0.5 bg-gray-600"></div>
                    </button>
                    
                    <!-- Desktop Menu -->
                    <div class="hidden md:flex items-center space-x-4">
                        <button type="button" onclick="showUserLogin()" class="bg-blue-500 hover:bg-blue-600 text-white px-6 py-2 rounded-lg font-semibold transition-colors cursor-pointer">
                            दान करें
                        </button>
                        <button type="button" onclick="showAdminLogin()" class="bg-purple-500 hover:bg-purple-600 text-white px-6 py-2 rounded-lg font-semibold transition-colors cursor-pointer">
                            Admin
                        </button>
                    </div>
                </div>
                
                <!-- Mobile Menu -->
                <div id="mobileMenu" class="hidden md:hidden absolute top-full left-0 right-0 bg-white shadow-lg border-t z-50">
                    <div class="p-4 space-y-3">
                        <button type="button" onclick="showUserLogin(); hideMobileMenu();" class="w-full bg-blue-500 hover:bg-blue-600 text-white px-6 py-3 rounded-lg font-semibold transition-colors cursor-pointer">
                            🙏 दान करें
                        </button>
                        <button type="button" onclick="showAdminLogin(); hideMobileMenu();" class="w-full bg-purple-500 hover:bg-purple-600 text-white px-6 py-3 rounded-lg font-semibold transition-colors cursor-pointer">
                            👨‍💼 Admin
                        </button>
                    </div>
                </div>
            </div>
        </header>

        <!-- Hero Section -->
        <section class="hero-section text-white py-12 md:py-20 relative">
            <div class="container mx-auto px-4 text-center relative z-10">
                <div class="text-6xl md:text-8xl mb-4 md:mb-6 float-element">🐄</div>
                <h2 class="text-3xl md:text-5xl font-bold mb-4 md:mb-6 stat-number">गौ माता की सेवा करें</h2>
                <p class="text-base md:text-xl mb-6 md:mb-8 max-w-3xl mx-auto px-2 stat-number">गौ माता हमारी संस्कृति का अभिन्न अंग हैं। आपका छोटा सा दान भी गौ माता की सेवा में महत्वपूर्ण योगदान देगा।</p>
                <div class="flex justify-center">
                    <button type="button" onclick="showUserLogin()" class="bg-white text-orange-600 px-6 md:px-8 py-3 md:py-4 rounded-lg font-bold text-base md:text-lg hover:bg-gray-100 transition-all duration-300 cursor-pointer neon-glow hover:scale-105">
                        🙏 अभी दान करें
                    </button>
                </div>
            </div>
            
            <!-- Floating Elements -->
            <div class="absolute top-10 left-10 text-4xl opacity-20 float-element" style="animation-delay: 0s;">🌸</div>
            <div class="absolute top-20 right-20 text-3xl opacity-20 float-element" style="animation-delay: 1s;">🕉️</div>
            <div class="absolute bottom-20 left-20 text-5xl opacity-20 float-element" style="animation-delay: 2s;">🙏</div>
            <div class="absolute bottom-10 right-10 text-4xl opacity-20 float-element" style="animation-delay: 3s;">🌺</div>
        </section>

        <!-- Statistics Section -->
        <section class="py-12 md:py-16 gradient-bg text-white">
            <div class="container mx-auto px-4">
                <h3 class="text-2xl md:text-4xl font-bold text-center mb-8 md:mb-12">📊 हमारी उपलब्धियां</h3>
                <div class="grid grid-cols-2 md:grid-cols-4 gap-4 md:gap-6">
                    <div class="text-center glass rounded-lg p-4 md:p-6 card-hover">
                        <div class="text-2xl md:text-4xl font-bold mb-2 stat-number" id="homeStatPanchayats">0</div>
                        <div class="text-orange-100 text-sm md:text-base">गौशालाएं</div>
                    </div>
                    <div class="text-center glass rounded-lg p-4 md:p-6 card-hover">
                        <div class="text-2xl md:text-4xl font-bold mb-2 stat-number" id="homeStatDonations">₹0</div>
                        <div class="text-orange-100 text-sm md:text-base">कुल दान राशि</div>
                    </div>
                    <div class="text-center glass rounded-lg p-4 md:p-6 card-hover">
                        <div class="text-2xl md:text-4xl font-bold mb-2 stat-number" id="homeStatDonors">0</div>
                        <div class="text-orange-100 text-sm md:text-base">दानदाता</div>
                    </div>
                    <div class="text-center glass rounded-lg p-4 md:p-6 card-hover">
                        <div class="text-2xl md:text-4xl font-bold mb-2 stat-number" id="homeStatCows">0</div>
                        <div class="text-orange-100 text-sm md:text-base">गौ माता</div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Footer -->
        <footer class="bg-gray-800 text-white py-8">
            <div class="container mx-auto px-4 text-center">
                <div class="text-4xl mb-4">🐄</div>
                <p class="text-gray-300 mb-4">गौ माता रक्षा योजना - सभी गौ माता की सेवा में समर्पित</p>
                <p class="text-sm text-gray-400">© 2024 गौ माता रक्षा योजना। सभी अधिकार सुरक्षित।</p>
            </div>
        </footer>
    </div>

    <!-- User Login Modal -->
    <div id="userLoginModal" class="fixed inset-0 bg-black bg-opacity-50 hidden items-center justify-center z-50 p-4">
        <div class="bg-white rounded-xl p-6 md:p-8 max-w-md w-full">
            <div class="text-center mb-6">
                <div class="text-6xl mb-4">🙏</div>
                <h3 class="text-2xl font-bold text-gray-800">दान करने के लिए प्रवेश करें</h3>
            </div>
            
            <form onsubmit="userLogin(event)">
                <div class="mb-4">
                    <label class="block text-gray-700 font-semibold mb-2">आपका नाम *</label>
                    <input type="text" id="userLoginName" required class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500">
                </div>
                <div class="mb-6">
                    <label class="block text-gray-700 font-semibold mb-2">मोबाइल नंबर *</label>
                    <input type="tel" id="userLoginPhone" required class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500">
                </div>
                <div class="flex space-x-4">
                    <button type="submit" class="flex-1 bg-blue-500 hover:bg-blue-600 text-white py-3 rounded-lg font-semibold">
                        प्रवेश करें
                    </button>
                    <button type="button" onclick="hideUserLogin()" class="flex-1 bg-gray-300 hover:bg-gray-400 text-gray-700 py-3 rounded-lg font-semibold">
                        रद्द करें
                    </button>
                </div>
            </form>
        </div>
    </div>

    <!-- Admin Login Modal -->
    <div id="adminLoginModal" class="fixed inset-0 bg-black bg-opacity-50 hidden items-center justify-center z-50 p-4">
        <div class="bg-white rounded-xl p-6 md:p-8 max-w-md w-full">
            <h3 class="text-2xl font-bold mb-6 text-gray-800 text-center">👨‍💼 एडमिन लॉगिन</h3>
            <form onsubmit="adminLogin(event)">
                <div class="mb-4">
                    <label class="block text-gray-700 font-semibold mb-2">यूजरनेम</label>
                    <input type="text" id="adminUsername" required class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                </div>
                <div class="mb-6">
                    <label class="block text-gray-700 font-semibold mb-2">पासवर्ड</label>
                    <input type="password" id="adminPassword" required class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                </div>
                <div class="mb-4">
                    <button type="button" onclick="showPanchayatRegistration()" class="w-full bg-green-500 hover:bg-green-600 text-white py-2 rounded-lg font-semibold mb-2">
                        🏠 नई पंचायत रजिस्ट्रेशन
                    </button>
                </div>
                <div class="flex space-x-4">
                    <button type="submit" class="flex-1 bg-purple-500 hover:bg-purple-600 text-white py-3 rounded-lg font-semibold">
                        लॉगिन करें
                    </button>
                    <button type="button" onclick="hideAdminLogin()" class="flex-1 bg-gray-300 hover:bg-gray-400 text-gray-700 py-3 rounded-lg font-semibold">
                        रद्द करें
                    </button>
                </div>
            </form>
        </div>
    </div>

    <!-- User Dashboard -->
    <div id="userDashboard" class="min-h-screen hidden">
        <header class="user-bg text-white py-4 md:py-6 shadow-lg relative">
            <div class="container mx-auto px-4">
                <div class="flex items-center justify-between">
                    <div class="flex items-center space-x-3">
                        <div class="text-3xl md:text-4xl">🙏</div>
                        <div>
                            <h1 class="text-lg md:text-2xl font-bold">गौ माता सेवा</h1>
                            <p class="text-blue-100 text-sm md:text-base" id="userWelcome">स्वागत है</p>
                        </div>
                    </div>
                    
                    <!-- Mobile Menu Button -->
                    <button onclick="toggleUserMobileMenu()" class="md:hidden flex flex-col space-y-1 p-2">
                        <div class="w-6 h-0.5 bg-white"></div>
                        <div class="w-6 h-0.5 bg-white"></div>
                        <div class="w-6 h-0.5 bg-white"></div>
                    </button>
                    
                    <!-- Desktop Menu -->
                    <div class="hidden md:flex items-center space-x-6">
                        <nav class="flex space-x-6">
                            <button onclick="showUserSection('userDonate')" class="hover:text-blue-200">दान करें</button>
                            <button onclick="showUserSection('userFeed')" class="hover:text-blue-200">चारा दान</button>
                            <button onclick="showUserSection('userHistory')" class="hover:text-blue-200">मेरा इतिहास</button>
                            <button onclick="showUserSection('userDonors')" class="hover:text-blue-200">दानदाता सूची</button>
                        </nav>
                        <!-- Notification Bell -->
                        <div class="relative">
                            <button onclick="toggleNotifications()" class="relative bg-black hover:bg-gray-800 text-white p-2 rounded-full">
                                🔔
                                <span id="notificationBadge" class="absolute -top-1 -right-1 bg-red-500 text-white text-xs rounded-full w-5 h-5 flex items-center justify-center hidden">0</span>
                            </button>
                            <!-- Notification Dropdown -->
                            <div id="notificationDropdown" class="absolute right-0 mt-2 w-80 bg-white rounded-lg shadow-lg border hidden z-50">
                                <div class="p-4 border-b">
                                    <h3 class="font-bold text-gray-800">📢 नोटिफिकेशन</h3>
                                </div>
                                <div id="notificationList" class="max-h-64 overflow-y-auto">
                                    <div class="p-4 text-center text-gray-500">कोई नोटिफिकेशन नहीं</div>
                                </div>
                            </div>
                        </div>
                        <button onclick="logout()" class="bg-blue-600 hover:bg-blue-700 px-4 py-2 rounded-lg">
                            लॉगआउट
                        </button>
                    </div>
                </div>
                
                <!-- Mobile Menu -->
                <div id="userMobileMenu" class="hidden md:hidden absolute top-full left-0 right-0 bg-blue-600 shadow-lg border-t border-blue-500 z-50">
                    <div class="p-4 space-y-3">
                        <button onclick="showUserSection('userDonate'); hideUserMobileMenu();" class="w-full text-left text-white hover:text-blue-200 py-2 px-3 rounded">
                            🙏 दान करें
                        </button>
                        <button onclick="showUserSection('userFeed'); hideUserMobileMenu();" class="w-full text-left text-white hover:text-blue-200 py-2 px-3 rounded">
                            🌾 चारा दान
                        </button>
                        <button onclick="showUserSection('userHistory'); hideUserMobileMenu();" class="w-full text-left text-white hover:text-blue-200 py-2 px-3 rounded">
                            📋 मेरा इतिहास
                        </button>
                        <button onclick="showUserSection('userDonors'); hideUserMobileMenu();" class="w-full text-left text-white hover:text-blue-200 py-2 px-3 rounded">
                            👥 दानदाता सूची
                        </button>
                        <button onclick="toggleNotifications(); hideUserMobileMenu();" class="w-full text-left text-white hover:text-blue-200 py-2 px-3 rounded">
                            🔔 नोटिफिकेशन
                        </button>
                        <button onclick="logout()" class="w-full bg-blue-700 hover:bg-blue-800 text-white py-2 px-3 rounded-lg mt-2">
                            🚪 लॉगआउट
                        </button>
                    </div>
                </div>
            </div>
        </header>

        <main class="container mx-auto px-4 py-8">
            <!-- User Donate Section -->
            <section id="userDonate" class="user-section-content">
                <h2 class="text-3xl font-bold text-center mb-8 text-gray-800">🙏 गौ माता सेवा हेतु दान करें</h2>
                
                <div class="max-w-2xl mx-auto bg-white rounded-xl p-8 shadow-lg">
                    <form onsubmit="processUserDonation(event)">
                        <div class="mb-6">
                            <label class="block text-gray-700 font-semibold mb-2">पंचायत चुनें *</label>
                            <select id="userDonationPanchayat" required class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                                <option value="">पंचायत चुनें</option>
                            </select>
                        </div>

                        <div class="mb-6">
                            <label class="block text-gray-700 font-semibold mb-2">दान राशि चुनें *</label>
                            <div class="grid grid-cols-3 gap-3 mb-4">
                                <button type="button" onclick="selectAmount(51)" class="amount-btn bg-gray-100 hover:bg-blue-500 hover:text-white py-3 rounded-lg font-semibold">₹51</button>
                                <button type="button" onclick="selectAmount(101)" class="amount-btn bg-gray-100 hover:bg-blue-500 hover:text-white py-3 rounded-lg font-semibold">₹101</button>
                                <button type="button" onclick="selectAmount(251)" class="amount-btn bg-gray-100 hover:bg-blue-500 hover:text-white py-3 rounded-lg font-semibold">₹251</button>
                                <button type="button" onclick="selectAmount(501)" class="amount-btn bg-gray-100 hover:bg-blue-500 hover:text-white py-3 rounded-lg font-semibold">₹501</button>
                                <button type="button" onclick="selectAmount(1001)" class="amount-btn bg-gray-100 hover:bg-blue-500 hover:text-white py-3 rounded-lg font-semibold">₹1001</button>
                                <button type="button" onclick="selectAmount(2100)" class="amount-btn bg-gray-100 hover:bg-blue-500 hover:text-white py-3 rounded-lg font-semibold">₹2100</button>
                            </div>
                            <input type="number" id="userDonationAmount" placeholder="या अपनी राशि लिखें" min="51" class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                        </div>

                        <div class="mb-6">
                            <label class="block text-gray-700 font-semibold mb-2">भुगतान विधि चुनें *</label>
                            <div class="grid grid-cols-2 gap-3 mb-4">
                                <button type="button" onclick="selectPaymentMethod('qr')" class="payment-method-btn bg-gray-100 hover:bg-blue-500 hover:text-white py-3 rounded-lg font-semibold">📱 QR कोड</button>
                                <button type="button" onclick="selectPaymentMethod('bank')" class="payment-method-btn bg-gray-100 hover:bg-blue-500 hover:text-white py-3 rounded-lg font-semibold">🏦 बैंक ट्रांसफर</button>
                                <button type="button" onclick="selectPaymentMethod('cash')" class="payment-method-btn bg-gray-100 hover:bg-blue-500 hover:text-white py-3 rounded-lg font-semibold">💵 नकद</button>
                                <button type="button" onclick="selectPaymentMethod('other')" class="payment-method-btn bg-gray-100 hover:bg-blue-500 hover:text-white py-3 rounded-lg font-semibold">🔄 अन्य</button>
                            </div>
                            <input type="hidden" id="selectedPaymentMethod" required>
                        </div>

                        <button type="submit" class="w-full bg-blue-500 hover:bg-blue-600 text-white py-4 rounded-lg font-bold text-lg">
                            🙏 दान करें
                        </button>
                    </form>
                </div>
            </section>

            <!-- User Feed Section -->
            <section id="userFeed" class="user-section-content hidden">
                <h2 class="text-3xl font-bold text-center mb-8 text-gray-800">🌾 गौ माता के लिए चारा दान करें</h2>
                
                <div class="max-w-2xl mx-auto bg-white rounded-xl p-8 shadow-lg">
                    <form onsubmit="processUserFeedDonation(event)">
                        <div class="mb-6">
                            <label class="block text-gray-700 font-semibold mb-2">पंचायत चुनें *</label>
                            <select id="userFeedPanchayat" required class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                                <option value="">पंचायत चुनें</option>
                            </select>
                        </div>

                        <div class="mb-6">
                            <label class="block text-gray-700 font-semibold mb-2">चारे का प्रकार *</label>
                            <div class="grid grid-cols-2 gap-3 mb-4">
                                <button type="button" onclick="selectFeedType('bhusa')" class="feed-type-btn bg-gray-100 hover:bg-green-500 hover:text-white py-3 rounded-lg font-semibold">🌾 भूसा</button>
                                <button type="button" onclick="selectFeedType('grass')" class="feed-type-btn bg-gray-100 hover:bg-green-500 hover:text-white py-3 rounded-lg font-semibold">🌱 हरी घास</button>
                                <button type="button" onclick="selectFeedType('hay')" class="feed-type-btn bg-gray-100 hover:bg-green-500 hover:text-white py-3 rounded-lg font-semibold">🌿 सूखी घास</button>
                                <button type="button" onclick="selectFeedType('grains')" class="feed-type-btn bg-gray-100 hover:bg-green-500 hover:text-white py-3 rounded-lg font-semibold">🌾 अनाज</button>
                            </div>
                            <input type="hidden" id="selectedFeedType" required>
                        </div>

                        <div class="mb-6">
                            <label class="block text-gray-700 font-semibold mb-2">मात्रा (किलो में) *</label>
                            <input type="number" id="userFeedQuantity" placeholder="मात्रा किलो में" min="1" required class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                        </div>

                        <div class="mb-6">
                            <div class="bg-green-50 p-4 rounded-lg">
                                <p class="text-sm text-gray-600 mb-2">📝 नोट: चारा दान में पैसे की जरूरत नहीं है</p>
                                <p class="text-xs text-blue-600">आप सीधे चारा दान कर सकते हैं</p>
                            </div>
                        </div>

                        <button type="submit" class="w-full bg-green-500 hover:bg-green-600 text-white py-4 rounded-lg font-bold text-lg">
                            🌾 चारा दान करें (बिना पेमेंट)
                        </button>
                    </form>
                </div>
            </section>

            <!-- User History Section -->
            <section id="userHistory" class="user-section-content hidden">
                <h2 class="text-3xl font-bold text-center mb-8 text-gray-800">📋 मेरा दान इतिहास</h2>
                <div id="userHistoryList" class="space-y-4">
                    <!-- User's donation history will be loaded here -->
                </div>
            </section>

            <!-- User Donors Section -->
            <section id="userDonors" class="user-section-content hidden">
                <h2 class="text-3xl font-bold text-center mb-8 text-gray-800">🙏 सम्मानित दानदाता सूची</h2>
                <div id="userDonorsList" class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
                    <!-- Donors will be loaded here -->
                </div>
            </section>
        </main>
    </div>

    <!-- Admin Dashboard -->
    <div id="adminDashboard" class="min-h-screen hidden">
        <header class="admin-bg text-white py-4 md:py-6 shadow-lg relative">
            <div class="container mx-auto px-4">
                <div class="flex items-center justify-between">
                    <div class="flex items-center space-x-3">
                        <div class="text-3xl md:text-4xl">👨‍💼</div>
                        <div>
                            <h1 class="text-lg md:text-2xl font-bold">एडमिन पैनल - गौ माता रक्षा</h1>
                            <p class="text-purple-100 text-sm md:text-base">प्रबंधन डैशबोर्ड</p>
                        </div>
                    </div>
                    
                    <!-- Mobile Menu Button -->
                    <button onclick="toggleAdminMobileMenu()" class="md:hidden flex flex-col space-y-1 p-2">
                        <div class="w-6 h-0.5 bg-white"></div>
                        <div class="w-6 h-0.5 bg-white"></div>
                        <div class="w-6 h-0.5 bg-white"></div>
                    </button>
                    
                    <!-- Desktop Menu -->
                    <div class="hidden md:flex items-center space-x-6">
                        <nav class="flex space-x-6">
                            <button onclick="showAdminSection('adminHome')" class="hover:text-purple-200">डैशबोर्ड</button>
                            <button onclick="showAdminSection('adminPanchayats')" class="hover:text-purple-200">पंचायत</button>
                            <button onclick="showAdminSection('adminCows')" class="hover:text-purple-200">गौ माता</button>
                            <button onclick="showAdminSection('adminBulls')" class="hover:text-purple-200">सांड</button>
                            <button onclick="showAdminSection('adminDonations')" class="hover:text-purple-200">दान</button>
                            <button onclick="showAdminSection('adminFeed')" class="hover:text-purple-200">चारा</button>
                            <button onclick="showAdminSection('adminPayments')" class="hover:text-purple-200">भुगतान</button>
                        </nav>
                        <button onclick="logout()" class="bg-purple-600 hover:bg-purple-700 px-4 py-2 rounded-lg">
                            लॉगआउट
                        </button>
                    </div>
                </div>
                
                <!-- Mobile Menu -->
                <div id="adminMobileMenu" class="hidden md:hidden absolute top-full left-0 right-0 bg-purple-600 shadow-lg border-t border-purple-500 z-50">
                    <div class="p-4 space-y-3">
                        <button onclick="showAdminSection('adminHome'); hideAdminMobileMenu();" class="w-full text-left text-white hover:text-purple-200 py-2 px-3 rounded">
                            📊 डैशबोर्ड
                        </button>
                        <button onclick="showAdminSection('adminPanchayats'); hideAdminMobileMenu();" class="w-full text-left text-white hover:text-purple-200 py-2 px-3 rounded">
                            🏠 पंचायत
                        </button>
                        <button onclick="showAdminSection('adminCows'); hideAdminMobileMenu();" class="w-full text-left text-white hover:text-purple-200 py-2 px-3 rounded">
                            🐄 गौ माता
                        </button>
                        <button onclick="showAdminSection('adminBulls'); hideAdminMobileMenu();" class="w-full text-left text-white hover:text-purple-200 py-2 px-3 rounded">
                            🐂 सांड
                        </button>
                        <button onclick="showAdminSection('adminDonations'); hideAdminMobileMenu();" class="w-full text-left text-white hover:text-purple-200 py-2 px-3 rounded">
                            💰 दान
                        </button>
                        <button onclick="showAdminSection('adminFeed'); hideAdminMobileMenu();" class="w-full text-left text-white hover:text-purple-200 py-2 px-3 rounded">
                            🌾 चारा
                        </button>
                        <button onclick="showAdminSection('adminPayments'); hideAdminMobileMenu();" class="w-full text-left text-white hover:text-purple-200 py-2 px-3 rounded">
                            💳 भुगतान
                        </button>
                        <button onclick="logout()" class="w-full bg-purple-700 hover:bg-purple-800 text-white py-2 px-3 rounded-lg mt-2">
                            🚪 लॉगआउट
                        </button>
                    </div>
                </div>
            </div>
        </header>

        <main class="container mx-auto px-4 py-8">
            <!-- Admin Home Section -->
            <section id="adminHome" class="admin-section-content">
                <h2 class="text-3xl font-bold text-center mb-8 text-gray-800">📊 एडमिन डैशबोर्ड</h2>
                
                <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-6 gap-4 md:gap-6 mb-8">
                    <div class="bg-gradient-to-r from-blue-500 to-blue-600 text-white p-4 md:p-6 rounded-xl">
                        <div class="flex items-center justify-between">
                            <div>
                                <p class="text-blue-100 text-xs md:text-sm">कुल पंचायत</p>
                                <p class="text-2xl md:text-3xl font-bold" id="adminTotalPanchayats">0</p>
                            </div>
                            <div class="text-2xl md:text-4xl">🏠</div>
                        </div>
                    </div>
                    <div class="bg-gradient-to-r from-red-500 to-red-600 text-white p-4 md:p-6 rounded-xl">
                        <div class="flex items-center justify-between">
                            <div>
                                <p class="text-red-100 text-xs md:text-sm">कुल गौ माता</p>
                                <p class="text-2xl md:text-3xl font-bold" id="adminTotalCows">0</p>
                            </div>
                            <div class="text-2xl md:text-4xl">🐄</div>
                        </div>
                    </div>
                    <div class="bg-gradient-to-r from-yellow-500 to-yellow-600 text-white p-4 md:p-6 rounded-xl">
                        <div class="flex items-center justify-between">
                            <div>
                                <p class="text-yellow-100 text-xs md:text-sm">कुल सांड</p>
                                <p class="text-2xl md:text-3xl font-bold" id="adminTotalBulls">0</p>
                            </div>
                            <div class="text-2xl md:text-4xl">🐂</div>
                        </div>
                    </div>
                    <div class="bg-gradient-to-r from-green-500 to-green-600 text-white p-4 md:p-6 rounded-xl">
                        <div class="flex items-center justify-between">
                            <div>
                                <p class="text-green-100 text-xs md:text-sm">कुल दान राशि</p>
                                <p class="text-xl md:text-3xl font-bold" id="adminTotalAmount">₹0</p>
                            </div>
                            <div class="text-2xl md:text-4xl">💰</div>
                        </div>
                    </div>
                    <div class="bg-gradient-to-r from-purple-500 to-purple-600 text-white p-4 md:p-6 rounded-xl">
                        <div class="flex items-center justify-between">
                            <div>
                                <p class="text-purple-100 text-xs md:text-sm">कुल दानदाता</p>
                                <p class="text-2xl md:text-3xl font-bold" id="adminTotalDonors">0</p>
                            </div>
                            <div class="text-2xl md:text-4xl">👥</div>
                        </div>
                    </div>
                    <div class="bg-gradient-to-r from-orange-500 to-orange-600 text-white p-4 md:p-6 rounded-xl">
                        <div class="flex items-center justify-between">
                            <div>
                                <p class="text-orange-100 text-xs md:text-sm">आज के दान</p>
                                <p class="text-2xl md:text-3xl font-bold" id="adminTodayDonations">0</p>
                            </div>
                            <div class="text-2xl md:text-4xl">📅</div>
                        </div>
                    </div>
                </div>

                <div class="bg-white rounded-xl p-6 shadow-lg">
                    <h3 class="text-xl font-bold mb-4 text-gray-800">🔄 हाल की गतिविधियां (Real-Time)</h3>
                    <div id="recentActivities" class="space-y-3 max-h-96 overflow-y-auto">
                        <!-- Activities will be loaded here -->
                    </div>
                </div>
            </section>

            <!-- Admin Panchayats -->
            <section id="adminPanchayats" class="admin-section-content hidden">
                <div class="flex justify-between items-center mb-8">
                    <h2 class="text-3xl font-bold text-gray-800">पंचायत प्रबंधन</h2>
                    <button onclick="showAddPanchayatForm()" class="bg-purple-500 hover:bg-purple-600 text-white px-6 py-3 rounded-lg font-semibold">
                        + नई पंचायत जोड़ें
                    </button>
                </div>
                <div id="adminPanchayatsList" class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
                    <!-- Panchayats will be loaded here -->
                </div>
            </section>

            <!-- Admin Cows -->
            <section id="adminCows" class="admin-section-content hidden">
                <div class="flex justify-between items-center mb-8">
                    <h2 class="text-3xl font-bold text-gray-800">🐄 गौ माता प्रबंधन</h2>
                    <button onclick="showAddCowForm()" class="bg-red-500 hover:bg-red-600 text-white px-6 py-3 rounded-lg font-semibold">
                        + नई गौ माता जोड़ें
                    </button>
                </div>
                <div id="adminCowsList" class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
                    <!-- Cows will be loaded here -->
                </div>
            </section>

            <!-- Admin Bulls -->
            <section id="adminBulls" class="admin-section-content hidden">
                <div class="flex justify-between items-center mb-8">
                    <h2 class="text-3xl font-bold text-gray-800">🐂 सांड प्रबंधन</h2>
                    <button onclick="showAddBullForm()" class="bg-yellow-500 hover:bg-yellow-600 text-white px-6 py-3 rounded-lg font-semibold">
                        + नया सांड जोड़ें
                    </button>
                </div>
                <div id="adminBullsList" class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
                    <!-- Bulls will be loaded here -->
                </div>
            </section>

            <!-- Admin Donations -->
            <section id="adminDonations" class="admin-section-content hidden">
                <div class="flex justify-between items-center mb-8">
                    <h2 class="text-3xl font-bold text-gray-800">💰 दान प्रबंधन</h2>
                    <button onclick="generateDonationsPDF()" class="bg-red-500 hover:bg-red-600 text-white px-6 py-3 rounded-lg font-semibold">
                        📄 PDF डाउनलोड करें
                    </button>
                </div>
                <div class="bg-white rounded-xl shadow-lg overflow-hidden">
                    <div class="overflow-x-auto">
                        <table class="w-full text-sm md:text-base">
                            <thead class="bg-gray-50">
                                <tr>
                                    <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">दानदाता</th>
                                    <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">पंचायत</th>
                                    <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">राशि</th>
                                    <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">भुगतान विधि</th>
                                    <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">दिनांक</th>
                                    <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">कार्य</th>
                                </tr>
                            </thead>
                            <tbody id="adminDonationsTable" class="bg-white divide-y divide-gray-200">
                                <!-- Donations will be loaded here -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </section>

            <!-- Admin Feed -->
            <section id="adminFeed" class="admin-section-content hidden">
                <div class="flex justify-between items-center mb-8">
                    <h2 class="text-3xl font-bold text-gray-800">🌾 चारा प्रबंधन</h2>
                    <button onclick="generateFeedPDF()" class="bg-green-500 hover:bg-green-600 text-white px-6 py-3 rounded-lg font-semibold">
                        📄 PDF डाउनलोड करें
                    </button>
                </div>
                <div class="bg-white rounded-xl shadow-lg overflow-hidden">
                    <div class="overflow-x-auto">
                        <table class="w-full text-sm md:text-base">
                            <thead class="bg-gray-50">
                                <tr>
                                    <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">दानदाता</th>
                                    <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">पंचायत</th>
                                    <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">चारे का प्रकार</th>
                                    <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">मात्रा</th>
                                    <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">लागत</th>
                                    <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">दिनांक</th>
                                    <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase">कार्य</th>
                                </tr>
                            </thead>
                            <tbody id="adminFeedTable" class="bg-white divide-y divide-gray-200">
                                <!-- Feed donations will be loaded here -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </section>

            <!-- Admin Payments -->
            <section id="adminPayments" class="admin-section-content hidden">
                <h2 class="text-3xl font-bold text-center mb-8 text-gray-800">💳 भुगतान प्रबंधन</h2>
                
                <div class="grid md:grid-cols-2 gap-8">
                    <!-- QR Code Management -->
                    <div class="bg-white rounded-xl p-6 shadow-lg">
                        <h3 class="text-xl font-bold mb-4 text-gray-800">📱 QR कोड प्रबंधन</h3>
                        <div class="space-y-4">
                            <div>
                                <label class="block text-gray-700 font-semibold mb-2">UPI ID</label>
                                <input type="text" id="adminUpiId" value="gauraksha@paytm" class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                            </div>
                            <div>
                                <label class="block text-gray-700 font-semibold mb-2">प्राप्तकर्ता का नाम</label>
                                <input type="text" id="adminUpiName" value="Gau Mata Raksha" class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                            </div>
                            <div>
                                <label class="block text-gray-700 font-semibold mb-2">QR कोड इमेज अपलोड करें</label>
                                <input type="file" id="qrImageUpload" accept="image/*" onchange="handleQRImageUpload()" class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                                <p class="text-sm text-gray-500 mt-1">वैकल्पिक: अपना QR कोड इमेज अपलोड करें</p>
                                <div id="qrImagePreview" class="mt-2 hidden">
                                    <img id="qrPreviewImg" class="w-32 h-32 object-contain border rounded-lg" alt="QR Preview">
                                    <p class="text-sm text-green-600 mt-1">✅ QR कोड अपलोड हो गया</p>
                                </div>
                            </div>
                            <button onclick="updateQRSettings()" class="w-full bg-purple-500 hover:bg-purple-600 text-white py-3 rounded-lg font-semibold">
                                सेटिंग्स अपडेट करें
                            </button>
                        </div>
                    </div>

                    <!-- Bank Details -->
                    <div class="bg-white rounded-xl p-6 shadow-lg">
                        <h3 class="text-xl font-bold mb-4 text-gray-800">🏦 बैंक विवरण</h3>
                        <div class="space-y-4">
                            <div>
                                <label class="block text-gray-700 font-semibold mb-2">बैंक का नाम</label>
                                <input type="text" id="bankName" placeholder="बैंक का नाम" class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                            </div>
                            <div>
                                <label class="block text-gray-700 font-semibold mb-2">खाता संख्या</label>
                                <input type="text" id="accountNumber" placeholder="खाता संख्या" class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                            </div>
                            <div>
                                <label class="block text-gray-700 font-semibold mb-2">IFSC कोड</label>
                                <input type="text" id="ifscCode" placeholder="IFSC कोड" class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                            </div>
                            <div>
                                <label class="block text-gray-700 font-semibold mb-2">खाताधारक का नाम</label>
                                <input type="text" id="accountHolder" placeholder="खाताधारक का नाम" class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                            </div>
                            <button onclick="updateBankDetails()" class="w-full bg-blue-500 hover:bg-blue-600 text-white py-3 rounded-lg font-semibold">
                                बैंक विवरण अपडेट करें
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Notification System -->
                <div class="mt-8 bg-white rounded-xl p-6 shadow-lg">
                    <h3 class="text-xl font-bold mb-4 text-gray-800">📢 सभी यूजर्स को नोटिफिकेशन भेजें</h3>
                    <div class="space-y-4">
                        <div>
                            <label class="block text-gray-700 font-semibold mb-2">नोटिफिकेशन मैसेज</label>
                            <textarea id="notificationMessage" rows="3" placeholder="यहाँ अपना मैसेज लिखें..." class="w-full px-4 py-3 border border-gray-300 rounded-lg"></textarea>
                        </div>
                        <button onclick="sendNotificationToAll()" class="bg-red-500 hover:bg-red-600 text-white px-6 py-3 rounded-lg font-semibold">
                            📢 सभी को भेजें
                        </button>
                    </div>
                </div>

                <!-- Payment Statistics -->
                <div class="mt-8 bg-white rounded-xl p-6 shadow-lg">
                    <h3 class="text-xl font-bold mb-4 text-gray-800">📊 भुगतान आंकड़े</h3>
                    <div class="grid md:grid-cols-4 gap-6">
                        <div class="text-center">
                            <div class="text-3xl font-bold text-green-600" id="qrPayments">0</div>
                            <div class="text-gray-600">QR भुगतान</div>
                        </div>
                        <div class="text-center">
                            <div class="text-3xl font-bold text-blue-600" id="bankPayments">0</div>
                            <div class="text-gray-600">बैंक ट्रांसफर</div>
                        </div>
                        <div class="text-center">
                            <div class="text-3xl font-bold text-yellow-600" id="cashPayments">0</div>
                            <div class="text-gray-600">नकद भुगतान</div>
                        </div>
                        <div class="text-center">
                            <div class="text-3xl font-bold text-purple-600" id="otherPayments">0</div>
                            <div class="text-gray-600">अन्य भुगतान</div>
                        </div>
                    </div>
                </div>
            </section>
        </main>
    </div>

    <!-- Payment Modal -->
    <div id="paymentModal" class="fixed inset-0 bg-black bg-opacity-50 hidden items-center justify-center z-50 p-4">
        <div class="bg-white rounded-xl p-6 md:p-8 max-w-md w-full modal-enter glass">
            <h3 class="text-2xl font-bold mb-6 text-gray-800 text-center" id="paymentModalTitle">💳 भुगतान करें</h3>
            
            <div id="paymentContent" class="text-center mb-6">
                <!-- Payment content will be loaded here -->
            </div>

            <div class="flex space-x-4">
                <button onclick="confirmPayment()" class="w-full bg-green-500 hover:bg-green-600 text-white py-3 rounded-lg font-semibold transition-colors">
                    ✅ भुगतान पूर्ण
                </button>
                <button onclick="hidePaymentModal()" class="w-full bg-gray-300 hover:bg-gray-400 text-gray-700 py-3 rounded-lg font-semibold transition-colors">
                    बंद करें
                </button>
            </div>
        </div>
    </div>

    <!-- Add Panchayat Modal -->
    <div id="addPanchayatModal" class="fixed inset-0 bg-black bg-opacity-50 hidden items-center justify-center z-50 p-4">
        <div class="bg-white rounded-xl p-6 md:p-8 max-w-md w-full">
            <h3 class="text-2xl font-bold mb-6 text-gray-800">नई पंचायत जोड़ें</h3>
            <form onsubmit="addPanchayat(event)">
                <div class="mb-4">
                    <label class="block text-gray-700 font-semibold mb-2">पंचायत का नाम</label>
                    <input type="text" id="panchayatName" required class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                </div>
                <div class="mb-4">
                    <label class="block text-gray-700 font-semibold mb-2">जिला</label>
                    <input type="text" id="panchayatDistrict" required class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                </div>
                <div class="mb-6">
                    <label class="block text-gray-700 font-semibold mb-2">राज्य</label>
                    <input type="text" id="panchayatState" required class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                </div>
                <div class="flex space-x-4">
                    <button type="submit" class="flex-1 bg-purple-500 hover:bg-purple-600 text-white py-3 rounded-lg font-semibold">
                        जोड़ें
                    </button>
                    <button type="button" onclick="hideAddPanchayatForm()" class="flex-1 bg-gray-300 hover:bg-gray-400 text-gray-700 py-3 rounded-lg font-semibold">
                        रद्द करें
                    </button>
                </div>
            </form>
        </div>
    </div>

    <!-- Add Cow Modal -->
    <div id="addCowModal" class="fixed inset-0 bg-black bg-opacity-50 hidden items-center justify-center z-50 p-4">
        <div class="bg-white rounded-xl p-6 md:p-8 max-w-md w-full">
            <h3 class="text-2xl font-bold mb-6 text-gray-800">🐄 नई गौ माता जोड़ें</h3>
            <form onsubmit="addCow(event)">
                <div class="mb-4">
                    <label class="block text-gray-700 font-semibold mb-2">गौ माता का नाम</label>
                    <input type="text" id="cowName" required class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                </div>
                <div class="mb-4">
                    <label class="block text-gray-700 font-semibold mb-2">पंचायत चुनें</label>
                    <select id="cowPanchayat" required class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                        <option value="">पंचायत चुनें</option>
                    </select>
                </div>
                <div class="mb-4">
                    <label class="block text-gray-700 font-semibold mb-2">उम्र (वर्ष में)</label>
                    <input type="number" id="cowAge" required min="1" max="25" class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                </div>
                <div class="mb-4">
                    <label class="block text-gray-700 font-semibold mb-2">नस्ल</label>
                    <select id="cowBreed" required class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                        <option value="">नस्ल चुनें</option>
                        <option value="गिर">गिर</option>
                        <option value="साहीवाल">साहीवाल</option>
                        <option value="थारपारकर">थारपारकर</option>
                        <option value="हरियाणवी">हरियाणवी</option>
                        <option value="राठी">राठी</option>
                        <option value="कांकरेज">कांकरेज</option>
                        <option value="देसी">देसी</option>
                    </select>
                </div>
                <div class="mb-6">
                    <label class="block text-gray-700 font-semibold mb-2">स्वास्थ्य स्थिति</label>
                    <select id="cowHealth" required class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                        <option value="">स्वास्थ्य चुनें</option>
                        <option value="स्वस्थ">स्वस्थ</option>
                        <option value="बीमार">बीमार</option>
                        <option value="गर्भवती">गर्भवती</option>
                        <option value="दूध देने वाली">दूध देने वाली</option>
                        <option value="बुजुर्ग">बुजुर्ग</option>
                    </select>
                </div>
                <div class="flex space-x-4">
                    <button type="submit" class="flex-1 bg-red-500 hover:bg-red-600 text-white py-3 rounded-lg font-semibold">
                        जोड़ें
                    </button>
                    <button type="button" onclick="hideAddCowForm()" class="flex-1 bg-gray-300 hover:bg-gray-400 text-gray-700 py-3 rounded-lg font-semibold">
                        रद्द करें
                    </button>
                </div>
            </form>
        </div>
    </div>

    <!-- Add Bull Modal -->
    <div id="addBullModal" class="fixed inset-0 bg-black bg-opacity-50 hidden items-center justify-center z-50 p-4">
        <div class="bg-white rounded-xl p-6 md:p-8 max-w-md w-full">
            <h3 class="text-2xl font-bold mb-6 text-gray-800">🐂 नया सांड जोड़ें</h3>
            <form onsubmit="addBull(event)">
                <div class="mb-4">
                    <label class="block text-gray-700 font-semibold mb-2">सांड का नाम</label>
                    <input type="text" id="bullName" required class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                </div>
                <div class="mb-4">
                    <label class="block text-gray-700 font-semibold mb-2">पंचायत चुनें</label>
                    <select id="bullPanchayat" required class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                        <option value="">पंचायत चुनें</option>
                    </select>
                </div>
                <div class="mb-4">
                    <label class="block text-gray-700 font-semibold mb-2">उम्र (वर्ष में)</label>
                    <input type="number" id="bullAge" required min="1" max="25" class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                </div>
                <div class="mb-4">
                    <label class="block text-gray-700 font-semibold mb-2">नस्ल</label>
                    <select id="bullBreed" required class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                        <option value="">नस्ल चुनें</option>
                        <option value="गिर">गिर</option>
                        <option value="साहीवाल">साहीवाल</option>
                        <option value="थारपारकर">थारपारकर</option>
                        <option value="हरियाणवी">हरियाणवी</option>
                        <option value="राठी">राठी</option>
                        <option value="कांकरेज">कांकरेज</option>
                        <option value="देसी">देसी</option>
                    </select>
                </div>
                <div class="mb-6">
                    <label class="block text-gray-700 font-semibold mb-2">स्वास्थ्य स्थिति</label>
                    <select id="bullHealth" required class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                        <option value="">स्वास्थ्य चुनें</option>
                        <option value="स्वस्थ">स्वस्थ</option>
                        <option value="बीमार">बीमार</option>
                        <option value="प्रजनन के लिए तैयार">प्रजनन के लिए तैयार</option>
                        <option value="बुजुर्ग">बुजुर्ग</option>
                        <option value="काम में सक्षम">काम में सक्षम</option>
                    </select>
                </div>
                <div class="flex space-x-4">
                    <button type="submit" class="flex-1 bg-yellow-500 hover:bg-yellow-600 text-white py-3 rounded-lg font-semibold">
                        जोड़ें
                    </button>
                    <button type="button" onclick="hideAddBullForm()" class="flex-1 bg-gray-300 hover:bg-gray-400 text-gray-700 py-3 rounded-lg font-semibold">
                        रद्द करें
                    </button>
                </div>
            </form>
        </div>
    </div>

    <!-- Panchayat Registration Modal -->
    <div id="panchayatRegistrationModal" class="fixed inset-0 bg-black bg-opacity-50 hidden items-center justify-center z-50 p-4">
        <div class="bg-white rounded-xl p-6 md:p-8 max-w-lg w-full">
            <h3 class="text-2xl font-bold mb-6 text-gray-800">🏠 नई पंचायत रजिस्ट्रेशन</h3>
            <form onsubmit="registerPanchayat(event)">
                <div class="grid md:grid-cols-2 gap-4 mb-4">
                    <div>
                        <label class="block text-gray-700 font-semibold mb-2">पंचायत का नाम *</label>
                        <input type="text" id="regPanchayatName" required class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                    </div>
                    <div>
                        <label class="block text-gray-700 font-semibold mb-2">जिला *</label>
                        <input type="text" id="regPanchayatDistrict" required class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                    </div>
                </div>
                <div class="mb-4">
                    <label class="block text-gray-700 font-semibold mb-2">राज्य *</label>
                    <input type="text" id="regPanchayatState" required class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                </div>
                <div class="grid md:grid-cols-2 gap-4 mb-4">
                    <div>
                        <label class="block text-gray-700 font-semibold mb-2">एडमिन का नाम *</label>
                        <input type="text" id="regAdminName" required class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                    </div>
                    <div>
                        <label class="block text-gray-700 font-semibold mb-2">मोबाइल नंबर *</label>
                        <input type="tel" id="regAdminPhone" required class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                    </div>
                </div>
                <div class="grid md:grid-cols-2 gap-4 mb-6">
                    <div>
                        <label class="block text-gray-700 font-semibold mb-2">यूजरनेम *</label>
                        <input type="text" id="regAdminUsername" required class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                    </div>
                    <div>
                        <label class="block text-gray-700 font-semibold mb-2">पासवर्ड *</label>
                        <input type="password" id="regAdminPassword" required class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                    </div>
                </div>
                <div class="flex space-x-4">
                    <button type="submit" class="flex-1 bg-green-500 hover:bg-green-600 text-white py-3 rounded-lg font-semibold">
                        रजिस्टर करें
                    </button>
                    <button type="button" onclick="hidePanchayatRegistration()" class="flex-1 bg-gray-300 hover:bg-gray-400 text-gray-700 py-3 rounded-lg font-semibold">
                        रद्द करें
                    </button>
                </div>
            </form>
        </div>
    </div>

    <script>
        // Global Variables
        let panchayats = JSON.parse(localStorage.getItem('panchayats')) || [];
        let donations = JSON.parse(localStorage.getItem('donations')) || [];
        let feedDonations = JSON.parse(localStorage.getItem('feedDonations')) || [];
        let recentActivities = JSON.parse(localStorage.getItem('recentActivities')) || [];
        let qrSettings = JSON.parse(localStorage.getItem('qrSettings')) || { upiId: 'gauraksha@paytm', upiName: 'Gau Mata Raksha', qrImage: null };
        let bankDetails = JSON.parse(localStorage.getItem('bankDetails')) || { bankName: '', accountNumber: '', ifscCode: '', accountHolder: '' };
        let cows = JSON.parse(localStorage.getItem('cows')) || [];
        let bulls = JSON.parse(localStorage.getItem('bulls')) || [];
        let admins = JSON.parse(localStorage.getItem('admins')) || [];
        let users = JSON.parse(localStorage.getItem('users')) || [];
        let currentUser = null;
        let currentDonationData = null;
        let currentFeedDonationData = null;

        // Ensure ALL functions are available globally
        window.showUserLogin = showUserLogin;
        window.showAdminLogin = showAdminLogin;
        window.toggleMobileMenu = toggleMobileMenu;
        window.hideMobileMenu = hideMobileMenu;
        window.hideUserLogin = hideUserLogin;
        window.hideAdminLogin = hideAdminLogin;
        window.userLogin = userLogin;
        window.adminLogin = adminLogin;
        window.logout = logout;
        window.showUserSection = showUserSection;
        window.showAdminSection = showAdminSection;
        window.toggleUserMobileMenu = toggleUserMobileMenu;
        window.hideUserMobileMenu = hideUserMobileMenu;
        window.toggleAdminMobileMenu = toggleAdminMobileMenu;
        window.hideAdminMobileMenu = hideAdminMobileMenu;
        window.selectAmount = selectAmount;
        window.selectPaymentMethod = selectPaymentMethod;
        window.selectFeedType = selectFeedType;
        window.processUserDonation = processUserDonation;
        window.processUserFeedDonation = processUserFeedDonation;
        window.confirmPayment = confirmPayment;
        window.hidePaymentModal = hidePaymentModal;
        window.showAddPanchayatForm = showAddPanchayatForm;
        window.hideAddPanchayatForm = hideAddPanchayatForm;
        window.addPanchayat = addPanchayat;
        window.showAddCowForm = showAddCowForm;
        window.hideAddCowForm = hideAddCowForm;
        window.addCow = addCow;
        window.showAddBullForm = showAddBullForm;
        window.hideAddBullForm = hideAddBullForm;
        window.addBull = addBull;
        window.showPanchayatRegistration = showPanchayatRegistration;
        window.hidePanchayatRegistration = hidePanchayatRegistration;
        window.registerPanchayat = registerPanchayat;
        window.deletePanchayat = deletePanchayat;
        window.deleteCow = deleteCow;
        window.deleteBull = deleteBull;
        window.deleteDonation = deleteDonation;
        window.deleteFeedDonation = deleteFeedDonation;
        window.generateDonationsPDF = generateDonationsPDF;
        window.generateFeedPDF = generateFeedPDF;
        window.updateQRSettings = updateQRSettings;
        window.updateBankDetails = updateBankDetails;
        window.handleQRImageUpload = handleQRImageUpload;
        window.loadQRSettings = loadQRSettings;
        window.sendNotificationToAll = sendNotificationToAll;
        window.toggleNotifications = toggleNotifications;
        window.loadNotifications = loadNotifications;

        // Notification system
        let notifications = JSON.parse(localStorage.getItem('notifications')) || [];
        
        // Initialize with sample data
        if (panchayats.length === 0) {
            panchayats = [
                { id: 1, name: 'राजपुर', district: 'मेरठ', state: 'उत्तर प्रदेश', status: 'active' },
                { id: 2, name: 'गंगापुर', district: 'हरिद्वार', state: 'उत्तराखंड', status: 'active' },
                { id: 3, name: 'शिवपुर', district: 'जयपुर', state: 'राजस्थान', status: 'active' }
            ];
            localStorage.setItem('panchayats', JSON.stringify(panchayats));
        }

        if (cows.length === 0) {
            cows = [
                { id: 1, name: 'गंगा', panchayatId: 1, age: 5, breed: 'गिर', health: 'स्वस्थ', status: 'active' },
                { id: 2, name: 'यमुना', panchayatId: 1, age: 3, breed: 'साहीवाल', health: 'स्वस्थ', status: 'active' },
                { id: 3, name: 'सरस्वती', panchayatId: 2, age: 7, breed: 'थारपारकर', health: 'स्वस्थ', status: 'active' },
                { id: 4, name: 'लक्ष्मी', panchayatId: 3, age: 4, breed: 'हरियाणवी', health: 'स्वस्थ', status: 'active' }
            ];
            localStorage.setItem('cows', JSON.stringify(cows));
        }

        if (bulls.length === 0) {
            bulls = [
                { id: 1, name: 'वीर', panchayatId: 1, age: 6, breed: 'गिर', health: 'स्वस्थ', status: 'active' },
                { id: 2, name: 'बलराम', panchayatId: 2, age: 4, breed: 'साहीवाल', health: 'प्रजनन के लिए तैयार', status: 'active' }
            ];
            localStorage.setItem('bulls', JSON.stringify(bulls));
        }

        if (admins.length === 0) {
            admins = [
                { id: 1, username: 'admin', password: 'admin123', name: 'मुख्य प्रशासक', panchayatId: null, role: 'super' },
                { id: 2, username: 'rajpur_admin', password: 'rajpur123', name: 'राजपुर प्रशासक', panchayatId: 1, role: 'panchayat' },
                { id: 3, username: 'gangapur_admin', password: 'gangapur123', name: 'गंगापुर प्रशासक', panchayatId: 2, role: 'panchayat' },
                { id: 4, username: 'shivpur_admin', password: 'shivpur123', name: 'शिवपुर प्रशासक', panchayatId: 3, role: 'panchayat' }
            ];
            localStorage.setItem('admins', JSON.stringify(admins));
        }

        // Initialize page on load
        document.addEventListener('DOMContentLoaded', function() {
            updateHomeStats();
            
            // No need for cost calculation in direct feed donation
            
            // Load existing QR settings in admin panel
            loadQRSettings();
        });

        // Mobile menu functions
        function toggleMobileMenu() {
            const menu = document.getElementById('mobileMenu');
            menu.classList.toggle('hidden');
        }

        function hideMobileMenu() {
            document.getElementById('mobileMenu').classList.add('hidden');
        }

        function toggleUserMobileMenu() {
            const menu = document.getElementById('userMobileMenu');
            menu.classList.toggle('hidden');
        }

        function hideUserMobileMenu() {
            document.getElementById('userMobileMenu').classList.add('hidden');
        }

        function toggleAdminMobileMenu() {
            const menu = document.getElementById('adminMobileMenu');
            menu.classList.toggle('hidden');
        }

        function hideAdminMobileMenu() {
            document.getElementById('adminMobileMenu').classList.add('hidden');
        }

        // User management functions
        function getUserKey(name, phone) {
            return `${name.toLowerCase().trim()}_${phone.trim()}`;
        }

        function findOrCreateUser(name, phone) {
            const userKey = getUserKey(name, phone);
            let user = users.find(u => u.key === userKey);
            
            if (!user) {
                user = {
                    id: Date.now(),
                    key: userKey,
                    name: name.trim(),
                    phone: phone.trim(),
                    createdAt: new Date().toISOString(),
                    donations: [],
                    feedDonations: []
                };
                users.push(user);
                localStorage.setItem('users', JSON.stringify(users));
            }
            
            return user;
        }

        // Real-time activity tracking
        function addRecentActivity(message, type) {
            const activity = {
                id: Date.now(),
                message: message,
                type: type,
                timestamp: new Date().toLocaleString('hi-IN'),
                date: new Date().toLocaleDateString('hi-IN'),
                time: new Date().toLocaleTimeString('hi-IN')
            };
            
            recentActivities.unshift(activity);
            
            // Keep only last 20 activities
            if (recentActivities.length > 20) {
                recentActivities = recentActivities.slice(0, 20);
            }
            
            localStorage.setItem('recentActivities', JSON.stringify(recentActivities));
            
            // Update admin dashboard if visible
            if (!document.getElementById('adminDashboard').classList.contains('hidden')) {
                loadRecentActivities();
            }
        }

        // Update all statistics
        function updateAllStats() {
            updateHomeStats();
            updateAdminStats();
        }

        // Update home page stats
        function updateHomeStats() {
            const totalMoney = donations.reduce((sum, d) => sum + parseInt(d.amount || 0), 0);
            const feedCost = feedDonations.reduce((sum, f) => sum + parseInt(f.cost || 0), 0);
            const grandTotal = totalMoney + feedCost;
            
            document.getElementById('homeStatPanchayats').textContent = panchayats.length;
            document.getElementById('homeStatDonations').textContent = `₹${grandTotal.toLocaleString('hi-IN')}`;
            document.getElementById('homeStatDonors').textContent = donations.length + feedDonations.length;
            document.getElementById('homeStatCows').textContent = cows.length;
        }

        // User Login Functions
        function showUserLogin() {
            document.getElementById('userLoginModal').classList.remove('hidden');
            document.getElementById('userLoginModal').classList.add('flex');
        }

        function hideUserLogin() {
            document.getElementById('userLoginModal').classList.add('hidden');
            document.getElementById('userLoginModal').classList.remove('flex');
            document.getElementById('userLoginName').value = '';
            document.getElementById('userLoginPhone').value = '';
        }

        function userLogin(event) {
            event.preventDefault();
            const name = document.getElementById('userLoginName').value;
            const phone = document.getElementById('userLoginPhone').value;
            
            // Find or create user
            const user = findOrCreateUser(name, phone);
            currentUser = { type: 'user', ...user };
            
            hideUserLogin();
            
            document.getElementById('homePage').classList.add('hidden');
            document.getElementById('userDashboard').classList.remove('hidden');
            document.getElementById('userWelcome').textContent = `स्वागत है, ${name}`;
            
            showUserSection('userDonate');
            loadUserDonationPanchayats();
            checkNotifications();
        }

        // Admin Login Functions
        function showAdminLogin() {
            document.getElementById('adminLoginModal').classList.remove('hidden');
            document.getElementById('adminLoginModal').classList.add('flex');
        }

        function hideAdminLogin() {
            document.getElementById('adminLoginModal').classList.add('hidden');
            document.getElementById('adminLoginModal').classList.remove('flex');
            document.getElementById('adminUsername').value = '';
            document.getElementById('adminPassword').value = '';
        }

        function adminLogin(event) {
            event.preventDefault();
            const username = document.getElementById('adminUsername').value;
            const password = document.getElementById('adminPassword').value;
            
            const admin = admins.find(a => a.username === username && a.password === password);
            
            if (admin) {
                currentUser = { type: 'admin', username: admin.username, name: admin.name, panchayatId: admin.panchayatId, role: admin.role };
                hideAdminLogin();
                document.getElementById('homePage').classList.add('hidden');
                document.getElementById('adminDashboard').classList.remove('hidden');
                showAdminSection('adminHome');
                
                // Add login activity
                addRecentActivity(`👨‍💼 ${admin.name} ने लॉगिन किया`, 'admin');
            } else {
                alert('❌ गलत यूजरनेम या पासवर्ड!');
            }
        }

        // Logout Function
        function logout() {
            currentUser = null;
            document.getElementById('homePage').classList.remove('hidden');
            document.getElementById('userDashboard').classList.add('hidden');
            document.getElementById('adminDashboard').classList.add('hidden');
            updateHomeStats();
        }

        // User Section Navigation
        function showUserSection(sectionName) {
            document.querySelectorAll('.user-section-content').forEach(section => {
                section.classList.add('hidden');
            });
            document.getElementById(sectionName).classList.remove('hidden');
            
            if (sectionName === 'userDonate') loadUserDonationPanchayats();
            if (sectionName === 'userFeed') loadUserFeedPanchayats();
            if (sectionName === 'userHistory') loadUserHistory();
            if (sectionName === 'userDonors') loadUserDonors();
        }

        // Admin Section Navigation
        function showAdminSection(sectionName) {
            document.querySelectorAll('.admin-section-content').forEach(section => {
                section.classList.add('hidden');
            });
            document.getElementById(sectionName).classList.remove('hidden');
            
            if (sectionName === 'adminHome') {
                updateAdminStats();
                loadRecentActivities();
            }
            if (sectionName === 'adminPanchayats') loadAdminPanchayats();
            if (sectionName === 'adminCows') loadAdminCows();
            if (sectionName === 'adminBulls') loadAdminBulls();
            if (sectionName === 'adminDonations') loadAdminDonations();
            if (sectionName === 'adminFeed') loadAdminFeed();
            if (sectionName === 'adminPayments') {
                loadAdminPayments();
                loadQRSettings();
            }
        }

        // Load panchayats for user donation
        function loadUserDonationPanchayats() {
            const select = document.getElementById('userDonationPanchayat');
            select.innerHTML = '<option value="">पंचायत चुनें</option>';
            
            panchayats.forEach(panchayat => {
                select.innerHTML += `<option value="${panchayat.id}">${panchayat.name}, ${panchayat.district}</option>`;
            });
        }

        // Load panchayats for feed donation
        function loadUserFeedPanchayats() {
            const select = document.getElementById('userFeedPanchayat');
            select.innerHTML = '<option value="">पंचायत चुनें</option>';
            
            panchayats.forEach(panchayat => {
                select.innerHTML += `<option value="${panchayat.id}">${panchayat.name}, ${panchayat.district}</option>`;
            });
        }

        // Select amount function
        function selectAmount(amount) {
            document.querySelectorAll('.amount-btn').forEach(btn => {
                btn.classList.remove('selected');
            });
            
            event.target.classList.add('selected');
            document.getElementById('userDonationAmount').value = amount;
        }

        // Select payment method function
        function selectPaymentMethod(method) {
            document.querySelectorAll('.payment-method-btn').forEach(btn => {
                btn.classList.remove('selected');
            });
            
            event.target.classList.add('selected');
            document.getElementById('selectedPaymentMethod').value = method;
        }

        // Process user donation
        function processUserDonation(event) {
            event.preventDefault();
            
            const panchayatId = document.getElementById('userDonationPanchayat').value;
            const amount = document.getElementById('userDonationAmount').value;
            const paymentMethod = document.getElementById('selectedPaymentMethod').value;
            
            if (!panchayatId) {
                alert('❌ कृपया पंचायत चुनें');
                return;
            }
            
            if (!amount || amount < 51) {
                alert('❌ कृपया न्यूनतम ₹51 की राशि दर्ज करें');
                return;
            }
            
            if (!paymentMethod) {
                alert('❌ कृपया भुगतान विधि चुनें');
                return;
            }
            
            const panchayat = panchayats.find(p => p.id === parseInt(panchayatId));
            
            // Show confirmation before proceeding
            const confirmMsg = `🙏 दान की पुष्टि करें:\n\n👤 दानदाता: ${currentUser.name}\n💰 राशि: ₹${amount}\n🏠 पंचायत: ${panchayat ? panchayat.name : 'अज्ञात'}\n💳 भुगतान: ${getPaymentMethodName(paymentMethod)}\n\nक्या आप दान करना चाहते हैं?`;
            
            if (confirm(confirmMsg)) {
                currentDonationData = {
                    donorName: currentUser.name,
                    donorPhone: currentUser.phone,
                    panchayatId: parseInt(panchayatId),
                    amount: amount,
                    paymentMethod: paymentMethod
                };

                showPaymentModal(amount, paymentMethod);
            }
        }

        // Get payment method name
        function getPaymentMethodName(method) {
            const names = {
                'qr': 'QR कोड',
                'bank': 'बैंक ट्रांसफर',
                'cash': 'नकद',
                'other': 'अन्य'
            };
            return names[method] || method;
        }

        // Select feed type
        function selectFeedType(type) {
            document.querySelectorAll('.feed-type-btn').forEach(btn => {
                btn.classList.remove('selected');
            });
            
            event.target.classList.add('selected');
            document.getElementById('selectedFeedType').value = type;
            calculateFeedCost();
        }

        // No cost calculation needed for direct feed donation
        function calculateFeedCost() {
            // Feed donation is direct, no payment required
            return;
        }

        // Process feed donation
        function processUserFeedDonation(event) {
            event.preventDefault();
            
            const panchayatId = document.getElementById('userFeedPanchayat').value;
            const feedType = document.getElementById('selectedFeedType').value;
            const quantity = document.getElementById('userFeedQuantity').value;
            
            if (!panchayatId) {
                alert('❌ कृपया पंचायत चुनें');
                return;
            }
            
            if (!feedType) {
                alert('❌ कृपया चारे का प्रकार चुनें');
                return;
            }
            
            if (!quantity || quantity < 1) {
                alert('❌ कृपया न्यूनतम 1 किलो चारा दान करें');
                return;
            }
            
            const feedTypeNames = {
                'bhusa': 'भूसा',
                'grass': 'हरी घास',
                'hay': 'सूखी घास',
                'grains': 'अनाज'
            };
            
            const panchayat = panchayats.find(p => p.id === parseInt(panchayatId));
            
            // Show confirmation before proceeding
            const confirmMsg = `🌾 चारा दान की पुष्टि करें:\n\n👤 दानदाता: ${currentUser.name}\n🌾 चारा: ${quantity} किलो ${feedTypeNames[feedType]}\n🏠 पंचायत: ${panchayat ? panchayat.name : 'अज्ञात'}\n\n📝 नोट: यह चारा दान है, पैसे की जरूरत नहीं\n\nक्या आप चारा दान करना चाहते हैं?`;
            
            if (confirm(confirmMsg)) {
                // Direct feed donation without payment
                const feedDonation = {
                    id: Date.now(),
                    donorName: currentUser.name,
                    donorPhone: currentUser.phone,
                    panchayatId: parseInt(panchayatId),
                    feedType: feedType,
                    feedTypeName: feedTypeNames[feedType],
                    quantity: quantity,
                    cost: 0, // No cost for direct feed donation
                    paymentMethod: 'feed_direct',
                    date: new Date().toLocaleDateString('hi-IN'),
                    time: new Date().toLocaleTimeString('hi-IN'),
                    panchayatName: panchayat ? panchayat.name : 'अज्ञात'
                };
                
                feedDonations.push(feedDonation);
                localStorage.setItem('feedDonations', JSON.stringify(feedDonations));
                
                // Update user's feed donation history
                const user = users.find(u => u.key === getUserKey(currentUser.name, currentUser.phone));
                if (user) {
                    user.feedDonations.push(feedDonation);
                    localStorage.setItem('users', JSON.stringify(users));
                }
                
                // Add to recent activities
                addRecentActivity(`🌾 ${feedDonation.donorName} ने ${panchayat ? panchayat.name : 'अज्ञात पंचायत'} के लिए ${feedDonation.quantity} किलो ${feedDonation.feedTypeName} दान किया (सीधा चारा दान)`, 'feed');
                
                // Reset form
                document.getElementById('userFeedQuantity').value = '';
                document.getElementById('userFeedPanchayat').value = '';
                document.getElementById('selectedFeedType').value = '';
                document.querySelectorAll('.feed-type-btn').forEach(btn => {
                    btn.classList.remove('selected');
                });
                
                alert(`🎉 चारा दान सफल!\n\n✅ दानदाता: ${feedDonation.donorName}\n🌾 चारा: ${feedDonation.quantity} किलो ${feedDonation.feedTypeName}\n🏠 पंचायत: ${panchayat ? panchayat.name : 'अज्ञात'}\n📅 दिनांक: ${feedDonation.date}\n\n📝 यह सीधा चारा दान है। आपका चारा दान सफलतापूर्वक दर्ज हो गया है। गौ माता का आशीर्वाद आप पर बना रहे! 🙏`);
                
                updateAllStats();
                
                // Real-time admin updates
                setTimeout(() => {
                    updateAdminStats();
                    loadRecentActivities();
                    
                    // Update admin tables if visible
                    if (!document.getElementById('adminFeed').classList.contains('hidden')) {
                        loadAdminFeed();
                    }
                }, 100);
            }
        }

        // Show Payment Modal
        function showPaymentModal(amount, method) {
            document.getElementById('paymentModalTitle').textContent = `💳 ${getPaymentMethodName(method)} भुगतान`;
            
            let content = '';
            
            if (method === 'qr') {
                content = `
                    <div id="qrCodeContainer" class="qr-container p-6 rounded-xl mx-auto mb-4 inline-block">
                        <div class="text-center p-4">
                            <div class="loading-spinner mx-auto mb-2"></div>
                            <p class="text-sm text-gray-600">QR कोड लोड हो रहा है...</p>
                        </div>
                    </div>
                    <p class="text-lg font-semibold text-gray-800 mb-2">भुगतान राशि: ₹${amount}</p>
                    <p class="text-sm text-gray-600 mb-4">QR कोड स्कैन करें या UPI ID का उपयोग करें</p>
                    <div class="bg-blue-50 p-3 rounded-lg text-left text-sm">
                        <p class="font-semibold text-blue-800 mb-2">📋 भुगतान के चरण:</p>
                        <ol class="text-blue-700 space-y-1">
                            <li>1️⃣ QR कोड स्कैन करें</li>
                            <li>2️⃣ राशि की पुष्टि करें</li>
                            <li>3️⃣ भुगतान पूरा करें</li>
                            <li>4️⃣ नीचे "भुगतान पूर्ण" बटन दबाएं</li>
                        </ol>
                    </div>
                `;
            } else if (method === 'bank') {
                content = `
                    <div class="bg-blue-50 p-4 rounded-lg mb-4">
                        <h4 class="font-bold text-blue-800 mb-2">🏦 बैंक विवरण:</h4>
                        <div class="text-sm text-blue-700 space-y-1">
                            <p><strong>बैंक:</strong> ${bankDetails.bankName || 'अपडेट करें'}</p>
                            <p><strong>खाता संख्या:</strong> ${bankDetails.accountNumber || 'अपडेट करें'}</p>
                            <p><strong>IFSC:</strong> ${bankDetails.ifscCode || 'अपडेट करें'}</p>
                            <p><strong>खाताधारक:</strong> ${bankDetails.accountHolder || 'अपडेट करें'}</p>
                        </div>
                    </div>
                    <p class="text-lg font-semibold text-gray-800 mb-2">भुगतान राशि: ₹${amount}</p>
                    <p class="text-sm text-gray-600">ऊपर दिए गए बैंक विवरण का उपयोग करके भुगतान करें</p>
                `;
            } else if (method === 'cash') {
                content = `
                    <div class="text-6xl mb-4">💵</div>
                    <p class="text-lg font-semibold text-gray-800 mb-2">नकद भुगतान: ₹${amount}</p>
                    <p class="text-sm text-gray-600 mb-4">कृपया निकटतम पंचायत कार्यालय में नकद भुगतान करें</p>
                    <div class="bg-yellow-50 p-3 rounded-lg text-sm">
                        <p class="font-semibold text-yellow-800">📝 नोट:</p>
                        <p class="text-yellow-700">भुगतान की रसीद अवश्य लें और सुरक्षित रखें</p>
                    </div>
                `;
            } else {
                content = `
                    <div class="text-6xl mb-4">🔄</div>
                    <p class="text-lg font-semibold text-gray-800 mb-2">अन्य भुगतान: ₹${amount}</p>
                    <p class="text-sm text-gray-600 mb-4">कृपया अपनी सुविधानुसार भुगतान करें</p>
                    <div class="bg-gray-50 p-3 rounded-lg text-sm">
                        <p class="font-semibold text-gray-800">💡 सुझाव:</p>
                        <p class="text-gray-700">चेक, डिमांड ड्राफ्ट या अन्य विधि से भुगतान कर सकते हैं</p>
                    </div>
                `;
            }
            
            document.getElementById('paymentContent').innerHTML = content;
            document.getElementById('paymentModal').classList.remove('hidden');
            document.getElementById('paymentModal').classList.add('flex');
            
            // Generate QR code if method is QR
            if (method === 'qr') {
                setTimeout(() => {
                    generateQRCode(amount);
                }, 500);
            }
        }

        // Generate QR Code
        function generateQRCode(amount) {
            try {
                const upiString = `upi://pay?pa=${qrSettings.upiId}&pn=${encodeURIComponent(qrSettings.upiName)}&am=${amount}&cu=INR&tn=Gau%20Mata%20Seva%20Donation`;
                
                // Clear container and show loading
                const container = document.getElementById('qrCodeContainer');
                container.innerHTML = `
                    <div class="text-center p-4">
                        <div class="loading-spinner mx-auto mb-2"></div>
                        <p class="text-sm text-gray-600">QR कोड जेनरेट हो रहा है...</p>
                    </div>
                `;
                
                setTimeout(() => {
                    console.log('QR Settings:', qrSettings);
                    console.log('QR Image exists:', !!qrSettings.qrImage);
                    
                    if (qrSettings.qrImage) {
                        // Use uploaded QR image with enhanced styling
                        container.innerHTML = `
                            <div class="text-center">
                                <div class="relative inline-block">
                                    <img src="${qrSettings.qrImage}" 
                                         class="w-48 h-48 object-contain rounded-lg shadow-lg neon-glow" 
                                         alt="QR Code"
                                         onerror="console.error('QR Image failed to load'); this.style.display='none';">
                                    <div class="absolute -top-2 -right-2 bg-green-500 text-white rounded-full w-6 h-6 flex items-center justify-center text-xs">
                                        ✓
                                    </div>
                                </div>
                                <p class="text-xs text-gray-500 mt-2">स्कैन करें और भुगतान करें</p>
                                <div class="mt-3 text-xs text-gray-600 bg-blue-50 p-2 rounded">
                                    <strong>UPI ID:</strong> ${qrSettings.upiId}
                                </div>
                            </div>
                        `;
                    } else {
                        // Generate QR code with enhanced styling
                        const qrContainer = document.createElement('div');
                        qrContainer.className = 'text-center';
                        
                        const canvas = document.createElement('canvas');
                        canvas.className = 'rounded-lg shadow-lg neon-glow mx-auto';
                        
                        QRCode.toCanvas(canvas, upiString, {
                            width: 200,
                            height: 200,
                            margin: 2,
                            color: {
                                dark: '#1f2937',
                                light: '#ffffff'
                            },
                            errorCorrectionLevel: 'M'
                        }, function (error) {
                            if (error) {
                                console.error('QR Code Error:', error);
                                container.innerHTML = `
                                    <div class="text-center p-6 glass rounded-xl">
                                        <div class="text-5xl mb-3 float-element">📱</div>
                                        <p class="text-lg font-semibold text-gray-800 mb-2">मैन्युअल भुगतान</p>
                                        <div class="bg-white p-4 rounded-lg border-2 border-blue-200 text-sm space-y-2">
                                            <div class="flex justify-between">
                                                <strong>UPI ID:</strong> 
                                                <span class="text-blue-600">${qrSettings.upiId}</span>
                                            </div>
                                            <div class="flex justify-between">
                                                <strong>राशि:</strong> 
                                                <span class="text-green-600 font-bold">₹${amount}</span>
                                            </div>
                                            <div class="flex justify-between">
                                                <strong>प्राप्तकर्ता:</strong> 
                                                <span>${qrSettings.upiName}</span>
                                            </div>
                                        </div>
                                        <p class="text-xs text-gray-500 mt-3">अपने UPI ऐप में मैन्युअल भुगतान करें</p>
                                    </div>
                                `;
                                return;
                            }
                            
                            qrContainer.appendChild(canvas);
                            
                            // Add success indicator and instructions
                            qrContainer.innerHTML += `
                                <div class="absolute -top-2 -right-2 bg-green-500 text-white rounded-full w-6 h-6 flex items-center justify-center text-xs">
                                    ✓
                                </div>
                                <p class="text-xs text-gray-500 mt-2">स्कैन करें और भुगतान करें</p>
                                <div class="mt-3 text-xs text-gray-600 bg-blue-50 p-2 rounded">
                                    <strong>UPI ID:</strong> ${qrSettings.upiId}
                                </div>
                            `;
                            
                            container.innerHTML = '';
                            container.appendChild(qrContainer);
                        });
                    }
                }, 1000); // Add delay for better UX
                
            } catch (error) {
                console.error('Error generating QR code:', error);
                document.getElementById('qrCodeContainer').innerHTML = `
                    <div class="text-center p-6 glass rounded-xl">
                        <div class="text-5xl mb-3 float-element">💳</div>
                        <p class="text-lg font-semibold text-gray-800 mb-2">भुगतान विवरण</p>
                        <div class="bg-white p-4 rounded-lg border-2 border-blue-200 text-sm space-y-2">
                            <div class="flex justify-between">
                                <strong>UPI ID:</strong> 
                                <span class="text-blue-600">${qrSettings.upiId}</span>
                            </div>
                            <div class="flex justify-between">
                                <strong>राशि:</strong> 
                                <span class="text-green-600 font-bold">₹${amount}</span>
                            </div>
                            <div class="flex justify-between">
                                <strong>प्राप्तकर्ता:</strong> 
                                <span>${qrSettings.upiName}</span>
                            </div>
                        </div>
                        <p class="text-xs text-gray-500 mt-3">अपने UPI ऐप में मैन्युअल भुगतान करें</p>
                    </div>
                `;
            }
        }

        // Hide Payment Modal
        function hidePaymentModal() {
            document.getElementById('paymentModal').classList.add('hidden');
            document.getElementById('paymentModal').classList.remove('flex');
            currentDonationData = null;
            currentFeedDonationData = null;
        }

        // Confirm Payment
        function confirmPayment() {
            try {
                if (currentDonationData) {
                    const panchayat = panchayats.find(p => p.id === currentDonationData.panchayatId);
                    const donation = {
                        ...currentDonationData,
                        id: Date.now(),
                        date: new Date().toLocaleDateString('hi-IN'),
                        time: new Date().toLocaleTimeString('hi-IN'),
                        panchayatName: panchayat ? panchayat.name : 'अज्ञात'
                    };
                    
                    donations.push(donation);
                    localStorage.setItem('donations', JSON.stringify(donations));
                    
                    // Update user's donation history
                    const user = users.find(u => u.key === getUserKey(currentUser.name, currentUser.phone));
                    if (user) {
                        user.donations.push(donation);
                        localStorage.setItem('users', JSON.stringify(users));
                    }
                    
                    // Add to recent activities
                    addRecentActivity(`💰 ${donation.donorName} ने ${panchayat ? panchayat.name : 'अज्ञात पंचायत'} के लिए ₹${donation.amount} का दान किया (${getPaymentMethodName(donation.paymentMethod)})`, 'donation');
                    
                    hidePaymentModal();
                    
                    // Reset form
                    document.getElementById('userDonationAmount').value = '';
                    document.getElementById('userDonationPanchayat').value = '';
                    document.getElementById('selectedPaymentMethod').value = '';
                    document.querySelectorAll('.amount-btn, .payment-method-btn').forEach(btn => {
                        btn.classList.remove('selected');
                    });
                    
                    alert(`🎉 दान सफल!\n\n✅ दानदाता: ${donation.donorName}\n💰 राशि: ₹${donation.amount}\n🏠 पंचायत: ${panchayat ? panchayat.name : 'अज्ञात'}\n💳 भुगतान: ${getPaymentMethodName(donation.paymentMethod)}\n📅 दिनांक: ${donation.date}\n\nआपका दान सफलतापूर्वक दर्ज हो गया है। गौ माता का आशीर्वाद आप पर बना रहे! 🙏`);
                    
                } else if (currentFeedDonationData) {
                    const panchayat = panchayats.find(p => p.id === currentFeedDonationData.panchayatId);
                    const feedDonation = {
                        ...currentFeedDonationData,
                        id: Date.now(),
                        date: new Date().toLocaleDateString('hi-IN'),
                        time: new Date().toLocaleTimeString('hi-IN'),
                        panchayatName: panchayat ? panchayat.name : 'अज्ञात'
                    };
                    
                    feedDonations.push(feedDonation);
                    localStorage.setItem('feedDonations', JSON.stringify(feedDonations));
                    
                    // Update user's feed donation history
                    const user = users.find(u => u.key === getUserKey(currentUser.name, currentUser.phone));
                    if (user) {
                        user.feedDonations.push(feedDonation);
                        localStorage.setItem('users', JSON.stringify(users));
                    }
                    
                    // Add to recent activities
                    addRecentActivity(`🌾 ${feedDonation.donorName} ने ${panchayat ? panchayat.name : 'अज्ञात पंचायत'} के लिए ${feedDonation.quantity} किलो ${feedDonation.feedTypeName} दान किया`, 'feed');
                    
                    hidePaymentModal();
                    
                    // Reset form
                    document.getElementById('userFeedQuantity').value = '';
                    document.getElementById('userFeedPanchayat').value = '';
                    document.getElementById('selectedFeedType').value = '';
                    document.getElementById('feedCostEstimate').textContent = '₹0';
                    document.querySelectorAll('.feed-type-btn').forEach(btn => {
                        btn.classList.remove('selected');
                    });
                    
                    alert(`🎉 चारा दान सफल!\n\n✅ दानदाता: ${feedDonation.donorName}\n🌾 चारा: ${feedDonation.quantity} किलो ${feedDonation.feedTypeName}\n💰 लागत: ₹${feedDonation.cost}\n🏠 पंचायत: ${panchayat ? panchayat.name : 'अज्ञात'}\n📅 दिनांक: ${feedDonation.date}\n\nआपका चारा दान सफलतापूर्वक दर्ज हो गया है। गौ माता का आशीर्वाद आप पर बना रहे! 🙏`);
                }
                
                updateAllStats();
                
                // Real-time admin updates
                setTimeout(() => {
                    updateAdminStats();
                    loadRecentActivities();
                    updatePaymentStats();
                    
                    // Update admin tables if visible
                    if (!document.getElementById('adminDonations').classList.contains('hidden')) {
                        loadAdminDonations();
                    }
                    if (!document.getElementById('adminFeed').classList.contains('hidden')) {
                        loadAdminFeed();
                    }
                }, 100);
                
            } catch (error) {
                console.error('❌ Error in confirmPayment:', error);
                alert('❌ भुगतान प्रक्रिया में समस्या हुई। कृपया फिर से कोशिश करें।');
            }
        }

        // Load user history
        function loadUserHistory() {
            const container = document.getElementById('userHistoryList');
            container.innerHTML = '';
            
            const user = users.find(u => u.key === getUserKey(currentUser.name, currentUser.phone));
            if (!user || (user.donations.length === 0 && user.feedDonations.length === 0)) {
                container.innerHTML = '<div class="text-center text-gray-500 py-8">अभी तक कोई दान नहीं किया गया</div>';
                return;
            }
            
            // Combine and sort donations
            const allDonations = [
                ...user.donations.map(d => ({...d, type: 'donation'})),
                ...user.feedDonations.map(f => ({...f, type: 'feed'}))
            ].sort((a, b) => b.id - a.id);
            
            allDonations.forEach(donation => {
                const panchayat = panchayats.find(p => p.id === donation.panchayatId);
                const isRegularDonation = donation.type === 'donation';
                const amount = isRegularDonation ? donation.amount : donation.cost;
                const typeIcon = isRegularDonation ? '💰' : '🌾';
                const typeText = isRegularDonation ? 'दान' : `चारा दान (${donation.quantity} किलो ${donation.feedTypeName})`;
                
                container.innerHTML += `
                    <div class="bg-white rounded-xl p-6 shadow-lg">
                        <div class="flex items-center justify-between mb-4">
                            <div class="flex items-center space-x-3">
                                <div class="text-3xl">${typeIcon}</div>
                                <div>
                                    <h3 class="text-lg font-bold text-gray-800">${typeText}</h3>
                                    <p class="text-sm text-gray-600">📍 ${panchayat ? panchayat.name : 'अज्ञात पंचायत'}</p>
                                </div>
                            </div>
                            <div class="text-right">
                                <p class="text-2xl font-bold text-green-600">₹${parseInt(amount).toLocaleString('hi-IN')}</p>
                                <p class="text-sm text-gray-500">${donation.date}</p>
                            </div>
                        </div>
                        <div class="flex justify-between items-center">
                            <span class="inline-block bg-blue-100 text-blue-800 px-3 py-1 rounded-full text-xs font-semibold">
                                ${getPaymentMethodName(donation.paymentMethod)}
                            </span>
                            <span class="text-sm text-gray-500">${donation.time}</span>
                        </div>
                    </div>
                `;
            });
        }

        // Load user donors
        function loadUserDonors() {
            const container = document.getElementById('userDonorsList');
            container.innerHTML = '';
            
            const allDonors = [...donations, ...feedDonations];
            
            if (allDonors.length === 0) {
                container.innerHTML = '<div class="col-span-full text-center text-gray-500 py-8">अभी तक कोई दान नहीं मिला</div>';
                return;
            }
            
            allDonors.sort((a, b) => {
                const amountA = parseInt(a.amount || a.cost || 0);
                const amountB = parseInt(b.amount || b.cost || 0);
                return amountB - amountA;
            });
            
            allDonors.forEach((donor, index) => {
                const panchayat = panchayats.find(p => p.id === donor.panchayatId);
                const medal = index === 0 ? '🥇' : index === 1 ? '🥈' : index === 2 ? '🥉' : '🙏';
                const amount = donor.amount || donor.cost || 0;
                const type = donor.amount ? 'दान' : 'चारा दान';
                
                container.innerHTML += `
                    <div class="bg-white rounded-xl p-6 shadow-lg card-hover">
                        <div class="flex items-center mb-4">
                            <div class="text-3xl mr-3">${medal}</div>
                            <div>
                                <h3 class="text-lg font-bold text-gray-800">${donor.donorName}</h3>
                                <p class="text-sm text-gray-600">${donor.date}</p>
                            </div>
                        </div>
                        <div class="mb-3">
                            <p class="text-2xl font-bold text-green-600">₹${parseInt(amount).toLocaleString('hi-IN')}</p>
                            <p class="text-sm text-gray-600">📍 ${panchayat ? panchayat.name : 'अज्ञात पंचायत'}</p>
                            <p class="text-sm text-blue-600">${type}</p>
                        </div>
                        <div class="text-center">
                            <span class="inline-block bg-green-100 text-green-800 px-3 py-1 rounded-full text-xs font-semibold">
                                गौ माता का आशीर्वाद प्राप्त
                            </span>
                        </div>
                    </div>
                `;
            });
        }

        // Admin Functions
        function updateAdminStats() {
            // Filter data based on admin role
            let filteredPanchayats = panchayats;
            let filteredCows = cows;
            let filteredBulls = bulls;
            let filteredDonations = donations;
            let filteredFeedDonations = feedDonations;
            
            if (currentUser && currentUser.role === 'panchayat') {
                filteredPanchayats = panchayats.filter(p => p.id === currentUser.panchayatId);
                filteredCows = cows.filter(c => c.panchayatId === currentUser.panchayatId);
                filteredBulls = bulls.filter(b => b.panchayatId === currentUser.panchayatId);
                filteredDonations = donations.filter(d => d.panchayatId === currentUser.panchayatId);
                filteredFeedDonations = feedDonations.filter(f => f.panchayatId === currentUser.panchayatId);
            }
            
            document.getElementById('adminTotalPanchayats').textContent = filteredPanchayats.length;
            document.getElementById('adminTotalCows').textContent = filteredCows.length;
            document.getElementById('adminTotalBulls').textContent = filteredBulls.length;
            document.getElementById('adminTotalDonors').textContent = filteredDonations.length + filteredFeedDonations.length;
            
            const totalMoney = filteredDonations.reduce((sum, d) => sum + parseInt(d.amount || 0), 0);
            const feedCost = filteredFeedDonations.reduce((sum, f) => sum + parseInt(f.cost || 0), 0);
            const grandTotal = totalMoney + feedCost;
            document.getElementById('adminTotalAmount').textContent = `₹${grandTotal.toLocaleString('hi-IN')}`;
            
            const today = new Date().toLocaleDateString('hi-IN');
            const todayDonations = filteredDonations.filter(d => d.date === today).length;
            const todayFeedDonations = filteredFeedDonations.filter(f => f.date === today).length;
            document.getElementById('adminTodayDonations').textContent = todayDonations + todayFeedDonations;
        }

        // Load recent activities
        function loadRecentActivities() {
            const container = document.getElementById('recentActivities');
            container.innerHTML = '';
            
            if (recentActivities.length === 0) {
                container.innerHTML = '<p class="text-gray-500">कोई हाल की गतिविधि नहीं</p>';
                return;
            }
            
            recentActivities.slice(0, 10).forEach(activity => {
                const typeIcon = activity.type === 'donation' ? '💰' : activity.type === 'feed' ? '🌾' : '📝';
                
                container.innerHTML += `
                    <div class="activity-item flex items-start justify-between p-3 bg-gray-50 rounded hover:bg-gray-100">
                        <div class="flex items-start space-x-2">
                            <span class="text-lg">${typeIcon}</span>
                            <div>
                                <p class="font-medium text-sm text-gray-800">${activity.message}</p>
                                <p class="text-xs text-gray-500">${activity.time}</p>
                            </div>
                        </div>
                        <span class="text-xs text-gray-400">${activity.date}</span>
                    </div>
                `;
            });
        }

        // Load admin panchayats
        function loadAdminPanchayats() {
            const container = document.getElementById('adminPanchayatsList');
            container.innerHTML = '';
            
            panchayats.forEach(panchayat => {
                const panchayatDonations = donations.filter(d => d.panchayatId === panchayat.id);
                const panchayatFeed = feedDonations.filter(f => f.panchayatId === panchayat.id);
                const totalAmount = panchayatDonations.reduce((sum, d) => sum + parseInt(d.amount || 0), 0);
                const totalFeedCost = panchayatFeed.reduce((sum, f) => sum + parseInt(f.cost || 0), 0);
                const grandTotal = totalAmount + totalFeedCost;
                
                container.innerHTML += `
                    <div class="bg-white rounded-xl p-6 shadow-lg card-hover">
                        <h3 class="text-xl font-semibold text-gray-800 mb-2">${panchayat.name}</h3>
                        <p class="text-gray-600 mb-2">📍 ${panchayat.district}, ${panchayat.state}</p>
                        <p class="text-lg font-bold text-green-600 mb-2">कुल: ₹${grandTotal.toLocaleString('hi-IN')}</p>
                        <p class="text-sm text-gray-600 mb-4">दानदाता: ${panchayatDonations.length + panchayatFeed.length}</p>
                        <div class="flex space-x-2">
                            <button onclick="deletePanchayat(${panchayat.id})" class="flex-1 bg-red-500 hover:bg-red-600 text-white py-2 rounded-lg text-sm">
                                हटाएं
                            </button>
                        </div>
                    </div>
                `;
            });
        }

        // Show add panchayat form
        function showAddPanchayatForm() {
            document.getElementById('addPanchayatModal').classList.remove('hidden');
            document.getElementById('addPanchayatModal').classList.add('flex');
        }

        // Hide add panchayat form
        function hideAddPanchayatForm() {
            document.getElementById('addPanchayatModal').classList.add('hidden');
            document.getElementById('addPanchayatModal').classList.remove('flex');
            document.getElementById('panchayatName').value = '';
            document.getElementById('panchayatDistrict').value = '';
            document.getElementById('panchayatState').value = '';
        }

        // Add panchayat
        function addPanchayat(event) {
            event.preventDefault();
            const name = document.getElementById('panchayatName').value;
            const district = document.getElementById('panchayatDistrict').value;
            const state = document.getElementById('panchayatState').value;
            
            const newPanchayat = {
                id: Date.now(),
                name: name,
                district: district,
                state: state,
                status: 'active'
            };
            
            panchayats.push(newPanchayat);
            localStorage.setItem('panchayats', JSON.stringify(panchayats));
            
            addRecentActivity(`🏠 नई पंचायत "${name}" जोड़ी गई`, 'admin');
            hideAddPanchayatForm();
            loadAdminPanchayats();
            updateAdminStats();
            alert('✅ पंचायत सफलतापूर्वक जोड़ी गई!');
        }

        // Delete panchayat
        function deletePanchayat(id) {
            if (confirm('क्या आप वाकई इस पंचायत को हटाना चाहते हैं?')) {
                const panchayat = panchayats.find(p => p.id === id);
                panchayats = panchayats.filter(p => p.id !== id);
                localStorage.setItem('panchayats', JSON.stringify(panchayats));
                
                if (panchayat) {
                    addRecentActivity(`🗑️ पंचायत "${panchayat.name}" हटाई गई`, 'admin');
                }
                
                loadAdminPanchayats();
                updateAdminStats();
                alert('✅ पंचायत हटा दी गई!');
            }
        }

        // Load admin cows
        function loadAdminCows() {
            const container = document.getElementById('adminCowsList');
            container.innerHTML = '';
            
            cows.forEach(cow => {
                const panchayat = panchayats.find(p => p.id === cow.panchayatId);
                
                container.innerHTML += `
                    <div class="bg-white rounded-xl p-6 shadow-lg card-hover">
                        <div class="flex items-center mb-4">
                            <div class="text-4xl mr-3">🐄</div>
                            <div>
                                <h3 class="text-xl font-semibold text-gray-800">${cow.name}</h3>
                                <p class="text-gray-600">📍 ${panchayat ? panchayat.name : 'अज्ञात पंचायत'}</p>
                            </div>
                        </div>
                        <div class="space-y-2 mb-4">
                            <p class="text-sm"><strong>उम्र:</strong> ${cow.age} वर्ष</p>
                            <p class="text-sm"><strong>नस्ल:</strong> ${cow.breed}</p>
                            <p class="text-sm"><strong>स्वास्थ्य:</strong> ${cow.health}</p>
                        </div>
                        <button onclick="deleteCow(${cow.id})" class="w-full bg-red-500 hover:bg-red-600 text-white py-2 rounded-lg text-sm">
                            हटाएं
                        </button>
                    </div>
                `;
            });
        }

        // Show add cow form
        function showAddCowForm() {
            const select = document.getElementById('cowPanchayat');
            select.innerHTML = '<option value="">पंचायत चुनें</option>';
            
            panchayats.forEach(panchayat => {
                select.innerHTML += `<option value="${panchayat.id}">${panchayat.name}, ${panchayat.district}</option>`;
            });
            
            document.getElementById('addCowModal').classList.remove('hidden');
            document.getElementById('addCowModal').classList.add('flex');
        }

        // Hide add cow form
        function hideAddCowForm() {
            document.getElementById('addCowModal').classList.add('hidden');
            document.getElementById('addCowModal').classList.remove('flex');
            document.getElementById('cowName').value = '';
            document.getElementById('cowPanchayat').value = '';
            document.getElementById('cowAge').value = '';
            document.getElementById('cowBreed').value = '';
            document.getElementById('cowHealth').value = '';
        }

        // Add cow
        function addCow(event) {
            event.preventDefault();
            const name = document.getElementById('cowName').value;
            const panchayatId = parseInt(document.getElementById('cowPanchayat').value);
            const age = parseInt(document.getElementById('cowAge').value);
            const breed = document.getElementById('cowBreed').value;
            const health = document.getElementById('cowHealth').value;
            
            const newCow = {
                id: Date.now(),
                name: name,
                panchayatId: panchayatId,
                age: age,
                breed: breed,
                health: health,
                status: 'active'
            };
            
            cows.push(newCow);
            localStorage.setItem('cows', JSON.stringify(cows));
            
            const panchayat = panchayats.find(p => p.id === panchayatId);
            addRecentActivity(`🐄 नई गौ माता "${name}" ${panchayat ? panchayat.name : 'अज्ञात पंचायत'} में जोड़ी गई`, 'admin');
            
            hideAddCowForm();
            loadAdminCows();
            updateAdminStats();
            alert('✅ गौ माता सफलतापूर्वक जोड़ी गई!');
        }

        // Delete cow
        function deleteCow(id) {
            if (confirm('क्या आप वाकई इस गौ माता को हटाना चाहते हैं?')) {
                const cow = cows.find(c => c.id === id);
                cows = cows.filter(c => c.id !== id);
                localStorage.setItem('cows', JSON.stringify(cows));
                
                if (cow) {
                    addRecentActivity(`🗑️ गौ माता "${cow.name}" हटाई गई`, 'admin');
                }
                
                loadAdminCows();
                updateAdminStats();
                alert('✅ गौ माता हटा दी गई!');
            }
        }

        // Load admin bulls
        function loadAdminBulls() {
            const container = document.getElementById('adminBullsList');
            container.innerHTML = '';
            
            bulls.forEach(bull => {
                const panchayat = panchayats.find(p => p.id === bull.panchayatId);
                
                container.innerHTML += `
                    <div class="bg-white rounded-xl p-6 shadow-lg card-hover">
                        <div class="flex items-center mb-4">
                            <div class="text-4xl mr-3">🐂</div>
                            <div>
                                <h3 class="text-xl font-semibold text-gray-800">${bull.name}</h3>
                                <p class="text-gray-600">📍 ${panchayat ? panchayat.name : 'अज्ञात पंचायत'}</p>
                            </div>
                        </div>
                        <div class="space-y-2 mb-4">
                            <p class="text-sm"><strong>उम्र:</strong> ${bull.age} वर्ष</p>
                            <p class="text-sm"><strong>नस्ल:</strong> ${bull.breed}</p>
                            <p class="text-sm"><strong>स्वास्थ्य:</strong> ${bull.health}</p>
                        </div>
                        <button onclick="deleteBull(${bull.id})" class="w-full bg-red-500 hover:bg-red-600 text-white py-2 rounded-lg text-sm">
                            हटाएं
                        </button>
                    </div>
                `;
            });
        }

        // Show add bull form
        function showAddBullForm() {
            const select = document.getElementById('bullPanchayat');
            select.innerHTML = '<option value="">पंचायत चुनें</option>';
            
            panchayats.forEach(panchayat => {
                select.innerHTML += `<option value="${panchayat.id}">${panchayat.name}, ${panchayat.district}</option>`;
            });
            
            document.getElementById('addBullModal').classList.remove('hidden');
            document.getElementById('addBullModal').classList.add('flex');
        }

        // Hide add bull form
        function hideAddBullForm() {
            document.getElementById('addBullModal').classList.add('hidden');
            document.getElementById('addBullModal').classList.remove('flex');
            document.getElementById('bullName').value = '';
            document.getElementById('bullPanchayat').value = '';
            document.getElementById('bullAge').value = '';
            document.getElementById('bullBreed').value = '';
            document.getElementById('bullHealth').value = '';
        }

        // Add bull
        function addBull(event) {
            event.preventDefault();
            const name = document.getElementById('bullName').value;
            const panchayatId = parseInt(document.getElementById('bullPanchayat').value);
            const age = parseInt(document.getElementById('bullAge').value);
            const breed = document.getElementById('bullBreed').value;
            const health = document.getElementById('bullHealth').value;
            
            const newBull = {
                id: Date.now(),
                name: name,
                panchayatId: panchayatId,
                age: age,
                breed: breed,
                health: health,
                status: 'active'
            };
            
            bulls.push(newBull);
            localStorage.setItem('bulls', JSON.stringify(bulls));
            
            const panchayat = panchayats.find(p => p.id === panchayatId);
            addRecentActivity(`🐂 नया सांड "${name}" ${panchayat ? panchayat.name : 'अज्ञात पंचायत'} में जोड़ा गया`, 'admin');
            
            hideAddBullForm();
            loadAdminBulls();
            updateAdminStats();
            alert('✅ सांड सफलतापूर्वक जोड़ा गया!');
        }

        // Delete bull
        function deleteBull(id) {
            if (confirm('क्या आप वाकई इस सांड को हटाना चाहते हैं?')) {
                const bull = bulls.find(b => b.id === id);
                bulls = bulls.filter(b => b.id !== id);
                localStorage.setItem('bulls', JSON.stringify(bulls));
                
                if (bull) {
                    addRecentActivity(`🗑️ सांड "${bull.name}" हटाया गया`, 'admin');
                }
                
                loadAdminBulls();
                updateAdminStats();
                alert('✅ सांड हटा दिया गया!');
            }
        }

        // Load admin donations
        function loadAdminDonations() {
            const tbody = document.getElementById('adminDonationsTable');
            tbody.innerHTML = '';
            
            donations.forEach(donation => {
                const panchayat = panchayats.find(p => p.id === donation.panchayatId);
                
                tbody.innerHTML += `
                    <tr>
                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-900">${donation.donorName}</td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-900">${panchayat ? panchayat.name : 'अज्ञात'}</td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-green-600">₹${parseInt(donation.amount).toLocaleString('hi-IN')}</td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-900">${getPaymentMethodName(donation.paymentMethod)}</td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-900">${donation.date}</td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm">
                            <button onclick="deleteDonation(${donation.id})" class="text-red-600 hover:text-red-900">हटाएं</button>
                        </td>
                    </tr>
                `;
            });
        }

        // Load admin feed
        function loadAdminFeed() {
            const tbody = document.getElementById('adminFeedTable');
            tbody.innerHTML = '';
            
            feedDonations.forEach(feed => {
                const panchayat = panchayats.find(p => p.id === feed.panchayatId);
                
                const costDisplay = feed.cost > 0 ? `₹${parseInt(feed.cost).toLocaleString('hi-IN')}` : 'सीधा दान';
                const paymentType = feed.paymentMethod === 'feed_direct' ? 'सीधा चारा दान' : getPaymentMethodName(feed.paymentMethod);
                
                tbody.innerHTML += `
                    <tr>
                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-900">${feed.donorName}</td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-900">${panchayat ? panchayat.name : 'अज्ञात'}</td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-900">${feed.feedTypeName}</td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-900">${feed.quantity} किलो</td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm font-medium ${feed.cost > 0 ? 'text-green-600' : 'text-blue-600'}">${costDisplay}</td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-900">${feed.date}</td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm">
                            <button onclick="deleteFeedDonation(${feed.id})" class="text-red-600 hover:text-red-900">हटाएं</button>
                        </td>
                    </tr>
                `;
            });
        }

        // Delete donation
        function deleteDonation(id) {
            if (confirm('क्या आप वाकई इस दान को हटाना चाहते हैं?')) {
                donations = donations.filter(d => d.id !== id);
                localStorage.setItem('donations', JSON.stringify(donations));
                loadAdminDonations();
                updateAdminStats();
                alert('✅ दान हटा दिया गया!');
            }
        }

        // Delete feed donation
        function deleteFeedDonation(id) {
            if (confirm('क्या आप वाकई इस चारा दान को हटाना चाहते हैं?')) {
                feedDonations = feedDonations.filter(f => f.id !== id);
                localStorage.setItem('feedDonations', JSON.stringify(feedDonations));
                loadAdminFeed();
                updateAdminStats();
                alert('✅ चारा दान हटा दिया गया!');
            }
        }

        // Load admin payments
        function loadAdminPayments() {
            updatePaymentStats();
        }

        // Update payment statistics
        function updatePaymentStats() {
            const qrCount = donations.filter(d => d.paymentMethod === 'qr').length;
            const bankCount = donations.filter(d => d.paymentMethod === 'bank').length;
            const cashCount = donations.filter(d => d.paymentMethod === 'cash').length;
            const otherCount = donations.filter(d => d.paymentMethod === 'other').length;
            
            document.getElementById('qrPayments').textContent = qrCount;
            document.getElementById('bankPayments').textContent = bankCount;
            document.getElementById('cashPayments').textContent = cashCount;
            document.getElementById('otherPayments').textContent = otherCount;
        }

        // Load QR settings in admin panel
        function loadQRSettings() {
            const upiIdInput = document.getElementById('adminUpiId');
            const upiNameInput = document.getElementById('adminUpiName');
            const preview = document.getElementById('qrImagePreview');
            const previewImg = document.getElementById('qrPreviewImg');
            
            if (upiIdInput) upiIdInput.value = qrSettings.upiId || 'gauraksha@paytm';
            if (upiNameInput) upiNameInput.value = qrSettings.upiName || 'Gau Mata Raksha';
            
            // Show existing QR image if available
            if (qrSettings.qrImage && preview && previewImg) {
                previewImg.src = qrSettings.qrImage;
                preview.classList.remove('hidden');
            }
        }

        // Handle QR image upload
        function handleQRImageUpload() {
            const fileInput = document.getElementById('qrImageUpload');
            const file = fileInput.files[0];
            
            if (file) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    const imageData = e.target.result;
                    
                    // Store image data
                    qrSettings.qrImage = imageData;
                    localStorage.setItem('qrSettings', JSON.stringify(qrSettings));
                    
                    // Show preview
                    const preview = document.getElementById('qrImagePreview');
                    const previewImg = document.getElementById('qrPreviewImg');
                    
                    previewImg.src = imageData;
                    preview.classList.remove('hidden');
                    
                    console.log('QR Image uploaded and saved successfully!');
                    alert('✅ QR कोड इमेज सफलतापूर्वक अपलोड हो गई!');
                };
                reader.readAsDataURL(file);
            }
        }

        // Update QR settings
        function updateQRSettings() {
            const upiId = document.getElementById('adminUpiId').value;
            const upiName = document.getElementById('adminUpiName').value;
            
            qrSettings.upiId = upiId;
            qrSettings.upiName = upiName;
            
            localStorage.setItem('qrSettings', JSON.stringify(qrSettings));
            alert('✅ QR सेटिंग्स अपडेट हो गईं!');
        }

        // Update bank details
        function updateBankDetails() {
            const bankName = document.getElementById('bankName').value;
            const accountNumber = document.getElementById('accountNumber').value;
            const ifscCode = document.getElementById('ifscCode').value;
            const accountHolder = document.getElementById('accountHolder').value;
            
            bankDetails = {
                bankName: bankName,
                accountNumber: accountNumber,
                ifscCode: ifscCode,
                accountHolder: accountHolder
            };
            
            localStorage.setItem('bankDetails', JSON.stringify(bankDetails));
            alert('✅ बैंक विवरण अपडेट हो गए!');
        }

        // Show panchayat registration
        function showPanchayatRegistration() {
            hideAdminLogin();
            document.getElementById('panchayatRegistrationModal').classList.remove('hidden');
            document.getElementById('panchayatRegistrationModal').classList.add('flex');
        }

        // Hide panchayat registration
        function hidePanchayatRegistration() {
            document.getElementById('panchayatRegistrationModal').classList.add('hidden');
            document.getElementById('panchayatRegistrationModal').classList.remove('flex');
        }

        // Register panchayat
        function registerPanchayat(event) {
            event.preventDefault();
            
            const panchayatName = document.getElementById('regPanchayatName').value;
            const district = document.getElementById('regPanchayatDistrict').value;
            const state = document.getElementById('regPanchayatState').value;
            const adminName = document.getElementById('regAdminName').value;
            const phone = document.getElementById('regAdminPhone').value;
            const username = document.getElementById('regAdminUsername').value;
            const password = document.getElementById('regAdminPassword').value;
            
            // Check if username already exists
            if (admins.find(a => a.username === username)) {
                alert('❌ यह यूजरनेम पहले से मौजूद है!');
                return;
            }
            
            // Create new panchayat
            const newPanchayat = {
                id: Date.now(),
                name: panchayatName,
                district: district,
                state: state,
                status: 'active'
            };
            
            panchayats.push(newPanchayat);
            localStorage.setItem('panchayats', JSON.stringify(panchayats));
            
            // Create new admin
            const newAdmin = {
                id: Date.now() + 1,
                username: username,
                password: password,
                name: adminName,
                phone: phone,
                panchayatId: newPanchayat.id,
                role: 'panchayat'
            };
            
            admins.push(newAdmin);
            localStorage.setItem('admins', JSON.stringify(admins));
            
            addRecentActivity(`🏠 नई पंचायत "${panchayatName}" रजिस्टर हुई`, 'admin');
            
            hidePanchayatRegistration();
            alert(`✅ पंचायत सफलतापूर्वक रजिस्टर हो गई!\n\n📋 विवरण:\n🏠 पंचायत: ${panchayatName}\n👤 एडमिन: ${adminName}\n🔑 यूजरनेम: ${username}\n\nअब आप लॉगिन कर सकते हैं!`);
        }

        // Generate donations PDF (placeholder)
        function generateDonationsPDF() {
            alert('📄 PDF जेनरेशन फीचर जल्द ही उपलब्ध होगा!');
        }

        // Generate feed PDF (placeholder)
        function generateFeedPDF() {
            alert('📄 PDF जेनरेशन फीचर जल्द ही उपलब्ध होगा!');
        }

        // Send notification to all users
        function sendNotificationToAll() {
            const message = document.getElementById('notificationMessage').value.trim();
            
            if (!message) {
                alert('❌ कृपया नोटिफिकेशन मैसेज लिखें');
                return;
            }
            
            const notification = {
                id: Date.now(),
                message: message,
                date: new Date().toLocaleDateString('hi-IN'),
                time: new Date().toLocaleTimeString('hi-IN'),
                timestamp: new Date().toISOString()
            };
            
            notifications.unshift(notification);
            localStorage.setItem('notifications', JSON.stringify(notifications));
            
            // Clear the message input
            document.getElementById('notificationMessage').value = '';
            
            // Add to recent activities
            addRecentActivity(`📢 सभी यूजर्स को नोटिफिकेशन भेजा गया: "${message.substring(0, 50)}${message.length > 50 ? '...' : ''}"`, 'admin');
            
            alert(`✅ नोटिफिकेशन सफलतापूर्वक भेजा गया!\n\n📢 मैसेज: ${message}\n📅 समय: ${notification.time}\n\nसभी यूजर्स को यह नोटिफिकेशन दिखेगा।`);
        }

        // Toggle notifications dropdown
        function toggleNotifications() {
            const dropdown = document.getElementById('notificationDropdown');
            const badge = document.getElementById('notificationBadge');
            
            if (dropdown.classList.contains('hidden')) {
                dropdown.classList.remove('hidden');
                loadNotifications();
                // Hide badge when notifications are viewed
                badge.classList.add('hidden');
            } else {
                dropdown.classList.add('hidden');
            }
        }

        // Load notifications in dropdown
        function loadNotifications() {
            const container = document.getElementById('notificationList');
            container.innerHTML = '';
            
            if (notifications.length === 0) {
                container.innerHTML = '<div class="p-4 text-center text-gray-500">कोई नोटिफिकेशन नहीं</div>';
                return;
            }
            
            notifications.slice(0, 10).forEach(notification => {
                container.innerHTML += `
                    <div class="p-4 border-b hover:bg-gray-50">
                        <p class="text-sm text-gray-800 mb-2">${notification.message}</p>
                        <div class="flex justify-between items-center">
                            <span class="text-xs text-gray-500">${notification.date}</span>
                            <span class="text-xs text-gray-400">${notification.time}</span>
                        </div>
                    </div>
                `;
            });
        }

        // Update notification badge
        function updateNotificationBadge() {
            const badge = document.getElementById('notificationBadge');
            if (badge && notifications.length > 0) {
                badge.textContent = notifications.length;
                badge.classList.remove('hidden');
            }
        }

        // Check for new notifications on user login
        function checkNotifications() {
            if (notifications.length > 0) {
                updateNotificationBadge();
            }
        }
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9760fe11c7583c8e',t:'MTc1NjM1NDU3OC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
