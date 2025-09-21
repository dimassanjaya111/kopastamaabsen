<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Absensi Kopastama</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        'primary': '#8b5cf6',
                        'primary-dark': '#7c3aed',
                        'secondary': '#06b6d4',
                        'accent': '#f59e0b',
                        'success': '#10b981',
                        'danger': '#ef4444',
                        'gold': '#FFD700',
                        'silver': '#C0C0C0',
                        'bronze': '#CD7F32'
                    }
                }
            }
        }
    </script>
</head>
<body class="bg-gradient-to-br from-primary via-primary-dark to-secondary min-h-screen">

    <div id="homePage" class="container mx-auto px-4 py-8">
        <div class="max-w-md mx-auto bg-white rounded-lg shadow-xl p-8">
            <div class="text-center mb-8">
                <h1 class="text-4xl font-bold bg-gradient-to-r from-primary to-secondary bg-clip-text text-transparent mb-2">KOPASTAMA</h1>
                <p class="text-primary-dark font-semibold">Sistem Absensi Online</p>
            </div>
            
            <div class="bg-gradient-to-r from-secondary/20 to-accent/20 border-l-4 border-secondary p-4 mb-6 shadow-md rounded-lg">
                <h2 class="text-lg font-semibold text-secondary mb-2">Selamat Datang!</h2>
                <p class="text-primary-dark">Silakan masukkan nama pengguna untuk melanjutkan ke sistem absensi.</p>
            </div>
            
            <div class="mb-6">
                <label class="block text-primary font-semibold mb-2">Nama Pengguna</label>
                <input type="text" id="userName" maxlength="10" 
                       class="w-full px-4 py-3 border-2 border-gray-300 rounded-lg focus:border-secondary focus:outline-none transition-colors"
                       placeholder="Maksimal 10 huruf">
            </div>
            
            <button onclick="goToQuestions()" 
                    class="w-full bg-gradient-to-r from-primary to-secondary hover:from-accent hover:to-primary text-white font-semibold py-3 px-6 rounded-lg transition-all duration-300 shadow-lg hover:shadow-xl transform hover:scale-105">
                Masuk
            </button>
        </div>
    </div>

    <div id="questionPage" class="hidden container mx-auto px-4 py-8">
        <div class="max-w-2xl mx-auto bg-white rounded-lg shadow-xl p-8">
            <div class="text-center mb-8 bg-gradient-to-r from-primary/20 to-secondary/20 p-6 rounded-lg shadow-md border border-primary/30">
                <h1 class="text-3xl font-bold bg-gradient-to-r from-primary to-secondary bg-clip-text text-transparent mb-2">Form Absensi</h1>
                <p class="text-primary-dark font-medium">Isi data absensi dengan lengkap</p>
            </div>

            <form id="attendanceForm" onsubmit="submitAttendance(event)">
                <div id="nameFields">
                    <div class="mb-6 name-field">
                        <label class="block text-primary font-semibold mb-2">Nama</label>
                        <select class="w-full px-4 py-3 border-2 border-gray-300 rounded-lg focus:border-secondary focus:outline-none name-select" onchange="handleNameChange(this)">
                            <option value="">Pilih Nama</option>
                            <option value="01">Afina Nur Asifa</option>
                            <option value="02">Aini Rosilawati</option>
                            <option value="03">Ana Khairunnisa</option>
                            <option value="04">Aura Al-maidah</option>
                            <option value="05">Devanza Adihutama</option>
                            <option value="06">Diana Rahmah</option>
                            <option value="07">Dikri</option>
                            <option value="08">Disti Dzulianti</option>
                            <option value="09">Fadilla Priyadi</option>
                            <option value="10">Khaina Anandya Putri</option>
                            <option value="11">Lailatul Faiqoh</option>
                            <option value="12">Muhamad Rohman Nabasi</option>
                            <option value="13">Muhammad Anil Anfal</option>
                            <option value="14">Muhammad Bayudi</option>
                            <option value="15">Muhammad Dimas Sanjaya</option>
                            <option value="16">Muhammad Fikri Ramadhan</option>
                            <option value="17">Muhammad Irfan Efendi</option>
                            <option value="18">Muhammad Rifki</option>
                            <option value="19">Naila Nafisyah</option>
                            <option value="20">Nibras Bany Sarim</option>
                            <option value="21">Novita Sari</option>
                            <option value="22">Putri Ameliya</option>
                            <option value="23">Rizki Hidayatullah</option>
                            <option value="24">Shafira Maula Ariffanti</option>
                            <option value="25">Silvina Uswatun</option>
                            <option value="26">Tazkiyatun Nufus</option>
                            <option value="27">Wildan Bagus Pratama</option>
                        </select>
                    </div>
                </div>

                <div class="mb-6">
                    <label class="block text-primary font-semibold mb-2">Acara</label>
                    <input type="text" id="eventName" required
                           class="w-full px-4 py-3 border-2 border-gray-300 rounded-lg focus:border-secondary focus:outline-none"
                           placeholder="Nama acara">
                </div>

                <div class="mb-6">
                    <label class="block text-primary font-semibold mb-2">Tanggal</label>
                    <input type="date" id="eventDate" required
                           class="w-full px-4 py-3 border-2 border-gray-300 rounded-lg focus:border-secondary focus:outline-none">
                </div>

                <div class="mb-6">
                    <label class="block text-primary font-semibold mb-2">Keterangan</label>
                    <select id="attendance" onchange="handleAttendanceChange()" required
                             class="w-full px-4 py-3 border-2 border-gray-300 rounded-lg focus:border-secondary focus:outline-none">
                        <option value="">Pilih Keterangan</option>
                        <option value="HADIR">HADIR</option>
                        <option value="IZIN">IZIN</option>
                        <option value="SAKIT">SAKIT</option>
                    </select>
                </div>

                <div id="reasonField" class="mb-6 hidden">
                    <label class="block text-primary font-semibold mb-2">Alasan</label>
                    <textarea id="reason" rows="3"
                               class="w-full px-4 py-3 border-2 border-gray-300 rounded-lg focus:border-secondary focus:outline-none"
                               placeholder="Tuliskan alasan tidak hadir"></textarea>
                </div>

                <button type="submit" 
                         class="w-full bg-gradient-to-r from-success to-secondary hover:from-accent hover:to-success text-white font-bold py-3 px-6 rounded-lg transition-all duration-300 shadow-lg hover:shadow-xl transform hover:scale-105">
                    Kirim
                </button>
            </form>
        </div>
    </div>

    <div id="answerPage" class="container mx-auto px-4 py-8">
        <div id="passwordSection" class="max-w-md mx-auto bg-white rounded-lg shadow-xl p-8 mb-8">
            <div class="text-center mb-6 bg-gradient-to-r from-accent/20 to-primary/20 p-4 rounded-lg border border-accent/30">
                <h2 class="text-2xl font-bold bg-gradient-to-r from-accent to-primary bg-clip-text text-transparent mb-2">Akses Data Absensi</h2>
                <p class="text-primary-dark font-medium">Masukkan password untuk melihat data</p>
            </div>
            
            <div class="mb-6">
                <label class="block text-primary font-semibold mb-2">Password</label>
                <input type="password" id="accessPassword" 
                       class="w-full px-4 py-3 border-2 border-gray-300 rounded-lg focus:border-accent focus:outline-none"
                       placeholder="Masukkan password">
            </div>
            
            <button onclick="checkPassword()" 
                    class="w-full bg-gradient-to-r from-accent to-primary hover:from-primary hover:to-secondary text-white font-bold py-3 px-6 rounded-lg transition-all duration-300 shadow-lg hover:shadow-xl transform hover:scale-105">
                Akses Data
            </button>
            
            <div id="passwordError" class="hidden mt-4 p-3 bg-red-100 border border-red-400 text-red-700 rounded">
                Password salah! Silakan coba lagi.
            </div>
        </div>

        <div id="dataSection" class="hidden">
            <div class="max-w-4xl mx-auto">
                <div class="bg-gradient-to-r from-secondary/20 to-primary/20 rounded-lg shadow-xl p-6 mb-6 border-2 border-secondary/30">
                    <div class="flex justify-between items-center mb-4">
                        <h1 class="text-3xl font-bold bg-gradient-to-r from-secondary to-primary bg-clip-text text-transparent">Data Absensi</h1>
                        <button onclick="lockData()" 
                                class="bg-gradient-to-r from-danger to-red-600 hover:from-red-600 hover:to-danger text-white font-semibold py-2 px-4 rounded-lg transition-all duration-300 transform hover:scale-105">
                            Kunci Data
                        </button>
                    </div>
                    
                    <div class="mb-4">
                        <input type="text" id="searchCode" placeholder="Cari dengan kode 10 digit"
                               class="w-full px-4 py-3 border-2 border-gray-300 rounded-lg focus:border-secondary focus:outline-none"
                               oninput="searchAnswers()">
                    </div>

                    <div id="selectionMode" class="hidden mb-4 p-4 bg-gradient-to-r from-accent/10 to-secondary/10 rounded-lg border border-accent/20">
                        <div class="flex gap-4">
                            <button onclick="rekapSelected()" 
                                    class="bg-gradient-to-r from-primary to-secondary hover:from-secondary hover:to-primary text-white px-4 py-2 rounded-lg transition-all duration-300 transform hover:scale-105">
                                Rekap
                            </button>
                            <button onclick="deleteSelected()" 
                                    class="bg-gradient-to-r from-danger to-red-600 hover:from-red-600 hover:to-danger text-white px-4 py-2 rounded-lg transition-all duration-300 transform hover:scale-105">
                                Hapus
                            </button>
                            <button onclick="cancelSelection()" 
                                    class="bg-gradient-to-r from-gray-500 to-gray-600 hover:from-gray-600 hover:to-gray-700 text-white px-4 py-2 rounded-lg transition-all duration-300 transform hover:scale-105">
                                Batal
                            </button>
                        </div>
                        <p class="text-sm text-primary-dark mt-2 font-medium">Dipilih: <span id="selectedCount">0</span> item</p>
                    </div>
                </div>

                <div id="answersList" class="space-y-4">
                    </div>
            </div>
        </div>
    </div>

    <div id="rankPage" class="hidden container mx-auto px-4 py-8">
        <div class="max-w-4xl mx-auto bg-white rounded-lg shadow-xl p-8">
            <div class="text-center mb-8 bg-gradient-to-r from-accent/20 to-success/20 p-6 rounded-lg shadow-md border border-accent/30">
                <h1 class="text-3xl font-bold bg-gradient-to-r from-accent to-success bg-clip-text text-transparent mb-2">Ranking Kehadiran</h1>
                <p class="text-primary-dark font-medium">Peringkat anggota berdasarkan tingkat kehadiran</p>
            </div>
            
            <div id="rankingList" class="space-y-4">
                </div>
        </div>
    </div>

    <div id="rekapPage" class="hidden container mx-auto px-4 py-8">
        <div class="max-w-4xl mx-auto bg-white rounded-lg shadow-xl p-8">
            <div class="text-center mb-6 bg-gradient-to-r from-primary/20 to-accent/20 p-6 rounded-lg shadow-md border border-primary/30">
                <h1 class="text-3xl font-bold bg-gradient-to-r from-primary to-accent bg-clip-text text-transparent">Rekap Absensi</h1>
                <p class="text-primary-dark font-medium mt-2">Rekap dikelompokkan berdasarkan tanggal acara</p>
            </div>
            
            <div id="rekapContent" class="bg-gray-50 p-6 rounded-lg">
                </div>
        </div>
    </div>

    <div id="successModal" class="hidden fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50">
        <div class="bg-white rounded-lg shadow-2xl max-w-md mx-4 transform transition-all duration-300 scale-95">
            <div class="p-8 text-center">
                <div class="mx-auto flex items-center justify-center h-16 w-16 rounded-full bg-gradient-to-r from-success to-secondary mb-6">
                    <svg class="h-8 w-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path>
                    </svg>
                </div>
                
                <h3 class="text-2xl font-bold bg-gradient-to-r from-primary to-secondary bg-clip-text text-transparent mb-4">
                    Jawaban Sudah Terkirim
                </h3>
                <p class="text-primary-dark font-medium mb-6">
                    Terimakasih! Data absensi Anda telah berhasil disimpan.
                </p>
                
                <button onclick="closeSuccessModal()" 
                        class="bg-gradient-to-r from-primary to-secondary hover:from-secondary hover:to-primary text-white font-bold py-3 px-8 rounded-lg transition-all duration-300 shadow-lg hover:shadow-xl transform hover:scale-105">
                    OK
                </button>
            </div>
        </div>
    </div>

    <script>
        let attendanceData = JSON.parse(localStorage.getItem('attendanceData')) || [];
        let selectedAnswers = [];
        let selectionMode = false;
        let isDataUnlocked = false;
        const correctPassword = "0012025";

        document.addEventListener('DOMContentLoaded', function() {
            const today = new Date().toISOString().split('T')[0];
            document.getElementById('eventDate').value = today;
        });

        function goToQuestions() {
            const userName = document.getElementById('userName').value.trim();
            if (!userName && document.getElementById('homePage').style.display !== 'none') {
                alert('Silakan masukkan nama pengguna terlebih dahulu!');
                return;
            }
            
            document.getElementById('homePage').classList.add('hidden');
            document.getElementById('questionPage').classList.remove('hidden');
            document.getElementById('answerPage').classList.remove('hidden');
            document.getElementById('rankPage').classList.add('hidden');
            document.getElementById('rekapPage').classList.add('hidden');
            
            isDataUnlocked = false;
            document.getElementById('passwordSection').classList.remove('hidden');
            document.getElementById('dataSection').classList.add('hidden');
        }

        function checkPassword() {
            const password = document.getElementById('accessPassword').value;
            const errorDiv = document.getElementById('passwordError');
            
            if (password === correctPassword) {
                isDataUnlocked = true;
                errorDiv.classList.add('hidden');
