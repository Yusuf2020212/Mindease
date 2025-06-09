<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mindease - Your AI Mental Health Companion</title>
    <!-- Favicon - You can replace this with a real favicon later -->
    <link rel="icon" href="https://placehold.co/32x32/000000/FFFFFF?text=ME" type="image/x-icon">
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        inter: ['Inter', 'sans-serif'],
                    },
                    colors: {
                        'mindease-green': '#376E6F',
                        'mindease-light-green': '#A7D4C8',
                        'mindease-yellow': '#FDCB6E',
                        'mindease-bg-light': '#F8F4E3',
                        'mindease-text-dark': '#2B2B2B',
                    },
                    keyframes: { // Define custom keyframes for animations
                        'fade-in-down': {
                            '0%': { opacity: '0', transform: 'translateY(-10px)' },
                            '100%': { opacity: '1', transform: 'translateY(0)' },
                        },
                        'fade-in-up': {
                            '0%': { opacity: '0', transform: 'translateY(10px)' },
                            '100%': { opacity: '1', transform: 'translateY(0)' },
                        },
                        'bounce-in': { // A more pronounced entrance bounce
                            '0%': { opacity: '0', transform: 'scale(0.3) translateY(20px)' },
                            '20%': { opacity: '1', transform: 'scale(1.1) translateY(-10px)' },
                            '40%': { transform: 'scale(0.9) translateY(5px)' },
                            '60%': { transform: 'scale(1.03) translateY(-3px)' },
                            '80%': { transform: 'scale(0.97) translateY(1px)' },
                            '100%': { transform: 'scale(1) translateY(0)' },
                        },
                    },
                    animation: { // Map keyframes to animation utility classes
                        'fade-in-down': 'fade-in-down 0.8s ease-out forwards',
                        'fade-in-up': 'fade-in-up 0.8s ease-out forwards',
                        'bounce-in': 'bounce-in 1.2s ease-out forwards', // Adjusted duration
                    }
                }
            }
        }
    </script>
    <style>
        /* Custom font import for Inter - if not loaded via Tailwind CDN default */
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');
        body {
            font-family: 'Inter', sans-serif;
            background-color: #F8F4E3; /* mindease-bg-light */
            color: #2B2B2B; /* mindease-text-dark */
        }
        /* Smooth scrolling for anchor links */
        html {
            scroll-behavior: smooth;
        }
        /* Custom scrollbar for better aesthetics */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #f1f1f1;
            border-radius: 10px;
        }
        ::-webkit-scrollbar-thumb {
            background: #888;
            border-radius: 10px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #555;
            cursor: pointer;
        }

        /* Ensure elements start hidden for animation */
        .initial-hidden {
            opacity: 0;
            transform: translateY(20px); /* For fade-in-up */
        }
        .initial-hidden-down {
            opacity: 0;
            transform: translateY(-20px); /* For fade-in-down */
        }
        .initial-hidden-bounce {
            opacity: 0;
            transform: scale(0.3); /* For bounce-in */
        }
        /* Spinner styles */
        .spinner {
            border: 4px solid rgba(0, 0, 0, 0.1);
            border-left-color: #376E6F;
            border-radius: 50%;
            width: 24px;
            height: 24px;
            animation: spin 1s linear infinite;
            display: inline-block;
            vertical-align: middle;
            margin-left: 8px;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    </style>
</head>
<body class="font-inter">

    <!-- Header Section -->
    <header class="bg-mindease-green text-white shadow-lg fixed w-full z-10">
        <nav class="container mx-auto px-6 py-4 flex flex-col md:flex-row justify-between items-center">
            <!-- Logo -->
            <div class="flex items-center space-x-2 mb-4 md:mb-0">
                <!-- Replace this src with your actual logo URL (e.g., 'Generate a minimalis.jpg' if hosted in the same directory) -->
                <img src="https://placehold.co/1000x1000/F8F4E3/376E6F?text=Mindease+Logo" alt="Mindease Logo" class="h-10 rounded-full shadow-md" onerror="this.onerror=null;this.src='https://placehold.co/50x50/376E6F/F8F4E3?text=ME';">
                <span class="text-3xl font-bold tracking-tight">Mindease</span>
            </div>

            <!-- Navigation Links (Desktop) -->
            <div class="hidden md:flex space-x-8 text-lg font-medium">
                <a href="#hero" class="hover:text-mindease-yellow transition duration-300">Home</a>
                <a href="#about" class="hover:text-mindease-yellow transition duration-300">About Us</a>
                <a href="#features" class="hover:text-mindease-yellow transition duration-300">Features</a>
                <a href="#model" class="hover:text-mindease-yellow transition duration-300">Business Model</a>
                <a href="#mood-insight" class="hover:text-mindease-yellow transition duration-300">Mood Insight ✨</a>
                <a href="#chatbot" class="bg-mindease-yellow text-mindease-green px-6 py-2 rounded-full hover:bg-white transition duration-300 shadow-md">Chatbot ✨</a>
            </div>

            <!-- Mobile Menu Button -->
            <div class="md:hidden">
                <button id="mobile-menu-button" class="text-white focus:outline-none">
                    <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path></svg>
                </button>
            </div>
        </nav>
        <!-- Mobile Menu Overlay -->
        <div id="mobile-menu" class="md:hidden hidden bg-mindease-green text-white py-4">
            <a href="#hero" class="block px-6 py-2 hover:bg-mindease-light-green hover:text-mindease-green transition duration-300">Home</a>
            <a href="#about" class="block px-6 py-2 hover:bg-mindease-light-green hover:text-mindease-green transition duration-300">About Us</a>
            <a href="#features" class="block px-6 py-2 hover:bg-mindease-light-green hover:text-mindease-green transition duration-300">Features</a>
            <a href="#model" class="block px-6 py-2 hover:bg-mindease-light-green hover:text-mindease-green transition duration-300">Business Model</a>
            <a href="#mood-insight" class="block px-6 py-2 hover:bg-mindease-light-green hover:text-mindease-green transition duration-300">Mood Insight ✨</a>
            <a href="#chatbot" class="block px-6 py-2 bg-mindease-yellow text-mindease-green hover:bg-white transition duration-300 mt-2 mx-6 rounded-full text-center shadow-md">Chatbot ✨</a>
        </div>
    </header>

    <main class="pt-24"> <!-- Padding to account for fixed header -->

        <!-- Hero Section -->
        <section id="hero" class="relative bg-gradient-to-br from-mindease-light-green to-mindease-green min-h-[calc(100vh-6rem)] flex items-center justify-center p-8 text-white text-center overflow-hidden rounded-bl-[100px] rounded-tr-[100px] md:rounded-bl-[200px] md:rounded-tr-[200px] shadow-xl">
            <div class="absolute inset-0 z-0">
                <!-- Subtle background pattern or illustration -->
                <svg class="absolute bottom-0 left-0 w-full h-full opacity-10" viewBox="0 0 100 100" preserveAspectRatio="xMidYMid slice">
                    <defs>
                        <pattern id="pattern-circles" x="0" y="0" width="10" height="10" patternUnits="userSpaceOnUse">
                            <circle cx="2" cy="2" r="1.5" fill="rgba(255,255,255,0.2)"/>
                        </pattern>
                    </defs>
                    <rect x="0" y="0" width="100%" height="100%" fill="url(#pattern-circles)"/>
                </svg>
            </div>
            <div class="relative z-10 max-w-4xl mx-auto">
                <h1 class="text-5xl md:text-7xl font-extrabold leading-tight mb-6 initial-hidden-down">
                    Nurture Your Mind, Find Your Ease.
                </h1>
                <p class="text-xl md:text-2xl mb-8 opacity-90 initial-hidden">
                    Accessible, anonymous, and affordable AI mental health support for young adults in Sub-Saharan Africa.
                </p>
                <a href="#chatbot" class="inline-block bg-mindease-yellow text-mindease-green font-bold text-xl px-10 py-4 rounded-full shadow-lg hover:bg-white hover:scale-105 transition duration-300 transform initial-hidden-bounce">
                    Start Your Journey
                </a>
            </div>
        </section>

        <!-- About Us Section -->
        <section id="about" class="container mx-auto px-8 py-20 bg-white rounded-lg shadow-xl my-16 initial-hidden">
            <h2 class="text-4xl font-bold text-center mb-12 text-mindease-green">About Mindease</h2>
            <div class="flex flex-col md:flex-row items-center justify-between gap-12">
                <div class="md:w-1/2">
                    <p class="text-lg leading-relaxed mb-6">
                        Mindease is an innovative AI-powered mental health chatbot app designed to bridge the critical gap in mental health services across Sub-Saharan Africa. We leverage cutting-edge technology to provide anonymous, affordable, and culturally relevant support.
                    </p>
                    <p class="text-lg leading-relaxed mb-6">
                        Our mission is to empower young adults (18-35) in regions like Nigeria, where over 85% of mental health needs remain unmet due to stigma, cost, and limited access. We believe everyone deserves accessible mental well-being support, anytime, anywhere.
                    </p>
                    <p class="text-lg leading-relaxed">
                        Founded by a 21-year-old architecture student with a passion for AI, Mindease is built on a foundation of local insight and a commitment to making a real impact.
                    </p>
                </div>
                <div class="md:w-1/2 flex justify-center">
                    <img src="https://placehold.co/600x400/A7D4C8/376E6F?text=Empowering+Minds" alt="About Mindease Illustration" class="rounded-2xl shadow-lg transform hover:scale-105 transition duration-300">
                </div>
            </div>
        </section>

        <!-- Features Section -->
        <section id="features" class="bg-mindease-bg-light px-8 py-20">
            <div class="container mx-auto">
                <h2 class="text-4xl font-bold text-center mb-12 text-mindease-green">Key Features That Support You</h2>
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-10">
                    <!-- Feature 1: Anonymous AI Chatbot (now powered by Gemini) -->
                    <div class="bg-white p-8 rounded-2xl shadow-md border-b-4 border-mindease-light-green transform hover:scale-105 transition duration-300 initial-hidden">
                        <div class="text-mindease-green text-5xl mb-4 text-center">
                            <span class="block mt-2">🤖</span>
                        </div>
                        <h3 class="text-2xl font-semibold text-center mb-4 text-mindease-text-dark">Anonymous AI Chatbot ✨</h3>
                        <p class="text-center text-lg text-gray-700">Engage with our AI for empathetic support, coping strategies, and a safe space to express yourself, completely anonymously.</p>
                    </div>
                    <!-- Feature 2: Mood Tracking & Analysis (now enhanced by Gemini) -->
                    <div class="bg-white p-8 rounded-2xl shadow-md border-b-4 border-mindease-light-green transform hover:scale-105 transition duration-300 initial-hidden">
                        <div class="text-mindease-green text-5xl mb-4 text-center">
                            <span class="block mt-2">📈</span>
                        </div>
                        <h3 class="text-2xl font-semibold text-center mb-4 text-mindease-text-dark">Mood Tracking & Analysis ✨</h3>
                        <p class="text-center text-lg text-gray-700">Log your daily moods and triggers. Our AI provides insights to help you understand patterns and promote self-awareness.</p>
                    </div>
                    <!-- Feature 3 -->
                    <div class="bg-white p-8 rounded-2xl shadow-md border-b-4 border-mindease-light-green transform hover:scale-105 transition duration-300 initial-hidden">
                        <div class="text-mindease-green text-5xl mb-4 text-center">
                            <span class="block mt-2">🌿</span>
                        </div>
                        <h3 class="text-2xl font-semibold text-center mb-4 text-mindease-text-dark">Mindfulness & Resources</h3>
                        <p class="text-center text-lg text-gray-700">Access free breathing exercises, mindfulness tips, and a curated library of educational articles and videos on mental well-being.</p>
                    </div>
                    <!-- Feature 4 (Premium) -->
                    <div class="bg-white p-8 rounded-2xl shadow-md border-b-4 border-mindease-yellow transform hover:scale-105 transition duration-300 initial-hidden">
                        <div class="text-mindease-yellow text-5xl mb-4 text-center">
                            <span class="block mt-2">🌟</span>
                        </div>
                        <h3 class="text-2xl font-semibold text-center mb-4 text-mindease-text-dark">Premium Personalized Plans</h3>
                        <p class="text-center text-lg text-gray-700">Unlock personalized therapy plans, virtual group sessions, and advanced analytics with our affordable premium tiers.</p>
                    </div>
                    <!-- Feature 5 (Premium) -->
                    <div class="bg-white p-8 rounded-2xl shadow-md border-b-4 border-mindease-yellow transform hover:scale-105 transition duration-300 initial-hidden">
                        <div class="text-mindease-yellow text-5xl mb-4 text-center">
                            <span class="block mt-2">🤝</span>
                        </div>
                        <h3 class="text-2xl font-semibold text-center mb-4 text-mindease-text-dark">Community Support</h3>
                        <p class="text-center text-lg text-gray-700">Join virtual group sessions and connect with a supportive community (Premium feature).</p>
                    </div>
                    <!-- Feature 6 (Premium) -->
                    <div class="bg-white p-8 rounded-2xl shadow-md border-b-4 border-mindease-yellow transform hover:scale-105 transition duration-300 initial-hidden">
                        <div class="text-mindease-yellow text-5xl mb-4 text-center">
                            <span class="block mt-2">📊</span>
                        </div>
                        <h3 class="text-2xl font-semibold text-center mb-4 text-mindease-text-dark">Advanced Insights</h3>
                        <p class="text-center text-lg text-gray-700">Deeper analytics and insights into your mental well-being, shareable with your healthcare provider (Premium feature).</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Business Model Section -->
        <section id="model" class="container mx-auto px-8 py-20 bg-white rounded-lg shadow-xl my-16 initial-hidden">
            <h2 class="text-4xl font-bold text-center mb-12 text-mindease-green">Our Business Model</h2>
            <div class="flex flex-col lg:flex-row items-start gap-12">
                <div class="lg:w-1/2">
                    <p class="text-lg leading-relaxed mb-6">
                        Mindease operates on a flexible **freemium model**, designed to make mental health support accessible to everyone while offering advanced features for those seeking more in-depth care.
                    </p>
                    <div class="mb-8">
                        <h3 class="text-2xl font-semibold mb-4 text-mindease-text-dark">Free Tier: Empowering Basic Support</h3>
                        <ul class="list-disc list-inside text-lg text-gray-700 space-y-2">
                            <li>Anonymous AI chatbot conversations for empathetic support.</li>
                            <li>Basic mood tracking to monitor daily emotional shifts.</li>
                            <li>Access to a library of generic mindfulness exercises and educational resources.</li>
                            <li><span class="font-bold">Goal:</span> Build a large, engaged user base and foster initial awareness.</li>
                        </ul>
                    </div>
                    <div>
                        <h3 class="text-2xl font-semibold mb-4 text-mindease-text-dark">Premium Tiers: Deeper Engagement</h3>
                        <p class="text-lg leading-relaxed mb-4">
                            For users seeking personalized growth and enhanced features, we offer affordable premium subscriptions:
                        </p>
                        <ul class="list-disc list-inside text-lg text-gray-700 space-y-2">
                            <li><strong>Basic Premium ($1/month):</strong> Personalized insights from mood tracking.</li>
                            <li><strong>Standard Premium ($3/month):</strong> Guided therapy plans and advanced mood analysis.</li>
                            <li><strong>Pro Premium ($5/month):</strong> Virtual group sessions (via Zoom API) and exclusive expert content.</li>
                            <li><span class="font-bold">Goal:</span> Generate sustainable revenue, aiming for 30,000 premium users to reach $90,000/month within 12 months.</li>
                        </ul>
                    </div>
                </div>
                <div class="lg:w-1/2 mt-8 lg:mt-0">
                    <h3 class="text-2xl font-semibold mb-4 text-mindease-text-dark">Additional Revenue Streams:</h3>
                    <ul class="list-disc list-inside text-lg text-gray-700 space-y-4">
                        <li>
                            <span class="font-semibold">NGO Partnerships:</span> Collaborating with non-governmental organizations to offer subsidized access, generating commissions per referred user ($0.50/user).
                        </li>
                        <li>
                            <span class="font-semibold">Corporate Wellness Programs:</span> Providing Mindease access to corporate employees as part of their wellness initiatives (rates from $1,000–$10,000/month).
                        </li>
                        <li>
                            <span class="font-semibold">Organic Growth Focus:</span> Leveraging content marketing (X, Instagram), user referrals, and strategic local partnerships to minimize ad spend and maximize reach.
                        </li>
                    </ul>
                    <img src="https://placehold.co/600x400/FDCB6E/376E6F?text=Growth+Model" alt="Business Model Illustration" class="rounded-2xl shadow-lg mt-8 transform hover:scale-105 transition duration-300">
                </div>
            </div>
        </section>

        <!-- Mood Analysis & Insight Section (New Gemini API Feature) -->
        <section id="mood-insight" class="bg-mindease-bg-light px-8 py-20 initial-hidden">
            <div class="container mx-auto">
                <h2 class="text-4xl font-bold text-center mb-12 text-mindease-green">Your Mood, Our Insight ✨</h2>
                <p class="text-center text-lg mb-8 text-gray-700 max-w-2xl mx-auto">
                    Tell us how you're feeling, and our AI will provide a supportive insight or a gentle suggestion.
                </p>
                <div class="max-w-xl mx-auto bg-white rounded-2xl shadow-lg border-4 border-mindease-yellow overflow-hidden p-8">
                    <div class="mb-6">
                        <label for="mood-select" class="block text-mindease-text-dark text-xl font-semibold mb-3">How are you feeling today?</label>
                        <select id="mood-select" class="w-full p-3 border border-gray-300 rounded-lg text-lg focus:outline-none focus:ring-2 focus:ring-mindease-yellow">
                            <option value="">Select your mood</option>
                            <option value="Happy">😊 Happy</option>
                            <option value="Calm">😌 Calm</option>
                            <option value="Neutral">😐 Neutral</option>
                            <option value="Anxious">😟 Anxious</option>
                            <option value="Sad">😢 Sad</option>
                            <option value="Stressed">😩 Stressed</option>
                            <option value="Angry">😡 Angry</option>
                            <option value="Tired">😴 Tired</option>
                        </select>
                    </div>
                    <div class="mb-6">
                        <label for="mood-description" class="block text-mindease-text-dark text-xl font-semibold mb-3">Tell us more (optional):</label>
                        <textarea id="mood-description" rows="4" class="w-full p-3 border border-gray-300 rounded-lg text-lg focus:outline-none focus:ring-2 focus:ring-mindease-yellow" placeholder="What's making you feel this way?"></textarea>
                    </div>
                    <button id="get-insight-button" class="bg-mindease-yellow text-mindease-green font-bold text-xl px-8 py-3 rounded-full shadow-md hover:bg-mindease-green hover:text-white transition duration-300 w-full flex items-center justify-center">
                        Get Insight ✨
                        <span id="insight-spinner" class="spinner ml-3 hidden"></span>
                    </button>
                    <div id="mood-insight-result" class="mt-6 p-4 bg-mindease-light-green text-mindease-green rounded-lg shadow-inner hidden">
                        <p class="text-lg font-medium"></p>
                    </div>
                </div>
            </div>
        </section>


        <!-- Chatbot Section (Now Powered by Gemini API) -->
        <section id="chatbot" class="bg-mindease-bg-light px-8 py-20">
            <div class="container mx-auto">
                <h2 class="text-4xl font-bold text-center mb-12 text-mindease-green">Chat with Mindease AI ✨</h2>
                <p class="text-center text-lg mb-8 text-gray-700 max-w-2xl mx-auto">
                    Experience dynamic, empathetic conversations with our AI. Ask it anything about mental well-being or just share what's on your mind.
                </p>
                <div class="max-w-xl mx-auto bg-white rounded-2xl shadow-lg border-4 border-mindease-light-green overflow-hidden">
                    <!-- Chat Header -->
                    <div class="bg-mindease-green text-white p-4 flex items-center rounded-t-xl">
                        <img src="https://placehold.co/50x50/FDCB6E/376E6F?text=AI" alt="AI Avatar" class="h-12 w-12 rounded-full mr-4 border-2 border-white">
                        <div>
                            <h3 class="text-xl font-semibold">Mindease AI</h3>
                            <p class="text-sm opacity-80">Online</p>
                        </div>
                    </div>

                    <!-- Chat Messages Display -->
                    <div id="chat-messages" class="p-4 h-96 overflow-y-auto flex flex-col space-y-4">
                        <!-- Initial AI Message -->
                        <div class="flex justify-start">
                            <div class="bg-mindease-light-green text-mindease-green p-3 rounded-tr-xl rounded-bl-xl rounded-br-xl shadow max-w-[80%]">
                                <p>Hello! I'm here to listen. How can I support you today?</p>
                            </div>
                        </div>
                    </div>

                    <!-- Chat Input -->
                    <div class="p-4 border-t border-gray-200 flex items-center">
                        <input type="text" id="chat-input" class="flex-grow p-3 border border-gray-300 rounded-full focus:outline-none focus:ring-2 focus:ring-mindease-green focus:border-transparent mr-2" placeholder="Type your message here...">
                        <button id="send-button" class="bg-mindease-green text-white p-3 rounded-full shadow-md hover:bg-mindease-yellow hover:text-mindease-green transition duration-300 flex items-center justify-center">
                            Send
                            <span id="chat-spinner" class="spinner ml-2 hidden"></span>
                        </button>
                    </div>
                </div>
            </div>
        </section>

        <!-- Call to Action / Download Section (Placeholder) -->
        <section class="container mx-auto px-8 py-20 text-center initial-hidden">
            <h2 class="text-4xl font-bold text-mindease-green mb-6">Ready to Find Your Ease?</h2>
            <p class="text-xl text-gray-700 mb-10 max-w-3xl mx-auto">
                Join the Mindease community and start your journey towards a healthier, happier mind.
            </p>
            <div class="flex flex-col sm:flex-row justify-center gap-6">
                <a href="#" class="inline-block bg-mindease-green text-white font-bold text-xl px-10 py-4 rounded-full shadow-lg hover:bg-mindease-yellow hover:text-mindease-green transition duration-300 transform hover:scale-105">
                    Download on Google Play
                </a>
                <a href="#" class="inline-block bg-white text-mindease-green border-2 border-mindease-green font-bold text-xl px-10 py-4 rounded-full shadow-lg hover:bg-mindease-green hover:text-white transition duration-300 transform hover:scale-105">
                    Download on App Store
                </a>
            </div>
            <p class="mt-8 text-sm text-gray-500">
                (Links are placeholders and would lead to actual app stores once available)
            </p>
        </section>

        <!-- Contact Section -->
        <section id="contact" class="bg-mindease-green text-white px-8 py-20 rounded-tl-[100px] rounded-br-[100px] md:rounded-tl-[200px] md:rounded-br-[200px] shadow-xl initial-hidden">
            <div class="container mx-auto text-center">
                <h2 class="text-4xl font-bold mb-8">Get In Touch</h2>
                <p class="text-xl mb-10 max-w-2xl mx-auto">
                    Have questions or want to partner with Mindease? We'd love to hear from you.
                </p>
                <div class="flex flex-col md:flex-row justify-center gap-12 mb-10">
                    <div class="flex items-center flex-col md:flex-row">
                        <svg class="w-12 h-12 mr-4 mb-2 md:mb-0" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"></path></svg>
                        <p class="text-lg">info@mindease.com (placeholder)</p>
                    </div>
                    <div class="flex items-center flex-col md:flex-row">
                        <svg class="w-12 h-12 mr-4 mb-2 md:mb-0" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.828 0L6.343 16.657m10.607-2.828l1.414-1.414A4 4 0 0014.121 7.46l-2.828 2.828m0 0L7.46 14.121A4 4 0 0010.121 16.88l2.828-2.828m0 0L17.657 10.343a4 4 0 00-5.656-5.656l-1.414 1.414"></path></svg>
                        <p class="text-lg">Abuja, Nigeria</p>
                    </div>
                </div>
                <div class="mt-8 text-xl font-medium">
                    Follow us on:
                    <a href="https://twitter.com/Yuzey2020" target="_blank" class="text-mindease-yellow hover:text-white transition duration-300 ml-4 mr-2">X (@Yuzey2020)</a>
                    <a href="https://instagram.com/mindease" target="_blank" class="text-mindease-yellow hover:text-white transition duration-300 ml-2">Instagram</a>
                </div>
            </div>
        </section>

    </main>

    <!-- Footer Section -->
    <footer class="bg-mindease-text-dark text-white py-8 text-center text-sm">
        <div class="container mx-auto px-6">
            <p>&copy; 2025 Mindease. All rights reserved.</p>
            <p class="mt-2">Designed with 💚 for mental well-being.</p>
        </div>
    </footer>

    <script>
        // Mobile Menu Toggle
        const mobileMenuButton = document.getElementById('mobile-menu-button');
        const mobileMenu = document.getElementById('mobile-menu');

        mobileMenuButton.addEventListener('click', () => {
            mobileMenu.classList.toggle('hidden');
        });

        // Close mobile menu when a link is clicked
        mobileMenu.querySelectorAll('a').forEach(link => {
            link.addEventListener('click', () => {
                mobileMenu.classList.add('hidden');
            });
        });

        // --- Gemini API Integration for Chatbot ---
        const chatMessages = document.getElementById('chat-messages');
        const chatInput = document.getElementById('chat-input');
        const sendButton = document.getElementById('send-button');
        const chatSpinner = document.getElementById('chat-spinner');

        // Store chat history for context
        let chatHistory = [];

        function appendMessage(sender, message) {
            const messageDiv = document.createElement('div');
            messageDiv.classList.add('flex', sender === 'user' ? 'justify-end' : 'justify-start');

            const messageBubble = document.createElement('div');
            messageBubble.classList.add(
                'p-3',
                'rounded-xl',
                'shadow',
                'max-w-[80%]',
                sender === 'user' ? 'bg-mindease-green text-white rounded-br-none' : 'bg-mindease-light-green text-mindease-green rounded-bl-none'
            );
            messageBubble.innerHTML = `<p>${message}</p>`;

            messageDiv.appendChild(messageBubble);
            chatMessages.appendChild(messageDiv);

            // Scroll to the latest message
            chatMessages.scrollTop = chatMessages.scrollHeight;
        }

        async function sendChatMessage() {
            const userMessage = chatInput.value.trim();
            if (userMessage === '') return;

            // Display user message
            appendMessage('user', userMessage);
            chatInput.value = '';
            chatInput.disabled = true; // Disable input while AI is thinking
            sendButton.disabled = true; // Disable send button
            chatSpinner.classList.remove('hidden'); // Show spinner

            // Add user message to chat history for context
            chatHistory.push({ role: "user", parts: [{ text: userMessage }] });

            try {
                // Gemini API call
                const apiKey = ""; // Canvas will provide this in runtime
                const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=${apiKey}`;

                const payload = {
                    contents: chatHistory
                };

                const response = await fetch(apiUrl, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(payload)
                });

                const result = await response.json();

                if (result.candidates && result.candidates.length > 0 &&
                    result.candidates[0].content && result.candidates[0].content.parts &&
                    result.candidates[0].content.parts.length > 0) {
                    const aiResponse = result.candidates[0].content.parts[0].text;
                    appendMessage('ai', aiResponse);
                    // Add AI response to chat history
                    chatHistory.push({ role: "model", parts: [{ text: aiResponse }] });
                } else {
                    console.error("Gemini API response structure unexpected:", result);
                    appendMessage('ai', "I'm sorry, I couldn't generate a response. Please try again.");
                }
            } catch (error) {
                console.error("Error calling Gemini API for chatbot:", error);
                appendMessage('ai', "I'm experiencing a bit of trouble right now. Please check your network connection or try again later.");
            } finally {
                chatInput.disabled = false; // Re-enable input
                sendButton.disabled = false; // Re-enable send button
                chatSpinner.classList.add('hidden'); // Hide spinner
                chatInput.focus(); // Focus input for next message
            }
        }

        sendButton.addEventListener('click', sendChatMessage);
        chatInput.addEventListener('keypress', (e) => {
            if (e.key === 'Enter' && !sendButton.disabled) { // Prevent sending if disabled
                sendChatMessage();
            }
        });

        // --- Gemini API Integration for Mood Insight ---
        const moodSelect = document.getElementById('mood-select');
        const moodDescription = document.getElementById('mood-description');
        const getInsightButton = document.getElementById('get-insight-button');
        const insightResult = document.getElementById('mood-insight-result');
        const insightResultText = insightResult.querySelector('p');
        const insightSpinner = document.getElementById('insight-spinner');

        getInsightButton.addEventListener('click', async () => {
            const selectedMood = moodSelect.value;
            const description = moodDescription.value.trim();

            if (!selectedMood) {
                insightResult.classList.remove('hidden');
                insightResult.classList.add('bg-red-200', 'text-red-800'); // Temporary error style
                insightResultText.textContent = "Please select your mood first.";
                return;
            }

            insightResult.classList.add('hidden'); // Hide previous result
            getInsightButton.disabled = true;
            insightSpinner.classList.remove('hidden');

            try {
                const apiKey = ""; // Canvas will provide this in runtime
                const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=${apiKey}`;

                let prompt = `Given that a user is feeling ${selectedMood}.`;
                if (description) {
                    prompt += ` They have described their feelings as: "${description}".`;
                }
                prompt += ` Provide a very short (2-3 sentences), empathetic, and helpful insight or a simple coping suggestion. Focus on positive framing and support.`;

                const payload = {
                    contents: [{ role: "user", parts: [{ text: prompt }] }]
                };

                const response = await fetch(apiUrl, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(payload)
                });

                const result = await response.json();

                if (result.candidates && result.candidates.length > 0 &&
                    result.candidates[0].content && result.candidates[0].content.parts &&
                    result.candidates[0].content.parts.length > 0) {
                    const insight = result.candidates[0].content.parts[0].text;
                    insightResultText.textContent = insight;
                    insightResult.classList.remove('hidden', 'bg-red-200', 'text-red-800');
                    insightResult.classList.add('bg-mindease-light-green', 'text-mindease-green'); // Revert to normal style
                } else {
                    console.error("Gemini API response structure unexpected:", result);
                    insightResultText.textContent = "Could not generate an insight. Please try again.";
                    insightResult.classList.remove('hidden');
                    insightResult.classList.add('bg-red-200', 'text-red-800'); // Error style
                }
            } catch (error) {
                console.error("Error calling Gemini API for mood insight:", error);
                insightResultText.textContent = "There was an error getting your insight. Please try again later.";
                insightResult.classList.remove('hidden');
                insightResult.classList.add('bg-red-200', 'text-red-800'); // Error style
            } finally {
                getInsightButton.disabled = false;
                insightSpinner.classList.add('hidden');
            }
        });


        // Animation logic
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    // Remove initial hidden classes and add animation classes
                    if (entry.target.classList.contains('initial-hidden')) {
                        entry.target.classList.remove('initial-hidden');
                        entry.target.classList.add('animate-fade-in-up');
                    }
                    if (entry.target.classList.contains('initial-hidden-down')) {
                        entry.target.classList.remove('initial-hidden-down');
                        entry.target.classList.add('animate-fade-in-down');
                    }
                    if (entry.target.classList.contains('initial-hidden-bounce')) {
                        entry.target.classList.remove('initial-hidden-bounce');
                        entry.target.classList.add('animate-bounce-in');
                    }
                    observer.unobserve(entry.target); // Stop observing once animated
                }
            });
        }, { threshold: 0.1 }); // Trigger when 10% of the element is visible

        // Apply initial hidden classes and observe elements
        document.querySelectorAll('.initial-hidden, .initial-hidden-down, .initial-hidden-bounce').forEach(el => {
            observer.observe(el);
        });

        // Special handling for Hero Section elements since they have different starting states
        const heroTitle = document.querySelector('#hero h1');
        const heroParagraph = document.querySelector('#hero p');
        const heroButton = document.querySelector('#hero a');

        // Force initial state and then trigger animation after a short delay
        heroTitle.classList.add('initial-hidden-down');
        heroParagraph.classList.add('initial-hidden');
        heroButton.classList.add('initial-hidden-bounce');

        setTimeout(() => {
            if (heroTitle) {
                heroTitle.classList.remove('initial-hidden-down');
                heroTitle.classList.add('animate-fade-in-down');
            }
        }, 300); // Delay for title

        setTimeout(() => {
            if (heroParagraph) {
                heroParagraph.classList.remove('initial-hidden');
                heroParagraph.classList.add('animate-fade-in-up');
            }
        }, 600); // Delay for paragraph

        setTimeout(() => {
            if (heroButton) {
                heroButton.classList.remove('initial-hidden-bounce');
                heroButton.classList.add('animate-bounce-in');
            }
        }, 900); // Delay for button

        // Ensure other sections that were previously marked initial-hidden are observed
        document.querySelectorAll('section:not(#hero)').forEach(section => {
            section.classList.add('initial-hidden');
            observer.observe(section);
        });

        document.querySelectorAll('.grid > div').forEach(card => {
            card.classList.add('initial-hidden'); // Apply initial hidden class to cards
            observer.observe(card);
        });

    </script>
</body>
</html>
