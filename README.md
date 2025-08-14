<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistem Manajemen Sekolah</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
</head>
<body class="bg-gradient-to-br from-blue-50 to-indigo-100 min-h-screen">
    <!-- Login Screen -->
    <div id="loginScreen" class="min-h-screen flex items-center justify-center p-4">
        <div class="bg-white rounded-2xl shadow-2xl p-8 w-full max-w-md">
            <div class="text-center mb-8">
                <div class="bg-blue-600 w-20 h-20 rounded-full flex items-center justify-center mx-auto mb-4">
                    <i class="fas fa-school text-white text-3xl"></i>
                </div>
                <h1 class="text-2xl font-bold text-gray-800">Sistem Manajemen Sekolah</h1>
                <p class="text-gray-600 mt-2">Silakan masuk untuk melanjutkan</p>
            </div>
            
            <form id="loginForm" class="space-y-6">
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-2">Username</label>
                    <input type="text" id="username" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" placeholder="Masukkan username" required>
                </div>
                
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-2">Password</label>
                    <input type="password" id="password" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent" placeholder="Masukkan password" required>
                </div>
                
                <button type="submit" class="w-full bg-blue-600 text-white py-3 rounded-lg hover:bg-blue-700 transition duration-200 font-medium">
                    Masuk
                </button>
                
                <div class="text-center text-sm text-gray-500">
                    Password default: 12345
                </div>
            </form>
        </div>
    </div>

    <!-- Main Dashboard -->
    <div id="dashboard" class="hidden">
        <!-- Header -->
        <header class="bg-white shadow-lg">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="flex justify-between items-center py-4">
                    <div class="flex items-center">
                        <div class="bg-blue-600 w-12 h-12 rounded-lg flex items-center justify-center mr-4">
                            <i class="fas fa-school text-white text-xl"></i>
                        </div>
                        <div>
                            <h1 class="text-xl font-bold text-gray-800" id="schoolName">SMPN 1 Tongkonan Satap</h1>
                            <p class="text-sm text-gray-600">Sistem Manajemen Sekolah</p>
                        </div>
                    </div>
                    <div class="flex items-center space-x-4">
                        <button onclick="showSchoolSettings()" class="text-gray-600 hover:text-blue-600 transition duration-200">
                            <i class="fas fa-cog text-xl"></i>
                        </button>
                        <button onclick="logout()" class="bg-red-500 text-white px-4 py-2 rounded-lg hover:bg-red-600 transition duration-200">
                            <i class="fas fa-sign-out-alt mr-2"></i>Keluar
                        </button>
                    </div>
                </div>
            </div>
        </header>

        <!-- Navigation -->
        <nav class="bg-blue-600 shadow-lg">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="flex space-x-8 overflow-x-auto py-4">
                    <button onclick="showModule('dashboard')" class="nav-btn active text-white px-4 py-2 rounded-lg whitespace-nowrap hover:bg-blue-700 transition duration-200">
                        <i class="fas fa-home mr-2"></i>Dashboard
                    </button>
                    <button onclick="showModule('guru-wali')" class="nav-btn text-blue-100 px-4 py-2 rounded-lg whitespace-nowrap hover:bg-blue-700 hover:text-white transition duration-200">
                        <i class="fas fa-chalkboard-teacher mr-2"></i>Guru Wali
                    </button>
                    <button onclick="showModule('student-record')" class="nav-btn text-blue-100 px-4 py-2 rounded-lg whitespace-nowrap hover:bg-blue-700 hover:text-white transition duration-200">
                        <i class="fas fa-users mr-2"></i>Student Record
                    </button>
                    <button onclick="showModule('ekstrakurikuler')" class="nav-btn text-blue-100 px-4 py-2 rounded-lg whitespace-nowrap hover:bg-blue-700 hover:text-white transition duration-200">
                        <i class="fas fa-futbol mr-2"></i>Ekstrakurikuler
                    </button>
                    <button onclick="showModule('daftar-hadir')" class="nav-btn text-blue-100 px-4 py-2 rounded-lg whitespace-nowrap hover:bg-blue-700 hover:text-white transition duration-200">
                        <i class="fas fa-calendar-check mr-2"></i>Daftar Hadir
                    </button>
                    <button onclick="showModule('7kaih')" class="nav-btn text-blue-100 px-4 py-2 rounded-lg whitespace-nowrap hover:bg-blue-700 hover:text-white transition duration-200">
                        <i class="fas fa-star mr-2"></i>7 KAIH
                    </button>
                    <button onclick="showModule('monitor-ujian')" class="nav-btn text-blue-100 px-4 py-2 rounded-lg whitespace-nowrap hover:bg-blue-700 hover:text-white transition duration-200">
                        <i class="fas fa-clipboard-list mr-2"></i>Monitor Ujian
                    </button>
                    <button onclick="showModule('portal-kombel')" class="nav-btn text-blue-100 px-4 py-2 rounded-lg whitespace-nowrap hover:bg-blue-700 hover:text-white transition duration-200">
                        <i class="fas fa-comments mr-2"></i>Portal Kombel
                    </button>
                    <button onclick="showModule('nomor-surat')" class="nav-btn text-blue-100 px-4 py-2 rounded-lg whitespace-nowrap hover:bg-blue-700 hover:text-white transition duration-200">
                        <i class="fas fa-envelope mr-2"></i>Nomor Surat
                    </button>
                    <button onclick="showModule('supervisi')" class="nav-btn text-blue-100 px-4 py-2 rounded-lg whitespace-nowrap hover:bg-blue-700 hover:text-white transition duration-200">
                        <i class="fas fa-eye mr-2"></i>Supervisi
                    </button>
                    <button onclick="showModule('ppdb')" class="nav-btn text-blue-100 px-4 py-2 rounded-lg whitespace-nowrap hover:bg-blue-700 hover:text-white transition duration-200">
                        <i class="fas fa-user-plus mr-2"></i>P.P.D.B.
                    </button>
                    <button onclick="showModule('perpustakaan')" class="nav-btn text-blue-100 px-4 py-2 rounded-lg whitespace-nowrap hover:bg-blue-700 hover:text-white transition duration-200">
                        <i class="fas fa-book mr-2"></i>Perpustakaan
                    </button>
                    <button onclick="showModule('asesmen')" class="nav-btn text-blue-100 px-4 py-2 rounded-lg whitespace-nowrap hover:bg-blue-700 hover:text-white transition duration-200">
                        <i class="fas fa-tasks mr-2"></i>Asesmen
                    </button>
                    <button onclick="showModule('buku-tamu')" class="nav-btn text-blue-100 px-4 py-2 rounded-lg whitespace-nowrap hover:bg-blue-700 hover:text-white transition duration-200">
                        <i class="fas fa-address-book mr-2"></i>Buku Tamu
                    </button>
                </div>
            </div>
        </nav>

        <!-- Main Content -->
        <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
            <!-- Dashboard Module -->
            <div id="module-dashboard" class="module-content">
                <div class="mb-8">
                    <h2 class="text-3xl font-bold text-gray-800 mb-2">Dashboard</h2>
                    <p class="text-gray-600">Selamat datang di Sistem Manajemen Sekolah</p>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
                    <div class="bg-white rounded-xl shadow-lg p-6">
                        <div class="flex items-center">
                            <div class="bg-blue-100 p-3 rounded-lg">
                                <i class="fas fa-users text-blue-600 text-2xl"></i>
                            </div>
                            <div class="ml-4">
                                <p class="text-sm text-gray-600">Total Siswa</p>
                                <p class="text-2xl font-bold text-gray-800">245</p>
                            </div>
                        </div>
                    </div>

                    <div class="bg-white rounded-xl shadow-lg p-6">
                        <div class="flex items-center">
                            <div class="bg-green-100 p-3 rounded-lg">
                                <i class="fas fa-chalkboard-teacher text-green-600 text-2xl"></i>
                            </div>
                            <div class="ml-4">
                                <p class="text-sm text-gray-600">Total Guru</p>
                                <p class="text-2xl font-bold text-gray-800">28</p>
                            </div>
                        </div>
                    </div>

                    <div class="bg-white rounded-xl shadow-lg p-6">
                        <div class="flex items-center">
                            <div class="bg-yellow-100 p-3 rounded-lg">
                                <i class="fas fa-door-open text-yellow-600 text-2xl"></i>
                            </div>
                            <div class="ml-4">
                                <p class="text-sm text-gray-600">Total Kelas</p>
                                <p class="text-2xl font-bold text-gray-800">12</p>
                            </div>
                        </div>
                    </div>

                    <div class="bg-white rounded-xl shadow-lg p-6">
                        <div class="flex items-center">
                            <div class="bg-purple-100 p-3 rounded-lg">
                                <i class="fas fa-futbol text-purple-600 text-2xl"></i>
                            </div>
                            <div class="ml-4">
                                <p class="text-sm text-gray-600">Ekstrakurikuler</p>
                                <p class="text-2xl font-bold text-gray-800">8</p>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                    <div class="bg-white rounded-xl shadow-lg p-6">
                        <h3 class="text-xl font-bold text-gray-800 mb-4">Informasi Sekolah</h3>
                        <div class="space-y-3">
                            <div class="flex justify-between">
                                <span class="text-gray-600">Nama Sekolah:</span>
                                <span class="font-medium" id="dashboardSchoolName">SMPN 1 Tongkonan Satap</span>
                            </div>
                            <div class="flex justify-between">
                                <span class="text-gray-600">Alamat:</span>
                                <span class="font-medium" id="dashboardAddress">Ds. Tasangtongkonan</span>
                            </div>
                            <div class="flex justify-between">
                                <span class="text-gray-600">Kecamatan:</span>
                                <span class="font-medium" id="dashboardDistrict">Basse Sangtempe Utara</span>
                            </div>
                            <div class="flex justify-between">
                                <span class="text-gray-600">Kabupaten:</span>
                                <span class="font-medium" id="dashboardCity">Luwu</span>
                            </div>
                            <div class="flex justify-between">
                                <span class="text-gray-600">Provinsi:</span>
                                <span class="font-medium" id="dashboardProvince">Sulawesi Selatan</span>
                            </div>
                        </div>
                    </div>

                    <div class="bg-white rounded-xl shadow-lg p-6">
                        <h3 class="text-xl font-bold text-gray-800 mb-4">Aktivitas Terbaru</h3>
                        <div class="space-y-4">
                            <div class="flex items-center p-3 bg-blue-50 rounded-lg">
                                <i class="fas fa-user-plus text-blue-600 mr-3"></i>
                                <div>
                                    <p class="font-medium text-gray-800">Siswa baru terdaftar</p>
                                    <p class="text-sm text-gray-600">5 menit yang lalu</p>
                                </div>
                            </div>
                            <div class="flex items-center p-3 bg-green-50 rounded-lg">
                                <i class="fas fa-check text-green-600 mr-3"></i>
                                <div>
                                    <p class="font-medium text-gray-800">Absensi kelas VII-A selesai</p>
                                    <p class="text-sm text-gray-600">15 menit yang lalu</p>
                                </div>
                            </div>
                            <div class="flex items-center p-3 bg-yellow-50 rounded-lg">
                                <i class="fas fa-book text-yellow-600 mr-3"></i>
                                <div>
                                    <p class="font-medium text-gray-800">Buku baru ditambahkan</p>
                                    <p class="text-sm text-gray-600">1 jam yang lalu</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Guru Wali Module -->
            <div id="module-guru-wali" class="module-content hidden">
                <div class="mb-8">
                    <h2 class="text-3xl font-bold text-gray-800 mb-2">Data Guru Wali</h2>
                    <p class="text-gray-600">Kelola data guru wali dan peserta didiknya</p>
                </div>

                <div class="bg-white rounded-xl shadow-lg p-6 mb-6">
                    <div class="flex justify-between items-center mb-6">
                        <h3 class="text-xl font-bold text-gray-800">Daftar Guru Wali</h3>
                        <button onclick="addGuruWali()" class="bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700 transition duration-200">
                            <i class="fas fa-plus mr-2"></i>Tambah Guru Wali
                        </button>
                    </div>

                    <div class="overflow-x-auto">
                        <table class="w-full table-auto">
                            <thead>
                                <tr class="bg-gray-50">
                                    <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Nama Guru</th>
                                    <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Kelas</th>
                                    <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Jumlah Siswa</th>
                                    <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Aksi</th>
                                </tr>
                            </thead>
                            <tbody id="guruWaliTable">
                                <tr class="border-b">
                                    <td class="px-4 py-3">Dra. Siti Aminah</td>
                                    <td class="px-4 py-3">VII-A</td>
                                    <td class="px-4 py-3">24 siswa</td>
                                    <td class="px-4 py-3">
                                        <button onclick="viewSiswaWali('VII-A')" class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-eye"></i>
                                        </button>
                                        <button onclick="editGuruWali('VII-A')" class="text-green-600 hover:text-green-800 mr-3">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                        <button onclick="deleteGuruWali('VII-A')" class="text-red-600 hover:text-red-800">
                                            <i class="fas fa-trash"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr class="border-b">
                                    <td class="px-4 py-3">Ahmad Fauzi, S.Pd</td>
                                    <td class="px-4 py-3">VII-B</td>
                                    <td class="px-4 py-3">23 siswa</td>
                                    <td class="px-4 py-3">
                                        <button onclick="viewSiswaWali('VII-B')" class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-eye"></i>
                                        </button>
                                        <button onclick="editGuruWali('VII-B')" class="text-green-600 hover:text-green-800 mr-3">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                        <button onclick="deleteGuruWali('VII-B')" class="text-red-600 hover:text-red-800">
                                            <i class="fas fa-trash"></i>
                                        </button>
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>

            <!-- Student Record Module -->
            <div id="module-student-record" class="module-content hidden">
                <div class="mb-8">
                    <h2 class="text-3xl font-bold text-gray-800 mb-2">Student Record</h2>
                    <p class="text-gray-600">Database lengkap peserta didik</p>
                </div>

                <div class="bg-white rounded-xl shadow-lg p-6">
                    <div class="flex justify-between items-center mb-6">
                        <h3 class="text-xl font-bold text-gray-800">Data Peserta Didik</h3>
                        <div class="flex space-x-3">
                            <input type="text" placeholder="Cari siswa..." class="px-4 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500">
                            <button onclick="addStudent()" class="bg-blue-600 text-white px-4 py-2 rounded-lg hover:bg-blue-700 transition duration-200">
                                <i class="fas fa-plus mr-2"></i>Tambah Siswa
                            </button>
                        </div>
                    </div>

                    <div class="overflow-x-auto">
                        <table class="w-full table-auto">
                            <thead>
                                <tr class="bg-gray-50">
                                    <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">NISN</th>
                                    <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Nama Lengkap</th>
                                    <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Kelas</th>
                                    <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Jenis Kelamin</th>
                                    <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Status</th>
                                    <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Aksi</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr class="border-b">
                                    <td class="px-4 py-3">1234567890</td>
                                    <td class="px-4 py-3">Andi Pratama</td>
                                    <td class="px-4 py-3">VII-A</td>
                                    <td class="px-4 py-3">Laki-laki</td>
                                    <td class="px-4 py-3"><span class="bg-green-100 text-green-800 px-2 py-1 rounded-full text-xs">Aktif</span></td>
                                    <td class="px-4 py-3">
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-eye"></i>
                                        </button>
                                        <button class="text-green-600 hover:text-green-800 mr-3">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                        <button class="text-red-600 hover:text-red-800">
                                            <i class="fas fa-trash"></i>
                                        </button>
                                    </td>
                                </tr>
                                <tr class="border-b">
                                    <td class="px-4 py-3">1234567891</td>
                                    <td class="px-4 py-3">Sari Dewi</td>
                                    <td class="px-4 py-3">VII-A</td>
                                    <td class="px-4 py-3">Perempuan</td>
                                    <td class="px-4 py-3"><span class="bg-green-100 text-green-800 px-2 py-1 rounded-full text-xs">Aktif</span></td>
                                    <td class="px-4 py-3">
                                        <button class="text-blue-600 hover:text-blue-800 mr-3">
                                            <i class="fas fa-eye"></i>
                                        </button>
                                        <button class="text-green-600 hover:text-green-800 mr-3">
                                            <i class="fas fa-edit"></i>
                                        </button>
                                        <button class="text-red-600 hover:text-red-800">
                                            <i class="fas fa-trash"></i>
                                        </button>
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>

            <!-- Other modules will be similar structure -->
            <div id="module-ekstrakurikuler" class="module-content hidden">
                <div class="mb-8">
                    <h2 class="text-3xl font-bold text-gray-800 mb-2">Ekstrakurikuler</h2>
                    <p class="text-gray-600">Kelola data dan absensi ekstrakurikuler</p>
                </div>
                <div class="bg-white rounded-xl shadow-lg p-6">
                    <h3 class="text-xl font-bold text-gray-800 mb-4">Daftar Ekstrakurikuler</h3>
                    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                        <div class="border border-gray-200 rounded-lg p-4">
                            <h4 class="font-bold text-gray-800">Pramuka</h4>
                            <p class="text-gray-600 text-sm">Pembina: Pak Budi</p>
                            <p class="text-gray-600 text-sm">Anggota: 45 siswa</p>
                            <button class="mt-3 bg-blue-600 text-white px-3 py-1 rounded text-sm hover:bg-blue-700">Kelola</button>
                        </div>
                        <div class="border border-gray-200 rounded-lg p-4">
                            <h4 class="font-bold text-gray-800">Sepak Bola</h4>
                            <p class="text-gray-600 text-sm">Pelatih: Pak Ahmad</p>
                            <p class="text-gray-600 text-sm">Anggota: 22 siswa</p>
                            <button class="mt-3 bg-blue-600 text-white px-3 py-1 rounded text-sm hover:bg-blue-700">Kelola</button>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Continue with other modules... -->
            <div id="module-daftar-hadir" class="module-content hidden">
                <div class="mb-8">
                    <h2 class="text-3xl font-bold text-gray-800 mb-2">Daftar Hadir</h2>
                    <p class="text-gray-600">Rekap daftar hadir harian siswa</p>
                </div>
                <div class="bg-white rounded-xl shadow-lg p-6">
                    <div class="flex justify-between items-center mb-6">
                        <h3 class="text-xl font-bold text-gray-800">Absensi Hari Ini</h3>
                        <input type="date" class="px-4 py-2 border border-gray-300 rounded-lg">
                    </div>
                    <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                        <div class="bg-green-50 p-4 rounded-lg">
                            <h4 class="font-bold text-green-800">Hadir</h4>
                            <p class="text-2xl font-bold text-green-600">230</p>
                        </div>
                        <div class="bg-yellow-50 p-4 rounded-lg">
                            <h4 class="font-bold text-yellow-800">Izin</h4>
                            <p class="text-2xl font-bold text-yellow-600">8</p>
                        </div>
                        <div class="bg-red-50 p-4 rounded-lg">
                            <h4 class="font-bold text-red-800">Alpha</h4>
                            <p class="text-2xl font-bold text-red-600">7</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Add other modules similarly -->
            <div id="module-7kaih" class="module-content hidden">
                <div class="mb-8">
                    <h2 class="text-3xl font-bold text-gray-800 mb-2">7 Kebiasaan Anak Indonesia Hebat</h2>
                    <p class="text-gray-600">Data rekap 7 KAIH siswa</p>
                </div>
                <div class="bg-white rounded-xl shadow-lg p-6">
                    <p class="text-gray-600">Modul 7 KAIH dalam pengembangan...</p>
                </div>
            </div>

            <div id="module-monitor-ujian" class="module-content hidden">
                <div class="mb-8">
                    <h2 class="text-3xl font-bold text-gray-800 mb-2">Monitor Ujian</h2>
                    <p class="text-gray-600">Kontrol daftar hadir peserta ujian, pengawas dan panitia</p>
                </div>
                <div class="bg-white rounded-xl shadow-lg p-6">
                    <p class="text-gray-600">Modul Monitor Ujian dalam pengembangan...</p>
                </div>
            </div>

            <div id="module-portal-kombel" class="module-content hidden">
                <div class="mb-8">
                    <h2 class="text-3xl font-bold text-gray-800 mb-2">Portal Kombel</h2>
                    <p class="text-gray-600">Media Komunitas Belajar Sekolah</p>
                </div>
                <div class="bg-white rounded-xl shadow-lg p-6">
                    <p class="text-gray-600">Portal Kombel dalam pengembangan...</p>
                </div>
            </div>

            <div id="module-nomor-surat" class="module-content hidden">
                <div class="mb-8">
                    <h2 class="text-3xl font-bold text-gray-800 mb-2">Nomor Surat</h2>
                    <p class="text-gray-600">Cek nomor surat terakhir dan ambil nomor baru</p>
                </div>
                <div class="bg-white rounded-xl shadow-lg p-6">
                    <div class="text-center">
                        <h3 class="text-xl font-bold mb-4">Nomor Surat Terakhir</h3>
                        <p class="text-3xl font-bold text-blue-600 mb-4">001/SMPN1TK/XII/2024</p>
                        <button class="bg-blue-600 text-white px-6 py-3 rounded-lg hover:bg-blue-700">
                            Ambil Nomor Surat Baru
                        </button>
                    </div>
                </div>
            </div>

            <div id="module-supervisi" class="module-content hidden">
                <div class="mb-8">
                    <h2 class="text-3xl font-bold text-gray-800 mb-2">Supervisi</h2>
                    <p class="text-gray-600">Pilih dan lihat data supervisi</p>
                </div>
                <div class="bg-white rounded-xl shadow-lg p-6">
                    <p class="text-gray-600">Modul Supervisi dalam pengembangan...</p>
                </div>
            </div>

            <div id="module-ppdb" class="module-content hidden">
                <div class="mb-8">
                    <h2 class="text-3xl font-bold text-gray-800 mb-2">P.P.D.B.</h2>
                    <p class="text-gray-600">Penerimaan Peserta Didik Baru</p>
                </div>
                <div class="bg-white rounded-xl shadow-lg p-6">
                    <p class="text-gray-600">Modul PPDB dalam pengembangan...</p>
                </div>
            </div>

            <div id="module-perpustakaan" class="module-content hidden">
                <div class="mb-8">
                    <h2 class="text-3xl font-bold text-gray-800 mb-2">Perpustakaan</h2>
                    <p class="text-gray-600">Pengelolaan buku perpustakaan</p>
                </div>
                <div class="bg-white rounded-xl shadow-lg p-6">
                    <p class="text-gray-600">Modul Perpustakaan dalam pengembangan...</p>
                </div>
            </div>

            <div id="module-asesmen" class="module-content hidden">
                <div class="mb-8">
                    <h2 class="text-3xl font-bold text-gray-800 mb-2">Asesmen</h2>
                    <p class="text-gray-600">Pengelolaan Asesmen Sekolah</p>
                </div>
                <div class="bg-white rounded-xl shadow-lg p-6">
                    <p class="text-gray-600">Modul Asesmen dalam pengembangan...</p>
                </div>
            </div>

            <div id="module-buku-tamu" class="module-content hidden">
                <div class="mb-8">
                    <h2 class="text-3xl font-bold text-gray-800 mb-2">Buku Tamu</h2>
                    <p class="text-gray-600">Pengelolaan Buku Tamu Digital</p>
                </div>
                <div class="bg-white rounded-xl shadow-lg p-6">
                    <div class="mb-6">
                        <h3 class="text-xl font-bold text-gray-800 mb-4">Tambah Tamu Baru</h3>
                        <form class="grid grid-cols-1 md:grid-cols-2 gap-4">
                            <input type="text" placeholder="Nama Lengkap" class="px-4 py-2 border border-gray-300 rounded-lg">
                            <input type="text" placeholder="Instansi/Asal" class="px-4 py-2 border border-gray-300 rounded-lg">
                            <input type="text" placeholder="Keperluan" class="px-4 py-2 border border-gray-300 rounded-lg">
                            <input type="tel" placeholder="No. Telepon" class="px-4 py-2 border border-gray-300 rounded-lg">
                            <button type="submit" class="md:col-span-2 bg-blue-600 text-white py-2 rounded-lg hover:bg-blue-700">
                                Simpan Data Tamu
                            </button>
                        </form>
                    </div>
                    <div>
                        <h3 class="text-xl font-bold text-gray-800 mb-4">Daftar Tamu Hari Ini</h3>
                        <div class="space-y-3">
                            <div class="border border-gray-200 rounded-lg p-4">
                                <div class="flex justify-between items-center">
                                    <div>
                                        <h4 class="font-bold">Dr. Andi Mappaseng</h4>
                                        <p class="text-gray-600 text-sm">Dinas Pendidikan Kab. Luwu</p>
                                        <p class="text-gray-600 text-sm">Keperluan: Supervisi Sekolah</p>
                                    </div>
                                    <div class="text-right">
                                        <p class="text-sm text-gray-600">09:30 WIB</p>
                                        <span class="bg-green-100 text-green-800 px-2 py-1 rounded-full text-xs">Masuk</span>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </main>
    </div>

    <!-- School Settings Modal -->
    <div id="schoolSettingsModal" class="fixed inset-0 bg-black bg-opacity-50 hidden flex items-center justify-center p-4 z-50">
        <div class="bg-white rounded-2xl shadow-2xl p-8 w-full max-w-md">
            <div class="flex justify-between items-center mb-6">
                <h2 class="text-2xl font-bold text-gray-800">Pengaturan Sekolah</h2>
                <button onclick="closeSchoolSettings()" class="text-gray-500 hover:text-gray-700">
                    <i class="fas fa-times text-xl"></i>
                </button>
            </div>
            
            <form id="schoolSettingsForm" class="space-y-4">
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-2">Nama Sekolah</label>
                    <input type="text" id="settingsSchoolName" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500" value="SMPN 1 Tongkonan Satap">
                </div>
                
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-2">Alamat</label>
                    <input type="text" id="settingsAddress" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500" value="Ds. Tasangtongkonan">
                </div>
                
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-2">Kecamatan</label>
                    <input type="text" id="settingsDistrict" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500" value="Basse Sangtempe Utara">
                </div>
                
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-2">Kabupaten/Kota</label>
                    <input type="text" id="settingsCity" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500" value="Luwu">
                </div>
                
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-2">Provinsi</label>
                    <input type="text" id="settingsProvince" class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500" value="Sulawesi Selatan">
                </div>
                
                <div class="flex space-x-4 pt-4">
                    <button type="button" onclick="closeSchoolSettings()" class="flex-1 bg-gray-300 text-gray-700 py-3 rounded-lg hover:bg-gray-400 transition duration-200">
                        Batal
                    </button>
                    <button type="submit" class="flex-1 bg-blue-600 text-white py-3 rounded-lg hover:bg-blue-700 transition duration-200">
                        Simpan
                    </button>
                </div>
            </form>
        </div>
    </div>

    <script>
        // School data
        let schoolData = {
            name: 'SMPN 1 Tongkonan Satap',
            address: 'Ds. Tasangtongkonan',
            district: 'Basse Sangtempe Utara',
            city: 'Luwu',
            province: 'Sulawesi Selatan'
        };

        // Login functionality
        document.getElementById('loginForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            
            if (password === '12345') {
                document.getElementById('loginScreen').classList.add('hidden');
                document.getElementById('dashboard').classList.remove('hidden');
            } else {
                alert('Password salah! Gunakan password: 12345');
            }
        });

        // Navigation functionality
        function showModule(moduleName) {
            // Hide all modules
            const modules = document.querySelectorAll('.module-content');
            modules.forEach(module => module.classList.add('hidden'));
            
            // Show selected module
            document.getElementById('module-' + moduleName).classList.remove('hidden');
            
            // Update navigation buttons
            const navButtons = document.querySelectorAll('.nav-btn');
            navButtons.forEach(btn => {
                btn.classList.remove('active', 'text-white', 'bg-blue-700');
                btn.classList.add('text-blue-100');
            });
            
            event.target.classList.add('active', 'text-white', 'bg-blue-700');
            event.target.classList.remove('text-blue-100');
        }

        // School settings functionality
        function showSchoolSettings() {
            document.getElementById('schoolSettingsModal').classList.remove('hidden');
            
            // Populate form with current data
            document.getElementById('settingsSchoolName').value = schoolData.name;
            document.getElementById('settingsAddress').value = schoolData.address;
            document.getElementById('settingsDistrict').value = schoolData.district;
            document.getElementById('settingsCity').value = schoolData.city;
            document.getElementById('settingsProvince').value = schoolData.province;
        }

        function closeSchoolSettings() {
            document.getElementById('schoolSettingsModal').classList.add('hidden');
        }

        // Save school settings
        document.getElementById('schoolSettingsForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Update school data
            schoolData.name = document.getElementById('settingsSchoolName').value;
            schoolData.address = document.getElementById('settingsAddress').value;
            schoolData.district = document.getElementById('settingsDistrict').value;
            schoolData.city = document.getElementById('settingsCity').value;
            schoolData.province = document.getElementById('settingsProvince').value;
            
            // Update UI elements
            document.getElementById('schoolName').textContent = schoolData.name;
            document.getElementById('dashboardSchoolName').textContent = schoolData.name;
            document.getElementById('dashboardAddress').textContent = schoolData.address;
            document.getElementById('dashboardDistrict').textContent = schoolData.district;
            document.getElementById('dashboardCity').textContent = schoolData.city;
            document.getElementById('dashboardProvince').textContent = schoolData.province;
            
            closeSchoolSettings();
            alert('Data sekolah berhasil diperbarui!');
        });

        // Logout functionality
        function logout() {
            if (confirm('Apakah Anda yakin ingin keluar?')) {
                document.getElementById('dashboard').classList.add('hidden');
                document.getElementById('loginScreen').classList.remove('hidden');
                document.getElementById('username').value = '';
                document.getElementById('password').value = '';
            }
        }

        // Sample functions for guru wali module
        function addGuruWali() {
            alert('Fitur tambah guru wali akan segera tersedia');
        }

        function viewSiswaWali(kelas) {
            alert('Menampilkan siswa kelas ' + kelas);
        }

        function editGuruWali(kelas) {
            alert('Edit guru wali kelas ' + kelas);
        }

        function deleteGuruWali(kelas) {
            if (confirm('Hapus guru wali kelas ' + kelas + '?')) {
                alert('Data guru wali kelas ' + kelas + ' dihapus');
            }
        }

        function addStudent() {
            alert('Fitur tambah siswa akan segera tersedia');
        }

        // Close modal when clicking outside
        document.getElementById('schoolSettingsModal').addEventListener('click', function(e) {
            if (e.target === this) {
                closeSchoolSettings();
            }
        });
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'96f099ef00d91dd6',t:'MTc1NTE3NjA3MS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
