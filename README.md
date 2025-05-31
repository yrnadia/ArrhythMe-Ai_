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
      font-family: "Poppins", sans-serif;
      background-color: #fff;
      min-height: 100vh;
    }
    /* Scrollbar for chat */
    ::-webkit-scrollbar {
      width: 8px;
    }
    ::-webkit-scrollbar-track {
      background: #f1f1f1;
    }
    ::-webkit-scrollbar-thumb {
      background: #dc2626;
      border-radius: 4px;
    }
    ::-webkit-scrollbar-thumb:hover {
      background: #b91c1c;
    }
  </style>
 </head>
 <body class="min-h-screen flex flex-col bg-white bg-opacity-90 backdrop-blur-sm">
  <!-- Container -->
  <div class="flex-grow flex flex-col max-w-7xl mx-auto p-4 sm:p-6 md:p-10" id="app" style="background-image: url('Background.jpeg'); background-size: cover; background-position: center; background-repeat: no-repeat;">
   <!-- Logo and Header -->
   <header class="flex items-center justify-between mb-8 border-b border-red-300 pb-4" role="banner">
    <div class="flex items-center space-x-4">
     <img alt="Logo persegi panjang ArrhythME-AI milik pengguna" class="w-36 h-16 rounded-md shadow-md object-contain" height="160" id="logo" src="LOGO.png" width="360"/>
     <h1 class="text-3xl font-extrabold text-red-700 select-none">
      ArrhythME-AI
     </h1>
    </div>
    <nav aria-label="Primary navigation" class="space-x-4 hidden md:flex">
     <button class="text-red-700 font-semibold hover:text-red-900 transition" id="nav-login-btn" type="button">
      Login
     </button>
     <button class="text-red-700 font-semibold hover:text-red-900 transition" id="nav-register-btn" type="button">
      Register
     </button>
    </nav>
   </header>
   <!-- Main Content Area -->
   <main class="flex-grow bg-white bg-opacity-90 rounded-xl shadow-lg p-6 md:p-10 max-w-5xl mx-auto w-full" role="main">
    <!-- AUTH SECTION -->
    <section aria-label="Authentication section" class="max-w-md mx-auto" id="auth-section">
     <!-- Tabs -->
     <div class="flex justify-center mb-6 border-b border-red-300" role="tablist">
      <button aria-controls="login-form" aria-selected="true" class="px-6 py-2 font-semibold text-red-700 border-b-2 border-red-700 focus:outline-none" id="tab-login" role="tab" tabindex="0" type="button">
       Login
      </button>
      <button aria-controls="register-form" aria-selected="false" class="px-6 py-2 font-semibold text-gray-500 hover:text-red-700 focus:outline-none" id="tab-register" role="tab" tabindex="-1" type="button">
       Register
      </button>
     </div>
     <!-- Login Form -->
     <form aria-label="Login form" autocomplete="off" class="space-y-6" id="login-form" novalidate="">
      <div>
       <label class="block text-sm font-medium text-gray-700" for="login-username-email">
        Username atau Email
       </label>
       <input autocomplete="username" class="mt-1 block w-full rounded-md border border-gray-300 px-3 py-2 shadow-sm placeholder-gray-400 focus:border-red-600 focus:ring focus:ring-red-300 focus:ring-opacity-50" id="login-username-email" name="login-username-email" placeholder="Masukkan username atau email" required="" type="text"/>
      </div>
      <div>
       <label class="block text-sm font-medium text-gray-700" for="login-password">
        Password
       </label>
       <input autocomplete="current-password" class="mt-1 block w-full rounded-md border border-gray-300 px-3 py-2 shadow-sm placeholder-gray-400 focus:border-red-600 focus:ring focus:ring-red-300 focus:ring-opacity-50" id="login-password" name="login-password" placeholder="Masukkan password" required="" type="password"/>
      </div>
      <button class="w-full bg-red-700 hover:bg-red-800 text-white font-semibold py-2 rounded-md transition" type="submit">
       Masuk
      </button>
     </form>
     <!-- Register Form -->
     <form aria-label="Register form" autocomplete="off" class="space-y-6 hidden" id="register-form" novalidate="">
      <div>
       <label class="block text-sm font-medium text-gray-700" for="register-fullname">
        Nama Lengkap
       </label>
       <input autocomplete="name" class="mt-1 block w-full rounded-md border border-gray-300 px-3 py-2 shadow-sm placeholder-gray-400 focus:border-red-600 focus:ring focus:ring-red-300 focus:ring-opacity-50" id="register-fullname" name="register-fullname" placeholder="Masukkan nama lengkap" required="" type="text"/>
      </div>
      <div>
       <label class="block text-sm font-medium text-gray-700" for="register-username">
        Username
       </label>
       <input autocomplete="username" class="mt-1 block w-full rounded-md border border-gray-300 px-3 py-2 shadow-sm placeholder-gray-400 focus:border-red-600 focus:ring focus:ring-red-300 focus:ring-opacity-50" id="register-username" name="register-username" placeholder="Buat username" required="" type="text"/>
      </div>
      <div>
       <label class="block text-sm font-medium text-gray-700" for="register-email">
        Email
       </label>
       <input autocomplete="email" class="mt-1 block w-full rounded-md border border-gray-300 px-3 py-2 shadow-sm placeholder-gray-400 focus:border-red-600 focus:ring focus:ring-red-300 focus:ring-opacity-50" id="register-email" name="register-email" placeholder="Masukkan email" required="" type="email"/>
      </div>
      <div>
       <label class="block text-sm font-medium text-gray-700" for="register-password">
        Password
       </label>
       <input autocomplete="new-password" class="mt-1 block w-full rounded-md border border-gray-300 px-3 py-2 shadow-sm placeholder-gray-400 focus:border-red-600 focus:ring focus:ring-red-300 focus:ring-opacity-50" id="register-password" name="register-password" placeholder="Buat password" required="" type="password"/>
      </div>
      <div>
       <label class="block text-sm font-medium text-gray-700" for="register-role">
        Daftar sebagai
       </label>
       <select class="mt-1 block w-full rounded-md border border-gray-300 px-3 py-2 shadow-sm focus:border-red-600 focus:ring focus:ring-red-300 focus:ring-opacity-50" id="register-role" name="register-role" required="">
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
      <button class="w-full bg-red-700 hover:bg-red-800 text-white font-semibold py-2 rounded-md transition" type="submit">
       Daftar
      </button>
     </form>
    </section>
    <!-- DASHBOARD SECTION -->
    <section aria-label="Dashboard section" class="hidden max-w-7xl mx-auto flex flex-col" id="dashboard-section">
     <!-- Dashboard Header -->
     <nav aria-label="Dashboard navigation" class="flex items-center justify-between bg-red-700 text-white rounded-t-xl px-6 py-3 shadow-md" id="dashboard-nav" role="navigation">
      <div class="flex items-center space-x-4">
       <img alt="Logo persegi panjang ArrhythME-AI milik pengguna" class="w-28 h-12 rounded-md object-contain" height="120" src="LOGO.png" width="280"/>
       <h2 class="text-xl font-bold" id="dashboard-title">
        Dashboard
       </h2>
      </div>
      <div class="flex items-center space-x-4">
       <button class="flex items-center space-x-2 bg-white text-red-700 font-semibold px-3 py-1 rounded-md hover:bg-red-100 transition" id="dashboard-logout-btn" type="button">
        <i class="fas fa-sign-out-alt">
        </i>
        <span>
         Logout
        </span>
       </button>
      </div>
     </nav>
     <!-- Dashboard Content -->
     <div class="bg-white rounded-b-xl shadow-lg p-6 grid grid-cols-1 md:grid-cols-5 gap-6 min-h-[700px]" id="dashboard-content">
      <!-- Sidebar -->
      <aside aria-label="Dashboard sidebar" class="col-span-1 bg-red-50 rounded-lg p-4 flex flex-col space-y-4" id="dashboard-sidebar">
       <div class="flex flex-col items-center space-y-3 mb-6">
        <img alt="Foto profil pengguna" class="w-24 h-24 rounded-full border-4 border-red-700 object-cover" height="96" id="profile-photo" src="https://storage.googleapis.com/a1aa/image/d3f40b0f-ff43-4f76-9d11-41fe69c8c4ae.jpg" width="96"/>
        <h3 class="text-lg font-semibold text-red-700 text-center break-words" id="profile-name">
         Nama Pengguna
        </h3>
        <p class="text-sm text-red-600 font-medium uppercase tracking-wide" id="profile-role">
         Role
        </p>
       </div>
       <nav aria-label="Dashboard main navigation" class="flex flex-col space-y-3 text-red-700 font-semibold">
        <button class="dashboard-nav-btn flex items-center space-x-3 px-3 py-2 rounded-md hover:bg-red-100 transition" data-target="dashboard-welcome" type="button">
         <i class="fas fa-home fa-lg">
         </i>
         <span>
          Dashboard
         </span>
        </button>
        <button class="dashboard-nav-btn flex items-center space-x-3 px-3 py-2 rounded-md hover:bg-red-100 transition" data-target="profile-section" type="button">
         <i class="fas fa-user-circle fa-lg">
         </i>
         <span>
          Profil
         </span>
        </button>
        <button class="dashboard-nav-btn flex items-center space-x-3 px-3 py-2 rounded-md hover:bg-red-100 transition" data-target="heart-section" type="button">
         <i class="fas fa-heartbeat fa-lg">
         </i>
         <span>
          Heart Monitor
         </span>
        </button>
        <button class="dashboard-nav-btn flex items-center space-x-3 px-3 py-2 rounded-md hover:bg-red-100 transition" data-target="chat-section" type="button">
         <i class="fas fa-comments fa-lg">
         </i>
         <span>
          Live Chat
         </span>
        </button>
        <button class="dashboard-nav-btn flex items-center space-x-3 px-3 py-2 rounded-md hover:bg-red-100 transition" data-target="education-section" type="button">
         <i class="fas fa-book-medical fa-lg"></i>
         <span>
          Edukasi
         </span>
        </button>
        <button class="dashboard-nav-btn flex items-center space-x-3 px-3 py-2 rounded-md hover:bg-red-100 transition hidden" data-target="patients-section" id="sidebar-patients-btn" type="button">
         <i class="fas fa-users fa-lg">
         </i>
         <span>
          Pasien
         </span>
        </button>
        <button class="dashboard-nav-btn flex items-center space-x-3 px-3 py-2 rounded-md hover:bg-red-100 transition hidden" data-target="notifications-section" id="sidebar-notifications-btn" type="button">
         <i class="fas fa-bell fa-lg">
         </i>
         <span>
          Notifikasi
         </span>
        </button>
       </nav>
      </aside>
      <!-- Main Content -->
      <section class="col-span-4 bg-red-50 rounded-lg p-6 overflow-auto max-h-[700px] flex flex-col" id="dashboard-main">
       <!-- Welcome Dashboard (for patient and doctor) -->
       <section aria-label="Welcome dashboard" class="hidden space-y-6" id="dashboard-welcome">
        <h3 class="text-3xl font-bold text-red-700 mb-2" id="welcome-title">
         Selamat datang
        </h3>
        <p class="text-lg text-gray-700 flex items-center space-x-3">
         <i class="fas fa-heartbeat text-red-700 text-2xl">
         </i>
         <span id="welcome-message">
          Ada yang bisa saya bantu?
         </span>
        </p>
        <div id="patient-notifications" class="hidden bg-white border border-red-300 rounded-md p-4 shadow space-y-3 max-w-md">
         <h4 class="text-xl font-semibold text-red-700 flex items-center space-x-2">
          <i class="fas fa-bell"></i>
          <span>Notifikasi</span>
         </h4>
         <ul id="patient-notifications-list" class="list-disc list-inside text-gray-700 max-h-48 overflow-y-auto" role="list">
          <li>Belum ada notifikasi.</li>
         </ul>
        </div>
       </section>
       <!-- Profile Section -->
       <section aria-label="Profile section" class="hidden space-y-6 overflow-y-auto" id="profile-section">
        <h3 class="text-2xl font-bold text-red-700 mb-4 flex items-center space-x-3">
         <i class="fas fa-user-circle">
         </i>
         <span>
          Profil Saya
         </span>
        </h3>
        <!-- Patient Profile Form -->
        <form class="space-y-4 max-w-3xl" id="profile-form" novalidate="">
         <div class="flex flex-col md:flex-row md:space-x-6">
          <div class="flex-shrink-0 mb-4 md:mb-0">
           <img alt="Foto profil pengguna" class="w-32 h-32 rounded-full border-4 border-red-700 object-cover" height="128" id="profile-photo-form" src="https://storage.googleapis.com/a1aa/image/d3f40b0f-ff43-4f76-9d11-41fe69c8c4ae.jpg" width="128"/>
          </div>
          <div class="flex-grow grid grid-cols-1 md:grid-cols-2 gap-6">
           <div>
            <label class="block font-semibold text-red-700 mb-1" for="profile-fullname">
             Nama Lengkap
            </label>
            <input autocomplete="name" class="w-full rounded-md border border-red-300 px-3 py-2 focus:outline-none focus:ring-2 focus:ring-red-400" id="profile-fullname" name="profile-fullname" placeholder="Masukkan nama lengkap" required="" type="text"/>
           </div>
           <div>
            <label class="block font-semibold text-red-700 mb-1" for="profile-email">
             Email
            </label>
            <input autocomplete="email" class="w-full rounded-md border border-red-300 px-3 py-2 focus:outline-none focus:ring-2 focus:ring-red-400" id="profile-email" name="profile-email" placeholder="Masukkan email" required="" type="email"/>
           </div>
           <div>
            <label class="block font-semibold text-red-700 mb-1" for="profile-phone">
             Nomor Telepon
            </label>
            <input autocomplete="tel" class="w-full rounded-md border border-red-300 px-3 py-2 focus:outline-none focus:ring-2 focus:ring-red-400" id="profile-phone" name="profile-phone" pattern="[0-9+ ]{6,20}" placeholder="Masukkan nomor telepon" type="tel"/>
           </div>
           <div>
            <label class="block font-semibold text-red-700 mb-1" for="profile-address">
             Alamat
            </label>
            <textarea class="w-full rounded-md border border-red-300 px-3 py-2 focus:outline-none focus:ring-2 focus:ring-red-400" id="profile-address" name="profile-address" placeholder="Masukkan alamat lengkap" rows="2"></textarea>
           </div>
           <div>
            <label class="block font-semibold text-red-700 mb-1" for="profile-birthplace">
             Tempat Lahir
            </label>
            <input class="w-full rounded-md border border-red-300 px-3 py-2 focus:outline-none focus:ring-2 focus:ring-red-400" id="profile-birthplace" name="profile-birthplace" placeholder="Masukkan tempat lahir" type="text"/>
           </div>
           <div>
            <label class="block font-semibold text-red-700 mb-1" for="profile-birthdate">
             Tanggal Lahir
            </label>
            <input class="w-full rounded-md border border-red-300 px-3 py-2 focus:outline-none focus:ring-2 focus:ring-red-400" id="profile-birthdate" name="profile-birthdate" type="date"/>
           </div>
           <div>
            <label class="block font-semibold text-red-700 mb-1" for="profile-age">
             Usia
            </label>
            <input class="w-full rounded-md border border-red-300 px-3 py-2 bg-red-100 cursor-not-allowed" id="profile-age" name="profile-age" placeholder="Usia otomatis" readonly="" type="number"/>
           </div>
           <div>
            <label class="block font-semibold text-red-700 mb-1" for="profile-height">
             Tinggi Badan (cm)
            </label>
            <input class="w-full rounded-md border border-red-300 px-3 py-2 focus:outline-none focus:ring-2 focus:ring-red-400" id="profile-height" min="1" name="profile-height" placeholder="Masukkan tinggi badan" step="0.1" type="number"/>
           </div>
           <div>
            <label class="block font-semibold text-red-700 mb-1" for="profile-weight">
             Berat Badan (kg)
            </label>
            <input class="w-full rounded-md border border-red-300 px-3 py-2 focus:outline-none focus:ring-2 focus:ring-red-400" id="profile-weight" min="1" name="profile-weight" placeholder="Masukkan berat badan" step="0.1" type="number"/>
           </div>
           <div>
            <label class="block font-semibold text-red-700 mb-1" for="profile-bmi">
             BMI
            </label>
            <input class="w-full rounded-md border border-red-300 px-3 py-2 bg-red-100 cursor-not-allowed" id="profile-bmi" name="profile-bmi" placeholder="BMI otomatis" readonly="" type="text"/>
           </div>
           <div class="md:col-span-2">
            <label class="block font-semibold text-red-700 mb-1" for="profile-medical-history">
             Riwayat Penyakit
            </label>
            <textarea class="w-full rounded-md border border-red-300 px-3 py-2 focus:outline-none focus:ring-2 focus:ring-red-400" id="profile-medical-history" name="profile-medical-history" placeholder="Masukkan riwayat penyakit jika ada" rows="3"></textarea>
           </div>
          </div>
         </div>
         <div class="flex justify-end">
          <button class="bg-red-700 hover:bg-red-800 text-white font-semibold px-6 py-2 rounded-md transition" type="submit">
           Simpan Profil
          </button>
         </div>
        </form>
        <!-- Doctor Profile Form -->
        <form class="space-y-4 max-w-3xl hidden" id="profile-form-doctor" novalidate="">
         <div class="flex flex-col md:flex-row md:space-x-6">
          <div class="flex-shrink-0 mb-4 md:mb-0">
           <img alt="Foto profil dokter" class="w-32 h-32 rounded-full border-4 border-red-700 object-cover" height="128" id="profile-photo-form-doctor" src="https://storage.googleapis.com/a1aa/image/370a4b63-6026-49df-aeac-f785dd9e9bb4.jpg" width="128"/>
          </div>
          <div class="flex-grow grid grid-cols-1 md:grid-cols-2 gap-6">
           <div>
            <label class="block font-semibold text-red-700 mb-1" for="doctor-fullname">
             Nama Lengkap
            </label>
            <input autocomplete="name" class="w-full rounded-md border border-red-300 px-3 py-2 focus:outline-none focus:ring-2 focus:ring-red-400" id="doctor-fullname" name="doctor-fullname" placeholder="Masukkan nama lengkap" required="" type="text"/>
           </div>
           <div>
            <label class="block font-semibold text-red-700 mb-1" for="doctor-specialist">
             Spesialis
            </label>
            <input class="w-full rounded-md border border-red-300 px-3 py-2 focus:outline-none focus:ring-2 focus:ring-red-400" id="doctor-specialist" name="doctor-specialist" placeholder="Masukkan spesialisasi" required="" type="text"/>
           </div>
           <div>
            <label class="block font-semibold text-red-700 mb-1" for="doctor-phone">
             Nomor Telepon
            </label>
            <input autocomplete="tel" class="w-full rounded-md border border-red-300 px-3 py-2 focus:outline-none focus:ring-2 focus:ring-red-400" id="doctor-phone" name="doctor-phone" pattern="[0-9+ ]{6,20}" placeholder="Masukkan nomor telepon" type="tel"/>
           </div>
           <div>
            <label class="block font-semibold text-red-700 mb-1" for="doctor-email">
             Email
            </label>
            <input autocomplete="email" class="w-full rounded-md border border-red-300 px-3 py-2 focus:outline-none focus:ring-2 focus:ring-red-400" id="doctor-email" name="doctor-email" placeholder="Masukkan email" required="" type="email"/>
           </div>
           <div class="md:col-span-2">
            <label class="block font-semibold text-red-700 mb-1" for="doctor-address">
             Alamat Praktik
            </label>
            <textarea class="w-full rounded-md border border-red-300 px-3 py-2 focus:outline-none focus:ring-2 focus:ring-red-400" id="doctor-address" name="doctor-address" placeholder="Masukkan alamat praktik" rows="2"></textarea>
           </div>
          </div>
         </div>
         <div class="flex justify-end">
          <button class="bg-red-700 hover:bg-red-800 text-white font-semibold px-6 py-2 rounded-md transition" type="submit">
           Simpan Profil
          </button>
         </div>
        </form>
       </section>
       <!-- Heart Monitor Section -->
       <section aria-label="Heart monitor section" class="hidden space-y-6 max-w-3xl" id="heart-section">
        <h3 class="text-2xl font-bold text-red-700 mb-4 flex items-center space-x-3">
         <i class="fas fa-heartbeat">
         </i>
         <span>
          Heart Monitor
         </span>
        </h3>
        <div class="bg-white rounded-lg shadow p-6 border border-red-300 flex flex-col space-y-4">
         <p class="text-gray-700">
          Tekan tombol
          <span class="font-semibold">
           Mulai
          </span>
          untuk memulai pengambilan sinyal ECG selama 30 detik.
         </p>
         <button class="bg-red-700 hover:bg-red-800 text-white font-semibold px-6 py-2 rounded-md transition flex items-center space-x-2 self-start" id="start-ecg-btn" type="button">
          <i class="fas fa-play">
          </i>
          <span>
           Mulai
          </span>
         </button>
         <div aria-live="polite" class="mt-6 space-y-3 hidden" id="ecg-result">
          <div class="flex flex-wrap gap-6">
           <div class="flex items-center space-x-2 bg-red-50 rounded-md p-4 shadow w-full sm:w-auto">
            <i class="fas fa-tachometer-alt fa-3x text-red-700">
            </i>
            <div>
             <p class="text-sm text-gray-600">
              BPM (Detak Jantung)
             </p>
             <p aria-label="BPM value" class="text-4xl font-bold text-red-700" id="bpm-value">
              --
             </p>
            </div>
           </div>
           <div class="flex items-center space-x-2 bg-red-50 rounded-md p-4 shadow w-full sm:w-auto">
            <i class="fas fa-info-circle fa-3x text-red-700">
            </i>
            <div>
             <p class="text-sm text-gray-600">
              Kategori
             </p>
             <p aria-label="BPM category" class="text-2xl font-semibold text-red-700" id="bpm-category">
              --
             </p>
            </div>
           </div>
          </div>
          <div>
           <h4 class="font-semibold text-red-700 mb-2">
            Riwayat Deteksi Sebelumnya
           </h4>
           <ul aria-label="Riwayat deteksi ECG" class="max-h-48 overflow-y-auto border border-red-300 rounded-md p-3 space-y-2 bg-white" id="ecg-history-list">
            <li class="text-gray-500 text-sm">
             Belum ada riwayat deteksi.
            </li>
           </ul>
          </div>
         </div>
        </div>
       </section>
       <!-- Live Chat Section -->
       <section aria-label="Live chat section" class="hidden max-w-5xl flex flex-col h-full" id="chat-section">
        <h3 class="text-2xl font-bold text-red-700 mb-4 flex items-center space-x-3">
         <i class="fas fa-comments">
         </i>
         <span>
          Live Chat
         </span>
        </h3>
        <div class="flex flex-col md:flex-row h-[500px] bg-white rounded-lg shadow border border-red-300 overflow-hidden">
         <!-- User List -->
         <aside aria-label="Daftar pengguna chat" class="w-full md:w-1/3 border-r border-red-300 overflow-y-auto" id="chat-user-list">
          <div class="p-4 border-b border-red-300 bg-red-50 font-semibold text-red-700">
           Daftar Chat
          </div>
          <ul class="divide-y divide-red-200" id="chat-users" role="list">
          </ul>
         </aside>
         <!-- Chat Window -->
         <section aria-label="Jendela chat" class="flex flex-col w-full md:w-2/3" hidden="" id="chat-window">
          <header class="flex items-center justify-between bg-red-700 text-white p-4" id="chat-header">
           <div class="flex items-center space-x-3">
            <img alt="Foto profil lawan chat" class="w-12 h-12 rounded-full object-cover border-2 border-white" height="48" id="chat-header-photo" src="https://storage.googleapis.com/a1aa/image/f43711ba-65ed-4443-3d46-8dd36289b122.jpg" width="48"/>
            <div>
             <h4 class="font-semibold text-lg" id="chat-header-name">
              Nama Lawan Chat
             </h4>
             <p class="text-sm opacity-80" id="chat-header-role">
              Role
             </p>
            </div>
           </div>
           <button aria-label="Tutup chat" class="text-white hover:text-red-300 focus:outline-none" id="chat-close-btn" title="Tutup Chat" type="button">
            <i class="fas fa-times fa-lg">
            </i>
           </button>
          </header>
          <div aria-live="polite" aria-relevant="additions" class="flex-grow p-4 overflow-y-auto space-y-4 bg-red-50" id="chat-messages" role="log">
          </div>
          <form aria-label="Form kirim pesan" autocomplete="off" class="flex border-t border-red-300 p-3 bg-white" id="chat-form" novalidate="">
           <input aria-required="true" class="flex-grow rounded-l-md border border-red-300 px-4 py-2 focus:outline-none focus:ring-2 focus:ring-red-400" id="chat-input" placeholder="Ketik pesan..." required="" type="text"/>
           <button aria-label="Kirim pesan" class="bg-red-700 hover:bg-red-800 text-white px-5 py-2 rounded-r-md transition" type="submit">
            <i class="fas fa-paper-plane">
            </i>
           </button>
          </form>
         </section>
        </div>
       </section>
       <!-- Patients Section (Doctor only) -->
       <section aria-label="Daftar pasien" class="hidden max-w-5xl space-y-6 overflow-auto" id="patients-section">
        <h3 class="text-2xl font-bold text-red-700 mb-4 flex items-center space-x-3">
         <i class="fas fa-users">
         </i>
         <span>
          Daftar Pasien
         </span>
        </h3>
        <div class="overflow-x-auto bg-white rounded-lg shadow border border-red-300">
         <table aria-label="Tabel pasien" class="min-w-full divide-y divide-red-200" role="table">
          <thead class="bg-red-700 text-white">
           <tr>
            <th class="px-6 py-3 text-left text-sm font-semibold" scope="col">
             Nama Lengkap
            </th>
            <th class="px-6 py-3 text-left text-sm font-semibold" scope="col">
             Email
            </th>
            <th class="px-6 py-3 text-left text-sm font-semibold" scope="col">
             Nomor Telepon
            </th>
            <th class="px-6 py-3 text-left text-sm font-semibold" scope="col">
             Jenis Kelamin
            </th>
            <th class="px-6 py-3 text-left text-sm font-semibold" scope="col">
             Usia
            </th>
            <th class="px-6 py-3 text-left text-sm font-semibold" scope="col">
             BMI
            </th>
            <th class="px-6 py-3 text-left text-sm font-semibold" scope="col">
             Riwayat Penyakit
            </th>
            <th class="px-6 py-3 text-left text-sm font-semibold" scope="col">
             Alamat
            </th>
            <th class="px-6 py-3 text-left text-sm font-semibold" scope="col">
             Status Aritmia
            </th>
            <th class="px-6 py-3 text-center text-sm font-semibold" scope="col">
             Aksi
            </th>
           </tr>
          </thead>
          <tbody class="divide-y divide-red-200 bg-white" id="patients-table-body" role="rowgroup">
          </tbody>
         </table>
        </div>
       </section>
       <!-- Notifications Section (Doctor only) -->
       <section aria-label="Notifikasi" class="hidden max-w-5xl space-y-6 overflow-auto" id="notifications-section">
        <h3 class="text-2xl font-bold text-red-700 mb-4 flex items-center space-x-3">
         <i class="fas fa-bell">
         </i>
         <span>
          Notifikasi
         </span>
        </h3>
        <div aria-live="polite" class="bg-white rounded-lg shadow border border-red-300 max-h-[500px] overflow-y-auto p-4" id="notifications-list" role="list">
         <p class="text-gray-500 text-center">
          Belum ada notifikasi.
         </p>
        </div>
       </section>
       <!-- Education Section -->
       <section aria-label="Edukasi" class="hidden max-w-4xl space-y-6" id="education-section">
        <h3 class="text-2xl font-bold text-red-700 mb-4 flex items-center space-x-3">
         <i class="fas fa-book-medical">
         </i>
         <span>
          Edukasi
         </span>
        </h3>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
         <article class="bg-white rounded-lg shadow p-4 border border-red-300 hover:shadow-lg transition cursor-pointer">
          <img alt="Ilustrasi anatomi jantung manusia dengan warna merah dan putih" class="rounded-md mb-3 object-cover w-full h-40" height="200" src="https://storage.googleapis.com/a1aa/image/f2b21616-5504-40ed-69b9-5445e7c8ee04.jpg" width="400"/>
          <h4 class="text-lg font-semibold text-red-700 mb-1">
           Anatomi Jantung
          </h4>
          <p class="text-gray-700 text-sm mb-2">
           Pelajari struktur dan fungsi jantung manusia secara mendalam.
          </p>
          <a href="https://www.heart.org/en/health-topics/heart-attack/about-heart-attacks/anatomy-of-the-heart" target="_blank" rel="noopener noreferrer" class="text-red-700 font-semibold hover:underline inline-flex items-center space-x-1">
           <span>Baca Selengkapnya</span>
           <i class="fas fa-external-link-alt text-sm"></i>
          </a>
         </article>
         <article class="bg-white rounded-lg shadow p-4 border border-red-300 hover:shadow-lg transition cursor-pointer">
          <img alt="Ilustrasi gelombang ECG dengan tanda aritmia berwarna merah" class="rounded-md mb-3 object-cover w-full h-40" height="200" src="https://storage.googleapis.com/a1aa/image/bcc24551-f469-463f-78f6-b619177b1800.jpg" width="400"/>
          <h4 class="text-lg font-semibold text-red-700 mb-1">
           Mengenal Aritmia
          </h4>
          <p class="text-gray-700 text-sm mb-2">
           Informasi tentang jenis-jenis aritmia dan dampaknya pada kesehatan.
          </p>
          <a href="https://www.heart.org/en/health-topics/arrhythmia/about-arrhythmia" target="_blank" rel="noopener noreferrer" class="text-red-700 font-semibold hover:underline inline-flex items-center space-x-1">
           <span>Baca Selengkapnya</span>
           <i class="fas fa-external-link-alt text-sm"></i>
          </a>
         </article>
         <article class="bg-white rounded-lg shadow p-4 border border-red-300 hover:shadow-lg transition cursor-pointer">
          <img alt="Ilustrasi makanan sehat berwarna merah dan putih di atas meja kayu" class="rounded-md mb-3 object-cover w-full h-40" height="200" src="https://storage.googleapis.com/a1aa/image/b8380a0c-09d6-49c7-740c-cab9c4168c3a.jpg" width="400"/>
          <h4 class="text-lg font-semibold text-red-700 mb-1">
           Pola Makan Sehat
          </h4>
          <p class="text-gray-700 text-sm mb-2">
           Tips dan panduan pola makan yang baik untuk kesehatan jantung.
          </p>
          <a href="https://www.heart.org/en/healthy-living/healthy-eating/eat-smart/nutrition-basics/healthy-eating-for-a-healthy-heart" target="_blank" rel="noopener noreferrer" class="text-red-700 font-semibold hover:underline inline-flex items-center space-x-1">
           <span>Baca Selengkapnya</span>
           <i class="fas fa-external-link-alt text-sm"></i>
          </a>
         </article>
         <article class="bg-white rounded-lg shadow p-4 border border-red-300 hover:shadow-lg transition cursor-pointer">
          <img alt="Ilustrasi orang berolahraga dan gaya hidup sehat dengan latar belakang merah putih" class="rounded-md mb-3 object-cover w-full h-40" height="200" src="https://storage.googleapis.com/a1aa/image/2d0e9a98-92b1-4da4-3670-e9c4b73bd49a.jpg" width="400"/>
          <h4 class="text-lg font-semibold text-red-700 mb-1">
           Gaya Hidup Sehat
          </h4>
          <p class="text-gray-700 text-sm mb-2">
           Cara menjaga pola hidup sehat untuk mencegah penyakit jantung.
          </p>
          <a href="https://www.heart.org/en/healthy-living/fitness/fitness-basics/physical-activity-improves-quality-of-life" target="_blank" rel="noopener noreferrer" class="text-red-700 font-semibold hover:underline inline-flex items-center space-x-1">
           <span>Baca Selengkapnya</span>
           <i class="fas fa-external-link-alt text-sm"></i>
          </a>
         </article>
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
    const authSection = document.getElementById("auth-section");
    const dashboardSection = document.getElementById("dashboard-section");
    const tabLogin = document.getElementById("tab-login");
    const tabRegister = document.getElementById("tab-register");
    const loginForm = document.getElementById("login-form");
    const registerForm = document.getElementById("register-form");
    const navLoginBtn = document.getElementById("nav-login-btn");
    const navRegisterBtn = document.getElementById("nav-register-btn");
    const dashboardLogoutBtn = document.getElementById("dashboard-logout-btn");
    const dashboardTitle = document.getElementById("dashboard-title");
    const profileName = document.getElementById("profile-name");
    const profileRole = document.getElementById("profile-role");
    const profilePhoto = document.getElementById("profile-photo");
    const dashboardNavBtns = document.querySelectorAll(".dashboard-nav-btn");
    const dashboardMain = document.getElementById("dashboard-main");
    const welcomeTitle = document.getElementById("welcome-title");
    const welcomeMessage = document.getElementById("welcome-message");

    // Sections
    const dashboardWelcome = document.getElementById("dashboard-welcome");
    const profileSection = document.getElementById("profile-section");
    const heartSection = document.getElementById("heart-section");
    const chatSection = document.getElementById("chat-section");
    const patientsSection = document.getElementById("patients-section");
    const notificationsSection = document.getElementById("notifications-section");
    const educationSection = document.getElementById("education-section");
    const sidebarPatientsBtn = document.getElementById("sidebar-patients-btn");
    const sidebarNotificationsBtn = document.getElementById("sidebar-notifications-btn");

    // Profile forms
    const profileFormPatient = document.getElementById("profile-form");
    const profilePhotoFormPatient = document.getElementById("profile-photo-form");
    const inputFullname = document.getElementById("profile-fullname");
    const inputEmail = document.getElementById("profile-email");
    const inputPhone = document.getElementById("profile-phone");
    const inputAddress = document.getElementById("profile-address");
    const inputBirthplace = document.getElementById("profile-birthplace");
    const inputBirthdate = document.getElementById("profile-birthdate");
    const inputAge = document.getElementById("profile-age");
    const inputWeight = document.getElementById("profile-weight");
    const inputHeight = document.getElementById("profile-height");
    const inputBMI = document.getElementById("profile-bmi");
    const inputMedicalHistory = document.getElementById("profile-medical-history");

    const profileFormDoctor = document.getElementById("profile-form-doctor");
    const profilePhotoFormDoctor = document.getElementById("profile-photo-form-doctor");
    const inputDoctorFullname = document.getElementById("doctor-fullname");
    const inputDoctorSpecialist = document.getElementById("doctor-specialist");
    const inputDoctorPhone = document.getElementById("doctor-phone");
    const inputDoctorEmail = document.getElementById("doctor-email");
    const inputDoctorAddress = document.getElementById("doctor-address");

    // Heart monitor elements
    const startEcgBtn = document.getElementById("start-ecg-btn");
    const ecgResult = document.getElementById("ecg-result");
    const bpmValue = document.getElementById("bpm-value");
    const bpmCategory = document.getElementById("bpm-category");
    const ecgHistoryList = document.getElementById("ecg-history-list");

    // Chat elements
    const chatUserList = document.getElementById("chat-users");
    const chatWindow = document.getElementById("chat-window");
    const chatHeaderName = document.getElementById("chat-header-name");
    const chatHeaderRole = document.getElementById("chat-header-role");
    const chatHeaderPhoto = document.getElementById("chat-header-photo");
    const chatMessages = document.getElementById("chat-messages");
    const chatForm = document.getElementById("chat-form");
    const chatInput = document.getElementById("chat-input");
    const chatCloseBtn = document.getElementById("chat-close-btn");

    // Patients table body (doctor)
    const patientsTableBody = document.getElementById("patients-table-body");

    // Notifications list (doctor)
    const notificationsList = document.getElementById("notifications-list");

    // Notifications list (patient)
    const patientNotifications = document.getElementById("patient-notifications");
    const patientNotificationsList = document.getElementById("patient-notifications-list");

    // State
    let currentUser = null;
    let currentUserData = null;
    let currentRole = null; // 'patient' or 'doctor'
    let currentChatUser = null; // userId of chat partner
    let chatUnsub = null;
    let ecgUnsub = null;
    let notificationsUnsub = null;
    let patientNotificationsUnsub = null;

    // Utility Functions
    function showSection(section) {
      // Hide all dashboard sections
      [
        dashboardWelcome,
        profileSection,
        heartSection,
        chatSection,
        patientsSection,
        notificationsSection,
        educationSection,
      ].forEach((s) => s.classList.add("hidden"));
      section.classList.remove("hidden");
    }

    function clearChatWindow() {
      chatMessages.innerHTML = "";
      chatHeaderName.textContent = "";
      chatHeaderRole.textContent = "";
      chatHeaderPhoto.src = "https://placehold.co/48x48/png?text=User";
      currentChatUser = null;
      if (chatUnsub) {
        chatUnsub();
        chatUnsub = null;
      }
      chatWindow.hidden = true;
    }

    function formatDateTime(timestamp) {
      const d = timestamp.toDate ? timestamp.toDate() : new Date(timestamp);
      return d.toLocaleString("id-ID", {
        year: "numeric",
        month: "short",
        day: "numeric",
        hour: "2-digit",
        minute: "2-digit",
      });
    }

    function calculateAge(birthdate) {
      if (!birthdate) return "";
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
      if (!weight || !height) return "";
      const heightM = height / 100;
      const bmi = weight / (heightM * heightM);
      return bmi.toFixed(1);
    }

    function categorizeBPM(bpm) {
      if (bpm < 60) return "Bradikardia";
      if (bpm <= 100) return "Normal";
      return "Takikardia";
    }

    // Authentication UI toggles
    function showLogin() {
      tabLogin.classList.add("border-red-700", "text-red-700");
      tabLogin.classList.remove("text-gray-500");
      tabRegister.classList.remove("border-red-700", "text-red-700");
      tabRegister.classList.add("text-gray-500");
      loginForm.classList.remove("hidden");
      registerForm.classList.add("hidden");
    }
    function showRegister() {
      tabRegister.classList.add("border-red-700", "text-red-700");
      tabRegister.classList.remove("text-gray-500");
      tabLogin.classList.remove("border-red-700", "text-red-700");
      tabLogin.classList.add("text-gray-500");
      registerForm.classList.remove("hidden");
      loginForm.classList.add("hidden");
    }

    // Navigation handlers
    tabLogin.addEventListener("click", () => {
      showLogin();
    });
    tabRegister.addEventListener("click", () => {
      showRegister();
    });
    navLoginBtn.addEventListener("click", () => {
      authSection.classList.remove("hidden");
      dashboardSection.classList.add("hidden");
      showLogin();
    });
    navRegisterBtn.addEventListener("click", () => {
      authSection.classList.remove("hidden");
      dashboardSection.classList.add("hidden");
      showRegister();
    });

    // Dashboard navigation buttons
    dashboardNavBtns.forEach((btn) => {
      btn.addEventListener("click", () => {
        const target = btn.getAttribute("data-target");
        if (!target) return;
        if (target === "patients-section" && currentRole !== "doctor") return;
        if (target === "notifications-section" && currentRole !== "doctor") return;
        showSection(document.getElementById(target));
      });
    });

    // Logout
    dashboardLogoutBtn.addEventListener("click", () => {
      auth.signOut();
    });

    // Register form submit
    registerForm.addEventListener("submit", async (e) => {
      e.preventDefault();
      const fullname = registerForm["register-fullname"].value.trim();
      const username = registerForm["register-username"].value.trim();
      const email = registerForm["register-email"].value.trim();
      const password = registerForm["register-password"].value;
      const role = registerForm["register-role"].value;

      if (!fullname || !username || !email || !password || !role) {
        alert("Mohon lengkapi semua data pendaftaran.");
        return;
      }

      try {
        // Check if username already exists
        const usernameQuery = await db
          .collection("users")
          .where("username", "==", username)
          .get();
        if (!usernameQuery.empty) {
          alert("Username sudah digunakan, silakan pilih yang lain.");
          return;
        }

        // Create user with email and password
        const userCredential = await auth.createUserWithEmailAndPassword(
          email,
          password
        );
        const user = userCredential.user;

        // Save user profile in Firestore
        await db.collection("users").doc(user.uid).set({
          fullname,
          username,
          email,
          role,
          createdAt: firebase.firestore.FieldValue.serverTimestamp(),
          profilePhotoURL: "",
          phone: "",
          gender: "",
          birthplace: "",
          birthdate: "",
          age: "",
          weight: "",
          height: "",
          bmi: "",
          medicalHistory: "",
          address: "",
          ecgHistory: [],
          chatWith: [],
          specialist: "",
          practiceAddress: "",
        });

        alert("Pendaftaran berhasil! Silakan login.");
        registerForm.reset();
        showLogin();
      } catch (error) {
        alert("Gagal mendaftar: " + error.message);
      }
    });

    // Login form submit
    loginForm.addEventListener("submit", async (e) => {
      e.preventDefault();
      const usernameOrEmail = loginForm["login-username-email"].value.trim();
      const password = loginForm["login-password"].value;

      if (!usernameOrEmail || !password) {
        alert("Mohon isi username/email dan password.");
        return;
      }

      try {
        // Try login by email first
        let userCredential;
        try {
          userCredential = await auth.signInWithEmailAndPassword(
            usernameOrEmail,
            password
          );
        } catch (err) {
          // If failed, try to find email by username
          const userQuery = await db
            .collection("users")
            .where("username", "==", usernameOrEmail)
            .get();
          if (userQuery.empty) throw new Error("User tidak ditemukan");
          const userData = userQuery.docs[0].data();
          userCredential = await auth.signInWithEmailAndPassword(
            userData.email,
            password
          );
        }

        currentUser = userCredential.user;
        await loadUserData();
        authSection.classList.add("hidden");
        dashboardSection.classList.remove("hidden");
        showSection(dashboardWelcome);
        dashboardTitle.textContent = `Dashboard ${
          currentRole === "doctor" ? "Dokter" : "Pasien"
        }`;
        if (currentRole === "doctor") {
          sidebarPatientsBtn.classList.remove("hidden");
          sidebarNotificationsBtn.classList.remove("hidden");
        } else {
          sidebarPatientsBtn.classList.add("hidden");
          sidebarNotificationsBtn.classList.add("hidden");
        }
      } catch (error) {
        alert("Gagal login: " + error.message);
      }
    });

    // Load user data from Firestore
    async function loadUserData() {
      if (!currentUser) return;
      const doc = await db.collection("users").doc(currentUser.uid).get();
      if (!doc.exists) {
        alert("Data pengguna tidak ditemukan.");
        return;
      }
      currentUserData = doc.data();
      currentRole = currentUserData.role;

      // Update sidebar profile info
      profileName.textContent = currentUserData.fullname || "Nama Pengguna";
      profileRole.textContent = currentRole === "doctor" ? "Dokter" : "Pasien";
      profilePhoto.src =
        currentUserData.profilePhotoURL || "https://placehold.co/96x96/png?text=User+Photo";

      // Update welcome dashboard text
      if (currentRole === "patient") {
        welcomeTitle.textContent = `Halo, ${currentUserData.fullname}`;
        welcomeMessage.textContent = "Ada yang bisa saya bantu?";
      } else if (currentRole === "doctor") {
        welcomeTitle.textContent = `Selamat datang Dokter, ${currentUserData.fullname}`;
        welcomeMessage.textContent = "Silakan pantau pasien dan konsultasi.";
      }

      // Show correct profile form and fill data
      if (currentRole === "patient") {
        profileFormPatient.classList.remove("hidden");
        profileFormDoctor.classList.add("hidden");

        profilePhotoFormPatient.src =
          currentUserData.profilePhotoURL || "https://placehold.co/128x128/png?text=User+Photo";
        inputFullname.value = currentUserData.fullname || "";
        inputEmail.value = currentUserData.email || "";
        inputPhone.value = currentUserData.phone || "";
        inputAddress.value = currentUserData.address || "";
        inputBirthplace.value = currentUserData.birthplace || "";
        inputBirthdate.value = currentUserData.birthdate || "";
        inputAge.value = currentUserData.age || "";
        inputWeight.value = currentUserData.weight || "";
        inputHeight.value = currentUserData.height || "";
        inputBMI.value = currentUserData.bmi || "";
        inputMedicalHistory.value = currentUserData.medicalHistory || "";
      } else if (currentRole === "doctor") {
        profileFormPatient.classList.add("hidden");
        profileFormDoctor.classList.remove("hidden");

        profilePhotoFormDoctor.src =
          currentUserData.profilePhotoURL || "https://placehold.co/128x128/png?text=Doctor+Photo";
        inputDoctorFullname.value = currentUserData.fullname || "";
        inputDoctorSpecialist.value = currentUserData.specialist || "";
        inputDoctorPhone.value = currentUserData.phone || "";
        inputDoctorEmail.value = currentUserData.email || "";
        inputDoctorAddress.value = currentUserData.practiceAddress || "";
      }

      // Load ECG history for patient
      if (currentRole === "patient") {
        renderECGHistory(currentUserData.ecgHistory || []);
        loadPatientNotifications();
      }

      // Load patients list for doctor
      if (currentRole === "doctor") {
        loadPatientsList();
        loadNotifications();
      }

      // Load chat user list
      loadChatUserList();
    }

    // Profile form submit (patient only)
    profileFormPatient.addEventListener("submit", async (e) => {
      e.preventDefault();
      if (currentRole !== "patient") return;

      const fullname = inputFullname.value.trim();
      const email = inputEmail.value.trim();
      const phone = inputPhone.value.trim();
      const address = inputAddress.value.trim();
      const birthplace = inputBirthplace.value.trim();
      const birthdate = inputBirthdate.value;
      const age = calculateAge(birthdate);
      const weight = parseFloat(inputWeight.value);
      const height = parseFloat(inputHeight.value);
      const bmi = calculateBMI(weight, height);
      const medicalHistory = inputMedicalHistory.value.trim();

      if (!fullname || !email) {
        alert("Nama lengkap dan email wajib diisi.");
        return;
      }

      try {
        await db.collection("users").doc(currentUser.uid).update({
          fullname,
          email,
          phone,
          address,
          birthplace,
          birthdate,
          age,
          weight,
          height,
          bmi,
          medicalHistory,
        });
        inputAge.value = age;
        inputBMI.value = bmi;
        alert("Profil berhasil disimpan.");
        await loadUserData();
      } catch (error) {
        alert("Gagal menyimpan profil: " + error.message);
      }
    });

    // Profile form submit (doctor only)
    profileFormDoctor.addEventListener("submit", async (e) => {
      e.preventDefault();
      if (currentRole !== "doctor") return;

      const fullname = inputDoctorFullname.value.trim();
      const specialist = inputDoctorSpecialist.value.trim();
      const phone = inputDoctorPhone.value.trim();
      const email = inputDoctorEmail.value.trim();
      const practiceAddress = inputDoctorAddress.value.trim();

      if (!fullname || !email) {
        alert("Nama lengkap dan email wajib diisi.");
        return;
      }

      try {
        await db.collection("users").doc(currentUser.uid).update({
          fullname,
          specialist,
          phone,
          email,
          practiceAddress,
        });
        alert("Profil berhasil disimpan.");
        await loadUserData();
      } catch (error) {
        alert("Gagal menyimpan profil: " + error.message);
      }
    });

    // Update age automatically when birthdate changes
    inputBirthdate.addEventListener("change", () => {
      const age = calculateAge(inputBirthdate.value);
      inputAge.value = age;
    });

    // Update BMI automatically when weight or height changes
    function updateBMI() {
      const weight = parseFloat(inputWeight.value);
      const height = parseFloat(inputHeight.value);
      const bmi = calculateBMI(weight, height);
      inputBMI.value = bmi;
    }
    inputWeight.addEventListener("input", updateBMI);
    inputHeight.addEventListener("input", updateBMI);

    // Render ECG history list
    function renderECGHistory(history) {
      ecgHistoryList.innerHTML = "";
      if (!history.length) {
        ecgHistoryList.innerHTML =
          '<li class="text-gray-500 text-sm">Belum ada riwayat deteksi.</li>';
        return;
      }
      history
        .slice()
        .reverse()
        .forEach((item) => {
          const li = document.createElement("li");
          li.className =
            "border border-red-300 rounded-md p-2 bg-white flex justify-between items-center";
          li.innerHTML = `
            <div>
              <p class="font-semibold text-red-700">BPM: ${item.bpm}</p>
              <p class="text-sm text-gray-600">Kategori: ${item.category}</p>
              <p class="text-xs text-gray-500">${formatDateTime(item.timestamp)}</p>
            </div>
          `;
          ecgHistoryList.appendChild(li);
        });
    }

    // Simulate ECG data fetching from IoT + Firebase
    async function fetchECGData() {
      // This function should be replaced with real IoT + Firebase integration
      // For demo, generate random BPM between 50 and 120
      return new Promise((resolve) => {
        setTimeout(() => {
          const bpm = Math.floor(Math.random() * 70) + 50;
          resolve(bpm);
        }, 3000);
      });
    }

    // Start ECG monitoring
    startEcgBtn.addEventListener("click", async () => {
      startEcgBtn.disabled = true;
      startEcgBtn.innerHTML = '<i class="fas fa-spinner fa-spin"></i> Mengambil data...';
      try {
        const bpm = await fetchECGData();
        const category = categorizeBPM(bpm);
        bpmValue.textContent = bpm;
        bpmCategory.textContent = category;
        ecgResult.classList.remove("hidden");

        // Save ECG data to Firestore
        const newEcgEntry = {
          bpm,
          category,
          timestamp: firebase.firestore.FieldValue.serverTimestamp(),
        };

        // Update user's ECG history array
        await db.collection("users").doc(currentUser.uid).update({
          ecgHistory: firebase.firestore.FieldValue.arrayUnion(newEcgEntry),
        });

        // Update local data and re-render history
        const doc = await db.collection("users").doc(currentUser.uid).get();
        currentUserData = doc.data();
        renderECGHistory(currentUserData.ecgHistory || []);

        // Notify doctor if patient and abnormal BPM
        if (
          currentRole === "patient" &&
          (category === "Takikardia" || category === "Bradikardia")
        ) {
          notifyDoctorOfAritmia(currentUser.uid, bpm, category);
        }
        if (currentRole === "patient") {
          loadPatientNotifications();
        }
      } catch (error) {
        alert("Gagal mengambil data ECG: " + error.message);
      } finally {
        startEcgBtn.disabled = false;
        startEcgBtn.innerHTML = '<i class="fas fa-play"></i> Mulai';
      }
    });

    // Notify doctor about aritmia detected for a patient
    async function notifyDoctorOfAritmia(patientId, bpm, category) {
      // Find doctors monitoring this patient (for demo, notify all doctors)
      const doctorsSnapshot = await db.collection("users").where("role", "==", "doctor").get();
      const notifications = [];
      doctorsSnapshot.forEach((doc) => {
        notifications.push(
          db.collection("notifications").add({
            toUserId: doc.id,
            fromUserId: patientId,
            type: "aritmia",
            bpm,
            category,
            timestamp: firebase.firestore.FieldValue.serverTimestamp(),
            read: false,
          })
        );
      });
      await Promise.all(notifications);

      // Also notify patient (self)
      await db.collection("notifications").add({
        toUserId: patientId,
        fromUserId: patientId,
        type: "aritmia",
        bpm,
        category,
        timestamp: firebase.firestore.FieldValue.serverTimestamp(),
        read: false,
      });

      // Refresh notifications if doctor is logged in
      if (currentRole === "doctor") {
        loadNotifications();
      }
    }

    // Load patients list for doctor
    async function loadPatientsList() {
      if (currentRole !== "doctor") return;
      patientsTableBody.innerHTML =
        '<tr><td colspan="10" class="text-center py-6 text-gray-500">Memuat data pasien...</td></tr>';
      try {
        const patientsSnapshot = await db.collection("users").where("role", "==", "patient").get();
        if (patientsSnapshot.empty) {
          patientsTableBody.innerHTML =
            '<tr><td colspan="10" class="text-center py-6 text-gray-500">Belum ada pasien terdaftar.</td></tr>';
          return;
        }
        patientsTableBody.innerHTML = "";
        patientsSnapshot.forEach((doc) => {
          const p = doc.data();
          const lastEcg =
            p.ecgHistory && p.ecgHistory.length ? p.ecgHistory[p.ecgHistory.length - 1] : null;
          const statusAritmia = lastEcg ? lastEcg.category : "-";
          const tr = document.createElement("tr");
          tr.className = "hover:bg-red-50 cursor-pointer";
          tr.innerHTML = `
            <td class="px-6 py-3 text-sm text-red-700 font-semibold">${p.fullname || "-"}</td>
            <td class="px-6 py-3 text-sm">${p.email || "-"}</td>
            <td class="px-6 py-3 text-sm">${p.phone || "-"}</td>
            <td class="px-6 py-3 text-sm">${
              p.gender === "female"
                ? "Perempuan"
                : p.gender === "male"
                ? "Laki-laki"
                : "-"
            }</td>
            <td class="px-6 py-3 text-sm">${p.age || "-"}</td>
            <td class="px-6 py-3 text-sm">${p.bmi || "-"}</td>
            <td class="px-6 py-3 text-sm max-w-xs truncate" title="${p.medicalHistory || "-"}">${
            p.medicalHistory || "-"
          }</td>
            <td class="px-6 py-3 text-sm max-w-xs truncate" title="${p.address || "-"}">${
            p.address || "-"
          }</td>
            <td class="px-6 py-3 text-sm font-semibold ${
              statusAritmia === "Normal" ? "text-green-600" : "text-red-700"
            }">${statusAritmia}</td>
            <td class="px-6 py-3 text-center space-x-2">
              <button class="btn-chat-patient bg-red-700 hover:bg-red-800 text-white px-3 py-1 rounded-md transition" data-patient-id="${doc.id}" data-patient-name="${p.fullname}" type="button" aria-label="Chat dengan ${p.fullname}">
                <i class="fas fa-comments"></i> Chat
              </button>
            </td>
          `;
          patientsTableBody.appendChild(tr);
        });

        // Add chat button listeners
        document.querySelectorAll(".btn-chat-patient").forEach((btn) => {
          btn.addEventListener("click", () => {
            const patientId = btn.getAttribute("data-patient-id");
            const patientName = btn.getAttribute("data-patient-name");
            openChat(patientId, patientName, "patient");
            showSection(chatSection);
          });
        });
      } catch (error) {
        patientsTableBody.innerHTML = `<tr><td colspan="10" class="text-center py-6 text-red-700 font-semibold">Gagal memuat data pasien: ${error.message}</td></tr>`;
      }
    }

    // Load notifications for doctor
    async function loadNotifications() {
      if (currentRole !== "doctor") return;
      notificationsList.innerHTML =
        '<p class="text-gray-500 text-center py-6">Memuat notifikasi...</p>';
      try {
        if (notificationsUnsub) notificationsUnsub();
        notificationsUnsub = db
          .collection("notifications")
          .where("toUserId", "==", currentUser.uid)
          .orderBy("timestamp", "desc")
          .onSnapshot((snapshot) => {
            notificationsList.innerHTML = "";
            if (snapshot.empty) {
              notificationsList.innerHTML =
                '<p class="text-gray-500 text-center py-6">Belum ada notifikasi.</p>';
              return;
            }
            snapshot.forEach((doc) => {
              const notif = doc.data();
              const time = notif.timestamp ? formatDateTime(notif.timestamp) : "";
              const isUnread = !notif.read;
              const li = document.createElement("div");
              li.className = `border-b border-red-200 py-3 px-4 ${
                isUnread ? "bg-red-100 font-semibold" : "bg-white"
              } rounded-md mb-2`;
              let content = "";
              if (notif.type === "aritmia") {
                content = `Pasien dengan ID <strong>${notif.fromUserId}</strong> mengalami <strong>${notif.category}</strong> dengan BPM ${notif.bpm}.`;
              } else {
                content = "Notifikasi baru.";
              }
              li.innerHTML = `
                <p>${content}</p>
                <p class="text-xs text-gray-500 mt-1">${time}</p>
              `;
              notificationsList.appendChild(li);
            });
          });
      } catch (error) {
        notificationsList.innerHTML = `<p class="text-red-700 text-center py-6 font-semibold">Gagal memuat notifikasi: ${error.message}</p>`;
      }
    }

    // Load notifications for patient
    async function loadPatientNotifications() {
      if (currentRole !== "patient") return;
      patientNotificationsList.innerHTML = '<li>Memuat notifikasi...</li>';
      patientNotifications.classList.remove("hidden");
      try {
        if (patientNotificationsUnsub) patientNotificationsUnsub();
        patientNotificationsUnsub = db
          .collection("notifications")
          .where("toUserId", "==", currentUser.uid)
          .orderBy("timestamp", "desc")
          .onSnapshot((snapshot) => {
            patientNotificationsList.innerHTML = "";
            if (snapshot.empty) {
              patientNotificationsList.innerHTML = "<li>Belum ada notifikasi.</li>";
              return;
            }
            snapshot.forEach((doc) => {
              const notif = doc.data();
              const time = notif.timestamp ? formatDateTime(notif.timestamp) : "";
              let content = "";
              if (notif.type === "aritmia") {
                content = `Anda mengalami <strong>${notif.category}</strong> dengan BPM ${notif.bpm}. Harap konsultasi dengan dokter.`;
              } else {
                content = "Notifikasi baru.";
              }
              const li = document.createElement("li");
              li.className = "mb-1";
              li.innerHTML = `${content} <span class="text-xs text-gray-500">(${time})</span>`;
              patientNotificationsList.appendChild(li);
            });
          });
      } catch (error) {
        patientNotificationsList.innerHTML = `<li class="text-red-700 font-semibold">Gagal memuat notifikasi: ${error.message}</li>`;
      }
    }

    // Load chat user list (for patient: doctors, for doctor: patients)
    async function loadChatUserList() {
      chatUserList.innerHTML = "";
      try {
        let usersSnapshot;
        if (currentRole === "patient") {
          usersSnapshot = await db.collection("users").where("role", "==", "doctor").get();
        } else if (currentRole === "doctor") {
          usersSnapshot = await db.collection("users").where("role", "==", "patient").get();
        } else {
          chatUserList.innerHTML = '<li class="p-4 text-gray-500">Tidak ada pengguna chat.</li>';
          return;
        }
        if (usersSnapshot.empty) {
          chatUserList.innerHTML = '<li class="p-4 text-gray-500">Tidak ada pengguna chat.</li>';
          return;
        }
        usersSnapshot.forEach((doc) => {
          const u = doc.data();
          const li = document.createElement("li");
          li.className = "p-3 hover:bg-red-100 cursor-pointer flex items-center space-x-3";
          li.setAttribute("data-user-id", doc.id);
          li.setAttribute("data-user-name", u.fullname);
          li.setAttribute("data-user-role", u.role);
          li.setAttribute("role", "button");
          li.setAttribute("tabindex", "0");
          li.innerHTML = `
            <img src="${u.profilePhotoURL || "https://placehold.co/48x48/png?text=User"}" alt="Foto profil ${u.fullname}" class="w-12 h-12 rounded-full object-cover border-2 border-red-700" />
            <div>
              <p class="font-semibold text-red-700">${u.fullname}</p>
              <p class="text-sm text-gray-600">${u.role === "doctor" ? "Dokter" : "Pasien"}</p>
            </div>
          `;
          li.addEventListener("click", () => {
            openChat(doc.id, u.fullname, u.role);
            showSection(chatSection);
          });
          li.addEventListener("keydown", (e) => {
            if (e.key === "Enter" || e.key === " ") {
              e.preventDefault();
              openChat(doc.id, u.fullname, u.role);
              showSection(chatSection);
            }
          });
          chatUserList.appendChild(li);
        });
      } catch (error) {
        chatUserList.innerHTML = `<li class="p-4 text-red-700 font-semibold">Gagal memuat daftar chat: ${error.message}</li>`;
      }
    }

    // Open chat with userId
    async function openChat(userId, userName, userRole) {
      currentChatUser = userId;
      chatWindow.hidden = false;
      chatHeaderName.textContent = userName;
      chatHeaderRole.textContent = userRole === "doctor" ? "Dokter" : "Pasien";

      // Load profile photo of chat partner
      try {
        const doc = await db.collection("users").doc(userId).get();
        if (doc.exists) {
          const data = doc.data();
          chatHeaderPhoto.src = data.profilePhotoURL || "https://placehold.co/48x48/png?text=User";
        }
      } catch {
        chatHeaderPhoto.src = "https://placehold.co/48x48/png?text=User";
      }

      // Load chat messages between currentUser and currentChatUser
      if (chatUnsub) chatUnsub();

      chatMessages.innerHTML =
        '<p class="text-gray-500 text-center mt-10">Memuat pesan...</p>';

      const chatId = generateChatId(currentUser.uid, currentChatUser);
      chatUnsub = db
        .collection("chats")
        .doc(chatId)
        .collection("messages")
        .orderBy("timestamp")
        .onSnapshot((snapshot) => {
          chatMessages.innerHTML = "";
          if (snapshot.empty) {
            chatMessages.innerHTML =
              '<p class="text-gray-500 text-center mt-10">Belum ada pesan.</p>';
            return;
          }
          snapshot.forEach((doc) => {
            const msg = doc.data();
            const isMe = msg.senderId === currentUser.uid;
            const msgDiv = document.createElement("div");
            msgDiv.className = `max-w-xs md:max-w-md px-4 py-2 rounded-lg break-words ${
              isMe
                ? "bg-red-700 text-white self-end"
                : "bg-white border border-red-300 text-red-700 self-start"
            }`;
            msgDiv.textContent = msg.text;
            chatMessages.appendChild(msgDiv);
          });
          chatMessages.scrollTop = chatMessages.scrollHeight;
        });
    }

    // Close chat window
    chatCloseBtn.addEventListener("click", () => {
      chatWindow.hidden = true;
      clearChatWindow();
    });

    // Chat form submit
    chatForm.addEventListener("submit", async (e) => {
      e.preventDefault();
      if (!currentChatUser) return;
      const text = chatInput.value.trim();
      if (!text) return;

      const chatId = generateChatId(currentUser.uid, currentChatUser);
      try {
        await db.collection("chats").doc(chatId).collection("messages").add({
          senderId: currentUser.uid,
          receiverId: currentChatUser,
          text,
          timestamp: firebase.firestore.FieldValue.serverTimestamp(),
        });
        chatInput.value = "";
      } catch (error) {
        alert("Gagal mengirim pesan: " + error.message);
      }
    });

    // Generate chat ID based on two user IDs (sorted)
    function generateChatId(uid1, uid2) {
      return uid1 < uid2 ? uid1 + "_" + uid2 : uid2 + "_" + uid1;
    }

    // Listen for auth state changes
    auth.onAuthStateChanged(async (user) => {
      if (user) {
        currentUser = user;
        await loadUserData();
        authSection.classList.add("hidden");
        dashboardSection.classList.remove("hidden");
        showSection(dashboardWelcome);
        dashboardTitle.textContent = `Dashboard ${
          currentRole === "doctor" ? "Dokter" : "Pasien"
        }`;
        if (currentRole === "doctor") {
          sidebarPatientsBtn.classList.remove("hidden");
          sidebarNotificationsBtn.classList.remove("hidden");
        } else {
          sidebarPatientsBtn.classList.add("hidden");
          sidebarNotificationsBtn.classList.add("hidden");
        }
      } else {
        currentUser = null;
        currentUserData = null;
        currentRole = null;
        authSection.classList.remove("hidden");
        dashboardSection.classList.add("hidden");
        showLogin();
        clearChatWindow();
        if (notificationsUnsub) {
          notificationsUnsub();
          notificationsUnsub = null;
        }
        if (patientNotificationsUnsub) {
          patientNotificationsUnsub();
          patientNotificationsUnsub = null;
        }
      }
    });
  </script>
 </body>
</html>
