<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tay Lee Music Hub | Upload & Play YOUR Music</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
            color: #fff;
            line-height: 1.6;
            min-height: 100vh;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        /* Header Styles */
        header {
            background: rgba(0, 0, 0, 0.8);
            backdrop-filter: blur(10px);
            position: sticky;
            top: 0;
            z-index: 1000;
            padding: 1rem 0;
            border-bottom: 2px solid #00dbde;
        }
        
        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .logo h1 {
            font-size: 1.8rem;
            background: linear-gradient(45deg, #00dbde, #fc00ff);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            font-weight: 700;
        }
        
        .logo-icon {
            font-size: 2rem;
            color: #00dbde;
        }
        
        nav ul {
            display: flex;
            list-style: none;
            gap: 2rem;
        }
        
        nav a {
            color: #fff;
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s;
            padding: 5px 10px;
            border-radius: 5px;
        }
        
        nav a:hover, nav a.active {
            color: #00dbde;
            background: rgba(0, 219, 222, 0.1);
        }
        
        /* Hero Section */
        .hero {
            padding: 4rem 0;
            text-align: center;
            background: linear-gradient(rgba(0,0,0,0.7), rgba(0,0,0,0.7)),
                        url('https://images.unsplash.com/photo-1511379938547-c1f69419868d?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80');
            background-size: cover;
            background-position: center;
            border-radius: 0 0 20px 20px;
            margin-bottom: 3rem;
        }
        
        .hero h2 {
            font-size: 3rem;
            margin-bottom: 1rem;
            background: linear-gradient(45deg, #00dbde, #fc00ff);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }
        
        .hero p {
            font-size: 1.2rem;
            max-width: 600px;
            margin: 0 auto 2rem;
            color: #ccc;
        }
        
        .cta-button {
            display: inline-block;
            background: linear-gradient(45deg, #00dbde, #fc00ff);
            color: white;
            padding: 12px 30px;
            border-radius: 50px;
            text-decoration: none;
            font-weight: bold;
            font-size: 1.1rem;
            transition: transform 0.3s, box-shadow 0.3s;
            border: none;
            cursor: pointer;
        }
        
        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(0, 219, 222, 0.3);
        }
        
        /* Upload Section */
        .upload-section {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            padding: 3rem;
            margin-bottom: 3rem;
            border: 1px solid rgba(0, 219, 222, 0.2);
        }
        
        .upload-section h3 {
            font-size: 2rem;
            margin-bottom: 2rem;
            color: #00dbde;
        }
        
        .upload-area {
            border: 3px dashed #00dbde;
            border-radius: 10px;
            padding: 3rem;
            text-align: center;
            margin-bottom: 2rem;
            transition: all 0.3s;
            background: rgba(0, 219, 222, 0.05);
        }
        
        .upload-area.drag-over {
            background: rgba(0, 219, 222, 0.1);
            border-color: #fc00ff;
        }
        
        .upload-icon {
            font-size: 4rem;
            color: #00dbde;
            margin-bottom: 1rem;
        }
        
        .upload-area p {
            margin-bottom: 1rem;
            color: #ccc;
        }
        
        .file-input {
            display: none;
        }
        
        .file-label {
            display: inline-block;
            background: linear-gradient(45deg, #00dbde, #fc00ff);
            color: white;
            padding: 10px 25px;
            border-radius: 5px;
            cursor: pointer;
            margin: 10px;
            transition: transform 0.3s;
        }
        
        .file-label:hover {
            transform: scale(1.05);
        }
        
        .upload-form {
            display: grid;
            gap: 1.5rem;
            max-width: 600px;
            margin: 0 auto;
        }
        
        .form-group {
            display: flex;
            flex-direction: column;
        }
        
        .form-group label {
            margin-bottom: 0.5rem;
            color: #00dbde;
            font-weight: 500;
        }
        
        .form-group input,
        .form-group select,
        .form-group textarea {
            padding: 12px;
            border-radius: 5px;
            border: 1px solid rgba(0, 219, 222, 0.3);
            background: rgba(255, 255, 255, 0.1);
            color: white;
            font-size: 1rem;
        }
        
        .form-group textarea {
            min-height: 100px;
            resize: vertical;
        }
        
        /* Music Library */
        .library-section {
            margin-bottom: 3rem;
        }
        
        .library-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem;
        }
        
        .library-header h3 {
            font-size: 2rem;
            color: #00dbde;
        }
        
        .search-box {
            display: flex;
            gap: 10px;
        }
        
        .search-box input {
            padding: 10px 15px;
            border-radius: 5px;
            border: 1px solid rgba(0, 219, 222, 0.3);
            background: rgba(255, 255, 255, 0.1);
            color: white;
            min-width: 300px;
        }
        
        .music-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 2rem;
        }
        
        .music-card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
            padding: 1.5rem;
            transition: transform 0.3s, box-shadow 0.3s;
            border: 1px solid rgba(0, 219, 222, 0.1);
        }
        
        .music-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
            border-color: #00dbde;
        }
        
        .music-cover {
            width: 100%;
            height: 200px;
            background: linear-gradient(45deg, #00dbde, #fc00ff);
            border-radius: 5px;
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            color: white;
            position: relative;
            overflow: hidden;
        }
        
        .music-cover img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .music-info h4 {
            font-size: 1.2rem;
            margin-bottom: 0.5rem;
            color: #fff;
        }
        
        .music-info p {
            color: #ccc;
            font-size: 0.9rem;
            margin-bottom: 0.5rem;
        }
        
        .music-player {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-top: 1rem;
        }
        
        .play-btn {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: #00dbde;
            border: none;
            color: white;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: background 0.3s;
        }
        
        .play-btn:hover {
            background: #fc00ff;
        }
        
        /* Statistics */
        .stats-section {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-bottom: 3rem;
        }
        
        .stat-card {
            background: rgba(255, 255, 255, 0.05);
            padding: 2rem;
            border-radius: 10px;
            text-align: center;
            border: 1px solid rgba(0, 219, 222, 0.1);
        }
        
        .stat-icon {
            font-size: 2.5rem;
            color: #00dbde;
            margin-bottom: 1rem;
        }
        
        .stat-number {
            font-size: 2.5rem;
            font-weight: bold;
            color: #fff;
            margin-bottom: 0.5rem;
        }
        
        /* GLOBAL MUSIC PLAYER */
        .global-player {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: rgba(0, 0, 0, 0.95);
            padding: 1rem;
            border-top: 2px solid #00dbde;
            display: none;
            z-index: 1001;
        }
        
        .player-content {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            align-items: center;
            gap: 2rem;
        }
        
        .player-info {
            flex: 1;
        }
        
        .player-controls {
            display: flex;
            align-items: center;
            gap: 1rem;
        }
        
        .player-btn {
            background: #00dbde;
            border: none;
            color: white;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            cursor: pointer;
        }
        
        .progress-bar {
            flex: 2;
            height: 4px;
            background: rgba(255, 255, 255, 0.2);
            border-radius: 2px;
            cursor: pointer;
            position: relative;
        }
        
        .progress-fill {
            position: absolute;
            height: 100%;
            background: #00dbde;
            border-radius: 2px;
            width: 0%;
        }
        
        .time-display {
            min-width: 100px;
            text-align: center;
            color: #ccc;
        }
        
        .volume-control {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        /* Footer */
        footer {
            background: rgba(0, 0, 0, 0.9);
            padding: 3rem 0;
            margin-top: 3rem;
            border-top: 2px solid #00dbde;
        }
        
        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 3rem;
        }
        
        .footer-section h4 {
            color: #00dbde;
            margin-bottom: 1rem;
            font-size: 1.2rem;
        }
        
        .footer-section p, .footer-section a {
            color: #ccc;
            margin-bottom: 0.5rem;
            display: block;
            text-decoration: none;
        }
        
        .footer-section a:hover {
            color: #00dbde;
        }
        
        .copyright {
            text-align: center;
            margin-top: 3rem;
            padding-top: 2rem;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            color: #999;
        }
        
        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 1001;
            align-items: center;
            justify-content: center;
        }
        
        .modal-content {
            background: #1a1a2e;
            padding: 2rem;
            border-radius: 10px;
            max-width: 500px;
            width: 90%;
            border: 2px solid #00dbde;
        }
        
        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1rem;
        }
        
        .close-modal {
            background: none;
            border: none;
            color: #fff;
            font-size: 1.5rem;
            cursor: pointer;
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                gap: 1rem;
            }
            
            nav ul {
                gap: 1rem;
            }
            
            .hero h2 {
                font-size: 2rem;
            }
            
            .upload-area {
                padding: 2rem 1rem;
            }
            
            .search-box {
                flex-direction: column;
            }
            
            .search-box input {
                min-width: auto;
            }
            
            .music-grid {
                grid-template-columns: 1fr;
            }
            
            .player-content {
                flex-direction: column;
                gap: 1rem;
            }
        }
        
        /* Loading Animation */
        .loading {
            display: none;
            text-align: center;
            margin: 2rem 0;
        }
        
        .spinner {
            border: 4px solid rgba(0, 219, 222, 0.3);
            border-radius: 50%;
            border-top: 4px solid #00dbde;
            width: 40px;
            height: 40px;
            animation: spin 1s linear infinite;
            margin: 0 auto;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        /* Spinning CD */
        .spinning {
            animation: spin 2s linear infinite;
        }
        
        /* File Preview */
        .file-preview {
            margin-top: 1rem;
            padding: 10px;
            background: rgba(0, 0, 0, 0.3);
            border-radius: 5px;
        }
        
        .file-preview-item {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 5px;
            padding: 5px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 3px;
        }
    </style>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
</head>
<body>
    <!-- Global Music Player -->
    <div class="global-player" id="globalPlayer">
        <div class="player-content">
            <div class="player-info">
                <h4 id="nowPlayingTitle">No track playing</h4>
                <p id="nowPlayingArtist">Select a track to play</p>
            </div>
            <div class="player-controls">
                <button class="player-btn" onclick="previousTrack()">
                    <i class="fas fa-step-backward"></i>
                </button>
                <button class="player-btn" onclick="togglePlay()" id="playPauseBtn">
                    <i class="fas fa-play"></i>
                </button>
                <button class="player-btn" onclick="nextTrack()">
                    <i class="fas fa-step-forward"></i>
                </button>
            </div>
            <div class="progress-bar" onclick="seekTrack(event)">
                <div class="progress-fill" id="progressFill"></div>
            </div>
            <div class="time-display">
                <span id="currentTime">0:00</span> / <span id="totalTime">0:00</span>
            </div>
            <div class="volume-control">
                <i class="fas fa-volume-up"></i>
                <input type="range" min="0" max="100" value="80" oninput="changeVolume(this.value)" style="width: 100px;">
            </div>
            <button class="player-btn" onclick="stopPlayer()">
                <i class="fas fa-stop"></i>
            </button>
        </div>
    </div>

    <!-- Header -->
    <header>
        <div class="container">
            <div class="header-content">
                <div class="logo">
                    <div class="logo-icon">🎵</div>
                    <h1>Tay Lee Music Hub</h1>
                </div>
                <nav>
                    <ul>
                        <li><a href="#home" class="active">Home</a></li>
                        <li><a href="#upload">Upload</a></li>
                        <li><a href="#library">Library</a></li>
                        <li><a href="#stats">Stats</a></li>
                        <li><a href="#about">About</a></li>
                    </ul>
                </nav>
            </div>
        </div>
    </header>

    <!-- Hero Section -->
    <section id="home" class="hero">
        <div class="container">
            <h2>Upload & Play YOUR Music</h2>
            <p>Upload your REAL music files and play them directly in your browser. No more sample tracks!</p>
            <button onclick="scrollToUpload()" class="cta-button">
                <i class="fas fa-cloud-upload-alt"></i> Upload Your Music
            </button>
        </div>
    </section>

    <!-- Upload Section -->
    <section id="upload" class="upload-section">
        <div class="container">
            <h3><i class="fas fa-upload"></i> Upload YOUR Music</h3>
            
            <div class="upload-area" id="uploadArea">
                <div class="upload-icon">
                    <i class="fas fa-music"></i>
                </div>
                <p>Drag & drop your REAL music files here</p>
                <p class="file-types">MP3, WAV, FLAC, M4A (Max 50MB per file)</p>
                <input type="file" id="musicFile" class="file-input" accept=".mp3,.wav,.flac,.m4a,.ogg,.aac" multiple>
                <label for="musicFile" class="file-label">
                    <i class="fas fa-folder-open"></i> Browse Your Music Files
                </label>
                <div id="selectedFiles" class="file-preview">
                    <!-- File preview will appear here -->
                </div>
            </div>

            <form class="upload-form" id="uploadForm">
                <div class="form-group">
                    <label for="trackTitle"><i class="fas fa-heading"></i> Track Title *</label>
                    <input type="text" id="trackTitle" placeholder="Enter your track title" required>
                </div>
                
                <div class="form-group">
                    <label for="artistName"><i class="fas fa-user"></i> Your Artist Name *</label>
                    <input type="text" id="artistName" placeholder="Enter your artist name" required>
                </div>
                
                <div class="form-group">
                    <label for="album"><i class="fas fa-compact-disc"></i> Album (Optional)</label>
                    <input type="text" id="album" placeholder="Enter album name">
                </div>
                
                <div class="form-group">
                    <label for="genre"><i class="fas fa-guitar"></i> Genre</label>
                    <select id="genre">
                        <option value="hiphop">Hip Hop</option>
                        <option value="rnb">R&B</option>
                        <option value="pop">Pop</option>
                        <option value="rock">Rock</option>
                        <option value="electronic">Electronic</option>
                        <option value="jazz">Jazz</option>
                        <option value="reggae">Reggae</option>
                        <option value="afrobeat">Afrobeat</option>
                        <option value="other">Other</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label for="description"><i class="fas fa-align-left"></i> Description (Optional)</label>
                    <textarea id="description" placeholder="Tell us about this track..."></textarea>
                </div>
                
                <div class="loading" id="uploadLoading">
                    <div class="spinner"></div>
                    <p>Processing your music file...</p>
                </div>
                
                <button type="submit" class="cta-button">
                    <i class="fas fa-cloud-upload-alt"></i> Upload & Save Track
                </button>
                <p style="text-align: center; color: #ccc; font-size: 0.9rem; margin-top: 10px;">
                    <i class="fas fa-info-circle"></i> Your music is stored in your browser (local storage)
                </p>
            </form>
        </div>
    </section>

    <!-- Music Library -->
    <section id="library" class="library-section">
        <div class="container">
            <div class="library-header">
                <h3><i class="fas fa-music"></i> YOUR Music Library</h3>
                <div class="search-box">
                    <input type="text" id="searchInput" placeholder="Search your tracks...">
                    <button class="cta-button" onclick="searchTracks()">
                        <i class="fas fa-search"></i> Search
                    </button>
                </div>
            </div>
            
            <div class="loading" id="libraryLoading">
                <div class="spinner"></div>
                <p>Loading your music library...</p>
            </div>
            
            <div id="noMusicMessage" style="display: none; text-align: center; padding: 3rem; color: #ccc;">
                <i class="fas fa-music" style="font-size: 3rem; margin-bottom: 1rem; display: block;"></i>
                <h3>No music yet</h3>
                <p>Upload your first track using the form above!</p>
            </div>
            
            <div class="music-grid" id="musicGrid">
                <!-- Your uploaded music will appear here -->
            </div>
        </div>
    </section>

    <!-- Statistics -->
    <section id="stats" class="stats-section">
        <div class="container">
            <div class="stat-card">
                <div class="stat-icon">
                    <i class="fas fa-music"></i>
                </div>
                <div class="stat-number" id="totalTracks">0</div>
                <p>Your Tracks</p>
            </div>
            
            <div class="stat-card">
                <div class="stat-icon">
                    <i class="fas fa-database"></i>
                </div>
                <div class="stat-number" id="storageUsed">0 MB</div>
                <p>Storage Used</p>
            </div>
            
            <div class="stat-card">
                <div class="stat-icon">
                    <i class="fas fa-users"></i>
                </div>
                <div class="stat-number" id="totalPlays">0</div>
                <p>Total Plays</p>
            </div>
            
            <div class="stat-card">
                <div class="stat-icon">
                    <i class="fas fa-calendar"></i>
                </div>
                <div class="stat-number" id="uploadsToday">0</div>
                <p>Uploads Today</p>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" style="padding: 3rem 0;">
        <div class="container">
            <div class="upload-section">
                <h3><i class="fas fa-info-circle"></i> How It Works</h3>
                <p style="margin-bottom: 1rem;">This platform stores your music files in YOUR browser's local storage. This means:</p>
                <ul style="margin-left: 2rem; margin-bottom: 2rem; color: #ccc;">
                    <li>✅ Your music stays on YOUR device</li>
                    <li>✅ No server storage needed</li>
                    <li>✅ Play your music instantly</li>
                    <li>✅ Works completely offline</li>
                    <li>✅ Private and secure</li>
                </ul>
                <p><strong>Note:</strong> If you clear browser cache, your uploaded music will be removed. For permanent storage, consider upgrading to server storage.</p>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-section">
                    <h4>Tay Lee Music Hub</h4>
                    <p>Your personal music upload platform. Upload and play YOUR music!</p>
                </div>
                
                <div class="footer-section">
                    <h4>Quick Links</h4>
                    <a href="#home">Home</a>
                    <a href="#upload">Upload Music</a>
                    <a href="#library">Your Library</a>
                    <a href="#stats">Statistics</a>
                </div>
                
                <div class="footer-section">
                    <h4>Contact</h4>
                    <p>Email: taylee@music.com</p>
                    <p>Support: support@tayleemusic.com</p>
                </div>
                
                <div class="footer-section">
                    <h4>Backup Your Music</h4>
                    <a href="#" onclick="backupMusic()">Download Backup</a>
                    <a href="#" onclick="restoreMusic()">Restore Backup</a>
                    <a href="#" onclick="clearAllMusic()">Clear All Music</a>
                </div>
            </div>
            
            <div class="copyright">
                <p>&copy; 2024 Tay Lee Music Hub. All rights reserved.</p>
                <p>Your music is stored locally in your browser.</p>
            </div>
        </div>
    </footer>

    <!-- Success Modal -->
    <div class="modal" id="successModal">
        <div class="modal-content">
            <div class="modal-header">
                <h3><i class="fas fa-check-circle" style="color: #4CAF50;"></i> Upload Successful!</h3>
                <button class="close-modal" onclick="closeModal()">&times;</button>
            </div>
            <p>Your music has been successfully uploaded and saved!</p>
            <p id="uploadDetails"></p>
            <button class="cta-button" onclick="closeModal()" style="margin-top: 1rem;">
                Play Now
            </button>
        </div>
    </div>

    <!-- Backup Modal -->
    <div class="modal" id="backupModal">
        <div class="modal-content">
            <div class="modal-header">
                <h3><i class="fas fa-download" style="color: #00dbde;"></i> Backup Your Music</h3>
                <button class="close-modal" onclick="closeBackupModal()">&times;</button>
            </div>
            <p>Download a backup file of all your music data:</p>
            <button class="cta-button" onclick="downloadBackup()" style="margin: 1rem 0;">
                <i class="fas fa-file-download"></i> Download Backup File
            </button>
            <p style="color: #ccc; font-size: 0.9rem;">
                Save this file to restore your music library later.
            </p>
        </div>
    </div>

    <!-- Restore Modal -->
    <div class="modal" id="restoreModal">
        <div class="modal-content">
            <div class="modal-header">
                <h3><i class="fas fa-upload" style="color: #00dbde;"></i> Restore Music Backup</h3>
                <button class="close-modal" onclick="closeRestoreModal()">&times;</button>
            </div>
            <p>Select your backup file to restore your music:</p>
            <input type="file" id="backupFile" accept=".json" style="margin: 1rem 0; padding: 10px; width: 100%;">
            <button class="cta-button" onclick="restoreFromBackup()">
                <i class="fas fa-file-upload"></i> Restore Backup
            </button>
            <p style="color: #ff6b6b; font-size: 0.9rem; margin-top: 1rem;">
                Warning: This will replace your current music library!
            </p>
        </div>
    </div>

    <script>
        // REAL MUSIC PLAYER SYSTEM WITH LOCAL STORAGE
        const audioPlayer = new Audio();
        let currentTrackIndex = -1;
        let isPlaying = false;
        let tracks = [];
        let progressInterval;
        
        // DOM Elements
        const uploadArea = document.getElementById('uploadArea');
        const musicFileInput = document.getElementById('musicFile');
        const selectedFiles = document.getElementById('selectedFiles');
        const uploadForm = document.getElementById('uploadForm');
        const musicGrid = document.getElementById('musicGrid');
        const searchInput = document.getElementById('searchInput');
        const libraryLoading = document.getElementById('libraryLoading');
        const uploadLoading = document.getElementById('uploadLoading');
        const noMusicMessage = document.getElementById('noMusicMessage');
        
        // Player elements
        const globalPlayer = document.getElementById('globalPlayer');
        const nowPlayingTitle = document.getElementById('nowPlayingTitle');
        const nowPlayingArtist = document.getElementById('nowPlayingArtist');
        const playPauseBtn = document.getElementById('playPauseBtn');
        const progressFill = document.getElementById('progressFill');
        const currentTime = document.getElementById('currentTime');
        const totalTime = document.getElementById('totalTime');
        
        // Statistics elements
        const totalTracksEl = document.getElementById('totalTracks');
        const storageUsedEl = document.getElementById('storageUsed');
        const totalPlaysEl = document.getElementById('totalPlays');
        const uploadsTodayEl = document.getElementById('uploadsToday');
        
        // Initialize the app
        function initApp() {
            // Load music from local storage
            loadMusicFromStorage();
            
            // Set up event listeners
            setupEventListeners();
            
            // Setup audio player events
            setupAudioPlayer();
            
            // Hide loading
            setTimeout(() => {
                libraryLoading.style.display = 'none';
                updateNoMusicMessage();
            }, 500);
        }
        
        // Load music from local storage
        function loadMusicFromStorage() {
            const savedMusic = localStorage.getItem('tayLeeMusicLibrary');
            if (savedMusic) {
                try {
                    tracks = JSON.parse(savedMusic);
                    updateStatistics();
                    renderMusicLibrary();
                } catch (e) {
                    console.error("Error loading music:", e);
                    tracks = [];
                }
            } else {
                tracks = [];
            }
        }
        
        // Save music to local storage
        function saveMusicToStorage() {
            try {
                localStorage.setItem('tayLeeMusicLibrary', JSON.stringify(tracks));
                console.log("Music saved to storage:", tracks.length, "tracks");
            } catch (e) {
                console.error("Error saving music:", e);
                // If storage is full, show warning
                if (e.name === 'QuotaExceededError') {
                    alert("Storage is full! Please delete some tracks or clear browser cache.");
                }
            }
        }
        
        // Set up audio player events
        function setupAudioPlayer() {
            audioPlayer.addEventListener('timeupdate', updateProgress);
            audioPlayer.addEventListener('loadedmetadata', function() {
                totalTime.textContent = formatTime(audioPlayer.duration);
            });
            audioPlayer.addEventListener('ended', nextTrack);
            audioPlayer.addEventListener('error', function(e) {
                console.log("Audio error:", e);
                alert("Error playing audio. Please check the file format.");
            });
            
            // Set initial volume
            audioPlayer.volume = 0.8;
        }
        
        // Handle file selection
        let selectedFile = null;
        
        function handleFiles(files) {
            selectedFiles.innerHTML = '';
            
            if (files.length > 0) {
                selectedFile = files[0]; // Store the first file
                
                const fileItem = document.createElement('div');
                fileItem.className = 'file-preview-item';
                fileItem.innerHTML = `
                    <i class="fas fa-music" style="color: #00dbde;"></i>
                    <div style="flex: 1;">
                        <strong>${selectedFile.name}</strong>
                        <div style="font-size: 0.8em; color: #ccc;">
                            ${formatFileSize(selectedFile.size)} • ${selectedFile.type}
                        </div>
                    </div>
                    <i class="fas fa-check-circle" style="color: #4CAF50;"></i>
                `;
                selectedFiles.appendChild(fileItem);
                
                // Auto-fill track title from filename
                const trackTitle = document.getElementById('trackTitle');
                if (!trackTitle.value) {
                    const fileName = selectedFile.name.replace(/\.[^/.]+$/, ""); // Remove extension
                    trackTitle.value = fileName;
                }
            } else {
                selectedFiles.innerHTML = '<p style="color: #ccc; text-align: center;">No file selected</p>';
                selectedFile = null;
            }
        }
        
        // Format file size
        function formatFileSize(bytes) {
            if (bytes === 0) return '0 Bytes';
            const k = 1024;
            const sizes = ['Bytes', 'KB', 'MB', 'GB'];
            const i = Math.floor(Math.log(bytes) / Math.log(k));
            return parseFloat((bytes / Math.pow(k, i)).toFixed(2)) + ' ' + sizes[i];
        }
        
        // Handle music upload
        async function handleUpload(e) {
            e.preventDefault();
            
            if (!selectedFile) {
                alert('Please select a music file to upload.');
                return;
            }
            
            // Validate file size (max 50MB)
            if (selectedFile.size > 50 * 1024 * 1024) {
                alert('File too large! Maximum size is 50MB.');
                return;
            }
            
            // Validate file type
            const validTypes = ['audio/mpeg', 'audio/wav', 'audio/flac', 'audio/mp4', 'audio/ogg', 'audio/aac'];
            if (!validTypes.includes(selectedFile.type.toLowerCase())) {
                alert('Invalid file type! Please upload MP3, WAV, FLAC, M4A, OGG, or AAC files.');
                return;
            }
            
            const title = document.getElementById('trackTitle').value;
            const artist = document.getElementById('artistName').value;
            const album = document.getElementById('album').value;
            const genre = document.getElementById('genre').value;
            const description = document.getElementById('description').value;
            
            if (!title || !artist) {
                alert('Please fill in track title and artist name.');
                return;
            }
            
            // Show loading
            uploadLoading.style.display = 'block';
            
            // Convert file to base64 for storage
            const reader = new FileReader();
            
            reader.onload = function(e) {
                // Create new track object with REAL file data
                const newTrack = {
                    id: Date.now(), // Unique ID
                    title: title,
                    artist: artist,
                    album: album || 'Single',
                    genre: genre,
                    description: description,
                    duration: '--:--', // Will be updated when played
                    size: formatFileSize(selectedFile.size),
                    plays: 0,
                    uploadDate: new Date().toISOString().split('T')[0],
                    fileType: selectedFile.type,
                    fileName: selectedFile.name,
                    audioData: e.target.result, // Base64 encoded audio
                    fileSize: selectedFile.size
                };
                
                // Add to tracks array
                tracks.unshift(newTrack);
                
                // Save to storage
                saveMusicToStorage();
                
                // Update UI
                renderMusicLibrary();
                updateStatistics();
                updateNoMusicMessage();
                
                // Reset form
                uploadForm.reset();
                selectedFiles.innerHTML = '<p style="color: #ccc; text-align: center;">No file selected</p>';
                selectedFile = null;
                
                // Hide loading
                uploadLoading.style.display = 'none';
                
                // Show success modal
                showSuccessModal(newTrack);
            };
            
            reader.onerror = function() {
                alert('Error reading file. Please try again.');
                uploadLoading.style.display = 'none';
            };
            
            // Read file as base64
            reader.readAsDataURL(selectedFile);
        }
        
        // Play a specific track
        function playTrack(trackId) {
            const trackIndex = tracks.findIndex(t => t.id === trackId);
            if (trackIndex === -1) return;
            
            const track = tracks[trackIndex];
            
            // Update play count
            track.plays++;
            updateStatistics();
            saveMusicToStorage();
            
            // If same track is already playing, toggle pause
            if (currentTrackIndex === trackIndex && isPlaying) {
                togglePlay();
                return;
            }
            
            // Set current track
            currentTrackIndex = trackIndex;
            
            // Load and play the track from base64 data
            audioPlayer.src = track.audioData;
            audioPlayer.play()
                .then(() => {
                    isPlaying = true;
                    updatePlayerUI();
                    showPlayer();
                    startProgressUpdate();
                    updatePlayButtons();
                    
                    // Update player display
                    nowPlayingTitle.textContent = track.title;
                    nowPlayingArtist.textContent = track.artist;
                    
                    // Update the CD spinning animation
                    updateCDAnimation();
                    
                    // Update duration when metadata loads
                    audioPlayer.addEventListener('loadedmetadata', function() {
                        if (!track.duration || track.duration === '--:--') {
                            track.duration = formatTime(audioPlayer.duration);
                            saveMusicToStorage();
                            renderMusicLibrary();
                        }
                    }, { once: true });
                })
                .catch(error => {
                    console.log("Playback error:", error);
                    alert("Error playing track. The file format might not be supported.");
                });
        }
        
        // Toggle play/pause
        function togglePlay() {
            if (!tracks[currentTrackIndex]) return;
            
            if (isPlaying) {
                audioPlayer.pause();
                isPlaying = false;
            } else {
                audioPlayer.play();
                isPlaying = true;
            }
            updatePlayerUI();
            updatePlayButtons();
            updateCDAnimation();
        }
        
        // Update player UI
        function updatePlayerUI() {
            const icon = playPauseBtn.querySelector('i');
            if (isPlaying) {
                icon.className = 'fas fa-pause';
            } else {
                icon.className = 'fas fa-play';
            }
        }
        
        // Update CD animation
        function updateCDAnimation() {
            // Remove spinning from all CDs
            document.querySelectorAll('.music-cover i').forEach(icon => {
                icon.classList.remove('spinning');
            });
            
            // Add spinning to current track if playing
            if (currentTrackIndex >= 0 && isPlaying) {
                const currentCard = document.querySelector(`.music-card[data-track-id="${tracks[currentTrackIndex].id}"] .music-cover i`);
                if (currentCard) {
                    currentCard.classList.add('spinning');
                }
            }
        }
        
        // Update progress bar
        function updateProgress() {
            if (!audioPlayer.duration) return;
            
            const progress = (audioPlayer.currentTime / audioPlayer.duration) * 100;
            progressFill.style.width = `${progress}%`;
            currentTime.textContent = formatTime(audioPlayer.currentTime);
        }
        
        // Start progress update interval
        function startProgressUpdate() {
            clearInterval(progressInterval);
            progressInterval = setInterval(updateProgress, 1000);
        }
        
        // Format time (seconds to MM:SS)
        function formatTime(seconds) {
            if (isNaN(seconds)) return '--:--';
            const mins = Math.floor(seconds / 60);
            const secs = Math.floor(seconds % 60);
            return `${mins}:${secs.toString().padStart(2, '0')}`;
        }
        
        // Seek to position in track
        function seekTrack(event) {
            if (!audioPlayer.duration) return;
            
            const progressBar = event.currentTarget;
            const rect = progressBar.getBoundingClientRect();
            const x = event.clientX - rect.left;
            const percentage = x / rect.width;
            
            audioPlayer.currentTime = percentage * audioPlayer.duration;
        }
        
        // Change volume
        function changeVolume(value) {
            audioPlayer.volume = value / 100;
        }
        
        // Next track
        function nextTrack() {
            if (tracks.length === 0) return;
            
            currentTrackIndex = (currentTrackIndex + 1) % tracks.length;
            playTrack(tracks[currentTrackIndex].id);
        }
        
        // Previous track
        function previousTrack() {
            if (tracks.length === 0) return;
            
            currentTrackIndex = (currentTrackIndex - 1 + tracks.length) % tracks.length;
            playTrack(tracks[currentTrackIndex].id);
        }
        
        // Stop player
        function stopPlayer() {
            audioPlayer.pause();
            audioPlayer.currentTime = 0;
            isPlaying = false;
            updatePlayerUI();
            updatePlayButtons();
            updateCDAnimation();
            progressFill.style.width = '0%';
            currentTime.textContent = '0:00';
        }
        
        // Show/hide player
        function showPlayer() {
            globalPlayer.style.display = 'block';
        }
        
        // Update play buttons in cards
        function updatePlayButtons() {
            document.querySelectorAll('.play-btn').forEach((btn) => {
                const trackId = parseInt(btn.closest('.music-card').dataset.trackId);
                const icon = btn.querySelector('i');
                if (currentTrackIndex >= 0 && tracks[currentTrackIndex].id === trackId && isPlaying) {
                    icon.className = 'fas fa-pause';
                } else {
                    icon.className = 'fas fa-play';
                }
            });
        }
        
        // Set up event listeners
        function setupEventListeners() {
            // Drag and drop events
            uploadArea.addEventListener('dragover', (e) => {
                e.preventDefault();
                uploadArea.classList.add('drag-over');
            });
            
            uploadArea.addEventListener('dragleave', () => {
                uploadArea.classList.remove('drag-over');
            });
            
            uploadArea.addEventListener('drop', (e) => {
                e.preventDefault();
                uploadArea.classList.remove('drag-over');
                handleFiles(e.dataTransfer.files);
                musicFileInput.files = e.dataTransfer.files;
            });
            
            // File input change
            musicFileInput.addEventListener('change', (e) => {
                handleFiles(e.target.files);
            });
            
            // Form submission
            uploadForm.addEventListener('submit', handleUpload);
            
            // Search input
            searchInput.addEventListener('keyup', (e) => {
                if (e.key === 'Enter') {
                    searchTracks();
                }
            });
        }
        
        // Show success modal
        function showSuccessModal(track) {
            const modal = document.getElementById('successModal');
            const details = document.getElementById('uploadDetails');
            
            details.textContent = `"${track.title}" by ${track.artist} has been added to your library.`;
            modal.style.display = 'flex';
        }
        
        // Close modal
        function closeModal() {
            document.getElementById('successModal').style.display = 'none';
        }
        
        // Render music library
        function renderMusicLibrary(filteredTracks = tracks) {
            musicGrid.innerHTML = '';
            
            if (filteredTracks.length === 0) {
                updateNoMusicMessage();
                return;
            }
            
            filteredTracks.forEach((track) => {
                const isCurrent = currentTrackIndex >= 0 && tracks[currentTrackIndex].id === track.id;
                const isPlayingCurrent = isCurrent && isPlaying;
                
                const card = document.createElement('div');
                card.className = 'music-card';
                card.dataset.trackId = track.id;
                card.innerHTML = `
                    <div class="music-cover">
                        <i class="fas fa-compact-disc ${isPlayingCurrent ? 'spinning' : ''}"></i>
                    </div>
                    <div class="music-info">
                        <h4>${track.title}</h4>
                        <p><i class="fas fa-user"></i> ${track.artist}</p>
                        <p><i class="fas fa-compact-disc"></i> ${track.album}</p>
                        <p><i class="fas fa-guitar"></i> ${track.genre}</p>
                        <p><i class="fas fa-clock"></i> ${track.duration} • ${track.size}</p>
                        <p><i class="fas fa-play-circle"></i> ${track.plays} plays</p>
                        <p>${track.description || 'No description'}</p>
                        <p style="font-size: 0.8em; color: #888;">
                            <i class="fas fa-calendar"></i> Uploaded: ${track.uploadDate}
                        </p>
                    </div>
                    <div class="music-player">
                        <button class="play-btn">
                            <i class="fas ${isPlayingCurrent ? 'fa-pause' : 'fa-play'}"></i>
                        </button>
                        <div style="flex: 1;">
                            <div style="height: 4px; background: rgba(255,255,255,0.1); border-radius: 2px; margin-top: 5px;"></div>
                        </div>
                        <button class="file-label delete-btn" style="padding: 5px 10px; background: #ff4757;">
                            <i class="fas fa-trash"></i>
                        </button>
                    </div>
                `;
                
                // Add click event to play button
                const playBtn = card.querySelector('.play-btn');
                playBtn.addEventListener('click', () => playTrack(track.id));
                
                // Add click event to delete button
                const deleteBtn = card.querySelector('.delete-btn');
                deleteBtn.addEventListener('click', (e) => {
                    e.stopPropagation();
                    if (confirm(`Delete "${track.title}" by ${track.artist}?`)) {
                        deleteTrack(track.id);
                    }
                });
                
                musicGrid.appendChild(card);
            });
            
            noMusicMessage.style.display = 'none';
        }
        
        // Delete a track
        function deleteTrack(trackId) {
            const trackIndex = tracks.findIndex(t => t.id === trackId);
            if (trackIndex === -1) return;
            
            // If deleting currently playing track, stop it
            if (currentTrackIndex >= 0 && tracks[currentTrackIndex].id === trackId) {
                stopPlayer();
                currentTrackIndex = -1;
            }
            
            // Remove track
            tracks.splice(trackIndex, 1);
            
            // Save to storage
            saveMusicToStorage();
            
            // Update UI
            renderMusicLibrary();
            updateStatistics();
            updateNoMusicMessage();
        }
        
        // Update no music message
        function updateNoMusicMessage() {
            if (tracks.length === 0) {
                noMusicMessage.style.display = 'block';
                musicGrid.innerHTML = '';
            } else {
                noMusicMessage.style.display = 'none';
            }
        }
        
        // Search tracks
        function searchTracks() {
            const query = searchInput.value.toLowerCase();
            
            if (query.trim() === '') {
                renderMusicLibrary();
                return;
            }
            
            const filtered = tracks.filter(track =>
                track.title.toLowerCase().includes(query) ||
                track.artist.toLowerCase().includes(query) ||
                track.album.toLowerCase().includes(query) ||
                track.genre.toLowerCase().includes(query) ||
                (track.description && track.description.toLowerCase().includes(query))
            );
            
            renderMusicLibrary(filtered);
        }
        
        // Update statistics
        function updateStatistics() {
            // Calculate totals
            const totalTracks = tracks.length;
            const totalStorage = tracks.reduce((sum, track) => {
                return sum + (track.fileSize || 0);
            }, 0);
            const totalPlays = tracks.reduce((sum, track) => {
                return sum + (track.plays || 0);
            }, 0);
            
            // Get today's date
            const today = new Date().toISOString().split('T')[0];
            const uploadsToday = tracks.filter(track => 
                track.uploadDate === today
            ).length;
            
            // Update DOM
            totalTracksEl.textContent = totalTracks;
            storageUsedEl.textContent = formatFileSize(totalStorage);
            totalPlaysEl.textContent = totalPlays;
            uploadsTodayEl.textContent = uploadsToday;
        }
        
        // Scroll to upload section
        function scrollToUpload() {
            document.getElementById('upload').scrollIntoView({
                behavior: 'smooth'
            });
        }
        
        // Backup functions
        function backupMusic() {
            document.getElementById('backupModal').style.display = 'flex';
        }
        
        function closeBackupModal() {
            document.getElementById('backupModal').style.display = 'none';
        }
        
        function downloadBackup() {
            const backupData = {
                version: '1.0',
                date: new Date().toISOString(),
                tracks: tracks
            };
            
            const dataStr = JSON.stringify(backupData, null, 2);
            const dataUri = 'data:application/json;charset=utf-8,'+ encodeURIComponent(dataStr);
            
            const exportFileDefaultName = `taylee-music-backup-${new Date().toISOString().split('T')[0]}.json`;
            
            const linkElement = document.createElement('a');
            linkElement.setAttribute('href', dataUri);
            linkElement.setAttribute('download', exportFileDefaultName);
            linkElement.click();
            
            closeBackupModal();
        }
        
        function restoreMusic() {
            document.getElementById('restoreModal').style.display = 'flex';
        }
        
        function closeRestoreModal() {
            document.getElementById('restoreModal').style.display = 'none';
        }
        
        function restoreFromBackup() {
            const fileInput = document.getElementById('backupFile');
            if (!fileInput.files.length) {
                alert('Please select a backup file.');
                return;
            }
            
            const file = fileInput.files[0];
            const reader = new FileReader();
            
            reader.onload = function(e) {
                try {
                    const backupData = JSON.parse(e.target.result);
                    
                    if (!backupData.tracks || !Array.isArray(backupData.tracks)) {
                        throw new Error('Invalid backup file format');
                    }
                    
                    if (confirm(`Restore ${backupData.tracks.length} tracks? This will replace your current library.`)) {
                        tracks = backupData.tracks;
                        saveMusicToStorage();
                        renderMusicLibrary();
                        updateStatistics();
                        updateNoMusicMessage();
                        alert('Music library restored successfully!');
                        closeRestoreModal();
                    }
                } catch (error) {
                    alert('Error restoring backup: ' + error.message);
                }
            };
            
            reader.onerror = function() {
                alert('Error reading backup file.');
            };
            
            reader.readAsText(file);
        }
        
        function clearAllMusic() {
            if (confirm('Delete ALL your music? This cannot be undone!')) {
                tracks = [];
                saveMusicToStorage();
                stopPlayer();
                renderMusicLibrary();
                updateStatistics();
                updateNoMusicMessage();
                alert('All music cleared.');
            }
        }
        
        // Initialize the app when page loads
        document.addEventListener('DOMContentLoaded', initApp);
        
        // Close modal if clicked outside
        window.onclick = function(event) {
            const modals = ['successModal', 'backupModal', 'restoreModal'];
            modals.forEach(modalId => {
                const modal = document.getElementById(modalId);
                if (event.target === modal) {
                    modal.style.display = 'none';
                }
            });
        }
    </script>
</body>
</html>
