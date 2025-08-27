<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>गौ माता रक्षा - पंचायत गौशाला योजना</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/qrcode@1.5.3/build/qrcode.min.js"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Noto+Sans+Devanagari:wght@300;400;500;600;700&display=swap');
        body { font-family: 'Noto Sans Devanagari', sans-serif; }
        .gradient-bg { background: linear-gradient(135deg, #ff9a56 0%, #ff6b35 100%); }
        .admin-bg { background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); }
        .user-bg { background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%); }
        .card-hover { transition: transform 0.3s ease, box-shadow 0.3s ease; }
        .card-hover:hover { transform: translateY(-5px); box-shadow: 0 20px 40px rgba(0,0,0,0.1); }
        .amount-btn { transition: all 0.3s ease; }
        .amount-btn:hover { transform: scale(1.05); }
        .amount-btn.selected { background: #10b981 !important; color: white !important; transform: scale(1.05); }
        .hero-section { 
            background: linear-gradient(135deg, rgba(255,154,86,0.9) 0%, rgba(255,107,53,0.9) 100%), 
                        url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1000 1000"><defs><pattern id="cow" patternUnits="userSpaceOnUse" width="100" height="100"><circle cx="50" cy="50" r="2" fill="rgba(255,255,255,0.1)"/></pattern></defs><rect width="1000" height="1000" fill="url(%23cow)"/></svg>');
            background-size: cover;
        }
        .activity-item {
            animation: slideIn 0.5s ease-out;
        }
        @keyframes slideIn {
            from { opacity: 0; transform: translateX(-20px); }
            to { opacity: 1; transform: translateX(0); }
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
                    <!-- Mobile Menu Button -->
                    <button onclick="toggleMobileMenu()" class="md:hidden flex flex-col space-y-1 p-2">
                        <div class="w-6 h-0.5 bg-gray-600"></div>
                        <div class="w-6 h-0.5 bg-gray-600"></div>
                        <div class="w-6 h-0.5 bg-gray-600"></div>
                    </button>
                    
                    <div class="flex items-center space-x-3">
                        <div class="text-3xl md:text-4xl">🐄</div>
                        <div>
                            <h1 class="text-lg md:text-2xl font-bold text-gray-800">गौ माता रक्षा योजना</h1>
                            <p class="text-xs md:text-sm text-gray-600">पंचायत गौशाला सेवा</p>
                        </div>
                    </div>
                    
                    <!-- Desktop Menu -->
                    <div class="hidden md:flex items-center space-x-4">
                        <button onclick="showUserLogin()" class="bg-blue-500 hover:bg-blue-600 text-white px-6 py-2 rounded-lg font-semibold transition-colors">
                            दान करें
                        </button>
                        <button onclick="showAdminLogin()" class="bg-purple-500 hover:bg-purple-600 text-white px-6 py-2 rounded-lg font-semibold transition-colors">
                            Admin
                        </button>
                    </div>
                </div>
                
                <!-- Mobile Menu -->
                <div id="mobileMenu" class="hidden md:hidden absolute top-full left-0 right-0 bg-white shadow-lg border-t z-50">
                    <div class="p-4 space-y-3">
                        <button onclick="showUserLogin(); hideMobileMenu();" class="w-full bg-blue-500 hover:bg-blue-600 text-white px-6 py-3 rounded-lg font-semibold transition-colors">
                            🙏 दान करें
                        </button>
                        <button onclick="showAdminLogin(); hideMobileMenu();" class="w-full bg-purple-500 hover:bg-purple-600 text-white px-6 py-3 rounded-lg font-semibold transition-colors">
                            👨‍💼 Admin
                        </button>
                    </div>
                </div>
            </div>
        </header>

        <!-- Hero Section -->
        <section class="hero-section text-white py-12 md:py-20">
            <div class="container mx-auto px-4 text-center">
                <div class="text-6xl md:text-8xl mb-4 md:mb-6">🐄</div>
                <h2 class="text-3xl md:text-5xl font-bold mb-4 md:mb-6">गौ माता की सेवा करें</h2>
                <p class="text-base md:text-xl mb-6 md:mb-8 max-w-3xl mx-auto px-2">गौ माता हमारी संस्कृति का अभिन्न अंग हैं। आपका छोटा सा दान भी गौ माता की सेवा में महत्वपूर्ण योगदान देगा।</p>
                <div class="flex justify-center">
                    <button onclick="showUserLogin()" class="bg-white text-orange-600 px-6 md:px-8 py-3 md:py-4 rounded-lg font-bold text-base md:text-lg hover:bg-gray-100 transition-colors">
                        🙏 अभी दान करें
                    </button>
                </div>
            </div>
        </section>

        <!-- Statistics Section -->
        <section class="py-12 md:py-16 gradient-bg text-white">
            <div class="container mx-auto px-4">
                <h3 class="text-2xl md:text-4xl font-bold text-center mb-8 md:mb-12">📊 हमारी उपलब्धियां</h3>
                <div class="grid grid-cols-2 md:grid-cols-4 gap-4 md:gap-6">
                    <div class="text-center bg-white bg-opacity-10 rounded-lg p-4 md:p-6">
                        <div class="text-2xl md:text-4xl font-bold mb-2" id="homeStatPanchayats">0</div>
                        <div class="text-orange-100 text-sm md:text-base">गौशालाएं</div>
                    </div>
                    <div class="text-center bg-white bg-opacity-10 rounded-lg p-4 md:p-6">
                        <div class="text-2xl md:text-4xl font-bold mb-2" id="homeStatDonations">₹0</div>
                        <div class="text-orange-100 text-sm md:text-base">कुल दान राशि</div>
                    </div>
                    <div class="text-center bg-white bg-opacity-10 rounded-lg p-4 md:p-6">
                        <div class="text-2xl md:text-4xl font-bold mb-2" id="homeStatDonors">0</div>
                        <div class="text-orange-100 text-sm md:text-base">दानदाता</div>
                    </div>
                    <div class="text-center bg-white bg-opacity-10 rounded-lg p-4 md:p-6">
                        <div class="text-2xl md:text-4xl font-bold mb-2" id="homeStatCows">0</div>
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
                <div class="text-sm text-gray-600 mb-4 p-3 bg-gray-50 rounded">
                    <strong>मुख्य एडमिन:</strong> admin / admin123<br>
                    <strong>राजपुर एडमिन:</strong> rajpur_admin / rajpur123<br>
                    <strong>गंगापुर एडमिन:</strong> gangapur_admin / gangapur123<br>
                    <strong>शिवपुर एडमिन:</strong> shivpur_admin / shivpur123
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
                    <!-- Mobile Menu Button -->
                    <button onclick="toggleUserMobileMenu()" class="md:hidden flex flex-col space-y-1 p-2">
                        <div class="w-6 h-0.5 bg-white"></div>
                        <div class="w-6 h-0.5 bg-white"></div>
                        <div class="w-6 h-0.5 bg-white"></div>
                    </button>
                    
                    <div class="flex items-center space-x-3">
                        <div class="text-3xl md:text-4xl">🙏</div>
                        <div>
                            <h1 class="text-lg md:text-2xl font-bold">गौ माता सेवा</h1>
                            <p class="text-blue-100 text-sm md:text-base" id="userWelcome">स्वागत है</p>
                        </div>
                    </div>
                    
                    <!-- Desktop Menu -->
                    <div class="hidden md:flex items-center space-x-6">
                        <nav class="flex space-x-6">
                            <button onclick="showUserSection('userDonate')" class="hover:text-blue-200">दान करें</button>
                            <button onclick="showUserSection('userFeed')" class="hover:text-blue-200">चारा दान</button>
                            <button onclick="showUserSection('userDonors')" class="hover:text-blue-200">दानदाता सूची</button>
                        </nav>
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
                        <button onclick="showUserSection('userDonors'); hideUserMobileMenu();" class="w-full text-left text-white hover:text-blue-200 py-2 px-3 rounded">
                            👥 दानदाता सूची
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
                                <p class="text-lg font-bold text-green-600" id="feedCostEstimate">₹0</p>
                                <p class="text-sm text-gray-600">अनुमानित लागत</p>
                            </div>
                        </div>

                        <button type="submit" class="w-full bg-green-500 hover:bg-green-600 text-white py-4 rounded-lg font-bold text-lg">
                            🌾 चारा दान करें
                        </button>
                    </form>
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
                    <!-- Mobile Menu Button -->
                    <button onclick="toggleAdminMobileMenu()" class="md:hidden flex flex-col space-y-1 p-2">
                        <div class="w-6 h-0.5 bg-white"></div>
                        <div class="w-6 h-0.5 bg-white"></div>
                        <div class="w-6 h-0.5 bg-white"></div>
                    </button>
                    
                    <div class="flex items-center space-x-3">
                        <div class="text-3xl md:text-4xl">👨‍💼</div>
                        <div>
                            <h1 class="text-lg md:text-2xl font-bold">एडमिन पैनल - गौ माता रक्षा</h1>
                            <p class="text-purple-100 text-sm md:text-base">प्रबंधन डैशबोर्ड</p>
                        </div>
                    </div>
                    
                    <!-- Desktop Menu -->
                    <div class="hidden md:flex items-center space-x-6">
                        <nav class="flex space-x-6">
                            <button onclick="showAdminSection('adminHome')" class="hover:text-purple-200">डैशबोर्ड</button>
                            <button onclick="showAdminSection('adminPanchayats')" class="hover:text-purple-200">पंचायत</button>
                            <button onclick="showAdminSection('adminCows')" class="hover:text-purple-200">गौ माता</button>
                            <button onclick="showAdminSection('adminDonations')" class="hover:text-purple-200">दान</button>
                            <button onclick="showAdminSection('adminFeed')" class="hover:text-purple-200">चारा</button>
                            <button onclick="showAdminSection('adminQR')" class="hover:text-purple-200">QR कोड</button>
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
                        <button onclick="showAdminSection('adminDonations'); hideAdminMobileMenu();" class="w-full text-left text-white hover:text-purple-200 py-2 px-3 rounded">
                            💰 दान
                        </button>
                        <button onclick="showAdminSection('adminFeed'); hideAdminMobileMenu();" class="w-full text-left text-white hover:text-purple-200 py-2 px-3 rounded">
                            🌾 चारा
                        </button>
                        <button onclick="showAdminSection('adminQR'); hideAdminMobileMenu();" class="w-full text-left text-white hover:text-purple-200 py-2 px-3 rounded">
                            📱 QR कोड
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
                
                <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-4 md:gap-6 mb-8">
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

            <!-- Admin QR Code Management -->
            <section id="adminQR" class="admin-section-content hidden">
                <h2 class="text-3xl font-bold text-center mb-8 text-gray-800">📱 QR कोड प्रबंधन</h2>
                
                <div class="grid md:grid-cols-2 gap-8">
                    <!-- Current QR Settings -->
                    <div class="bg-white rounded-xl p-6 shadow-lg">
                        <h3 class="text-xl font-bold mb-4 text-gray-800">🔧 वर्तमान QR सेटिंग्स</h3>
                        <div class="space-y-4">
                            <div>
                                <label class="block text-gray-700 font-semibold mb-2">UPI ID</label>
                                <input type="text" id="adminUpiId" value="gauraksha@paytm" class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                            </div>
                            <div>
                                <label class="block text-gray-700 font-semibold mb-2">प्राप्तकर्ता का नाम</label>
                                <input type="text" id="adminUpiName" value="Gau Mata Raksha" class="w-full px-4 py-3 border border-gray-300 rounded-lg">
                            </div>
                            <button onclick="updateQRSettings()" class="w-full bg-purple-500 hover:bg-purple-600 text-white py-3 rounded-lg font-semibold">
                                सेटिंग्स अपडेट करें
                            </button>
                        </div>
                    </div>

                    <!-- QR Code Preview -->
                    <div class="bg-white rounded-xl p-6 shadow-lg">
                        <h3 class="text-xl font-bold mb-4 text-gray-800">👁️ QR कोड प्रीव्यू</h3>
                        <div class="text-center">
                            <div id="adminQRPreview" class="bg-gray-50 p-4 rounded-lg mx-auto mb-4 inline-block"></div>
                            <p class="text-sm text-gray-600 mb-4">टेस्ट राशि: ₹100</p>
                            <button onclick="generateTestQR()" class="bg-blue-500 hover:bg-blue-600 text-white px-6 py-2 rounded-lg">
                                टेस्ट QR जेनरेट करें
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Combined PDF Download -->
                <div class="mt-8 bg-white rounded-xl p-6 shadow-lg">
                    <div class="flex justify-between items-center mb-4">
                        <h3 class="text-xl font-bold text-gray-800">📄 रिपोर्ट डाउनलोड</h3>
                        <button onclick="generateAllDataPDF()" class="bg-purple-500 hover:bg-purple-600 text-white px-6 py-3 rounded-lg font-semibold">
                            📊 संपूर्ण रिपोर्ट PDF
                        </button>
                    </div>
                </div>

                <!-- QR Statistics -->
                <div class="mt-8 bg-white rounded-xl p-6 shadow-lg">
                    <h3 class="text-xl font-bold mb-4 text-gray-800">📊 QR भुगतान आंकड़े</h3>
                    <div class="grid md:grid-cols-4 gap-6">
                        <div class="text-center">
                            <div class="text-3xl font-bold text-green-600" id="qrTotalPayments">0</div>
                            <div class="text-gray-600">कुल QR भुगतान</div>
                        </div>
                        <div class="text-center">
                            <div class="text-3xl font-bold text-blue-600" id="qrTotalAmount">₹0</div>
                            <div class="text-gray-600">कुल QR राशि</div>
                        </div>
                        <div class="text-center">
                            <div class="text-3xl font-bold text-purple-600" id="qrTodayPayments">0</div>
                            <div class="text-gray-600">आज के QR भुगतान</div>
                        </div>
                        <div class="text-center">
                            <div class="text-3xl font-bold text-orange-600" id="qrSuccessRate">100%</div>
                            <div class="text-gray-600">सफलता दर</div>
                        </div>
                    </div>
                </div>

                <!-- Recent QR Payments -->
                <div class="mt-8 bg-white rounded-xl p-6 shadow-lg">
                    <h3 class="text-xl font-bold mb-4 text-gray-800">🔄 हाल के QR भुगतान</h3>
                    <div id="recentQRPayments" class="space-y-3 max-h-96 overflow-y-auto">
                        <!-- Recent QR payments will be loaded here -->
                    </div>
                </div>
            </section>
        </main>
    </div>

    <!-- QR Payment Modal -->
    <div id="qrPaymentModal" class="fixed inset-0 bg-black bg-opacity-50 hidden items-center justify-center z-50 p-4">
        <div class="bg-white rounded-xl p-6 md:p-8 max-w-md w-full">
            <h3 class="text-2xl font-bold mb-6 text-gray-800 text-center">📱 भुगतान करें</h3>
            
            <div class="text-center mb-6">
                <div id="qrCodeContainer" class="bg-gray-50 p-4 rounded-lg mx-auto mb-4 inline-block border-2 border-dashed border-gray-300"></div>
                <p class="text-lg font-semibold text-gray-800 mb-2">भुगतान राशि: ₹<span id="qrAmount">0</span></p>
                <p class="text-sm text-gray-600 mb-4">QR कोड स्कैन करें या मैन्युअल भुगतान करें</p>
                
                <!-- Payment Instructions -->
                <div class="bg-blue-50 p-3 rounded-lg text-left text-sm">
                    <p class="font-semibold text-blue-800 mb-2">📋 भुगतान के चरण:</p>
                    <ol class="text-blue-700 space-y-1">
                        <li>1️⃣ QR कोड स्कैन करें या UPI ID का उपयोग करें</li>
                        <li>2️⃣ राशि की पुष्टि करें</li>
                        <li>3️⃣ भुगतान पूरा करें</li>
                        <li>4️⃣ नीचे "भुगतान पूर्ण" बटन दबाएं</li>
                    </ol>
                </div>
            </div>

            <div class="flex space-x-4">
                <button onclick="confirmQRPayment()" class="w-full bg-green-500 hover:bg-green-600 text-white py-3 rounded-lg font-semibold transition-colors">
                    ✅ भुगतान पूर्ण - नाम दर्ज करें
                </button>
                <button onclick="hideQRPayment()" class="w-full bg-gray-300 hover:bg-gray-400 text-gray-700 py-3 rounded-lg font-semibold transition-colors">
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
        let qrSettings = JSON.parse(localStorage.getItem('qrSettings')) || { upiId: 'gauraksha@paytm', upiName: 'Gau Mata Raksha' };
        let cows = JSON.parse(localStorage.getItem('cows')) || [];
        let admins = JSON.parse(localStorage.getItem('admins')) || [];
        let currentUser = null;
        let currentDonationData = null;
        let currentFeedDonationData = null;

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

        if (admins.length === 0) {
            admins = [
                { id: 1, username: 'admin', password: 'admin123', name: 'मुख्य प्रशासक', panchayatId: null, role: 'super' },
                { id: 2, username: 'rajpur_admin', password: 'rajpur123', name: 'राजपुर प्रशासक', panchayatId: 1, role: 'panchayat' },
                { id: 3, username: 'gangapur_admin', password: 'gangapur123', name: 'गंगापुर प्रशासक', panchayatId: 2, role: 'panchayat' },
                { id: 4, username: 'shivpur_admin', password: 'shivpur123', name: 'शिवपुर प्रशासक', panchayatId: 3, role: 'panchayat' }
            ];
            localStorage.setItem('admins', JSON.stringify(admins));
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
            
            currentUser = { type: 'user', name: name, phone: phone };
            hideUserLogin();
            
            document.getElementById('homePage').classList.add('hidden');
            document.getElementById('userDashboard').classList.remove('hidden');
            document.getElementById('userWelcome').textContent = `स्वागत है, ${name}`;
            
            showUserSection('userDonate');
            loadUserDonationPanchayats();
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
            if (sectionName === 'adminDonations') loadAdminDonations();
            if (sectionName === 'adminFeed') loadAdminFeed();
            if (sectionName === 'adminQR') loadAdminQR();
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

        // Process user donation
        function processUserDonation(event) {
            event.preventDefault();
            
            const panchayatId = document.getElementById('userDonationPanchayat').value;
            const amount = document.getElementById('userDonationAmount').value;
            
            if (!panchayatId) {
                alert('❌ कृपया पंचायत चुनें');
                return;
            }
            
            if (!amount || amount < 51) {
                alert('❌ कृपया न्यूनतम ₹51 की राशि दर्ज करें');
                return;
            }
            
            const panchayat = panchayats.find(p => p.id === parseInt(panchayatId));
            
            // Show confirmation before proceeding
            const confirmMsg = `🙏 दान की पुष्टि करें:\n\n👤 दानदाता: ${currentUser.name}\n💰 राशि: ₹${amount}\n🏠 पंचायत: ${panchayat ? panchayat.name : 'अज्ञात'}\n\nक्या आप दान करना चाहते हैं?`;
            
            if (confirm(confirmMsg)) {
                currentDonationData = {
                    donorName: currentUser.name,
                    donorPhone: currentUser.phone,
                    panchayatId: parseInt(panchayatId),
                    amount: amount
                };

                showQRPayment(amount);
            }
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

        // Calculate feed cost
        function calculateFeedCost() {
            const feedType = document.getElementById('selectedFeedType').value;
            const quantity = document.getElementById('userFeedQuantity').value;
            
            if (!feedType || !quantity) {
                document.getElementById('feedCostEstimate').textContent = '₹0';
                return;
            }
            
            const rates = {
                'bhusa': 18,
                'grass': 10,
                'hay': 12,
                'grains': 30
            };
            
            const cost = quantity * rates[feedType];
            document.getElementById('feedCostEstimate').textContent = `₹${cost}`;
        }

        // Add event listener for quantity input
        document.addEventListener('DOMContentLoaded', function() {
            const quantityInput = document.getElementById('userFeedQuantity');
            if (quantityInput) {
                quantityInput.addEventListener('input', calculateFeedCost);
            }
        });

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
            
            const rates = {
                'bhusa': 18,
                'grass': 10,
                'hay': 12,
                'grains': 30
            };
            
            const feedTypeNames = {
                'bhusa': 'भूसा',
                'grass': 'हरी घास',
                'hay': 'सूखी घास',
                'grains': 'अनाज'
            };
            
            const cost = quantity * rates[feedType];
            const panchayat = panchayats.find(p => p.id === parseInt(panchayatId));
            
            // Show confirmation before proceeding
            const confirmMsg = `🌾 चारा दान की पुष्टि करें:\n\n👤 दानदाता: ${currentUser.name}\n🌾 चारा: ${quantity} किलो ${feedTypeNames[feedType]}\n💰 लागत: ₹${cost}\n🏠 पंचायत: ${panchayat ? panchayat.name : 'अज्ञात'}\n\nक्या आप चारा दान करना चाहते हैं?`;
            
            if (confirm(confirmMsg)) {
                currentFeedDonationData = {
                    donorName: currentUser.name,
                    donorPhone: currentUser.phone,
                    panchayatId: parseInt(panchayatId),
                    feedType: feedType,
                    feedTypeName: feedTypeNames[feedType],
                    quantity: quantity,
                    cost: cost
                };

                showQRPayment(cost);
            }
        }

        // Show QR Payment
        function showQRPayment(amount) {
            try {
                document.getElementById('qrAmount').textContent = amount;
                document.getElementById('qrCodeContainer').innerHTML = '<div class="text-center p-4">QR कोड लोड हो रहा है...</div>';
                
                // Show modal first
                document.getElementById('qrPaymentModal').classList.remove('hidden');
                document.getElementById('qrPaymentModal').classList.add('flex');
                
                // Generate QR code after modal is shown
                setTimeout(() => {
                    try {
                        const upiString = `upi://pay?pa=${qrSettings.upiId}&pn=${encodeURIComponent(qrSettings.upiName)}&am=${amount}&cu=INR&tn=Gau%20Mata%20Seva%20Donation`;
                        
                        // Clear container
                        document.getElementById('qrCodeContainer').innerHTML = '';
                        
                        // Create canvas element
                        const canvas = document.createElement('canvas');
                        document.getElementById('qrCodeContainer').appendChild(canvas);
                        
                        QRCode.toCanvas(canvas, upiString, {
                            width: 200,
                            height: 200,
                            margin: 2,
                            color: {
                                dark: '#000000',
                                light: '#FFFFFF'
                            }
                        }, function (error) {
                            if (error) {
                                console.error('QR Code Error:', error);
                                document.getElementById('qrCodeContainer').innerHTML = `
                                    <div class="text-center p-4 bg-blue-50 rounded-lg">
                                        <div class="text-4xl mb-2">📱</div>
                                        <p class="text-sm text-gray-700">QR कोड उपलब्ध नहीं</p>
                                        <p class="text-xs text-gray-500 mt-1">कृपया मैन्युअल भुगतान करें</p>
                                        <div class="mt-3 p-2 bg-white rounded border text-xs">
                                            <strong>UPI ID:</strong> ${qrSettings.upiId}<br>
                                            <strong>राशि:</strong> ₹${amount}
                                        </div>
                                    </div>
                                `;
                            } else {
                                console.log('✅ QR Code generated successfully');
                            }
                        });
                    } catch (qrError) {
                        console.error('QR Generation Error:', qrError);
                        document.getElementById('qrCodeContainer').innerHTML = `
                            <div class="text-center p-4 bg-blue-50 rounded-lg">
                                <div class="text-4xl mb-2">💳</div>
                                <p class="text-sm text-gray-700">मैन्युअल भुगतान करें</p>
                                <div class="mt-3 p-3 bg-white rounded border text-sm">
                                    <strong>UPI ID:</strong> ${qrSettings.upiId}<br>
                                    <strong>नाम:</strong> ${qrSettings.upiName}<br>
                                    <strong>राशि:</strong> ₹${amount}
                                </div>
                            </div>
                        `;
                    }
                }, 500);
                
                console.log('✅ QR Payment modal opened for amount:', amount);
            } catch (error) {
                console.error('Error showing QR payment:', error);
                // Don't show error alert, just proceed with manual payment option
                document.getElementById('qrAmount').textContent = amount;
                document.getElementById('qrCodeContainer').innerHTML = `
                    <div class="text-center p-4 bg-blue-50 rounded-lg">
                        <div class="text-4xl mb-2">💳</div>
                        <p class="text-sm text-gray-700">मैन्युअल भुगतान करें</p>
                        <div class="mt-3 p-3 bg-white rounded border text-sm">
                            <strong>UPI ID:</strong> ${qrSettings.upiId}<br>
                            <strong>नाम:</strong> ${qrSettings.upiName}<br>
                            <strong>राशि:</strong> ₹${amount}
                        </div>
                    </div>
                `;
                document.getElementById('qrPaymentModal').classList.remove('hidden');
                document.getElementById('qrPaymentModal').classList.add('flex');
            }
        }

        // Hide QR Payment
        function hideQRPayment() {
            document.getElementById('qrPaymentModal').classList.add('hidden');
            document.getElementById('qrPaymentModal').classList.remove('flex');
            currentDonationData = null;
            currentFeedDonationData = null;
        }

        // Confirm QR Payment
        function confirmQRPayment() {
            try {
                console.log('🔄 Confirming payment...');
                console.log('Current donation data:', currentDonationData);
                console.log('Current feed donation data:', currentFeedDonationData);
                
                // Ask for donor name confirmation
                let donorName = '';
                if (currentDonationData) {
                    donorName = prompt(`💰 भुगतान की पुष्टि करें!\n\nकृपया अपना नाम दर्ज करें:\n(वर्तमान: ${currentDonationData.donorName})`, currentDonationData.donorName);
                } else if (currentFeedDonationData) {
                    donorName = prompt(`🌾 चारा दान की पुष्टि करें!\n\nकृपया अपना नाम दर्ज करें:\n(वर्तमान: ${currentFeedDonationData.donorName})`, currentFeedDonationData.donorName);
                }
                
                if (!donorName || donorName.trim() === '') {
                    alert('❌ कृपया अपना नाम दर्ज करें');
                    return;
                }
                
                if (currentDonationData) {
                    // Update donor name
                    currentDonationData.donorName = donorName.trim();
                    const panchayat = panchayats.find(p => p.id === currentDonationData.panchayatId);
                    const donation = {
                        ...currentDonationData,
                        id: Date.now(),
                        date: new Date().toLocaleDateString('hi-IN'),
                        time: new Date().toLocaleTimeString('hi-IN'),
                        paymentMethod: 'QR',
                        panchayatName: panchayat ? panchayat.name : 'अज्ञात'
                    };
                    
                    console.log('💰 Processing donation:', donation);
                    
                    donations.push(donation);
                    localStorage.setItem('donations', JSON.stringify(donations));
                    
                    console.log('✅ Donation saved to localStorage');
                    console.log('Total donations now:', donations.length);
                    
                    // Add to recent activities
                    addRecentActivity(`💰 ${donation.donorName} ने ${panchayat ? panchayat.name : 'अज्ञात पंचायत'} के लिए ₹${donation.amount} का दान किया`, 'donation');
                    
                    hideQRPayment();
                    
                    // Reset form
                    document.getElementById('userDonationAmount').value = '';
                    document.getElementById('userDonationPanchayat').value = '';
                    document.querySelectorAll('.amount-btn').forEach(btn => {
                        btn.classList.remove('selected');
                    });
                    
                    // Show success message with details
                    const successMsg = `🎉 दान सफल!\n\n✅ दानदाता: ${donation.donorName}\n💰 राशि: ₹${donation.amount}\n🏠 पंचायत: ${panchayat ? panchayat.name : 'अज्ञात'}\n📅 दिनांक: ${donation.date}\n\nआपका दान सफलतापूर्वक दर्ज हो गया है। गौ माता का आशीर्वाद आप पर बना रहे! 🙏`;
                    alert(successMsg);
                    
                    updateAllStats();
                    
                    // Real-time admin updates
                    setTimeout(() => {
                        updateAdminStats();
                        loadRecentActivities();
                        updateQRStats();
                        loadRecentQRPayments();
                        
                        // Update admin tables if visible
                        if (!document.getElementById('adminDonations').classList.contains('hidden')) {
                            loadAdminDonations();
                        }
                        if (!document.getElementById('adminFeed').classList.contains('hidden')) {
                            loadAdminFeed();
                        }
                    }, 100);
                    
                    console.log('✅ Donation process completed successfully');
                    
                } else if (currentFeedDonationData) {
                    // Update donor name
                    currentFeedDonationData.donorName = donorName.trim();
                    const panchayat = panchayats.find(p => p.id === currentFeedDonationData.panchayatId);
                    const feedDonation = {
                        ...currentFeedDonationData,
                        id: Date.now(),
                        date: new Date().toLocaleDateString('hi-IN'),
                        time: new Date().toLocaleTimeString('hi-IN'),
                        paymentMethod: 'QR',
                        panchayatName: panchayat ? panchayat.name : 'अज्ञात'
                    };
                    
                    console.log('🌾 Processing feed donation:', feedDonation);
                    
                    feedDonations.push(feedDonation);
                    localStorage.setItem('feedDonations', JSON.stringify(feedDonations));
                    
                    console.log('✅ Feed donation saved to localStorage');
                    console.log('Total feed donations now:', feedDonations.length);
                    
                    // Add to recent activities
                    addRecentActivity(`🌾 ${feedDonation.donorName} ने ${panchayat ? panchayat.name : 'अज्ञात पंचायत'} के लिए ${feedDonation.quantity} किलो ${feedDonation.feedTypeName} दान किया`, 'feed');
                    
                    hideQRPayment();
                    
                    // Reset form
                    document.getElementById('userFeedQuantity').value = '';
                    document.getElementById('userFeedPanchayat').value = '';
                    document.getElementById('selectedFeedType').value = '';
                    document.getElementById('feedCostEstimate').textContent = '₹0';
                    document.querySelectorAll('.feed-type-btn').forEach(btn => {
                        btn.classList.remove('selected');
                    });
                    
                    // Show success message with details
                    const successMsg = `🎉 चारा दान सफल!\n\n✅ दानदाता: ${feedDonation.donorName}\n🌾 चारा: ${feedDonation.quantity} किलो ${feedDonation.feedTypeName}\n💰 लागत: ₹${feedDonation.cost}\n🏠 पंचायत: ${panchayat ? panchayat.name : 'अज्ञात'}\n📅 दिनांक: ${feedDonation.date}\n\nआपका चारा दान सफलतापूर्वक दर्ज हो गया है। गौ माता का आशीर्वाद आप पर बना रहे! 🙏`;
                    alert(successMsg);
                    
                    updateAllStats();
                    
                    // Real-time admin updates
                    setTimeout(() => {
                        updateAdminStats();
                        loadRecentActivities();
                        updateQRStats();
                        loadRecentQRPayments();
                        
                        // Update admin tables if visible
                        if (!document.getElementById('adminDonations').classList.contains('hidden')) {
                            loadAdminDonations();
                        }
                        if (!document.getElementById('adminFeed').classList.contains('hidden')) {
                            loadAdminFeed();
                        }
                    }, 100);
                    
                    console.log('✅ Feed donation process completed successfully');
                    
                } else {
                    console.error('❌ No donation data found');
                    alert('❌ दान की जानकारी नहीं मिली। कृपया फिर से कोशिश करें।');
                }
            } catch (error) {
                console.error('❌ Error in confirmQRPayment:', error);
                alert('❌ दान प्रक्रिया में समस्या हुई। कृपया फिर से कोशिश करें।');
            }
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
            let filteredDonations = donations;
            let filteredFeedDonations = feedDonations;
            
            if (currentUser && currentUser.role === 'panchayat') {
                filteredPanchayats = panchayats.filter(p => p.id === currentUser.panchayatId);
                filteredCows = cows.filter(c => c.panchayatId === currentUser.panchayatId);
                filteredDonations = donations.filter(d => d.panchayatId === currentUser.panchayatId);
                filteredFeedDonations = feedDonations.filter(f => f.panchayatId === currentUser.panchayatId);
            }
            
            document.getElementById('adminTotalPanchayats').textContent = filteredPanchayats.length;
            document.getElementById('adminTotalCows').textContent = filteredCows.length;
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
            
            // Add to recent activities
            addRecentActivity(`🏠 नई पंचायत "${name}" जोड़ी गई - ${district}, ${state}`, 'admin');
            
            hideAddPanchayatForm();
            loadAdminPanchayats();
            updateAllStats();
            alert('🎉 नई पंचायत सफलतापूर्वक जोड़ी गई!');
        }

        // Delete panchayat
        function deletePanchayat(id) {
            if (confirm('क्या आप वाकई इस पंचायत को हटाना चाहते हैं?')) {
                const panchayat = panchayats.find(p => p.id === id);
                panchayats = panchayats.filter(p => p.id !== id);
                localStorage.setItem('panchayats', JSON.stringify(panchayats));
                
                // Add to recent activities
                addRecentActivity(`🗑️ पंचायत "${panchayat.name}" को हटा दिया गया`, 'admin');
                
                loadAdminPanchayats();
                updateAllStats();
            }
        }

        // Load admin cows
        function loadAdminCows() {
            const container = document.getElementById('adminCowsList');
            container.innerHTML = '';
            
            let filteredCows = cows;
            if (currentUser && currentUser.role === 'panchayat') {
                filteredCows = cows.filter(c => c.panchayatId === currentUser.panchayatId);
            }
            
            filteredCows.forEach(cow => {
                const panchayat = panchayats.find(p => p.id === cow.panchayatId);
                const healthColor = cow.health === 'स्वस्थ' ? 'text-green-600' : 
                                  cow.health === 'बीमार' ? 'text-red-600' : 
                                  cow.health === 'गर्भवती' ? 'text-purple-600' : 'text-blue-600';
                
                container.innerHTML += `
                    <div class="bg-white rounded-xl p-6 shadow-lg card-hover">
                        <div class="flex items-center justify-between mb-4">
                            <h3 class="text-xl font-semibold text-gray-800">🐄 ${cow.name}</h3>
                            <span class="text-sm ${healthColor} font-semibold">${cow.health}</span>
                        </div>
                        <div class="space-y-2 mb-4">
                            <p class="text-gray-600">📍 ${panchayat ? panchayat.name : 'अज्ञात पंचायत'}</p>
                            <p class="text-gray-600">🎂 उम्र: ${cow.age} वर्ष</p>
                            <p class="text-gray-600">🧬 नस्ल: ${cow.breed}</p>
                        </div>
                        <div class="flex space-x-2">
                            <button onclick="editCow(${cow.id})" class="flex-1 bg-blue-500 hover:bg-blue-600 text-white py-2 rounded-lg text-sm">
                                संपादित करें
                            </button>
                            <button onclick="deleteCow(${cow.id})" class="flex-1 bg-red-500 hover:bg-red-600 text-white py-2 rounded-lg text-sm">
                                हटाएं
                            </button>
                        </div>
                    </div>
                `;
            });
            
            if (filteredCows.length === 0) {
                container.innerHTML = '<div class="col-span-full text-center text-gray-500 py-8">कोई गौ माता नहीं मिली</div>';
            }
        }

        // Show add cow form
        function showAddCowForm() {
            // Load panchayats for cow form
            const select = document.getElementById('cowPanchayat');
            select.innerHTML = '<option value="">पंचायत चुनें</option>';
            
            let availablePanchayats = panchayats;
            if (currentUser && currentUser.role === 'panchayat') {
                availablePanchayats = panchayats.filter(p => p.id === currentUser.panchayatId);
            }
            
            availablePanchayats.forEach(panchayat => {
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
            const panchayatId = document.getElementById('cowPanchayat').value;
            const age = document.getElementById('cowAge').value;
            const breed = document.getElementById('cowBreed').value;
            const health = document.getElementById('cowHealth').value;
            
            const newCow = {
                id: Date.now(),
                name: name,
                panchayatId: parseInt(panchayatId),
                age: parseInt(age),
                breed: breed,
                health: health,
                status: 'active'
            };
            
            cows.push(newCow);
            localStorage.setItem('cows', JSON.stringify(cows));
            
            const panchayat = panchayats.find(p => p.id === parseInt(panchayatId));
            
            // Add to recent activities
            addRecentActivity(`🐄 नई गौ माता "${name}" जोड़ी गई - ${panchayat ? panchayat.name : 'अज्ञात पंचायत'}`, 'admin');
            
            hideAddCowForm();
            loadAdminCows();
            updateAllStats();
            alert('🎉 नई गौ माता सफलतापूर्वक जोड़ी गई!');
        }

        // Delete cow
        function deleteCow(id) {
            if (confirm('क्या आप वाकई इस गौ माता को हटाना चाहते हैं?')) {
                const cow = cows.find(c => c.id === id);
                cows = cows.filter(c => c.id !== id);
                localStorage.setItem('cows', JSON.stringify(cows));
                
                // Add to recent activities
                addRecentActivity(`🗑️ गौ माता "${cow.name}" को हटा दिया गया`, 'admin');
                
                loadAdminCows();
                updateAllStats();
            }
        }

        // Edit cow (placeholder function)
        function editCow(id) {
            alert('संपादन सुविधा जल्द ही उपलब्ध होगी!');
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
            // Clear form
            document.getElementById('regPanchayatName').value = '';
            document.getElementById('regPanchayatDistrict').value = '';
            document.getElementById('regPanchayatState').value = '';
            document.getElementById('regAdminName').value = '';
            document.getElementById('regAdminPhone').value = '';
            document.getElementById('regAdminUsername').value = '';
            document.getElementById('regAdminPassword').value = '';
        }

        // Register panchayat
        function registerPanchayat(event) {
            event.preventDefault();
            
            const panchayatName = document.getElementById('regPanchayatName').value;
            const district = document.getElementById('regPanchayatDistrict').value;
            const state = document.getElementById('regPanchayatState').value;
            const adminName = document.getElementById('regAdminName').value;
            const adminPhone = document.getElementById('regAdminPhone').value;
            const username = document.getElementById('regAdminUsername').value;
            const password = document.getElementById('regAdminPassword').value;
            
            // Check if username already exists
            const existingAdmin = admins.find(a => a.username === username);
            if (existingAdmin) {
                alert('❌ यह यूजरनेम पहले से मौजूद है। कृपया दूसरा यूजरनेम चुनें।');
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
            
            // Create new admin
            const newAdmin = {
                id: Date.now() + 1,
                username: username,
                password: password,
                name: adminName,
                phone: adminPhone,
                panchayatId: newPanchayat.id,
                role: 'panchayat'
            };
            
            // Save to localStorage
            panchayats.push(newPanchayat);
            admins.push(newAdmin);
            localStorage.setItem('panchayats', JSON.stringify(panchayats));
            localStorage.setItem('admins', JSON.stringify(admins));
            
            // Add to recent activities
            addRecentActivity(`🏠 नई पंचायत "${panchayatName}" रजिस्टर हुई - एडमिन: ${adminName}`, 'admin');
            
            hidePanchayatRegistration();
            updateAllStats();
            
            alert(`🎉 पंचायत रजिस्ट्रेशन सफल!\n\n📋 विवरण:\n🏠 पंचायत: ${panchayatName}\n📍 स्थान: ${district}, ${state}\n👨‍💼 एडमिन: ${adminName}\n📱 फोन: ${adminPhone}\n🔑 यूजरनेम: ${username}\n\nअब आप लॉगिन कर सकते हैं!`);
        }

        // Load admin donations
        function loadAdminDonations() {
            const tbody = document.getElementById('adminDonationsTable');
            tbody.innerHTML = '';
            
            donations.forEach(donation => {
                const panchayat = panchayats.find(p => p.id === donation.panchayatId);
                
                tbody.innerHTML += `
                    <tr>
                        <td class="px-6 py-4 whitespace-nowrap">
                            <div class="font-medium text-gray-900">${donation.donorName}</div>
                            <div class="text-sm text-gray-500">${donation.donorPhone || 'फोन नहीं'}</div>
                        </td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-900">
                            ${panchayat ? panchayat.name : 'अज्ञात'}
                        </td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">₹${donation.amount}</td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${donation.date}</td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm font-medium">
                            <button onclick="deleteDonation(${donation.id})" class="text-red-600 hover:text-red-900">हटाएं</button>
                        </td>
                    </tr>
                `;
            });
        }

        // Delete donation
        function deleteDonation(id) {
            if (confirm('क्या आप वाकई इस दान को हटाना चाहते हैं?')) {
                const donation = donations.find(d => d.id === id);
                donations = donations.filter(d => d.id !== id);
                localStorage.setItem('donations', JSON.stringify(donations));
                
                // Add to recent activities
                addRecentActivity(`🗑️ ${donation.donorName} का ₹${donation.amount} दान रिकॉर्ड हटाया गया`, 'admin');
                
                loadAdminDonations();
                updateAllStats();
            }
        }

        // Load admin feed
        function loadAdminFeed() {
            const tbody = document.getElementById('adminFeedTable');
            tbody.innerHTML = '';
            
            feedDonations.forEach(feedDonation => {
                const panchayat = panchayats.find(p => p.id === feedDonation.panchayatId);
                
                tbody.innerHTML += `
                    <tr>
                        <td class="px-6 py-4 whitespace-nowrap">
                            <div class="font-medium text-gray-900">${feedDonation.donorName}</div>
                            <div class="text-sm text-gray-500">${feedDonation.donorPhone || 'फोन नहीं'}</div>
                        </td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-900">
                            ${panchayat ? panchayat.name : 'अज्ञात'}
                        </td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-900">${feedDonation.feedTypeName}</td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">${feedDonation.quantity} किलो</td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">₹${feedDonation.cost}</td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">${feedDonation.date}</td>
                        <td class="px-6 py-4 whitespace-nowrap text-sm font-medium">
                            <button onclick="deleteFeedDonation(${feedDonation.id})" class="text-red-600 hover:text-red-900">हटाएं</button>
                        </td>
                    </tr>
                `;
            });
        }

        // Delete feed donation
        function deleteFeedDonation(id) {
            if (confirm('क्या आप वाकई इस चारा दान को हटाना चाहते हैं?')) {
                const feedDonation = feedDonations.find(f => f.id === id);
                feedDonations = feedDonations.filter(f => f.id !== id);
                localStorage.setItem('feedDonations', JSON.stringify(feedDonations));
                
                // Add to recent activities
                addRecentActivity(`🗑️ ${feedDonation.donorName} का ${feedDonation.quantity} किलो ${feedDonation.feedTypeName} चारा दान रिकॉर्ड हटाया गया`, 'admin');
                
                loadAdminFeed();
                updateAllStats();
            }
        }

        // Auto-refresh stats every 3 seconds
        function startAutoRefresh() {
            setInterval(() => {
                if (!document.getElementById('homePage').classList.contains('hidden')) {
                    updateHomeStats();
                }
            }, 3000);
        }

        // QR Admin Functions
        function loadAdminQR() {
            // Load current settings
            document.getElementById('adminUpiId').value = qrSettings.upiId;
            document.getElementById('adminUpiName').value = qrSettings.upiName;
            
            // Update QR statistics
            updateQRStats();
            loadRecentQRPayments();
            
            // Generate test QR automatically
            generateTestQR();
        }

        function updateQRSettings() {
            const upiId = document.getElementById('adminUpiId').value;
            const upiName = document.getElementById('adminUpiName').value;
            
            if (!upiId || !upiName) {
                alert('❌ कृपया सभी फील्ड भरें');
                return;
            }
            
            qrSettings = { upiId: upiId, upiName: upiName };
            localStorage.setItem('qrSettings', JSON.stringify(qrSettings));
            
            // Add to recent activities
            addRecentActivity(`⚙️ QR सेटिंग्स अपडेट की गई - UPI: ${upiId}`, 'admin');
            
            alert('✅ QR सेटिंग्स सफलतापूर्वक अपडेट हो गई!');
            generateTestQR();
        }

        function generateTestQR() {
            try {
                document.getElementById('adminQRPreview').innerHTML = '<div class="text-center p-2 text-sm">लोड हो रहा है...</div>';
                
                setTimeout(() => {
                    try {
                        const upiString = `upi://pay?pa=${qrSettings.upiId}&pn=${encodeURIComponent(qrSettings.upiName)}&am=100&cu=INR&tn=Test%20Payment`;
                        
                        // Clear container
                        document.getElementById('adminQRPreview').innerHTML = '';
                        
                        // Create canvas element
                        const canvas = document.createElement('canvas');
                        document.getElementById('adminQRPreview').appendChild(canvas);
                        
                        QRCode.toCanvas(canvas, upiString, {
                            width: 150,
                            height: 150,
                            margin: 2,
                            color: {
                                dark: '#000000',
                                light: '#FFFFFF'
                            }
                        }, function (error) {
                            if (error) {
                                console.error('QR Code Error:', error);
                                document.getElementById('adminQRPreview').innerHTML = `
                                    <div class="text-center p-3 bg-gray-100 rounded text-sm">
                                        <div class="text-2xl mb-1">📱</div>
                                        <p>QR प्रीव्यू उपलब्ध नहीं</p>
                                        <p class="text-xs mt-1">UPI: ${qrSettings.upiId}</p>
                                    </div>
                                `;
                            } else {
                                console.log('✅ Admin QR Preview generated successfully');
                            }
                        });
                    } catch (qrError) {
                        console.error('QR Generation Error:', qrError);
                        document.getElementById('adminQRPreview').innerHTML = `
                            <div class="text-center p-3 bg-gray-100 rounded text-sm">
                                <div class="text-2xl mb-1">💳</div>
                                <p>मैन्युअल सेटिंग्स</p>
                                <p class="text-xs mt-1">UPI: ${qrSettings.upiId}</p>
                            </div>
                        `;
                    }
                }, 300);
            } catch (error) {
                console.error('Error generating test QR:', error);
                document.getElementById('adminQRPreview').innerHTML = `
                    <div class="text-center p-3 bg-gray-100 rounded text-sm">
                        <div class="text-2xl mb-1">⚙️</div>
                        <p>QR सेटिंग्स सक्रिय</p>
                        <p class="text-xs mt-1">UPI: ${qrSettings.upiId}</p>
                    </div>
                `;
            }
        }

        function updateQRStats() {
            // Count QR payments (all donations and feed donations use QR)
            const totalQRPayments = donations.length + feedDonations.length;
            const totalMoney = donations.reduce((sum, d) => sum + parseInt(d.amount || 0), 0);
            const feedCost = feedDonations.reduce((sum, f) => sum + parseInt(f.cost || 0), 0);
            const totalQRAmount = totalMoney + feedCost;
            
            const today = new Date().toLocaleDateString('hi-IN');
            const todayDonations = donations.filter(d => d.date === today).length;
            const todayFeedDonations = feedDonations.filter(f => f.date === today).length;
            const todayQRPayments = todayDonations + todayFeedDonations;
            
            document.getElementById('qrTotalPayments').textContent = totalQRPayments;
            document.getElementById('qrTotalAmount').textContent = `₹${totalQRAmount.toLocaleString('hi-IN')}`;
            document.getElementById('qrTodayPayments').textContent = todayQRPayments;
            document.getElementById('qrSuccessRate').textContent = '100%'; // Assuming all confirmed payments are successful
        }

        function loadRecentQRPayments() {
            const container = document.getElementById('recentQRPayments');
            container.innerHTML = '';
            
            // Combine and sort all QR payments
            const allQRPayments = [
                ...donations.map(d => ({...d, type: 'donation', displayAmount: d.amount})),
                ...feedDonations.map(f => ({...f, type: 'feed', displayAmount: f.cost}))
            ].sort((a, b) => b.id - a.id);
            
            if (allQRPayments.length === 0) {
                container.innerHTML = '<p class="text-gray-500">कोई QR भुगतान नहीं मिला</p>';
                return;
            }
            
            allQRPayments.slice(0, 10).forEach(payment => {
                const panchayat = panchayats.find(p => p.id === payment.panchayatId);
                const typeIcon = payment.type === 'donation' ? '💰' : '🌾';
                const typeText = payment.type === 'donation' ? 'दान' : 'चारा दान';
                
                container.innerHTML += `
                    <div class="flex items-start justify-between p-3 bg-gray-50 rounded hover:bg-gray-100">
                        <div class="flex items-start space-x-2">
                            <span class="text-lg">${typeIcon}</span>
                            <div>
                                <p class="font-medium text-sm text-gray-800">${payment.donorName} - ₹${payment.displayAmount} (${typeText})</p>
                                <p class="text-xs text-gray-500">${panchayat ? panchayat.name : 'अज्ञात पंचायत'} • ${payment.time}</p>
                            </div>
                        </div>
                        <span class="text-xs text-green-600 font-semibold">✅ सफल</span>
                    </div>
                `;
            });
        }

        // Mobile Menu Functions
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

        // Close mobile menus when clicking outside
        document.addEventListener('click', function(event) {
            const mobileMenu = document.getElementById('mobileMenu');
            const userMobileMenu = document.getElementById('userMobileMenu');
            const adminMobileMenu = document.getElementById('adminMobileMenu');
            
            // Check if click is outside mobile menu
            if (!event.target.closest('header') && !mobileMenu.classList.contains('hidden')) {
                hideMobileMenu();
            }
            if (!event.target.closest('header') && !userMobileMenu.classList.contains('hidden')) {
                hideUserMobileMenu();
            }
            if (!event.target.closest('header') && !adminMobileMenu.classList.contains('hidden')) {
                hideAdminMobileMenu();
            }
        });

        // PDF Generation Functions
        function generateDonationsPDF() {
            try {
                let pdfContent = `
गौ माता रक्षा योजना - दान रिपोर्ट
=======================================
रिपोर्ट तिथि: ${new Date().toLocaleDateString('hi-IN')}
कुल दान: ${donations.length}
कुल राशि: ₹${donations.reduce((sum, d) => sum + parseInt(d.amount || 0), 0).toLocaleString('hi-IN')}

दानदाता सूची:
--------------
`;
                
                donations.forEach((donation, index) => {
                    const panchayat = panchayats.find(p => p.id === donation.panchayatId);
                    pdfContent += `
${index + 1}. दानदाता: ${donation.donorName}
   फोन: ${donation.donorPhone || 'N/A'}
   राशि: ₹${donation.amount}
   पंचायत: ${panchayat ? panchayat.name : 'अज्ञात'}
   दिनांक: ${donation.date}
   समय: ${donation.time}
   `;
                });
                
                downloadTextAsPDF(pdfContent, 'गौ-माता-दान-रिपोर्ट.txt');
                
                // Add to recent activities
                addRecentActivity(`📄 दान रिपोर्ट PDF डाउनलोड की गई (${donations.length} entries)`, 'admin');
                
            } catch (error) {
                console.error('PDF Generation Error:', error);
                alert('❌ PDF जेनरेशन में समस्या हुई');
            }
        }

        function generateFeedPDF() {
            try {
                let pdfContent = `
गौ माता रक्षा योजना - चारा दान रिपोर्ट
=====================================
रिपोर्ट तिथि: ${new Date().toLocaleDateString('hi-IN')}
कुल चारा दान: ${feedDonations.length}
कुल लागत: ₹${feedDonations.reduce((sum, f) => sum + parseInt(f.cost || 0), 0).toLocaleString('hi-IN')}

चारा दानदाता सूची:
------------------
`;
                
                feedDonations.forEach((feed, index) => {
                    const panchayat = panchayats.find(p => p.id === feed.panchayatId);
                    pdfContent += `
${index + 1}. दानदाता: ${feed.donorName}
   फोन: ${feed.donorPhone || 'N/A'}
   चारा प्रकार: ${feed.feedTypeName}
   मात्रा: ${feed.quantity} किलो
   लागत: ₹${feed.cost}
   पंचायत: ${panchayat ? panchayat.name : 'अज्ञात'}
   दिनांक: ${feed.date}
   समय: ${feed.time}
   `;
                });
                
                downloadTextAsPDF(pdfContent, 'गौ-माता-चारा-रिपोर्ट.txt');
                
                // Add to recent activities
                addRecentActivity(`📄 चारा दान रिपोर्ट PDF डाउनलोड की गई (${feedDonations.length} entries)`, 'admin');
                
            } catch (error) {
                console.error('PDF Generation Error:', error);
                alert('❌ PDF जेनरेशन में समस्या हुई');
            }
        }

        function generateAllDataPDF() {
            try {
                const totalMoney = donations.reduce((sum, d) => sum + parseInt(d.amount || 0), 0);
                const totalFeedCost = feedDonations.reduce((sum, f) => sum + parseInt(f.cost || 0), 0);
                const grandTotal = totalMoney + totalFeedCost;
                
                let pdfContent = `
गौ माता रक्षा योजना - संपूर्ण रिपोर्ट
===================================
रिपोर्ट तिथि: ${new Date().toLocaleDateString('hi-IN')}

📊 सारांश:
----------
कुल पंचायत: ${panchayats.length}
कुल गौ माता: ${cows.length}
कुल दान: ${donations.length}
कुल चारा दान: ${feedDonations.length}
कुल दान राशि: ₹${totalMoney.toLocaleString('hi-IN')}
कुल चारा लागत: ₹${totalFeedCost.toLocaleString('hi-IN')}
महा योग: ₹${grandTotal.toLocaleString('hi-IN')}

🏠 पंचायत सूची:
---------------
`;
                
                panchayats.forEach((panchayat, index) => {
                    pdfContent += `${index + 1}. ${panchayat.name}, ${panchayat.district}, ${panchayat.state}\n`;
                });
                
                pdfContent += `
🐄 गौ माता सूची:
----------------
`;
                
                cows.forEach((cow, index) => {
                    const panchayat = panchayats.find(p => p.id === cow.panchayatId);
                    pdfContent += `${index + 1}. ${cow.name} (${cow.breed}, ${cow.age} वर्ष) - ${panchayat ? panchayat.name : 'अज्ञात'}\n`;
                });
                
                pdfContent += `
💰 दान विवरण:
-------------
`;
                
                donations.forEach((donation, index) => {
                    const panchayat = panchayats.find(p => p.id === donation.panchayatId);
                    pdfContent += `${index + 1}. ${donation.donorName} - ₹${donation.amount} (${panchayat ? panchayat.name : 'अज्ञात'}) - ${donation.date}\n`;
                });
                
                pdfContent += `
🌾 चारा दान विवरण:
------------------
`;
                
                feedDonations.forEach((feed, index) => {
                    const panchayat = panchayats.find(p => p.id === feed.panchayatId);
                    pdfContent += `${index + 1}. ${feed.donorName} - ${feed.quantity} किलो ${feed.feedTypeName} (₹${feed.cost}) - ${panchayat ? panchayat.name : 'अज्ञात'} - ${feed.date}\n`;
                });
                
                downloadTextAsPDF(pdfContent, 'गौ-माता-संपूर्ण-रिपोर्ट.txt');
                
                // Add to recent activities
                addRecentActivity(`📊 संपूर्ण रिपोर्ट PDF डाउनलोड की गई (${donations.length + feedDonations.length} total entries)`, 'admin');
                
            } catch (error) {
                console.error('PDF Generation Error:', error);
                alert('❌ PDF जेनरेशन में समस्या हुई');
            }
        }

        function downloadTextAsPDF(content, filename) {
            try {
                // Create a blob with the content
                const blob = new Blob([content], { type: 'text/plain;charset=utf-8' });
                
                // Create download link
                const link = document.createElement('a');
                link.href = URL.createObjectURL(blob);
                link.download = filename;
                
                // Trigger download
                document.body.appendChild(link);
                link.click();
                document.body.removeChild(link);
                
                // Clean up
                URL.revokeObjectURL(link.href);
                
                alert('✅ रिपोर्ट सफलतापूर्वक डाउनलोड हो गई!');
                
            } catch (error) {
                console.error('Download Error:', error);
                alert('❌ डाउनलोड में समस्या हुई');
            }
        }

        // Initialize
        document.addEventListener('DOMContentLoaded', function() {
            updateHomeStats();
            startAutoRefresh();
        });
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'975c030de28ea765',t:'MTc1NjMwMjM1NC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
