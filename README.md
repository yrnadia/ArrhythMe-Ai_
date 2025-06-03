<html class="scroll-smooth" lang="en">
 <head>
  <meta charset="utf-8"/>
  <meta content="width=device-width, initial-scale=1" name="viewport"/>
  <title>
   ArrhythME-AI - Deteksi Aritmia
  </title>
  <script src="https://cdn.tailwindcss.com">
  </script>
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css" rel="stylesheet"/>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&amp;display=swap" rel="stylesheet"/>
  <style>
   body {
      font-family: 'Poppins', sans-serif;
      background-color: #fff;
      min-height: 100vh;
      background-image: none;
    }
    /* Background image as <img> behind content */
    #background-image {
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      object-fit: cover;
      z-index: -1;
      user-select: none;
      pointer-events: none;
      filter: brightness(0.9);
    }
    /* Scrollbar for chat */
    ::-webkit-scrollbar {
      width: 6px;
    }
    ::-webkit-scrollbar-track {
      background: #f1f1f1;
      border-radius: 10px;
    }
    ::-webkit-scrollbar-thumb {
      background: #dc2626;
      border-radius: 10px;
      border: 1.5px solid #f1f1f1;
    }
    ::-webkit-scrollbar-thumb:hover {
      background: #b91c1c;
    }
    /* Heartbeat animation */
    @keyframes heartbeat {
      0%, 100% {
        transform: scale(1);
        filter: drop-shadow(0 0 0 rgba(220, 38, 38, 0));
      }
      25% {
        transform: scale(1.15);
        filter: drop-shadow(0 0 8px rgba(220, 38, 38, 0.7));
      }
      50% {
        transform: scale(1);
        filter: drop-shadow(0 0 0 rgba(220, 38, 38, 0));
      }
      75% {
        transform: scale(1.1);
        filter: drop-shadow(0 0 6px rgba(220, 38, 38, 0.5));
      }
    }
    .heartbeat {
      animation: heartbeat 1.5s infinite;
      transform-origin: center;
    }
    /* Custom scrollbar for chat messages */
    #chat-messages::-webkit-scrollbar {
      width: 8px;
    }
    #chat-messages::-webkit-scrollbar-track {
      background: #fee2e2;
      border-radius: 10px;
    }
    #chat-messages::-webkit-scrollbar-thumb {
      background: #b91c1c;
      border-radius: 10px;
    }
    #chat-messages::-webkit-scrollbar-thumb:hover {
      background: #7f1d1d;
    }
    /* Button focus */
    button:focus, input:focus, select:focus, textarea:focus {
      outline: 2px solid #dc2626;
      outline-offset: 2px;
    }
    /* Profile photo container hover */
    #profile-photo-container:hover .overlay,
    #profile-photo-container:focus .overlay {
      opacity: 1;
    }
    .overlay {
      transition: opacity 0.3s ease;
      opacity: 0;
    }
    /* Fun floating hearts animation for header */
    .floating-heart {
      position: absolute;
      animation: floatUp 6s linear infinite;
      opacity: 0.8;
      filter: drop-shadow(0 0 3px #dc2626);
    }
    @keyframes floatUp {
      0% {
        transform: translateY(0) scale(1);
        opacity: 0.8;
      }
      50% {
        opacity: 1;
      }
      100% {
        transform: translateY(-150px) scale(1.3);
        opacity: 0;
      }
    }
    /* Shake animation for buttons on hover */
    @keyframes shake {
      0%, 100% { transform: translateX(0); }
      20%, 60% { transform: translateX(-5px); }
      40%, 80% { transform: translateX(5px); }
    }
    button:hover.shake {
      animation: shake 0.5s;
    }
    /* Cute heartbeat heart animation */
    .cute-heart {
      width: 120px;
      height: 120px;
      position: relative;
      transform-origin: center;
      animation: cuteHeartbeat 1.2s infinite;
      filter: drop-shadow(0 0 6px #f87171);
      cursor: default;
    }
    @keyframes cuteHeartbeat {
      0%, 100% {
        transform: scale(1);
        filter: drop-shadow(0 0 6px #f87171);
      }
      25% {
        transform: scale(1.2) rotate(-5deg);
        filter: drop-shadow(0 0 12px #f87171);
      }
      50% {
        transform: scale(1) rotate(5deg);
        filter: drop-shadow(0 0 6px #f87171);
      }
      75% {
        transform: scale(1.1) rotate(-3deg);
        filter: drop-shadow(0 0 9px #f87171);
      }
    }
    /* Cute heart face */
    .heart-face {
      position: absolute;
      top: 50%;
      left: 50%;
      width: 80px;
      height: 60px;
      transform: translate(-50%, -50%);
      pointer-events: none;
    }
    .heart-eye {
      position: absolute;
      top: 20px;
      width: 12px;
      height: 12px;
      background: #fff;
      border-radius: 50%;
      box-shadow: inset 0 0 3px #00000088;
    }
    .heart-eye.left {
      left: 20px;
    }
    .heart-eye.right {
      right: 20px;
    }
    .heart-pupil {
      position: absolute;
      top: 3px;
      left: 3px;
      width: 6px;
      height: 6px;
      background: #000;
      border-radius: 50%;
    }
    .heart-mouth {
      position: absolute;
      bottom: 10px;
      left: 50%;
      width: 30px;
      height: 12px;
      border-bottom: 3px solid #000;
      border-radius: 0 0 20px 20px;
      transform: translateX(-50%);
    }
  </style>
 </head>
 <body class="min-h-screen flex flex-col bg-gradient-to-br from-red-50 via-red-100 to-white relative overflow-x-hidden text-xs sm:text-sm md:text-base">
  <img alt="Background image showing a subtle red and white gradient with heart-themed abstract shapes" height="100%" id="background-image" src="Background.jpeg" width="100%"/>
  <!-- Floating hearts for fun -->
  <img alt="Small red heart icon floating up" class="floating-heart left-4 bottom-4 w-3 h-3 sm:w-5 sm:h-5" height="20" src="https://storage.googleapis.com/a1aa/image/fc82d6f0-2241-4f8f-22c9-77f28bc9eafd.jpg" style="animation-delay: 0s;" width="20"/>
  <img alt="Medium red heart icon floating up" class="floating-heart left-12 bottom-2 w-4 h-4 sm:w-7 sm:h-7" height="28" src="https://storage.googleapis.com/a1aa/image/47b7c557-34d9-4679-672f-8298132718aa.jpg" style="animation-delay: 2s;" width="28"/>
  <img alt="Tiny red heart icon floating up" class="floating-heart right-10 bottom-6 w-2 h-2 sm:w-4 sm:h-4" height="16" src="https://storage.googleapis.com/a1aa/image/4cedc776-1506-4df7-83f4-6df8f37f4413.jpg" style="animation-delay: 1.5s;" width="16"/>
  <img alt="Small red heart icon floating up" class="floating-heart right-16 bottom-4 w-3 h-3 sm:w-6 sm:h-6" height="24" src="https://storage.googleapis.com/a1aa/image/fc82d6f0-2241-4f8f-22c9-77f28bc9eafd.jpg" style="animation-delay: 3s;" width="24"/>
  <!-- Container -->
  <div class="flex-grow flex flex-col max-w-3xl mx-auto p-2 sm:p-4 md:p-6" id="app">
   <!-- Logo and Header -->
   <header class="flex items-center justify-between mb-4 sm:mb-6 relative z-10">
    <div class="flex items-center space-x-2 sm:space-x-3">
     <img alt="Logo aplikasi ArrhythME-AI" class="w-36 h-16 sm:w-48 sm:h-20 rounded-2xl shadow-xl transform hover:rotate-6 transition duration-500 object-contain" height="80" id="logo" src="LOGO.png" width="192"/>
     <h1 class="text-xl sm:text-3xl font-extrabold text-red-700 select-none tracking-wide drop-shadow-lg font-poppins leading-tight">
      ArrhythME-AI
     </h1>
    </div>
    <nav class="space-x-2 hidden md:flex">
     <button aria-label="Login ke aplikasi" class="text-red-700 font-bold hover:text-red-900 transition focus:ring-4 focus:ring-red-400 rounded-full px-2 py-1 sm:px-3 sm:py-1.5 bg-red-100 hover:bg-red-200 shadow-md shake text-xs sm:text-sm" id="nav-login-btn" type="button">
      <i class="fas fa-sign-in-alt mr-1">
      </i>
      Login
     </button>
     <button aria-label="Daftar akun baru" class="text-white font-bold hover:text-white transition focus:ring-4 focus:ring-red-600 rounded-full px-2 py-1 sm:px-3 sm:py-1.5 bg-red-700 hover:bg-red-800 shadow-lg shake text-xs sm:text-sm" id="nav-register-btn" type="button">
      <i class="fas fa-user-plus mr-1">
      </i>
      Register
     </button>
    </nav>
   </header>
   <!-- Main Content Area -->
   <main class="flex-grow bg-white bg-opacity-95 rounded-2xl shadow-2xl p-4 sm:p-6 md:p-8 max-w-full mx-auto w-full relative z-10">
    <!-- LOGIN & REGISTER CONTAINER -->
    <section aria-label="Form autentikasi" class="max-w-md mx-auto" id="auth-section">
     <!-- Tabs -->
     <div class="flex justify-center mb-4 sm:mb-6 border-b-4 border-red-500 rounded-t-2xl shadow-inner bg-red-50">
      <button aria-controls="login-form" aria-selected="true" class="px-4 py-1.5 sm:px-6 sm:py-2 font-extrabold text-red-700 border-b-4 border-red-700 focus:outline-none transition hover:text-red-900 text-base sm:text-lg tracking-wide" id="tab-login" role="tab" tabindex="0" type="button">
       <i class="fas fa-sign-in-alt mr-1.5">
       </i>
       Login
      </button>
      <button aria-controls="register-form" aria-selected="false" class="px-4 py-1.5 sm:px-6 sm:py-2 font-extrabold text-gray-400 hover:text-red-700 focus:outline-none transition text-base sm:text-lg tracking-wide" id="tab-register" role="tab" tabindex="-1" type="button">
       <i class="fas fa-user-plus mr-1.5">
       </i>
       Register
      </button>
     </div>
     <!-- Login Form -->
     <form aria-labelledby="tab-login" autocomplete="off" class="space-y-4 sm:space-y-6" id="login-form" role="tabpanel">
      <div>
       <label class="block text-sm sm:text-base font-semibold text-red-700 mb-1 sm:mb-2" for="login-username-email">
        Username atau Email
       </label>
       <input aria-required="true" class="mt-1 block w-full rounded-xl border border-red-300 px-3 py-1.5 sm:px-4 sm:py-2 shadow-sm placeholder-red-300 focus:border-red-600 focus:ring-2 focus:ring-red-300 focus:ring-opacity-50 text-sm sm:text-base font-medium" id="login-username-email" name="login-username-email" placeholder="Masukkan username atau email" required="" type="text"/>
      </div>
      <div>
       <label class="block text-sm sm:text-base font-semibold text-red-700 mb-1 sm:mb-2" for="login-password">
        Password
       </label>
       <input aria-required="true" class="mt-1 block w-full rounded-xl border border-red-300 px-3 py-1.5 sm:px-4 sm:py-2 shadow-sm placeholder-red-300 focus:border-red-600 focus:ring-2 focus:ring-red-300 focus:ring-opacity-50 text-sm sm:text-base font-medium" id="login-password" name="login-password" placeholder="Masukkan password" required="" type="password"/>
      </div>
      <button aria-label="Masuk ke dashboard" class="w-full bg-gradient-to-r from-red-600 via-red-700 to-red-800 hover:from-red-700 hover:via-red-800 hover:to-red-900 text-white font-extrabold py-2 sm:py-3 rounded-xl shadow-lg transition focus:ring-4 focus:ring-red-500 flex items-center justify-center space-x-2 text-base sm:text-lg" type="submit">
       <i class="fas fa-door-open fa-lg animate-pulse">
       </i>
       <span>
        Masuk
       </span>
      </button>
     </form>
     <!-- Register Form -->
     <form aria-labelledby="tab-register" autocomplete="off" class="space-y-4 sm:space-y-6 hidden" id="register-form" role="tabpanel" tabindex="-1">
      <div>
       <label class="block text-sm sm:text-base font-semibold text-red-700 mb-1 sm:mb-2" for="register-fullname">
        Nama Lengkap
       </label>
       <input aria-required="true" class="mt-1 block w-full rounded-xl border border-red-300 px-3 py-1.5 sm:px-4 sm:py-2 shadow-sm placeholder-red-300 focus:border-red-600 focus:ring-2 focus:ring-red-300 focus:ring-opacity-50 text-sm sm:text-base font-medium" id="register-fullname" name="register-fullname" placeholder="Masukkan nama lengkap" required="" type="text"/>
      </div>
      <div>
       <label class="block text-sm sm:text-base font-semibold text-red-700 mb-1 sm:mb-2" for="register-username">
        Username
       </label>
       <input aria-required="true" class="mt-1 block w-full rounded-xl border border-red-300 px-3 py-1.5 sm:px-4 sm:py-2 shadow-sm placeholder-red-300 focus:border-red-600 focus:ring-2 focus:ring-red-300 focus:ring-opacity-50 text-sm sm:text-base font-medium" id="register-username" name="register-username" placeholder="Buat username" required="" type="text"/>
      </div>
      <div>
       <label class="block text-sm sm:text-base font-semibold text-red-700 mb-1 sm:mb-2" for="register-email">
        Email
       </label>
       <input aria-required="true" class="mt-1 block w-full rounded-xl border border-red-300 px-3 py-1.5 sm:px-4 sm:py-2 shadow-sm placeholder-red-300 focus:border-red-600 focus:ring-2 focus:ring-red-300 focus:ring-opacity-50 text-sm sm:text-base font-medium" id="register-email" name="register-email" placeholder="Masukkan email" required="" type="email"/>
      </div>
      <div>
       <label class="block text-sm sm:text-base font-semibold text-red-700 mb-1 sm:mb-2" for="register-password">
        Password
       </label>
       <input aria-required="true" class="mt-1 block w-full rounded-xl border border-red-300 px-3 py-1.5 sm:px-4 sm:py-2 shadow-sm placeholder-red-300 focus:border-red-600 focus:ring-2 focus:ring-red-300 focus:ring-opacity-50 text-sm sm:text-base font-medium" id="register-password" name="register-password" placeholder="Buat password" required="" type="password"/>
      </div>
      <div>
       <label class="block text-sm sm:text-base font-semibold text-red-700 mb-1 sm:mb-2" for="register-role">
        Daftar sebagai
       </label>
       <select aria-required="true" class="mt-1 block w-full rounded-xl border border-red-300 px-3 py-1.5 sm:px-4 sm:py-2 shadow-sm focus:border-red-600 focus:ring-2 focus:ring-red-300 focus:ring-opacity-50 text-sm sm:text-base font-medium" id="register-role" name="register-role" required="">
        <option disabled="" selected="" value="">
         Pilih peran
        </option>
        <option value="patient">
         Pasien
        </option>
        <option value="doctor">
         Dokter
        </option>
       </select>
      </div>
      <button aria-label="Daftar akun baru" class="w-full bg-gradient-to-r from-red-600 via-red-700 to-red-800 hover:from-red-700 hover:via-red-800 hover:to-red-900 text-white font-extrabold py-2 sm:py-3 rounded-xl shadow-lg transition focus:ring-4 focus:ring-red-500 flex items-center justify-center space-x-2 text-base sm:text-lg" type="submit">
       <i class="fas fa-user-plus fa-lg animate-pulse">
       </i>
       <span>
        Daftar
       </span>
      </button>
     </form>
    </section>
    <!-- DASHBOARD CONTAINER -->
    <section aria-atomic="true" aria-live="polite" class="hidden max-w-full mx-auto" id="dashboard-section">
     <!-- DASHBOARD NAV -->
     <nav aria-label="Navigasi dashboard" class="flex items-center justify-between bg-gradient-to-r from-red-700 via-red-800 to-red-900 text-white rounded-t-2xl px-4 py-2 sm:px-6 sm:py-3 shadow-2xl" id="dashboard-nav" role="navigation">
      <div class="flex items-center space-x-3 sm:space-x-4">
       <img alt="Logo aplikasi ArrhythME-AI" class="w-48 h-20 sm:w-60 sm:h-24 rounded-2xl shadow-2xl transform hover:scale-110 transition duration-500 object-contain" height="80" src="LOGO.png" width="240"/>
       <h2 class="text-lg sm:text-xl font-extrabold tracking-widest drop-shadow-xl select-none" id="dashboard-title">
        Dashboard
       </h2>
      </div>
      <div class="flex items-center space-x-3 sm:space-x-4">
       <button aria-label="Logout dari aplikasi" class="flex items-center space-x-1.5 bg-white text-red-700 font-extrabold px-2.5 py-1 sm:px-3 sm:py-1.5 rounded-2xl hover:bg-red-100 shadow-lg transition focus:ring-4 focus:ring-red-400 text-xs sm:text-sm shake" id="dashboard-logout-btn" type="button">
        <i class="fas fa-sign-out-alt fa-lg">
        </i>
        <span>
         Logout
        </span>
       </button>
      </div>
     </nav>
     <!-- DASHBOARD CONTENT -->
     <div class="bg-white rounded-b-2xl shadow-2xl p-4 sm:p-6 md:p-8 grid grid-cols-1 md:grid-cols-4 gap-4 sm:gap-6 min-h-[480px]" id="dashboard-content">
      <!-- Sidebar -->
      <aside aria-label="Sidebar navigasi dashboard" class="col-span-1 bg-red-50 rounded-2xl p-4 sm:p-5 flex flex-col space-y-4 sm:space-y-5 shadow-inner" id="dashboard-sidebar">
       <div class="flex flex-col items-center space-y-3 sm:space-y-4 mb-4 sm:mb-6">
        <div aria-label="Ubah foto profil" class="relative group w-16 h-16 sm:w-24 sm:h-24 rounded-full border-4 border-red-700 overflow-hidden cursor-pointer shadow-lg" id="profile-photo-container" role="button" tabindex="0">
         <img alt="Foto profil pengguna" class="w-full h-full object-cover" height="96" id="profile-photo" src="https://storage.googleapis.com/a1aa/image/2dc99cc0-5403-4a4e-1e55-37470d3f2ae7.jpg" width="96"/>
         <div class="overlay absolute inset-0 bg-black bg-opacity-40 flex items-center justify-center text-white text-lg sm:text-xl font-semibold opacity-0 group-hover:opacity-100 group-focus:opacity-100 transition rounded-full">
          <i class="fas fa-camera mr-1.5">
          </i>
          Ubah Foto
         </div>
         <input accept="image/*" class="hidden" id="profile-photo-input" type="file"/>
        </div>
        <h3 aria-atomic="true" aria-live="polite" class="text-base sm:text-lg font-bold text-red-700 text-center break-words select-text" id="profile-name">
         Nama Pengguna
        </h3>
        <p aria-atomic="true" aria-live="polite" class="text-xs sm:text-sm text-red-600 font-semibold uppercase tracking-widest select-text" id="profile-role">
         Role
        </p>
       </div>
       <nav aria-label="Navigasi utama dashboard" class="flex flex-col space-y-2 sm:space-y-3 text-red-700 font-semibold text-xs sm:text-sm">
        <button aria-label="Buka profil saya" class="dashboard-nav-btn flex items-center space-x-2 sm:space-x-3 px-2 py-1 sm:px-3 sm:py-2 rounded-xl hover:bg-red-100 transition shadow-sm focus:ring-2 focus:ring-red-400" data-target="profile-section" type="button">
         <svg aria-hidden="true" class="h-4 w-4 sm:h-5 sm:w-5 text-red-700" fill="none" stroke="currentColor" stroke-width="2" viewbox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path d="M5.121 17.804A9 9 0 1118.88 6.196M15 11a3 3 0 11-6 0 3 3 0 016 0z" stroke-linecap="round" stroke-linejoin="round">
          </path>
         </svg>
         <span>
          Profil
         </span>
        </button>
        <button aria-label="Buka monitor detak jantung" class="dashboard-nav-btn flex items-center space-x-2 sm:space-x-3 px-2 py-1 sm:px-3 sm:py-2 rounded-xl hover:bg-red-100 transition shadow-sm focus:ring-2 focus:ring-red-400" data-target="heart-section" id="sidebar-heart-btn" type="button">
         <svg aria-hidden="true" class="h-4 w-4 sm:h-5 sm:w-5 text-red-700 heartbeat" fill="none" stroke="currentColor" stroke-width="2" viewbox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path d="M3 12h3l3 8 4-16 3 8h3" stroke-linecap="round" stroke-linejoin="round">
          </path>
         </svg>
         <span>
          Heart Monitor
         </span>
        </button>
        <button aria-label="Buka edukasi kesehatan jantung" class="dashboard-nav-btn flex items-center space-x-2 sm:space-x-3 px-2 py-1 sm:px-3 sm:py-2 rounded-xl hover:bg-red-100 transition shadow-sm focus:ring-2 focus:ring-red-400" data-target="education-section" id="sidebar-education-btn" type="button">
         <svg aria-hidden="true" class="h-4 w-4 sm:h-5 sm:w-5 text-red-700" fill="none" stroke="currentColor" stroke-width="2" viewbox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path d="M12 20h9M12 4h9M4 12h16M4 12l4 4m0-8l-4 4" stroke-linecap="round" stroke-linejoin="round">
          </path>
         </svg>
         <span>
          Edukasi
         </span>
        </button>
        <button aria-label="Buka live chat" class="dashboard-nav-btn flex items-center space-x-2 sm:space-x-3 px-2 py-1 sm:px-3 sm:py-2 rounded-xl hover:bg-red-100 transition shadow-sm focus:ring-2 focus:ring-red-400" data-target="chat-section" type="button">
         <svg aria-hidden="true" class="h-4 w-4 sm:h-5 sm:w-5 text-red-700" fill="none" stroke="currentColor" stroke-width="2" viewbox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path d="M17 8h2a2 2 0 012 2v6a2 2 0 01-2 2h-2m-4 0H7a2 2 0 01-2-2v-6a2 2 0 012-2h6m-3 4h.01" stroke-linecap="round" stroke-linejoin="round">
          </path>
         </svg>
         <span>
          Live Chat
         </span>
        </button>
        <button aria-label="Buka daftar pasien" class="dashboard-nav-btn flex items-center space-x-2 sm:space-x-3 px-2 py-1 sm:px-3 sm:py-2 rounded-xl hover:bg-red-100 transition shadow-sm focus:ring-2 focus:ring-red-400 hidden" data-target="patients-section" id="sidebar-patients-btn" type="button">
         <svg aria-hidden="true" class="h-4 w-4 sm:h-5 sm:w-5 text-red-700" fill="none" stroke="currentColor" stroke-width="2" viewbox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path d="M17 20h5v-2a4 4 0 00-3-3.87M9 20H4v-2a4 4 0 013-3.87M16 7a4 4 0 11-8 0 4 4 0 018 0z" stroke-linecap="round" stroke-linejoin="round">
          </path>
         </svg>
         <span>
          Pasien
         </span>
        </button>
        <button aria-label="Buka notifikasi" class="dashboard-nav-btn flex items-center space-x-2 sm:space-x-3 px-2 py-1 sm:px-3 sm:py-2 rounded-xl hover:bg-red-100 transition shadow-sm focus:ring-2 focus:ring-red-400 hidden" data-target="notifications-section" id="sidebar-notifications-btn" type="button">
         <svg aria-hidden="true" class="h-4 w-4 sm:h-5 sm:w-5 text-red-700 relative" fill="none" stroke="currentColor" stroke-width="2" viewbox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6 6 0 10-12 0v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9" stroke-linecap="round" stroke-linejoin="round">
          </path>
          <circle class="absolute top-0 right-0 text-red-700" cx="18" cy="6" fill="#dc2626" r="3">
          </circle>
         </svg>
         <span>
          Notifikasi
          <span class="ml-1 inline-block bg-red-700 text-white text-xs font-bold rounded-full px-1.5 py-0.5" id="notification-count" style="display:none;">
           0
          </span>
         </span>
        </button>
       </nav>
      </aside>
      <!-- Main Content -->
      <section aria-atomic="true" aria-live="polite" class="col-span-3 bg-red-50 rounded-2xl p-4 sm:p-6 overflow-auto max-h-[480px] shadow-inner flex flex-col" id="dashboard-main" tabindex="0">
       <!-- Welcome Section -->
       <section aria-label="Selamat datang dokter" class="hidden flex flex-col items-center justify-center space-y-4" id="doctor-welcome-section">
        <div class="flex flex-col items-center space-y-4 bg-white rounded-2xl shadow-2xl p-4 sm:p-8 w-full max-w-2xl border-2 border-red-300">
         <div class="flex items-center space-x-3 sm:space-x-5">
          <img alt="Ilustrasi ikon jantung lucu berwarna merah dengan wajah tersenyum dan tangan melambai" class="w-12 h-12 sm:w-20 sm:h-20" height="80" src="https://storage.googleapis.com/a1aa/image/ae480faf-55f7-4ab8-f1de-efa4b528daff.jpg" width="80"/>
          <h3 class="text-xl sm:text-3xl font-extrabold text-red-700 tracking-wide drop-shadow-lg max-w-lg">
           Selamat datang, dokter
           <span class="underline decoration-red-500 decoration-4" id="doctor-welcome-name">
           </span>
           <span aria-label="Heart emoji" class="inline-block animate-pulse" role="img">
            ❤️
           </span>
          </h3>
         </div>
         <p class="text-gray-700 text-sm sm:text-base max-w-lg text-center leading-relaxed font-semibold">
          Terima kasih telah bergabung. Pantau kondisi pasien dan kelola data dengan mudah melalui dashboard ini. Gunakan fitur Heart Monitor untuk deteksi dini aritmia dan Edukasi untuk meningkatkan pengetahuan kesehatan jantung.
         </p>
         <img alt="Ilustrasi jantung berdetak animasi dengan warna merah dan putih" class="rounded-2xl shadow-lg w-full max-w-xs sm:max-w-sm object-contain" height="160" src="https://storage.googleapis.com/a1aa/image/16b17650-b68e-41ce-d33a-6723b7af8761.jpg" width="256"/>
        </div>
       </section>
       <!-- Patient Profile Section -->
       <section aria-label="Profil pengguna" class="space-y-4" id="profile-section">
        <h3 class="text-lg sm:text-2xl font-bold text-red-700 mb-4 flex items-center space-x-3">
         <svg aria-hidden="true" class="h-5 w-5 sm:h-7 sm:w-7 text-red-700" fill="none" stroke="currentColor" stroke-width="2" viewbox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path d="M5.121 17.804A9 9 0 1118.88 6.196M15 11a3 3 0 11-6 0 3 3 0 016 0z" stroke-linecap="round" stroke-linejoin="round">
          </path>
         </svg>
         <span>
          Profil Saya
         </span>
        </h3>
        <form aria-label="Form profil pasien" class="space-y-4 max-w-full" id="profile-form-patient">
         <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 sm:gap-6">
          <div>
           <label class="block font-semibold text-red-700 mb-1 text-sm sm:text-base" for="profile-fullname-patient">
            Nama Lengkap
           </label>
           <input aria-required="true" class="w-full rounded-xl border border-red-300 px-3 py-1.5 sm:px-4 sm:py-2 focus:outline-none focus:ring-2 focus:ring-red-400 shadow-sm text-sm sm:text-base" id="profile-fullname-patient" name="profile-fullname-patient" placeholder="Masukkan nama lengkap" required="" type="text"/>
          </div>
          <div>
           <label class="block font-semibold text-red-700 mb-1 text-sm sm:text-base" for="profile-email-patient">
            Email
           </label>
           <input aria-required="true" class="w-full rounded-xl border border-red-300 px-3 py-1.5 sm:px-4 sm:py-2 focus:outline-none focus:ring-2 focus:ring-red-400 shadow-sm text-sm sm:text-base" id="profile-email-patient" name="profile-email-patient" placeholder="Masukkan email" required="" type="email"/>
          </div>
          <div>
           <label class="block font-semibold text-red-700 mb-1 text-sm sm:text-base" for="profile-phone-patient">
            Nomor Telepon
           </label>
           <input class="w-full rounded-xl border border-red-300 px-3 py-1.5 sm:px-4 sm:py-2 focus:outline-none focus:ring-2 focus:ring-red-400 shadow-sm text-sm sm:text-base" id="profile-phone-patient" name="profile-phone-patient" pattern="[0-9+ ]{6,20}" placeholder="Masukkan nomor telepon" type="tel"/>
          </div>
          <div>
           <label class="block font-semibold text-red-700 mb-1 text-sm sm:text-base" for="profile-gender-patient">
            Jenis Kelamin
           </label>
           <select class="w-full rounded-xl border border-red-300 px-3 py-1.5 sm:px-4 sm:py-2 focus:outline-none focus:ring-2 focus:ring-red-400 shadow-sm text-sm sm:text-base" id="profile-gender-patient" name="profile-gender-patient">
            <option disabled="" selected="" value="">
             Pilih jenis kelamin
            </option>
            <option value="female">
             Perempuan
            </option>
            <option value="male">
             Laki-laki
            </option>
           </select>
          </div>
          <div>
           <label class="block font-semibold text-red-700 mb-1 text-sm sm:text-base" for="profile-birthplace-patient">
            Tempat Lahir
           </label>
           <input class="w-full rounded-xl border border-red-300 px-3 py-1.5 sm:px-4 sm:py-2 focus:outline-none focus:ring-2 focus:ring-red-400 shadow-sm text-sm sm:text-base" id="profile-birthplace-patient" name="profile-birthplace-patient" placeholder="Tempat lahir" type="text"/>
          </div>
          <div>
           <label class="block font-semibold text-red-700 mb-1 text-sm sm:text-base" for="profile-birthdate-patient">
            Tanggal Lahir
           </label>
           <input class="w-full rounded-xl border border-red-300 px-3 py-1.5 sm:px-4 sm:py-2 focus:outline-none focus:ring-2 focus:ring-red-400 shadow-sm text-sm sm:text-base" id="profile-birthdate-patient" name="profile-birthdate-patient" type="date"/>
          </div>
          <div>
           <label class="block font-semibold text-red-700 mb-1 text-sm sm:text-base" for="profile-age-patient">
            Usia
           </label>
           <input class="w-full rounded-xl border border-red-300 px-3 py-1.5 sm:px-4 sm:py-2 bg-red-100 cursor-not-allowed shadow-inner text-sm sm:text-base" id="profile-age-patient" name="profile-age-patient" placeholder="Usia otomatis" readonly="" type="number"/>
          </div>
          <div>
           <label class="block font-semibold text-red-700 mb-1 text-sm sm:text-base" for="profile-weight-patient">
            Berat Badan (kg)
           </label>
           <input class="w-full rounded-xl border border-red-300 px-3 py-1.5 sm:px-4 sm:py-2 focus:outline-none focus:ring-2 focus:ring-red-400 shadow-sm text-sm sm:text-base" id="profile-weight-patient" min="1" name="profile-weight-patient" placeholder="Masukkan berat badan" step="0.1" type="number"/>
          </div>
          <div>
           <label class="block font-semibold text-red-700 mb-1 text-sm sm:text-base" for="profile-height-patient">
            Tinggi Badan (cm)
           </label>
           <input class="w-full rounded-xl border border-red-300 px-3 py-1.5 sm:px-4 sm:py-2 focus:outline-none focus:ring-2 focus:ring-red-400 shadow-sm text-sm sm:text-base" id="profile-height-patient" min="1" name="profile-height-patient" placeholder="Masukkan tinggi badan" step="0.1" type="number"/>
          </div>
          <div>
           <label class="block font-semibold text-red-700 mb-1 text-sm sm:text-base" for="profile-bmi-patient">
            BMI
           </label>
           <input class="w-full rounded-xl border border-red-300 px-3 py-1.5 sm:px-4 sm:py-2 bg-red-100 cursor-not-allowed shadow-inner text-sm sm:text-base" id="profile-bmi-patient" name="profile-bmi-patient" placeholder="BMI otomatis" readonly="" type="text"/>
          </div>
         </div>
         <div>
          <label class="block font-semibold text-red-700 mb-1 text-sm sm:text-base" for="profile-medical-history-patient">
           Riwayat Penyakit
          </label>
          <textarea class="w-full rounded-xl border border-red-300 px-3 py-1.5 sm:px-4 sm:py-2 focus:outline-none focus:ring-2 focus:ring-red-400 shadow-sm text-sm sm:text-base resize-none" id="profile-medical-history-patient" name="profile-medical-history-patient" placeholder="Masukkan riwayat penyakit jika ada" rows="3"></textarea>
         </div>
         <div>
          <label class="block font-semibold text-red-700 mb-1 text-sm sm:text-base" for="profile-address-patient">
           Alamat
          </label>
          <textarea class="w-full rounded-xl border border-red-300 px-3 py-1.5 sm:px-4 sm:py-2 focus:outline-none focus:ring-2 focus:ring-red-400 shadow-sm text-sm sm:text-base resize-none" id="profile-address-patient" name="profile-address-patient" placeholder="Masukkan alamat lengkap" rows="2"></textarea>
         </div>
         <div class="flex justify-end">
          <button aria-label="Simpan profil" class="bg-gradient-to-r from-red-700 via-red-800 to-red-900 hover:from-red-800 hover:via-red-900 hover:to-red-950 text-white font-extrabold px-4 py-1.5 sm:px-6 sm:py-2 rounded-xl shadow-lg transition focus:ring-4 focus:ring-red-500 flex items-center space-x-2 text-sm sm:text-base shake" type="submit">
           <i class="fas fa-save fa-lg">
           </i>
           <span>
            Simpan Profil
           </span>
          </button>
         </div>
        </form>
       </section>
       <!-- Heart Monitor Section -->
       <section aria-label="Monitor detak jantung" class="hidden space-y-4 max-w-full" id="heart-section">
        <h3 class="text-lg sm:text-2xl font-bold text-red-700 mb-4 flex items-center space-x-3">
         <svg aria-hidden="true" class="h-6 w-6 sm:h-8 sm:w-8 text-red-700 heartbeat" fill="none" stroke="currentColor" stroke-width="2" viewbox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path d="M3 12h3l3 8 4-16 3 8h3" stroke-linecap="round" stroke-linejoin="round">
          </path>
         </svg>
         <span>
          Heart Monitor
         </span>
        </h3>
        <div class="bg-white rounded-xl shadow-lg p-4 sm:p-6 border border-red-300 flex flex-col sm:flex-row items-center gap-4">
         <div class="flex flex-col items-center space-y-4">
          <img alt="Ilustrasi monitor detak jantung dengan grafik ECG berwarna merah dan putih" class="w-32 sm:w-48 rounded-xl shadow-md" height="128" src="https://storage.googleapis.com/a1aa/image/3f0e6729-3c29-4f82-4b25-ab352a0fb2e2.jpg" width="320"/>
          <div aria-label="Ilustrasi jantung lucu berdetak dengan wajah tersenyum dan animasi berdetak" class="cute-heart" role="img">
           <img alt="Ilustrasi jantung lucu berwarna merah dengan bentuk hati dan wajah tersenyum" class="w-full h-full object-contain" height="120" src="https://storage.googleapis.com/a1aa/image/a2e2198a-b40a-4ae5-d8f2-801fd8f8e8f0.jpg" width="120"/>
           <div class="heart-face">
            <div class="heart-eye left">
             <div class="heart-pupil">
             </div>
            </div>
            <div class="heart-eye right">
             <div class="heart-pupil">
             </div>
            </div>
            <div class="heart-mouth">
            </div>
           </div>
          </div>
         </div>
         <div class="flex-1">
          <p class="mb-3 sm:mb-4 text-gray-700 text-sm sm:text-base leading-relaxed font-semibold">
           Tekan tombol
           <span class="font-bold text-red-700">
            Start
           </span>
           untuk memulai pengambilan sinyal ECG selama 30 detik.
          </p>
          <button aria-label="Mulai pengambilan data ECG" class="bg-gradient-to-r from-red-700 via-red-800 to-red-900 hover:from-red-800 hover:via-red-900 hover:to-red-950 text-white font-extrabold px-4 py-1.5 sm:px-8 sm:py-2 rounded-xl shadow-lg transition flex items-center space-x-2 focus:ring-4 focus:ring-red-500 text-base sm:text-lg shake" id="start-ecg-btn" type="button">
           <i class="fas fa-play fa-lg animate-pulse">
           </i>
           <span>
            Start
           </span>
          </button>
         </div>
        </div>
        <div aria-atomic="true" aria-live="polite" class="mt-4 sm:mt-6 space-y-4 hidden" id="ecg-result">
         <div class="flex flex-col sm:flex-row items-center justify-around space-x-0 sm:space-x-8 space-y-4 sm:space-y-0">
          <div class="flex items-center space-x-3 bg-red-100 rounded-xl p-3 sm:p-4 shadow-md w-full sm:w-1/2">
           <i class="fas fa-tachometer-alt fa-2x text-red-700">
           </i>
           <div>
            <p class="text-sm sm:text-base text-gray-600 font-semibold tracking-wide">
             BPM (Detak Jantung)
            </p>
            <p aria-atomic="true" aria-live="polite" class="text-3xl sm:text-4xl font-extrabold text-red-700" id="bpm-value">
             --
            </p>
           </div>
          </div>
          <div class="flex items-center space-x-3 bg-red-100 rounded-xl p-3 sm:p-4 shadow-md w-full sm:w-1/2">
           <i class="fas fa-info-circle fa-2x text-red-700">
           </i>
           <div>
            <p class="text-sm sm:text-base text-gray-600 font-semibold tracking-wide">
             Kategori
            </p>
            <p aria-atomic="true" aria-live="polite" class="text-xl sm:text-2xl font-bold text-red-700" id="bpm-category">
             --
            </p>
           </div>
          </div>
         </div>
         <div>
          <h4 class="font-semibold text-red-700 mb-3 text-base sm:text-lg tracking-wide">
           Riwayat Deteksi Sebelumnya
          </h4>
          <ul aria-label="Riwayat deteksi ECG" class="max-h-40 sm:max-h-52 overflow-y-auto border border-red-300 rounded-xl p-3 sm:p-4 space-y-2 bg-white shadow-inner" id="ecg-history-list" tabindex="0">
          </ul>
         </div>
        </div>
       </section>
       <!-- Education Section -->
       <section aria-label="Edukasi kesehatan jantung" class="hidden max-w-full space-y-4 sm:space-y-6" id="education-section">
        <h3 class="text-lg sm:text-2xl font-bold text-red-700 mb-4 flex items-center space-x-3">
         <svg aria-hidden="true" class="h-6 w-6 sm:h-8 sm:w-8 text-red-700" fill="none" stroke="currentColor" stroke-width="2" viewbox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path d="M12 20h9M12 4h9M4 12h16M4 12l4 4m0-8l-4 4" stroke-linecap="round" stroke-linejoin="round">
          </path>
         </svg>
         <span>
          Edukasi
         </span>
        </h3>
        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 sm:gap-6">
         <article aria-label="Edukasi Anatomi Jantung" class="bg-white rounded-2xl shadow-lg p-3 sm:p-5 border border-red-300 hover:shadow-2xl transition cursor-pointer focus:outline-none focus:ring-4 focus:ring-red-400 flex flex-col items-center" role="article" tabindex="0">
          <img alt="Ilustrasi anatomi jantung manusia dengan warna merah dan putih" class="rounded-xl mb-3 sm:mb-4 object-cover w-full h-28 sm:h-40" height="112" src="https://storage.googleapis.com/a1aa/image/f2b21616-5504-40ed-69b9-5445e7c8ee04.jpg" width="224"/>
          <h4 class="text-base sm:text-lg font-semibold text-red-700 mb-1 tracking-wide text-center">
           Anatomi Jantung
          </h4>
          <p class="text-gray-700 text-xs sm:text-sm leading-relaxed text-center">
           Pelajari struktur dan fungsi jantung manusia secara mendalam.
          </p>
         </article>
         <article aria-label="Edukasi Mengenal Aritmia" class="bg-white rounded-2xl shadow-lg p-3 sm:p-5 border border-red-300 hover:shadow-2xl transition cursor-pointer focus:outline-none focus:ring-4 focus:ring-red-400 flex flex-col items-center" role="article" tabindex="0">
          <img alt="Ilustrasi gelombang ECG dengan tanda aritmia berwarna merah" class="rounded-xl mb-3 sm:mb-4 object-cover w-full h-28 sm:h-40" height="112" src="https://storage.googleapis.com/a1aa/image/bcc24551-f469-463f-78f6-b619177b1800.jpg" width="224"/>
          <h4 class="text-base sm:text-lg font-semibold text-red-700 mb-1 tracking-wide text-center">
           Mengenal Aritmia
          </h4>
          <p class="text-gray-700 text-xs sm:text-sm leading-relaxed text-center">
           Informasi tentang jenis-jenis aritmia dan dampaknya pada kesehatan.
          </p>
         </article>
         <article aria-label="Edukasi Pola Makan Sehat" class="bg-white rounded-2xl shadow-lg p-3 sm:p-5 border border-red-300 hover:shadow-2xl transition cursor-pointer focus:outline-none focus:ring-4 focus:ring-red-400 flex flex-col items-center" role="article" tabindex="0">
          <img alt="Ilustrasi makanan sehat berwarna merah dan putih di atas meja kayu" class="rounded-xl mb-3 sm:mb-4 object-cover w-full h-28 sm:h-40" height="112" src="https://storage.googleapis.com/a1aa/image/b8380a0c-09d6-49c7-740c-cab9c4168c3a.jpg" width="224"/>
          <h4 class="text-base sm:text-lg font-semibold text-red-700 mb-1 tracking-wide text-center">
           Pola Makan Sehat
          </h4>
          <p class="text-gray-700 text-xs sm:text-sm leading-relaxed text-center">
           Tips dan panduan pola makan yang baik untuk kesehatan jantung.
          </p>
         </article>
         <article aria-label="Edukasi Gaya Hidup Sehat" class="bg-white rounded-2xl shadow-lg p-3 sm:p-5 border border-red-300 hover:shadow-2xl transition cursor-pointer focus:outline-none focus:ring-4 focus:ring-red-400 flex flex-col items-center" role="article" tabindex="0">
          <img alt="Ilustrasi orang berolahraga dan gaya hidup sehat dengan latar belakang merah putih" class="rounded-xl mb-3 sm:mb-4 object-cover w-full h-28 sm:h-40" height="112" src="https://storage.googleapis.com/a1aa/image/2d0e9a98-92b1-4da4-3670-e9c4b73bd49a.jpg" width="224"/>
          <h4 class="text-base sm:text-lg font-semibold text-red-700 mb-1 tracking-wide text-center">
           Gaya Hidup Sehat
          </h4>
          <p class="text-gray-700 text-xs sm:text-sm leading-relaxed text-center">
           Cara menjaga pola hidup sehat untuk mencegah penyakit jantung.
          </p>
         </article>
        </div>
       </section>
       <!-- Chat Section -->
       <section aria-label="Live chat" class="hidden max-w-full flex flex-col h-full" id="chat-section">
        <h3 class="text-lg sm:text-2xl font-bold text-red-700 mb-4 flex items-center space-x-3">
         <svg aria-hidden="true" class="h-6 w-6 sm:h-8 sm:w-8 text-red-700" fill="none" stroke="currentColor" stroke-width="2" viewbox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path d="M17 8h2a2 2 0 012 2v6a2 2 0 01-2 2h-2m-4 0H7a2 2 0 01-2-2v-6a2 2 0 012-2h6m-3 4h.01" stroke-linecap="round" stroke-linejoin="round">
          </path>
         </svg>
         <span>
          Live Chat
         </span>
        </h3>
        <div class="flex flex-col md:flex-row h-[360px] sm:h-[460px] bg-white rounded-2xl shadow-lg border border-red-300 overflow-hidden">
         <aside aria-label="Daftar pengguna chat" class="w-full md:w-1/3 border-r border-red-300 overflow-y-auto" id="chat-user-list" tabindex="0">
          <div class="p-3 sm:p-4 border-b border-red-300 bg-red-50 font-semibold text-red-700 text-base tracking-wide select-none">
           Daftar Chat
          </div>
          <ul class="divide-y divide-red-200" id="chat-users" role="list">
          </ul>
         </aside>
         <section aria-atomic="true" aria-label="Jendela chat" aria-live="polite" aria-relevant="additions" class="flex flex-col w-full md:w-2/3" id="chat-window" tabindex="0">
          <header class="flex items-center justify-between bg-gradient-to-r from-red-600 via-red-700 to-red-800 text-white p-3 sm:p-4 shadow-lg" id="chat-header">
           <div class="flex items-center space-x-2 sm:space-x-3">
            <img alt="Foto profil lawan chat" class="w-10 h-10 sm:w-12 sm:h-12 rounded-full object-cover border-4 border-white shadow-lg" height="48" id="chat-header-photo" src="https://storage.googleapis.com/a1aa/image/a5b31a03-1d9b-4200-5f5a-3a7f4e2bf15c.jpg" width="48"/>
            <div>
             <h4 class="font-semibold text-base sm:text-xl" id="chat-header-name">
              Nama Lawan Chat
             </h4>
             <p class="text-xs sm:text-sm opacity-90" id="chat-header-role">
              Role
             </p>
            </div>
           </div>
           <button aria-label="Tutup chat" class="text-white hover:text-red-300 focus:outline-none focus:ring-2 focus:ring-white rounded-full p-1.5 sm:p-2" id="chat-close-btn" title="Tutup Chat" type="button">
            <i class="fas fa-times fa-lg">
            </i>
           </button>
          </header>
          <div aria-atomic="true" aria-label="Pesan chat" aria-live="polite" aria-relevant="additions" class="flex-grow p-3 sm:p-4 overflow-y-auto space-y-3 sm:space-y-4 bg-red-50" id="chat-messages" role="log" tabindex="0">
          </div>
          <form aria-label="Form kirim pesan" autocomplete="off" class="flex border-t border-red-300 p-2 sm:p-3 bg-white" id="chat-form">
           <input aria-label="Ketik pesan" class="flex-grow rounded-l-xl border border-red-300 px-3 py-1.5 sm:px-4 sm:py-2 focus:outline-none focus:ring-2 focus:ring-red-400 shadow-sm text-sm sm:text-base" id="chat-input" placeholder="Ketik pesan..." required="" type="text"/>
           <button aria-label="Kirim pesan" class="bg-red-700 hover:bg-red-800 text-white px-3 py-1.5 sm:px-5 sm:py-2 rounded-r-xl shadow-lg transition focus:ring-4 focus:ring-red-400" type="submit">
            <i class="fas fa-paper-plane fa-lg">
            </i>
           </button>
          </form>
         </section>
        </div>
       </section>
       <!-- Doctor Profile Section -->
       <section aria-label="Profil dokter" class="hidden max-w-full space-y-4" id="doctor-profile-section">
        <h3 class="text-lg sm:text-2xl font-bold text-red-700 mb-4 flex items-center space-x-3">
         <svg aria-hidden="true" class="h-6 w-6 sm:h-8 sm:w-8 text-red-700" fill="none" stroke="currentColor" stroke-width="2" viewbox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path d="M5.121 17.804A9 9 0 1118.88 6.196M15 11a3 3 0 11-6 0 3 3 0 016 0z" stroke-linecap="round" stroke-linejoin="round">
          </path>
         </svg>
         <span>
          Profil Saya
         </span>
        </h3>
        <form aria-label="Form profil dokter" class="space-y-4" id="profile-form-doctor">
         <div>
          <label class="block font-semibold text-red-700 mb-1 text-sm sm:text-base" for="profile-fullname-doctor">
           Nama Lengkap
          </label>
          <input aria-required="true" class="w-full rounded-xl border border-red-300 px-3 py-1.5 sm:px-4 sm:py-2 focus:outline-none focus:ring-2 focus:ring-red-400 shadow-sm text-sm sm:text-base" id="profile-fullname-doctor" name="profile-fullname-doctor" placeholder="Masukkan nama lengkap" required="" type="text"/>
         </div>
         <div>
          <label class="block font-semibold text-red-700 mb-1 text-sm sm:text-base" for="profile-phone-doctor">
           Nomor Telepon
          </label>
          <input class="w-full rounded-xl border border-red-300 px-3 py-1.5 sm:px-4 sm:py-2 focus:outline-none focus:ring-2 focus:ring-red-400 shadow-sm text-sm sm:text-base" id="profile-phone-doctor" name="profile-phone-doctor" pattern="[0-9+ ]{6,20}" placeholder="Masukkan nomor telepon" type="tel"/>
         </div>
         <div>
          <label class="block font-semibold text-red-700 mb-1 text-sm sm:text-base" for="profile-email-doctor">
           Email
          </label>
          <input aria-required="true" class="w-full rounded-xl border border-red-300 px-3 py-1.5 sm:px-4 sm:py-2 focus:outline-none focus:ring-2 focus:ring-red-400 shadow-sm text-sm sm:text-base" id="profile-email-doctor" name="profile-email-doctor" placeholder="Masukkan email" required="" type="email"/>
         </div>
         <div>
          <label class="block font-semibold text-red-700 mb-1 text-sm sm:text-base" for="profile-address-doctor">
           Alamat
          </label>
          <textarea class="w-full rounded-xl border border-red-300 px-3 py-1.5 sm:px-4 sm:py-2 focus:outline-none focus:ring-2 focus:ring-red-400 shadow-sm text-sm sm:text-base resize-none" id="profile-address-doctor" name="profile-address-doctor" placeholder="Masukkan alamat lengkap" rows="3"></textarea>
         </div>
         <div>
          <label class="block font-semibold text-red-700 mb-1 text-sm sm:text-base" for="profile-specialist-doctor">
           Spesialisasi
          </label>
          <input class="w-full rounded-xl border border-red-300 px-3 py-1.5 sm:px-4 sm:py-2 focus:outline-none focus:ring-2 focus:ring-red-400 shadow-sm text-sm sm:text-base" id="profile-specialist-doctor" name="profile-specialist-doctor" placeholder="Masukkan spesialisasi" type="text"/>
         </div>
         <div class="flex justify-end">
          <button aria-label="Simpan profil dokter" class="bg-gradient-to-r from-red-700 via-red-800 to-red-900 hover:from-red-800 hover:via-red-900 hover:to-red-950 text-white font-extrabold px-4 py-1.5 sm:px-6 sm:py-2 rounded-xl shadow-lg transition focus:ring-4 focus:ring-red-500 flex items-center space-x-2 text-sm sm:text-base shake" type="submit">
           <i class="fas fa-save fa-lg">
           </i>
           <span>
            Simpan Profil
           </span>
          </button>
         </div>
        </form>
       </section>
       <!-- Doctor Notifications Section -->
       <section aria-label="Notifikasi dokter" class="hidden max-w-full space-y-4" id="doctor-notifications-section">
        <h3 class="text-lg sm:text-2xl font-bold text-red-700 mb-4 flex items-center space-x-3">
         <svg aria-hidden="true" class="h-6 w-6 sm:h-8 sm:w-8 text-red-700" fill="none" stroke="currentColor" stroke-width="2" viewbox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6 6 0 10-12 0v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9" stroke-linecap="round" stroke-linejoin="round">
          </path>
         </svg>
         <span>
          Notifikasi Aritmia Pasien
         </span>
        </h3>
        <div aria-label="Daftar notifikasi aritmia pasien" class="bg-white rounded-2xl shadow-lg p-3 sm:p-5 border border-red-300 max-h-[320px] sm:max-h-[400px] overflow-y-auto" id="doctor-notifications-list" tabindex="0">
         <p class="text-gray-500 text-center text-base sm:text-lg font-semibold">
          Memuat notifikasi...
         </p>
        </div>
       </section>
       <!-- Doctor Patients Section -->
       <section aria-label="Daftar pasien dokter" class="hidden max-w-full space-y-4" id="doctor-patients-section">
        <h3 class="text-lg sm:text-2xl font-bold text-red-700 mb-4 flex items-center space-x-3">
         <svg aria-hidden="true" class="h-6 w-6 sm:h-8 sm:w-8 text-red-700" fill="none" stroke="currentColor" stroke-width="2" viewbox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path d="M17 20h5v-2a4 4 0 00-3-3.87M9 20H4v-2a4 4 0 013-3.87M16 7a4 4 0 11-8 0 4 4 0 018 0z" stroke-linecap="round" stroke-linejoin="round">
          </path>
         </svg>
         <span>
          Daftar Pasien
         </span>
        </h3>
        <div class="overflow-x-auto bg-white rounded-2xl shadow-lg border border-red-300">
         <table aria-label="Tabel daftar pasien" class="min-w-full divide-y divide-red-200 text-xs sm:text-sm" role="table">
          <thead class="bg-gradient-to-r from-red-700 via-red-800 to-red-900 text-white rounded-t-2xl">
           <tr>
            <th class="px-2 sm:px-4 py-2 text-left font-semibold tracking-wide" scope="col">
             Nama Lengkap
            </th>
            <th class="px-2 sm:px-4 py-2 text-left font-semibold tracking-wide" scope="col">
             Email
            </th>
            <th class="px-2 sm:px-4 py-2 text-left font-semibold tracking-wide" scope="col">
             Nomor Telepon
            </th>
            <th class="px-2 sm:px-4 py-2 text-left font-semibold tracking-wide" scope="col">
             Jenis Kelamin
            </th>
            <th class="px-2 sm:px-4 py-2 text-left font-semibold tracking-wide" scope="col">
             Usia
            </th>
            <th class="px-2 sm:px-4 py-2 text-left font-semibold tracking-wide" scope="col">
             BMI
            </th>
            <th class="px-2 sm:px-4 py-2 text-left font-semibold tracking-wide" scope="col">
             Riwayat Penyakit
            </th>
            <th class="px-2 sm:px-4 py-2 text-left font-semibold tracking-wide" scope="col">
             Alamat
            </th>
            <th class="px-2 sm:px-4 py-2 text-center font-semibold tracking-wide" scope="col">
             Aksi
            </th>
           </tr>
          </thead>
          <tbody class="divide-y divide-red-200 bg-white" id="doctor-patients-table-body" role="rowgroup">
          </tbody>
         </table>
        </div>
        <div aria-hidden="true" aria-labelledby="doctor-patient-detail-name" aria-modal="true" class="fixed inset-0 bg-black bg-opacity-70 flex items-center justify-center z-50 hidden" id="doctor-patient-detail-modal" role="dialog">
         <div class="bg-white rounded-2xl shadow-2xl max-w-3xl w-full max-h-[90vh] overflow-y-auto p-4 sm:p-6 relative">
          <button aria-label="Tutup" class="absolute top-3 right-3 text-red-700 hover:text-red-900 focus:outline-none focus:ring-2 focus:ring-red-400 rounded-full p-1.5 sm:p-2" id="doctor-patient-detail-close-btn" type="button">
           <i class="fas fa-times fa-lg">
           </i>
          </button>
          <h3 class="text-lg sm:text-2xl font-bold text-red-700 mb-4 flex items-center space-x-3">
           <svg aria-hidden="true" class="h-6 w-6 sm:h-8 sm:w-8 text-red-700" fill="none" stroke="currentColor" stroke-width="2" viewbox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
            <path d="M17 20h5v-2a4 4 0 00-3-3.87M9 20H4v-2a4 4 0 013-3.87M16 7a4 4 0 11-8 0 4 4 0 018 0z" stroke-linecap="round" stroke-linejoin="round">
            </path>
           </svg>
           <span id="doctor-patient-detail-name">
           </span>
          </h3>
          <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 sm:gap-6">
           <div>
            <img alt="Foto profil pasien" class="w-32 h-32 sm:w-44 sm:h-44 rounded-full object-cover border-4 sm:border-6 border-red-700 mb-3 sm:mb-5 shadow-lg" height="176" id="doctor-patient-detail-photo" src="https://storage.googleapis.com/a1aa/image/835b566a-8639-4c5c-37fe-7a654f34fbc1.jpg" width="176"/>
            <button aria-label="Ubah foto pasien" class="bg-gradient-to-r from-red-700 via-red-800 to-red-900 hover:from-red-800 hover:via-red-900 hover:to-red-950 text-white font-extrabold px-3 py-1.5 sm:px-5 sm:py-2 rounded-xl shadow-lg transition flex items-center space-x-2 focus:ring-4 focus:ring-red-500 text-sm sm:text-base shake" id="doctor-patient-photo-edit-btn" type="button">
             <i class="fas fa-camera fa-lg">
             </i>
             <span>
              Ubah Foto
             </span>
            </button>
            <input accept="image/*" class="hidden" id="doctor-patient-photo-input" type="file"/>
           </div>
           <div class="space-y-2 sm:space-y-3 text-xs sm:text-sm text-gray-800 font-semibold">
            <p>
             <span class="font-bold text-red-700">
              Email:
             </span>
             <span id="doctor-patient-detail-email">
             </span>
            </p>
            <p>
             <span class="font-bold text-red-700">
              Nomor Telepon:
             </span>
             <span id="doctor-patient-detail-phone">
             </span>
            </p>
            <p>
             <span class="font-bold text-red-700">
              Jenis Kelamin:
             </span>
             <span id="doctor-patient-detail-gender">
             </span>
            </p>
            <p>
             <span class="font-bold text-red-700">
              Usia:
             </span>
             <span id="doctor-patient-detail-age">
             </span>
            </p>
            <p>
             <span class="font-bold text-red-700">
              BMI:
             </span>
             <span id="doctor-patient-detail-bmi">
             </span>
            </p>
            <p>
             <span class="font-bold text-red-700">
              Riwayat Penyakit:
             </span>
            </p>
            <p class="whitespace-pre-wrap border border-red-300 rounded-xl p-2 sm:p-3 bg-red-50 shadow-inner" id="doctor-patient-detail-medical-history">
            </p>
            <p>
             <span class="font-bold text-red-700">
              Alamat:
             </span>
            </p>
            <p class="whitespace-pre-wrap border border-red-300 rounded-xl p-2 sm:p-3 bg-red-50 shadow-inner" id="doctor-patient-detail-address">
            </p>
           </div>
          </div>
          <div class="mt-4 sm:mt-6">
           <h4 class="text-base sm:text-xl font-bold text-red-700 mb-3 flex items-center space-x-3">
            <svg aria-hidden="true" class="h-5 w-5 sm:h-7 sm:w-7 text-red-700" fill="none" stroke="currentColor" stroke-width="2" viewbox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
             <path d="M3 12h3l3 8 4-16 3 8h3" stroke-linecap="round" stroke-linejoin="round">
             </path>
            </svg>
            <span>
             Riwayat BPM Pasien
            </span>
           </h4>
           <ul aria-label="Riwayat BPM pasien" class="max-h-40 sm:max-h-52 overflow-y-auto border border-red-300 rounded-xl p-3 sm:p-4 space-y-2 bg-white shadow-inner" id="doctor-patient-bpm-history-list" tabindex="0">
           </ul>
          </div>
         </div>
        </div>
       </section>
      </section>
     </div>
    </section>
   </main>
  </div>
  <!-- Firebase SDK -->
  <script src="https://www.gstatic.com/firebasejs/9.22.1/firebase-app-compat.js">
  </script>
  <script src="https://www.gstatic.com/firebasejs/9.22.1/firebase-auth-compat.js">
  </script>
  <script src="https://www.gstatic.com/firebasejs/9.22.1/firebase-firestore-compat.js">
  </script>
  <script src="https://www.gstatic.com/firebasejs/9.22.1/firebase-storage-compat.js">
  </script>
  <script>
   // Firebase config and initialization
    const firebaseConfig = {
      apiKey: "AIzaSyAXgZiJVV5csgH0WlKFSyu0Nn-QwqDgYKg",
      authDomain: "final-cd-5741c.firebaseapp.com",
      projectId: "final-cd-5741c",
      storageBucket: "final-cd-5741c.firebasestorage.app",
      messagingSenderId: "804886218291",
      appId: "1:804886218291:web:6797922c00ce21745a4546",
      measurementId: "G-L7YPR09ERN",
    };
    firebase.initializeApp(firebaseConfig);
    const auth = firebase.auth();
    const db = firebase.firestore();
    const storage = firebase.storage();

    // DOM Elements
    const authSection = document.getElementById('auth-section');
    const dashboardSection = document.getElementById('dashboard-section');
    const tabLogin = document.getElementById('tab-login');
    const tabRegister = document.getElementById('tab-register');
    const loginForm = document.getElementById('login-form');
    const registerForm = document.getElementById('register-form');
    const navLoginBtn = document.getElementById('nav-login-btn');
    const navRegisterBtn = document.getElementById('nav-register-btn');
    const dashboardLogoutBtn = document.getElementById('dashboard-logout-btn');
    const dashboardTitle = document.getElementById('dashboard-title');
    const profileName = document.getElementById('profile-name');
    const profileRole = document.getElementById('profile-role');
    const profilePhoto = document.getElementById('profile-photo');
    const dashboardNavBtns = document.querySelectorAll('.dashboard-nav-btn');
    const dashboardMain = document.getElementById('dashboard-main');

    // Patient dashboard elements
    const profileSection = document.getElementById('profile-section');
    const heartSection = document.getElementById('heart-section');
    const educationSection = document.getElementById('education-section');
    const chatSection = document.getElementById('chat-section');
    const sidebarHeartBtn = document.getElementById('sidebar-heart-btn');
    const sidebarEducationBtn = document.getElementById('sidebar-education-btn');
    const sidebarPatientsBtn = document.getElementById('sidebar-patients-btn');
    const sidebarNotificationsBtn = document.getElementById('sidebar-notifications-btn');
    const notificationCount = document.getElementById('notification-count');

    // Patient profile form inputs
    const profileFormPatient = document.getElementById('profile-form-patient');
    const inputFullnamePatient = document.getElementById('profile-fullname-patient');
    const inputEmailPatient = document.getElementById('profile-email-patient');
    const inputPhonePatient = document.getElementById('profile-phone-patient');
    const inputGenderPatient = document.getElementById('profile-gender-patient');
    const inputBirthplacePatient = document.getElementById('profile-birthplace-patient');
    const inputBirthdatePatient = document.getElementById('profile-birthdate-patient');
    const inputAgePatient = document.getElementById('profile-age-patient');
    const inputWeightPatient = document.getElementById('profile-weight-patient');
    const inputHeightPatient = document.getElementById('profile-height-patient');
    const inputBMIPatient = document.getElementById('profile-bmi-patient');
    const inputMedicalHistoryPatient = document.getElementById('profile-medical-history-patient');
    const inputAddressPatient = document.getElementById('profile-address-patient');

    // Heart monitor elements
    const startEcgBtn = document.getElementById('start-ecg-btn');
    const ecgResult = document.getElementById('ecg-result');
    const bpmValue = document.getElementById('bpm-value');
    const bpmCategory = document.getElementById('bpm-category');
    const ecgHistoryList = document.getElementById('ecg-history-list');

    // Chat elements
    const chatUserList = document.getElementById('chat-users');
    const chatWindow = document.getElementById('chat-window');
    const chatHeaderName = document.getElementById('chat-header-name');
    const chatHeaderRole = document.getElementById('chat-header-role');
    const chatHeaderPhoto = document.getElementById('chat-header-photo');
    const chatMessages = document.getElementById('chat-messages');
    const chatForm = document.getElementById('chat-form');
    const chatInput = document.getElementById('chat-input');
    const chatCloseBtn = document.getElementById('chat-close-btn');

    // Doctor dashboard elements
    const doctorWelcomeSection = document.getElementById('doctor-welcome-section');
    const doctorWelcomeName = document.getElementById('doctor-welcome-name');
    const doctorProfileSection = document.getElementById('doctor-profile-section');
    const doctorNotificationsSection = document.getElementById('doctor-notifications-section');
    const doctorNotificationsList = document.getElementById('doctor-notifications-list');
    const doctorPatientsSection = document.getElementById('doctor-patients-section');
    const doctorPatientsTableBody = document.getElementById('doctor-patients-table-body');
    const doctorPatientDetailModal = document.getElementById('doctor-patient-detail-modal');
    const doctorPatientDetailCloseBtn = document.getElementById('doctor-patient-detail-close-btn');
    const doctorPatientDetailName = document.getElementById('doctor-patient-detail-name');
    const doctorPatientDetailPhoto = document.getElementById('doctor-patient-detail-photo');
    const doctorPatientDetailEmail = document.getElementById('doctor-patient-detail-email');
    const doctorPatientDetailPhone = document.getElementById('doctor-patient-detail-phone');
    const doctorPatientDetailGender = document.getElementById('doctor-patient-detail-gender');
    const doctorPatientDetailAge = document.getElementById('doctor-patient-detail-age');
    const doctorPatientDetailBMI = document.getElementById('doctor-patient-detail-bmi');
    const doctorPatientDetailMedicalHistory = document.getElementById('doctor-patient-detail-medical-history');
    const doctorPatientDetailAddress = document.getElementById('doctor-patient-detail-address');
    const doctorPatientBpmHistoryList = document.getElementById('doctor-patient-bpm-history-list');
    const doctorPatientPhotoEditBtn = document.getElementById('doctor-patient-photo-edit-btn');
    const doctorPatientPhotoInput = document.getElementById('doctor-patient-photo-input');

    // Doctor profile form inputs
    const profileFormDoctor = document.getElementById('profile-form-doctor');
    const inputFullnameDoctor = document.getElementById('profile-fullname-doctor');
    const inputPhoneDoctor = document.getElementById('profile-phone-doctor');
    const inputEmailDoctor = document.getElementById('profile-email-doctor');
    const inputAddressDoctor = document.getElementById('profile-address-doctor');
    const inputSpecialistDoctor = document.getElementById('profile-specialist-doctor');

    // Profile photo edit elements
    const profilePhotoContainer = document.getElementById('profile-photo-container');
    const profilePhotoInput = document.getElementById('profile-photo-input');

    // State
    let currentUser = null;
    let currentUserData = null;
    let currentRole = null; // 'patient' or 'doctor'
    let currentChatUser = null; // userId of chat partner
    let chatUnsub = null;
    let notificationsUnsub = null;

    // Utility Functions
    function showSection(section) {
      // Hide all dashboard sections
      [
        doctorWelcomeSection, profileSection, heartSection, educationSection, chatSection,
        doctorProfileSection, doctorNotificationsSection, doctorPatientsSection
      ].forEach(s => s.classList.add('hidden'));
      section.classList.remove('hidden');
    }

    function clearChatWindow() {
      chatMessages.innerHTML = '';
      chatHeaderName.textContent = '';
      chatHeaderRole.textContent = '';
      chatHeaderPhoto.src = 'https://placehold.co/48x48/png?text=User';
      currentChatUser = null;
      if (chatUnsub) {
        chatUnsub();
        chatUnsub = null;
      }
    }

    function formatDateTime(timestamp) {
      const d = timestamp.toDate ? timestamp.toDate() : new Date(timestamp);
      return d.toLocaleString('id-ID', {
        year: 'numeric',
        month: 'short',
        day: 'numeric',
        hour: '2-digit',
        minute: '2-digit',
      });
    }

    function calculateAge(birthdate) {
      if (!birthdate) return '';
      const today = new Date();
      const birth = new Date(birthdate);
      let age = today.getFullYear() - birth.getFullYear();
      const m = today.getMonth() - birth.getMonth();
      if (m < 0 || (m === 0 && today.getDate() < birth.getDate())) {
        age--;
      }
      return age;
    }

    function calculateBMI(weight, height) {
      if (!weight || !height) return '';
      const heightM = height / 100;
      const bmi = weight / (heightM * heightM);
      return bmi.toFixed(1);
    }

    function categorizeBPM(bpm) {
      if (bpm < 60) return 'Bradikardia';
      if (bpm <= 100) return 'Normal';
      return 'Takikardia';
    }

    // Authentication UI toggles
    function showLogin() {
      tabLogin.classList.add('border-red-700', 'text-red-700');
      tabLogin.classList.remove('text-gray-400');
      tabRegister.classList.remove('border-red-700', 'text-red-700');
      tabRegister.classList.add('text-gray-400');
      loginForm.classList.remove('hidden');
      loginForm.setAttribute('tabindex', '0');
      registerForm.classList.add('hidden');
      registerForm.setAttribute('tabindex', '-1');
      tabLogin.setAttribute('aria-selected', 'true');
      tabRegister.setAttribute('aria-selected', 'false');
    }
    function showRegister() {
      tabRegister.classList.add('border-red-700', 'text-red-700');
      tabRegister.classList.remove('text-gray-400');
      tabLogin.classList.remove('border-red-700', 'text-red-700');
      tabLogin.classList.add('text-gray-400');
      registerForm.classList.remove('hidden');
      registerForm.setAttribute('tabindex', '0');
      loginForm.classList.add('hidden');
      loginForm.setAttribute('tabindex', '-1');
      tabRegister.setAttribute('aria-selected', 'true');
      tabLogin.setAttribute('aria-selected', 'false');
    }

    // Navigation handlers
    tabLogin.addEventListener('click', () => {
      showLogin();
    });
    tabRegister.addEventListener('click', () => {
      showRegister();
    });
    navLoginBtn.addEventListener('click', () => {
      authSection.classList.remove('hidden');
      dashboardSection.classList.add('hidden');
      showLogin();
    });
    navRegisterBtn.addEventListener('click', () => {
      authSection.classList.remove('hidden');
      dashboardSection.classList.add('hidden');
      showRegister();
    });

    // Dashboard navigation buttons
    dashboardNavBtns.forEach(btn => {
      btn.addEventListener('click', () => {
        const target = btn.getAttribute('data-target');
        if (!target) return;
        if (currentRole === 'doctor') {
          if (target === 'heart-section' || target === 'education-section') return; // hide for doctor
          if (target === 'profile-section') {
            showSection(doctorProfileSection);
            return;
          }
          if (target === 'notifications-section') {
            showSection(doctorNotificationsSection);
            return;
          }
          if (target === 'patients-section') {
            showSection(doctorPatientsSection);
            return;
          }
          if (target === 'chat-section') {
            showSection(chatSection);
            return;
          }
          if (target === 'welcome-section') {
            showSection(doctorWelcomeSection);
            return;
          }
        } else {
          // patient
          if (target === 'profile-section') {
            showSection(profileSection);
            return;
          }
          if (target === 'heart-section') {
            showSection(heartSection);
            return;
          }
          if (target === 'education-section') {
            showSection(educationSection);
            return;
          }
          if (target === 'chat-section') {
            showSection(chatSection);
            return;
          }
        }
      });
    });

    // Logout
    dashboardLogoutBtn.addEventListener('click', () => {
      auth.signOut();
    });

    // Register form submit
    registerForm.addEventListener('submit', async (e) => {
      e.preventDefault();
      const fullname = registerForm['register-fullname'].value.trim();
      const username = registerForm['register-username'].value.trim();
      const email = registerForm['register-email'].value.trim();
      const password = registerForm['register-password'].value;
      const role = registerForm['register-role'].value;

      if (!fullname || !username || !email || !password || !role) {
        alert('Mohon lengkapi semua data pendaftaran.');
        return;
      }

      try {
        // Check if username already exists
        const usernameQuery = await db.collection('users').where('username', '==', username).get();
        if (!usernameQuery.empty) {
          alert('Username sudah digunakan, silakan pilih yang lain.');
          return;
        }

        // Create user with email and password
        const userCredential = await auth.createUserWithEmailAndPassword(email, password);
        const user = userCredential.user;

        // Save user profile in Firestore
        await db.collection('users').doc(user.uid).set({
          fullname,
          username,
          email,
          role,
          createdAt: firebase.firestore.FieldValue.serverTimestamp(),
          profilePhotoURL: '',
          phone: '',
          specialist: '',
          address: '',
          // Patient fields empty for doctor
          gender: '',
          birthplace: '',
          birthdate: '',
          age: '',
          weight: '',
          height: '',
          bmi: '',
          medicalHistory: '',
          ecgHistory: [],
          chatWith: [],
        });

        alert('Pendaftaran berhasil! Silakan login.');
        registerForm.reset();
        showLogin();
      } catch (error) {
        alert('Gagal mendaftar: ' + error.message);
      }
    });

    // Login form submit
    loginForm.addEventListener('submit', async (e) => {
      e.preventDefault();
      const usernameOrEmail = loginForm['login-username-email'].value.trim();
      const password = loginForm['login-password'].value;

      if (!usernameOrEmail || !password) {
        alert('Mohon isi username/email dan password.');
        return;
      }

      try {
        // Try login by email first
        let userCredential;
        try {
          userCredential = await auth.signInWithEmailAndPassword(usernameOrEmail, password);
        } catch (err) {
          // If failed, try to find email by username
          const userQuery = await db.collection('users').where('username', '==', usernameOrEmail).get();
          if (userQuery.empty) throw new Error('User tidak ditemukan');
          const userData = userQuery.docs[0].data();
          userCredential = await auth.signInWithEmailAndPassword(userData.email, password);
        }

        currentUser = userCredential.user;
        await loadUserData();
        authSection.classList.add('hidden');
        dashboardSection.classList.remove('hidden');
        if (currentRole === 'doctor') {
          showSection(doctorWelcomeSection);
          sidebarPatientsBtn.classList.remove('hidden');
          sidebarNotificationsBtn.style.display = 'inline-block';
          sidebarHeartBtn.classList.add('hidden');
          sidebarEducationBtn.classList.add('hidden');
        } else {
          showSection(profileSection);
          sidebarPatientsBtn.classList.add('hidden');
          sidebarNotificationsBtn.style.display = 'none';
          sidebarHeartBtn.classList.remove('hidden');
          sidebarEducationBtn.classList.remove('hidden');
        }
        dashboardTitle.textContent = `Dashboard ${currentRole === 'doctor' ? 'Dokter' : 'Pasien'}`;
      } catch (error) {
        alert('Gagal login: ' + error.message);
      }
    });

    // Load user data from Firestore
    async function loadUserData() {
      if (!currentUser) return;
      const doc = await db.collection('users').doc(currentUser.uid).get();
      if (!doc.exists) {
        alert('Data pengguna tidak ditemukan.');
        return;
      }
      currentUserData = doc.data();
      currentRole = currentUserData.role;

      // Update sidebar profile info
      profileName.textContent = currentUserData.fullname || 'Nama Pengguna';
      profileRole.textContent = currentRole === 'doctor' ? 'Dokter' : 'Pasien';
      profilePhoto.src = currentUserData.profilePhotoURL || 'https://placehold.co/96x96/png?text=User+Photo';

      if (currentRole === 'doctor') {
        // Doctor profile form fill
        inputFullnameDoctor.value = currentUserData.fullname || '';
        inputPhoneDoctor.value = currentUserData.phone || '';
        inputEmailDoctor.value = currentUserData.email || '';
        inputAddressDoctor.value = currentUserData.address || '';
        inputSpecialistDoctor.value = currentUserData.specialist || '';
        doctorWelcomeName.textContent = currentUserData.fullname || '';

        loadDoctorPatients();
        subscribeNotifications();
      } else {
        // Patient profile form fill
        inputFullnamePatient.value = currentUserData.fullname || '';
        inputEmailPatient.value = currentUserData.email || '';
        inputPhonePatient.value = currentUserData.phone || '';
        inputGenderPatient.value = currentUserData.gender || '';
        inputBirthplacePatient.value = currentUserData.birthplace || '';
        inputBirthdatePatient.value = currentUserData.birthdate || '';
        inputAgePatient.value = currentUserData.age || '';
        inputWeightPatient.value = currentUserData.weight || '';
        inputHeightPatient.value = currentUserData.height || '';
        inputBMIPatient.value = currentUserData.bmi || '';
        inputMedicalHistoryPatient.value = currentUserData.medicalHistory || '';
        inputAddressPatient.value = currentUserData.address || '';
      }

      loadChatUserList();
    }

    // Patient profile form submit
    profileFormPatient.addEventListener('submit', async (e) => {
      e.preventDefault();
      if (currentRole !== 'patient') return;

      const fullname = inputFullnamePatient.value.trim();
      const email = inputEmailPatient.value.trim();
      const phone = inputPhonePatient.value.trim();
      const gender = inputGenderPatient.value;
      const birthplace = inputBirthplacePatient.value.trim();
      const birthdate = inputBirthdatePatient.value;
      const age = calculateAge(birthdate);
      const weight = parseFloat(inputWeightPatient.value);
      const height = parseFloat(inputHeightPatient.value);
      const bmi = calculateBMI(weight, height);
      const medicalHistory = inputMedicalHistoryPatient.value.trim();
      const address = inputAddressPatient.value.trim();

      if (!fullname || !email) {
        alert('Nama lengkap dan email wajib diisi.');
        return;
      }

      try {
        await db.collection('users').doc(currentUser.uid).update({
          fullname,
          email,
          phone,
          gender,
          birthplace,
          birthdate,
          age,
          weight,
          height,
          bmi,
          medicalHistory,
          address,
        });
        inputAgePatient.value = age;
        inputBMIPatient.value = bmi;
        alert('Profil berhasil disimpan.');
        await loadUserData();
      } catch (error) {
        alert('Gagal menyimpan profil: ' + error.message);
      }
    });

    // Update age automatically when birthdate changes
    inputBirthdatePatient.addEventListener('change', () => {
      const age = calculateAge(inputBirthdatePatient.value);
      inputAgePatient.value = age;
    });

    // Update BMI automatically when weight or height changes
    function updateBMIPatient() {
      const weight = parseFloat(inputWeightPatient.value);
      const height = parseFloat(inputHeightPatient.value);
      const bmi = calculateBMI(weight, height);
      inputBMIPatient.value = bmi;
    }
    inputWeightPatient.addEventListener('input', updateBMIPatient);
    inputHeightPatient.addEventListener('input', updateBMIPatient);

    // Heart monitor start button (patient only)
    startEcgBtn.addEventListener('click', async () => {
      if (currentRole !== 'patient') return;
      startEcgBtn.disabled = true;
      startEcgBtn.innerHTML = '<i class="fas fa-spinner fa-spin"></i> Mengambil data...';
      try {
        // Simulate ECG data fetching
        const bpm = Math.floor(Math.random() * 70) + 50;
        const category = categorizeBPM(bpm);
        bpmValue.textContent = bpm;
        bpmCategory.textContent = category;
        ecgResult.classList.remove('hidden');

        const newEcgEntry = {
          bpm,
          category,
          timestamp: firebase.firestore.FieldValue.serverTimestamp(),
        };

        await db.collection('users').doc(currentUser.uid).update({
          ecgHistory: firebase.firestore.FieldValue.arrayUnion(newEcgEntry),
        });

        const doc = await db.collection('users').doc(currentUser.uid).get();
        currentUserData = doc.data();
        renderECGHistory(currentUserData.ecgHistory || []);

        if (category === 'Takikardia' || category === 'Bradikardia') {
          notifyDoctorOfAritmia(currentUser.uid, bpm, category);
        }
      } catch (error) {
        alert('Gagal mengambil data ECG: ' + error.message);
      } finally {
        startEcgBtn.disabled = false;
        startEcgBtn.innerHTML = '<i class="fas fa-star"></i> Start';
      }
    });

    function renderECGHistory(history) {
      ecgHistoryList.innerHTML = '';
      if (!history.length) {
        ecgHistoryList.innerHTML = '<li class="text-gray-500 text-sm sm:text-base font-semibold">Belum ada riwayat deteksi.</li>';
        return;
      }
      history.slice().reverse().forEach(item => {
        const li = document.createElement('li');
        li.className = 'border border-red-300 rounded-xl p-2 sm:p-3 bg-white flex justify-between items-center shadow-sm';
        li.innerHTML = `
          <div>
            <p class="font-semibold text-red-700 text-base sm:text-lg">BPM: ${item.bpm}</p>
            <p class="text-sm sm:text-base text-gray-600">Kategori: ${item.category}</p>
            <p class="text-xs sm:text-sm text-gray-500">${formatDateTime(item.timestamp)}</p>
          </div>
        `;
        ecgHistoryList.appendChild(li);
      });
    }

    // Notify doctor about aritmia detected for a patient
    async function notifyDoctorOfAritmia(patientId, bpm, category) {
      const doctorsSnapshot = await db.collection('users').where('role', '==', 'doctor').get();
      const notifications = [];
      doctorsSnapshot.forEach(doc => {
        notifications.push(
          db.collection('notifications').add({
            toUserId: doc.id,
            fromUserId: patientId,
            type: 'aritmia',
            bpm,
            category,
            timestamp: firebase.firestore.FieldValue.serverTimestamp(),
            read: false,
          })
        );
      });
      await Promise.all(notifications);

      await db.collection('notifications').add({
        toUserId: patientId,
        fromUserId: patientId,
        type: 'aritmia',
        bpm,
        category,
        timestamp: firebase.firestore.FieldValue.serverTimestamp(),
        read: false,
      });
    }

    // Doctor profile form submit
    profileFormDoctor.addEventListener('submit', async (e) => {
      e.preventDefault();
      if (currentRole !== 'doctor') return;

      const fullname = inputFullnameDoctor.value.trim();
      const phone = inputPhoneDoctor.value.trim();
      const email = inputEmailDoctor.value.trim();
      const address = inputAddressDoctor.value.trim();
      const specialist = inputSpecialistDoctor.value.trim();

      if (!fullname || !email) {
        alert('Nama lengkap dan email wajib diisi.');
        return;
      }

      try {
        await db.collection('users').doc(currentUser.uid).update({
          fullname,
          phone,
          email,
          address,
          specialist,
        });
        alert('Profil berhasil disimpan.');
        await loadUserData();
      } catch (error) {
        alert('Gagal menyimpan profil: ' + error.message);
      }
    });

    // Profile photo upload (doctor)
    profilePhotoContainer.addEventListener('click', () => {
      profilePhotoInput.click();
    });
    profilePhotoInput.addEventListener('change', async (e) => {
      const file = e.target.files[0];
      if (!file) return;
      if (!file.type.startsWith('image/')) {
        alert('File harus berupa gambar.');
        return;
      }
      try {
        const storageRef = storage.ref();
        const photoRef = storageRef.child(`profilePhotos/${currentUser.uid}_${Date.now()}`);
        await photoRef.put(file);
        const photoURL = await photoRef.getDownloadURL();
        await db.collection('users').doc(currentUser.uid).update({
          profilePhotoURL: photoURL,
        });
        profilePhoto.src = photoURL;
        alert('Foto profil berhasil diperbarui.');
      } catch (error) {
        alert('Gagal mengunggah foto: ' + error.message);
      }
    });

    // Load doctor patients list
    async function loadDoctorPatients() {
      if (currentRole !== 'doctor') return;
      doctorPatientsTableBody.innerHTML = '<tr><td colspan="9" class="text-center py-4 text-gray-500 text-sm sm:text-base font-semibold">Memuat data pasien...</td></tr>';
      try {
        const patientsSnapshot = await db.collection('users').where('role', '==', 'patient').get();
        if (patientsSnapshot.empty) {
          doctorPatientsTableBody.innerHTML = '<tr><td colspan="9" class="text-center py-4 text-gray-500 text-sm sm:text-base font-semibold">Belum ada pasien terdaftar.</td></tr>';
          return;
        }
        doctorPatientsTableBody.innerHTML = '';
        patientsSnapshot.forEach(doc => {
          const p = doc.data();
          const tr = document.createElement('tr');
          tr.className = 'hover:bg-red-50 cursor-pointer transition-colors duration-200';
          tr.innerHTML = `
            <td class="px-2 sm:px-4 py-2 text-sm sm:text-base text-red-700 font-semibold">${p.fullname || '-'}</td>
            <td class="px-2 sm:px-4 py-2 text-sm sm:text-base">${p.email || '-'}</td>
            <td class="px-2 sm:px-4 py-2 text-sm sm:text-base">${p.phone || '-'}</td>
            <td class="px-2 sm:px-4 py-2 text-sm sm:text-base">${p.gender === 'female' ? 'Perempuan' : p.gender === 'male' ? 'Laki-laki' : '-'}</td>
            <td class="px-2 sm:px-4 py-2 text-sm sm:text-base">${p.age || '-'}</td>
            <td class="px-2 sm:px-4 py-2 text-sm sm:text-base">${p.bmi || '-'}</td>
            <td class="px-2 sm:px-4 py-2 text-sm sm:text-base max-w-xs truncate" title="${p.medicalHistory || '-'}">${p.medicalHistory || '-'}</td>
            <td class="px-2 sm:px-4 py-2 text-sm sm:text-base max-w-xs truncate" title="${p.address || '-'}">${p.address || '-'}</td>
            <td class="px-2 sm:px-4 py-2 text-center">
              <button class="btn-view-patient bg-red-700 hover:bg-red-800 text-white px-2 py-1 sm:px-3 sm:py-1.5 rounded-lg shadow-md transition focus:ring-4 focus:ring-red-400 text-xs sm:text-sm" data-patient-id="${doc.id}" type="button" aria-label="Lihat detail pasien ${p.fullname || ''}">
                <i class="fas fa-eye"></i> Detail
              </button>
            </td>
          `;
          doctorPatientsTableBody.appendChild(tr);
        });

        document.querySelectorAll('.btn-view-patient').forEach(btn => {
          btn.addEventListener('click', () => {
            const patientId = btn.getAttribute('data-patient-id');
            openDoctorPatientDetail(patientId);
          });
        });
      } catch (error) {
        doctorPatientsTableBody.innerHTML = `<tr><td colspan="9" class="text-center py-4 text-red-700 font-semibold text-sm sm:text-base">Gagal memuat data pasien: ${error.message}</td></tr>`;
      }
    }

    // Open doctor patient detail modal
    async function openDoctorPatientDetail(patientId) {
      try {
        const doc = await db.collection('users').doc(patientId).get();
        if (!doc.exists) {
          alert('Data pasien tidak ditemukan.');
          return;
        }
        const p = doc.data();
        doctorPatientDetailName.textContent = p.fullname || '-';
        doctorPatientDetailPhoto.src = p.profilePhotoURL || 'https://placehold.co/192x192/png?text=Foto+Pasien';
        doctorPatientDetailEmail.textContent = p.email || '-';
        doctorPatientDetailPhone.textContent = p.phone || '-';
        doctorPatientDetailGender.textContent = p.gender === 'female' ? 'Perempuan' : p.gender === 'male' ? 'Laki-laki' : '-';
        doctorPatientDetailAge.textContent = p.age || '-';
        doctorPatientDetailBMI.textContent = p.bmi || '-';
        doctorPatientDetailMedicalHistory.textContent = p.medicalHistory || '-';
        doctorPatientDetailAddress.textContent = p.address || '-';

        doctorPatientBpmHistoryList.innerHTML = '';
        if (p.ecgHistory && p.ecgHistory.length) {
          p.ecgHistory.slice().reverse().forEach(item => {
            const li = document.createElement('li');
            li.className = 'border border-red-300 rounded-xl p-2 sm:p-3 bg-white flex justify-between items-center shadow-sm text-xs sm:text-sm';
            li.innerHTML = `
              <div>
                <p class="font-semibold text-red-700 text-base sm:text-lg">BPM: ${item.bpm}</p>
                <p class="text-sm sm:text-base text-gray-600">Kategori: ${item.category}</p>
                <p class="text-xs sm:text-sm text-gray-500">${formatDateTime(item.timestamp)}</p>
              </div>
            `;
            doctorPatientBpmHistoryList.appendChild(li);
          });
        } else {
          doctorPatientBpmHistoryList.innerHTML = '<li class="text-gray-500 text-sm sm:text-base font-semibold">Belum ada riwayat BPM.</li>';
        }

        doctorPatientDetailModal.classList.remove('hidden');
        doctorPatientPhotoInput.dataset.patientId = patientId;
      } catch (error) {
        alert('Gagal memuat detail pasien: ' + error.message);
      }
    }

    // Close doctor patient detail modal
    doctorPatientDetailCloseBtn.addEventListener('click', () => {
      doctorPatientDetailModal.classList.add('hidden');
      doctorPatientPhotoInput.value = '';
    });

    // Doctor patient photo edit button click
    doctorPatientPhotoEditBtn.addEventListener('click', () => {
      doctorPatientPhotoInput.click();
    });

    // Doctor patient photo upload
    doctorPatientPhotoInput.addEventListener('change', async (e) => {
      const file = e.target.files[0];
      if (!file) return;
      if (!file.type.startsWith('image/')) {
        alert('File harus berupa gambar.');
        return;
      }
      const patientId = e.target.dataset.patientId;
      if (!patientId) return;

      try {
        const storageRef = storage.ref();
        const photoRef = storageRef.child(`profilePhotos/${patientId}_${Date.now()}`);
        await photoRef.put(file);
        const photoURL = await photoRef.getDownloadURL();
        await db.collection('users').doc(patientId).update({
          profilePhotoURL: photoURL,
        });
        doctorPatientDetailPhoto.src = photoURL;
        alert('Foto pasien berhasil diperbarui.');
        await loadDoctorPatients();
      } catch (error) {
        alert('Gagal mengunggah foto: ' + error.message);
      }
    });

    // Load chat user list (doctor: patients, patient: doctors)
    async function loadChatUserList() {
      chatUserList.innerHTML = '';
      try {
        let usersSnapshot;
        if (currentRole === 'doctor') {
          usersSnapshot = await db.collection('users').where('role', '==', 'patient').get();
        } else if (currentRole === 'patient') {
          usersSnapshot = await db.collection('users').where('role', '==', 'doctor').get();
        } else {
          chatUserList.innerHTML = '<li class="p-3 text-gray-500 text-sm sm:text-base font-semibold">Tidak ada pengguna chat.</li>';
          return;
        }
        if (usersSnapshot.empty) {
          chatUserList.innerHTML = '<li class="p-3 text-gray-500 text-sm sm:text-base font-semibold">Tidak ada pengguna chat.</li>';
          return;
        }
        usersSnapshot.forEach(doc => {
          const u = doc.data();
          const li = document.createElement('li');
          li.className = 'p-2 sm:p-3 hover:bg-red-100 cursor-pointer flex items-center space-x-2 sm:space-x-3 rounded-xl transition focus:outline-none focus:ring-2 focus:ring-red-400 text-sm sm:text-base font-semibold';
          li.setAttribute('data-user-id', doc.id);
          li.setAttribute('data-user-name', u.fullname);
          li.setAttribute('data-user-role', u.role);
          li.tabIndex = 0;
          li.setAttribute('role', 'button');
          li.setAttribute('aria-label', `Buka chat dengan ${u.fullname}`);
          li.innerHTML = `
            <img src="${u.profilePhotoURL || 'https://placehold.co/48x48/png?text=User'}" alt="Foto profil ${u.fullname}" class="w-8 h-8 sm:w-12 sm:h-12 rounded-full object-cover border-4 border-red-700 shadow-md" />
            <div>
              <p class="font-semibold text-red-700 text-sm sm:text-base">${u.fullname}</p>
              <p class="text-xs sm:text-sm text-gray-600">${u.role === 'doctor' ? 'Dokter' : 'Pasien'}</p>
            </div>
          `;
          li.addEventListener('click', () => {
            openChat(doc.id, u.fullname, u.role);
          });
          li.addEventListener('keypress', (e) => {
            if (e.key === 'Enter' || e.key === ' ') {
              e.preventDefault();
              openChat(doc.id, u.fullname, u.role);
            }
          });
          chatUserList.appendChild(li);
        });
      } catch (error) {
        chatUserList.innerHTML = `<li class="p-3 text-red-700 font-semibold text-sm sm:text-base">Gagal memuat daftar chat: ${error.message}</li>`;
      }
    }

    // Open chat with userId
    async function openChat(userId, userName, userRole) {
      currentChatUser = userId;
      chatWindow.classList.remove('hidden');
      chatHeaderName.textContent = userName;
      chatHeaderRole.textContent = userRole === 'doctor' ? 'Dokter' : 'Pasien';

      try {
        const doc = await db.collection('users').doc(userId).get();
        if (doc.exists) {
          const data = doc.data();
          chatHeaderPhoto.src = data.profilePhotoURL || 'https://placehold.co/48x48/png?text=User';
        }
      } catch {
        chatHeaderPhoto.src = 'https://placehold.co/48x48/png?text=User';
      }

      if (chatUnsub) chatUnsub();

      chatMessages.innerHTML = '<p class="text-gray-500 text-center mt-8 text-base sm:text-lg font-semibold">Memuat pesan...</p>';

      const chatId = generateChatId(currentUser.uid, currentChatUser);
      chatUnsub = db.collection('chats').doc(chatId).collection('messages').orderBy('timestamp')
        .onSnapshot(snapshot => {
          chatMessages.innerHTML = '';
          if (snapshot.empty) {
            chatMessages.innerHTML = '<p class="text-gray-500 text-center mt-8 text-base sm:text-lg font-semibold">Belum ada pesan.</p>';
            return;
          }
          snapshot.forEach(doc => {
            const msg = doc.data();
            const isMe = msg.senderId === currentUser.uid;
            const msgDiv = document.createElement('div');
            msgDiv.className = `max-w-xs md:max-w-md px-3 py-1.5 sm:px-5 sm:py-2 rounded-2xl break-words shadow-md ${
              isMe ? 'bg-red-700 text-white self-end' : 'bg-white border border-red-300 text-red-700 self-start'
            } text-sm sm:text-base`;
            msgDiv.textContent = msg.text;
            chatMessages.appendChild(msgDiv);
          });
          chatMessages.scrollTop = chatMessages.scrollHeight;
        });
    }

    // Close chat window
    chatCloseBtn.addEventListener('click', () => {
      chatWindow.classList.add('hidden');
      clearChatWindow();
    });

    // Chat form submit
    chatForm.addEventListener('submit', async (e) => {
      e.preventDefault();
      if (!currentChatUser) return;
      const text = chatInput.value.trim();
      if (!text) return;

      const chatId = generateChatId(currentUser.uid, currentChatUser);
      try {
        await db.collection('chats').doc(chatId).collection('messages').add({
          senderId: currentUser.uid,
          receiverId: currentChatUser,
          text,
          timestamp: firebase.firestore.FieldValue.serverTimestamp(),
        });
        chatInput.value = '';
      } catch (error) {
        alert('Gagal mengirim pesan: ' + error.message);
      }
    });

    // Generate chat ID based on two user IDs (sorted)
    function generateChatId(uid1, uid2) {
      return uid1 < uid2 ? uid1 + '_' + uid2 : uid2 + '_' + uid1;
    }

    // Subscribe to notifications for doctor
    function subscribeNotifications() {
      if (notificationsUnsub) notificationsUnsub();
      notificationsUnsub = db.collection('notifications')
        .where('toUserId', '==', currentUser.uid)
        .where('read', '==', false)
        .orderBy('timestamp', 'desc')
        .onSnapshot(snapshot => {
          const count = snapshot.size;
          if (count > 0) {
            notificationCount.style.display = 'inline-block';
            notificationCount.textContent = count;
          } else {
            notificationCount.style.display = 'none';
          }
          renderDoctorNotifications(snapshot.docs.map(doc => ({ id: doc.id, ...doc.data() })));
        });
    }

    // Render doctor notifications list
    function renderDoctorNotifications(notifications) {
      doctorNotificationsList.innerHTML = '';
      if (!notifications.length) {
        doctorNotificationsList.innerHTML = '<p class="text-gray-500 text-center text-base sm:text-lg font-semibold">Tidak ada notifikasi baru.</p>';
        return;
      }
      notifications.forEach(async (notif) => {
        const div = document.createElement('div');
        div.className = 'border border-red-300 rounded-xl p-3 sm:p-4 mb-3 bg-white flex justify-between items-center shadow-md text-sm sm:text-base';
        let patientName = 'Pasien';
        try {
          const patientDoc = await db.collection('users').doc(notif.fromUserId).get();
          if (patientDoc.exists) {
            patientName = patientDoc.data().fullname || patientName;
          }
        } catch {}
        div.innerHTML = `
          <div>
            <p class="font-semibold text-red-700 text-base sm:text-lg">Aritmia terdeteksi pada ${patientName}</p>
            <p class="text-base">BPM: ${notif.bpm}</p>
            <p class="text-base">Kategori: ${notif.category}</p>
            <p class="text-xs sm:text-sm text-gray-500">${formatDateTime(notif.timestamp)}</p>
          </div>
          <button class="bg-red-700 hover:bg-red-800 text-white px-3 py-1.5 rounded-xl shadow-md focus:ring-4 focus:ring-red-400 text-sm sm:text-base" data-id="${notif.id}" type="button" aria-label="Tandai notifikasi sudah dibaca">
            Tandai sudah dibaca
          </button>
        `;
        const btn = div.querySelector('button');
        btn.addEventListener('click', async () => {
          try {
            await db.collection('notifications').doc(notif.id).update({ read: true });
          } catch (error) {
            alert('Gagal menandai notifikasi: ' + error.message);
          }
        });
        doctorNotificationsList.appendChild(div);
      });
    }

    // Listen for auth state changes
    auth.onAuthStateChanged(async (user) => {
      if (user) {
        currentUser = user;
        await loadUserData();
        authSection.classList.add('hidden');
        dashboardSection.classList.remove('hidden');
        if (currentRole === 'doctor') {
          showSection(doctorWelcomeSection);
          sidebarPatientsBtn.classList.remove('hidden');
          sidebarNotificationsBtn.style.display = 'inline-block';
          sidebarHeartBtn.classList.add('hidden');
          sidebarEducationBtn.classList.add('hidden');
        } else {
          showSection(profileSection);
          sidebarPatientsBtn.classList.add('hidden');
          sidebarNotificationsBtn.style.display = 'none';
          sidebarHeartBtn.classList.remove('hidden');
          sidebarEducationBtn.classList.remove('hidden');
        }
        dashboardTitle.textContent = `Dashboard ${currentRole === 'doctor' ? 'Dokter' : 'Pasien'}`;
      } else {
        currentUser = null;
        currentUserData = null;
        currentRole = null;
        authSection.classList.remove('hidden');
        dashboardSection.classList.add('hidden');
        showLogin();
      }
    });
  </script>
 </body>
</html>
