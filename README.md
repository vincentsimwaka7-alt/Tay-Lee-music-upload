<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tay Lee Music Hub | Upload & Share Your Music</title>
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
            <h2>Share Your Music With The World</h2>
            <p>Upload, manage, and share your music collection. Built for musicians by Tay Lee.</p>
            <button onclick="scrollToUpload()" class="cta-button">
                <i class="fas fa-cloud-upload-alt"></i> Upload Your First Track
            </button>
        </div>
    </section>

    <!-- Upload Section -->
    <section id="upload" class="upload-section">
        <div class="container">
            <h3><i class="fas fa-upload"></i> Upload Music</h3>
            
            <div class="upload-area" id="uploadArea">
                <div class="upload-icon">
                    <i class="fas fa-music"></i>
                </div>
                <p>Drag & drop your music files here</p>
                <p class="file-types">MP3, WAV, FLAC, M4A (Max 50MB)</p>
                <input type="file" id="musicFile" class="file-input" accept=".mp3,.wav,.flac,.m4a" multiple>
                <label for="musicFile" class="file-label">
                    <i class="fas fa-folder-open"></i> Browse Files
                </label>
                <p id="selectedFiles">No files selected</p>
            </div>

            <form class="upload-form" id="uploadForm">
                <div class="form-group">
                    <label for="trackTitle"><i class="fas fa-heading"></i> Track Title</label>
                    <input type="text" id="trackTitle" placeholder="Enter track title" required>
                </div>
                
                <div class="form-group">
                    <label for="artistName"><i class="fas fa-user"></i> Artist Name</label>
                    <input type="text" id="artistName" placeholder="Enter artist name" required>
                </div>
                
                <div class="form-group">
                    <label for="album"><i class="fas fa-compact-disc"></i> Album (Optional)</label>
                    <input type="text" id="album" placeholder="Enter album name">
                </div>
                
                <div class="form-group">
                    <label for="genre"><i class="fas fa-guitar"></i> Genre</label>
                    <select id="genre">
                        <option value="pop">Pop</option>
                        <option value="rock">Rock</option>
                        <option value="hiphop">Hip Hop</option>
                        <option value="jazz">Jazz</option>
                        <option value="electronic">Electronic</option>
                        <option value="classical">Classical</option>
                        <option value="rnb">R&B</option>
                        <option value="country">Country</option>
                        <option value="other">Other</option>
                    </select>
                </div>
                
                <div class="form-group">
                    <label for="description"><i class="fas fa-align-left"></i> Description</label>
                    <textarea id="description" placeholder="Tell us about this track..."></textarea>
                </div>
                
                <div class="loading" id="uploadLoading">
                    <div class="spinner"></div>
                    <p>Uploading your music...</p>
                </div>
                
                <button type="submit" class="cta-button">
                    <i class="fas fa-cloud-upload-alt"></i> Upload Track
                </button>
            </form>
        </div>
    </section>

    <!-- Music Library -->
    <section id="library" class="library-section">
        <div class="container">
            <div class="library-header">
                <h3><i class="fas fa-music"></i> Music Library</h3>
                <div class="search-box">
                    <input type="text" id="searchInput" placeholder="Search tracks...">
                    <button class="cta-button" onclick="searchTracks()">
                        <i class="fas fa-search"></i> Search
                    </button>
                </div>
            </div>
            
            <div class="loading" id="libraryLoading">
                <div class="spinner"></div>
                <p>Loading music library...</p>
            </div>
            
            <div class="music-grid" id="musicGrid">
                <!-- Music cards will be dynamically added here -->
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
                <p>Total Tracks</p>
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
                <h3><i class="fas fa-info-circle"></i> About Tay Lee Music Hub</h3>
                <p style="margin-bottom: 1rem;">Welcome to your personal music upload platform! This website allows you to:</p>
                <ul style="margin-left: 2rem; margin-bottom: 2rem; color: #ccc;">
                    <li>Upload and store your music files</li>
                    <li>Organize your music library</li>
                    <li>Play tracks directly in the browser</li>
                    <li>Track your upload statistics</li>
                    <li>Share your music with others</li>
                </ul>
                <p>Built with ❤️ by Tay Lee for musicians and music lovers.</p>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-section">
                    <h4>Tay Lee Music Hub</h4>
                    <p>Your personal music upload platform. Share your sound with the world.</p>
                </div>
                
                <div class="footer-section">
                    <h4>Quick Links</h4>
                    <a href="#home">Home</a>
                    <a href="#upload">Upload Music</a>
                    <a href="#library">Music Library</a>
                    <a href="#stats">Statistics</a>
                </div>
                
                <div class="footer-section">
                    <h4>Contact</h4>
                    <p>Email: contact@tayleemusic.com</p>
                    <p>Support: support@tayleemusic.com</p>
                </div>
                
                <div class="footer-section">
                    <h4>Legal</h4>
                    <a href="#">Terms of Service</a>
                    <a href="#">Privacy Policy</a>
                    <a href="#">Copyright Info</a>
                </div>
            </div>
            
            <div class="copyright">
                <p>&copy; 2024 Tay Lee Music Hub. All rights reserved.</p>
                <p>This is a demo music upload platform.</p>
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
            <p>Your music has been successfully uploaded to Tay Lee Music Hub.</p>
            <p id="uploadDetails"></p>
            <button class="cta-button" onclick="closeModal()" style="margin-top: 1rem;">
                Continue
            </button>
        </div>
    </div>

    <script>
        // REAL MUSIC PLAYER SYSTEM
        const audioPlayer = new Audio();
        let currentTrackIndex = -1;
        let isPlaying = false;
        let tracks = [];
        let progressInterval;
        
        // Sample tracks with REAL music URLs (copyright-free music)
        const sampleTracks = [
            {
                id: 1,
                title: "Midnight Dreams",
                artist: "Tay Lee",
                album: "Night Vibes",
                genre: "Electronic",
                description: "Chill electronic track perfect for late nights",
                duration: "3:45",
                size: "8.2 MB",
                plays: 42,
                uploadDate: "2024-01-15",
                audioUrl: "https://assets.mixkit.co/music/preview/mixkit-tech-house-vibes-130.mp3"
            },
            {
                id: 2,
                title: "Summer Breeze",
                artist: "Tay Lee",
                album: "Seasonal Mix",
                genre: "Pop",
                description: "Upbeat pop track for summer days",
                duration: "4:12",
                size: "9.5 MB",
                plays: 67,
                uploadDate: "2024-02-10",
                audioUrl: "https://assets.mixkit.co/music/preview/mixkit-driving-ambition-32.mp3"
            },
            {
                id: 3,
                title: "Urban Echoes",
                artist: "City Beats",
                album: "City Sounds",
                genre: "Hip Hop",
                description: "Urban hip hop with smooth beats",
                duration: "3:28",
                size: "7.8 MB",
                plays: 31,
                uploadDate: "2024-03-05",
                audioUrl: "https://assets.mixkit.co/music/preview/mixkit-deep-urban-623.mp3"
            },
            {
                id: 4,
                title: "Ocean Waves",
                artist: "Tay Lee",
                album: "Nature Sounds",
                genre: "Ambient",
                description: "Relaxing ambient ocean sounds",
                duration: "5:20",
                size: "10.1 MB",
                plays: 89,
                uploadDate: "2024-03-20",
                audioUrl: "https://assets.mixkit.co/music/preview/mixkit-soothing-wind-567.mp3"
            },
            {
                id: 5,
                title: "Neon Lights",
                artist: "Synth Wave",
                album: "Cyber Dreams",
                genre: "Synthwave",
                description: "80s inspired synthwave track",
                duration: "4:05",
                size: "8.9 MB",
                plays: 54,
                uploadDate: "2024-04-01",
                audioUrl: "https://assets.mixkit.co/music/preview/mixkit-synthwave-01-464.mp3"
            },
            {
                id: 6,
                title: "Mountain High",
                artist: "Tay Lee",
                album: "Adventure Mix",
                genre: "Rock",
                description: "Epic rock instrumental",
                duration: "3:55",
                size: "9.2 MB",
                plays: 38,
                uploadDate: "2024-04-15",
                audioUrl: "https://assets.mixkit.co/music/preview/mixkit-epic-trailer-687.mp3"
            }
        ];
        
        // Music data storage
        let musicLibrary = [];
        let totalStorage = 0;
        let totalPlays = 0;
        
        // DOM Elements
        const uploadArea = document.getElementById('uploadArea');
        const musicFileInput = document.getElementById('musicFile');
        const selectedFiles = document.getElementById('selectedFiles');
        const uploadForm = document.getElementById('uploadForm');
        const musicGrid = document.getElementById('musicGrid');
        const searchInput = document.getElementById('searchInput');
        const libraryLoading = document.getElementById('libraryLoading');
        const uploadLoading = document.getElementById('uploadLoading');
        
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
            // Load sample data
            musicLibrary = [...sampleTracks];
            tracks = [...sampleTracks];
            
            // Calculate initial stats
            updateStatistics();
            
            // Render music library
            renderMusicLibrary();
            
            // Set up event listeners
            setupEventListeners();
            
            // Setup audio player events
            setupAudioPlayer();
            
            // Simulate library loading
            setTimeout(() => {
                libraryLoading.style.display = 'none';
            }, 1000);
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
                // Try fallback URL
                if (currentTrackIndex >= 0 && tracks[currentTrackIndex]) {
                    loadFallbackAudio();
                }
            });
            
            // Set initial volume
            audioPlayer.volume = 0.8;
        }
        
        // Load fallback audio
        function loadFallbackAudio() {
            const fallbackUrls = [
                "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3",
                "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-2.mp3",
                "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-3.mp3"
            ];
            const randomUrl = fallbackUrls[Math.floor(Math.random() * fallbackUrls.length)];
            audioPlayer.src = randomUrl;
            audioPlayer.play().catch(e => console.log("Fallback also failed:", e));
        }
        
        // Play a specific track
        function playTrack(trackId) {
            console.log("Playing track:", trackId);
            const trackIndex = tracks.findIndex(t => t.id === trackId);
            if (trackIndex === -1) {
                console.log("Track not found:", trackId);
                return;
            }
            
            const track = tracks[trackIndex];
            console.log("Found track:", track.title);
            
            // Update play count
            track.plays++;
            updateStatistics();
            
            // If same track is already playing, toggle pause
            if (currentTrackIndex === trackIndex && isPlaying) {
                togglePlay();
                return;
            }
            
            // Set current track
            currentTrackIndex = trackIndex;
            
            // Load and play the track
            audioPlayer.src = track.audioUrl;
            audioPlayer.play()
                .then(() => {
                    console.log("Playback started successfully");
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
                })
                .catch(error => {
                    console.log("Playback error:", error);
                    loadFallbackAudio();
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
                const currentCard = document.querySelector(`.music-card:nth-child(${currentTrackIndex + 1}) .music-cover i`);
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
            document.querySelectorAll('.play-btn').forEach((btn, index) => {
                const icon = btn.querySelector('i');
                if (index === currentTrackIndex && isPlaying) {
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
        
        // Handle selected files
        function handleFiles(files) {
            if (files.length > 0) {
                const fileNames = Array.from(files).map(file => file.name).join(', ');
                selectedFiles.textContent = `Selected: ${files.length} file(s) - ${fileNames}`;
                selectedFiles.style.color = '#00dbde';
            } else {
                selectedFiles.textContent = 'No files selected';
                selectedFiles.style.color = '#ccc';
            }
        }
        
        // Handle music upload
        function handleUpload(e) {
            e.preventDefault();
            
            const title = document.getElementById('trackTitle').value;
            const artist = document.getElementById('artistName').value;
            const album = document.getElementById('album').value;
            const genre = document.getElementById('genre').value;
            const description = document.getElementById('description').value;
            const files = musicFileInput.files;
            
            if (files.length === 0) {
                alert('Please select at least one music file to upload.');
                return;
            }
            
            // Show loading
            uploadLoading.style.display = 'block';
            
            // Simulate upload process
            setTimeout(() => {
                // Create new music object with demo audio URL
                const demoUrls = [
                    "https://assets.mixkit.co/music/preview/mixkit-tech-house-vibes-130.mp3",
                    "https://assets.mixkit.co/music/preview/mixkit-driving-ambition-32.mp3",
                    "https://assets.mixkit.co/music/preview/mixkit-deep-urban-623.mp3",
                    "https://assets.mixkit.co/music/preview/mixkit-soothing-wind-567.mp3"
                ];
                const randomUrl = demoUrls[Math.floor(Math.random() * demoUrls.length)];
                
                const newTrack = {
                    id: musicLibrary.length + 1,
                    title: title,
                    artist: artist,
                    album: album || 'Single',
                    genre: genre,
                    description: description,
                    duration: Math.floor(Math.random() * 4 + 2) + ':' + 
                              (Math.floor(Math.random() * 60)).toString().padStart(2, '0'),
                    size: (Math.random() * 10 + 5).toFixed(1) + ' MB',
                    plays: 0,
                    uploadDate: new Date().toISOString().split('T')[0],
                    audioUrl: randomUrl
                };
                
                // Add to library
                musicLibrary.unshift(newTrack);
                tracks.unshift(newTrack);
                
                // Update UI
                renderMusicLibrary();
                updateStatistics();
                
                // Reset form
                uploadForm.reset();
                selectedFiles.textContent = 'No files selected';
                selectedFiles.style.color = '#ccc';
                
                // Hide loading
                uploadLoading.style.display = 'none';
                
                // Show success modal
                showSuccessModal(newTrack);
                
            }, 2000);
        }
        
        // Show success modal
        function showSuccessModal(track) {
            const modal = document.getElementById('successModal');
            const details = document.getElementById('uploadDetails');
            
            details.textContent = `${track.title} by ${track.artist} has been added to your library.`;
            modal.style.display = 'flex';
        }
        
        // Close modal
        function closeModal() {
            document.getElementById('successModal').style.display = 'none';
        }
        
        // Render music library
        function renderMusicLibrary(filteredMusic = musicLibrary) {
            musicGrid.innerHTML = '';
            
            if (filteredMusic.length === 0) {
                musicGrid.innerHTML = `
                    <div style="grid-column: 1 / -1; text-align: center; padding: 3rem; color: #ccc;">
                        <i class="fas fa-music" style="font-size: 3rem; margin-bottom: 1rem; display: block;"></i>
                        <h3>No music found</h3>
                        <p>Try uploading some music or adjust your search.</p>
                    </div>
                `;
                return;
            }
            
            filteredMusic.forEach((track, index) => {
                const isCurrent = index === currentTrackIndex;
                const isPlayingCurrent = isCurrent && isPlaying;
                
                const card = document.createElement('div');
                card.className = 'music-card';
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
                        <p>${track.description}</p>
                    </div>
                    <div class="music-player">
                        <button class="play-btn" data-track-id="${track.id}">
                            <i class="fas ${isPlayingCurrent ? 'fa-pause' : 'fa-play'}"></i>
                        </button>
                        <div style="flex: 1;">
                            <div style="height: 4px; background: rgba(255,255,255,0.1); border-radius: 2px; margin-top: 5px;"></div>
                        </div>
                        <button class="file-label share-btn" style="padding: 5px 10px;">
                            <i class="fas fa-share"></i>
                        </button>
                    </div>
                `;
                
                // Add click event to play button
                const playBtn = card.querySelector('.play-btn');
                playBtn.addEventListener('click', () => playTrack(track.id));
                
                // Add click event to share button
                const shareBtn = card.querySelector('.share-btn');
                shareBtn.addEventListener('click', () => shareTrack(track.id));
                
                musicGrid.appendChild(card);
            });
        }
        
        // Share track
        function shareTrack(trackId) {
            const track = musicLibrary.find(t => t.id === trackId);
            if (track) {
                const url = window.location.href;
                const text = `Check out "${track.title}" by ${track.artist} on Tay Lee Music Hub!`;
                
                if (navigator.share) {
                    navigator.share({
                        title: track.title,
                        text: text,
                        url: url
                    });
                } else {
                    navigator.clipboard.writeText(`${text}\n${url}`).then(() => {
                        alert('Link copied to clipboard!');
                    });
                }
            }
        }
        
        // Search tracks
        function searchTracks() {
            const query = searchInput.value.toLowerCase();
            
            if (query.trim() === '') {
                renderMusicLibrary();
                return;
            }
            
            const filtered = musicLibrary.filter(track =>
                track.title.toLowerCase().includes(query) ||
                track.artist.toLowerCase().includes(query) ||
                track.album.toLowerCase().includes(query) ||
                track.genre.toLowerCase().includes(query)
            );
            
            renderMusicLibrary(filtered);
        }
        
        // Update statistics
        function updateStatistics() {
            // Calculate totals
            const totalTracks = musicLibrary.length;
            const totalStorage = musicLibrary.reduce((sum, track) => {
                return sum + parseFloat(track.size);
            }, 0);
            const totalPlays = musicLibrary.reduce((sum, track) => {
                return sum + track.plays;
            }, 0);
            
            // Get today's date
            const today = new Date().toISOString().split('T')[0];
            const uploadsToday = musicLibrary.filter(track => 
                track.uploadDate === today
            ).length;
            
            // Update DOM
            totalTracksEl.textContent = totalTracks;
            storageUsedEl.textContent = totalStorage.toFixed(1) + ' MB';
            totalPlaysEl.textContent = totalPlays;
            uploadsTodayEl.textContent = uploadsToday;
        }
        
        // Scroll to upload section
        function scrollToUpload() {
            document.getElementById('upload').scrollIntoView({
                behavior: 'smooth'
            });
        }
        
        // Initialize the app when page loads
        document.addEventListener('DOMContentLoaded', initApp);
        
        // Close modal if clicked outside
        window.onclick = function(event) {
            const modal = document.getElementById('successModal');
            if (event.target === modal) {
                closeModal();
            }
        }
    </script>
</body>
</html>
