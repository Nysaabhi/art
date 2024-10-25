# art
<head>
    <title>Luxury NFT Gallery</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        :root {
            --primary-color: #8b5cf6;
            --primary-hover: #7c3aed;
            --accent-color: #c4b5fd;
            --background-dark: #1a1b26;
            --background-light: #2c3e50;
            --text-light: #e2e8f0;
            --text-dark: #1f2937;
            --gold: #ffd700;
            --rose-gold: linear-gradient(45deg, #daa520, #b76e79);
            --platinum: linear-gradient(45deg, #e5e4e2, #c0c0c0);
            --marble: linear-gradient(45deg, #f3f4f6 0%, #e5e7eb 100%);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: var(--background-dark);
            padding: 20px;
            color: var(--text-light);
            background-image: 
                radial-gradient(circle at 10% 20%, rgba(139, 92, 246, 0.1) 0%, transparent 20%),
                radial-gradient(circle at 90% 80%, rgba(255, 215, 0, 0.1) 0%, transparent 20%);
        }

        .gallery-card {
            width: 100%;
            max-width: 1200px;
            height: 600px;
            background: linear-gradient(145deg, #1f2937, #111827);
            border-radius: 20px;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
            position: relative;
            overflow: hidden;
            border: 1px solid rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
        }

        .gallery-header {
            text-align: center;
            padding: 20px;
            background: var(--platinum);
            -webkit-background-clip: text;
            color: transparent;
            font-size: 2em;
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 2px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .gallery-container {
            height: calc(100% - 80px);
            overflow-y: auto;
            perspective: 2000px;
            scrollbar-width: thin;
            scrollbar-color: var(--primary-color) var(--background-dark);
        }

        .room {
            transform-style: preserve-3d;
            transition: transform 0.8s cubic-bezier(0.4, 0, 0.2, 1);
            padding: 20px;
        }

        .wall {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
            padding: 20px;
            position: relative;
        }

        .artwork-frame {
            background: var(--marble);
            border-radius: 15px;
            padding: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            height: 300px;
            transform: scale(0.98);
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            position: relative;
            overflow: hidden;
        }

        .artwork-frame:hover {
            transform: scale(1.02) translateY(-5px);
            box-shadow: 0 20px 40px rgba(139, 92, 246, 0.3);
        }

        .artwork {
            height: 100%;
            border-radius: 10px;
            overflow: hidden;
            position: relative;
            background: var(--background-dark);
            display: flex;
            flex-direction: column;
        }

        .artwork img {
            width: 100%;
            height: 70%;
            object-fit: cover;
            transition: transform 0.3s ease;
        }

        .artwork:hover img {
            transform: scale(1.05);
        }

        .artwork-info {
            padding: 15px;
            background: rgba(0,0,0,0.8);
            backdrop-filter: blur(5px);
            position: absolute;
            bottom: 0;
            width: 100%;
            transform: translateY(100%);
            transition: transform 0.3s ease;
        }

        .artwork-frame:hover .artwork-info {
            transform: translateY(0);
        }

        .premium-badge {
            position: absolute;
            top: 10px;
            right: 10px;
            background: var(--rose-gold);
            padding: 5px 10px;
            border-radius: 15px;
            font-size: 12px;
            color: var(--text-light);
            z-index: 2;
            display: flex;
            align-items: center;
            gap: 5px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.2);
        }

        .price-tag {
            position: absolute;
            top: 10px;
            left: 10px;
            background: var(--platinum);
            padding: 8px 15px;
            border-radius: 12px;
            font-weight: bold;
            color: var(--text-dark);
            display: flex;
            align-items: center;
            gap: 5px;
            z-index: 2;
        }

        .controls {
            position: absolute;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            gap: 15px;
            z-index: 100;
            background: rgba(0, 0, 0, 0.7);
            padding: 15px;
            border-radius: 25px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255,255,255,0.1);
        }

        .control-btn {
            padding: 10px 20px;
            background: var(--primary-color);
            color: var(--text-light);
            border: none;
            border-radius: 15px;
            cursor: pointer;
            font-size: 14px;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .control-btn:hover {
            background: var(--primary-hover);
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(139, 92, 246, 0.3);
        }

        @media (max-width: 1024px) {
            .wall {
                grid-template-columns: repeat(2, 1fr);
            }
        }

        @media (max-width: 768px) {
            .wall {
                grid-template-columns: 1fr;
            }
            
            .gallery-card {
                height: 500px;
            }

            .artwork-frame {
                height: 250px;
            }
        }
    </style>
</head>
<body>
    <div class="gallery-card">
        <div class="gallery-container">
            <div class="room">
                <div class="wall">
                    <div class="artwork-frame">
                        <div class="artwork">
                            <div class="premium-badge">
                                <i class="fas fa-crown"></i> Genesis
                            </div>
                            <div class="price-tag">
                                <i class="fab fa-ethereum"></i> 8.5 ETH
                            </div>
                            <img src="https://i.ibb.co/yFNbRqF/Whats-App-Image-2024-10-20-at-09-16-07-510389dd.jpg" alt="NFT 1">
                            <div class="artwork-info">
                                <h3>Celestial Harmony #1</h3>
                                <p>A rare piece from the Genesis collection</p>
                            </div>
                        </div>
                    </div>
                    
                    <div class="artwork-frame">
                        <div class="artwork">
                            <div class="premium-badge">
                                <i class="fas fa-gem"></i> Platinum
                            </div>
                            <div class="price-tag">
                                <i class="fab fa-ethereum"></i> 5.2 ETH
                            </div>
                            <img src="https://i.ibb.co/7vkRDZv/Whats-App-Image-2024-10-20-at-09-16-08-0798f91f.jpg" alt="NFT 2">
                            <div class="artwork-info">
                                <h3>Digital Dreams #2</h3>
                                <p>Exclusive platinum tier artwork</p>
                            </div>
                        </div>
                    </div>

                    <div class="artwork-frame">
                        <div class="artwork">
                            <div class="premium-badge">
                                <i class="fas fa-star"></i> Limited
                            </div>
                            <div class="price-tag">
                                <i class="fab fa-ethereum"></i> 3.8 ETH
                            </div>
                            <img src="https://i.ibb.co/k8zNj9j/a-captivating-and-dreamlike-scene-of-a-dali-esque-swof-qz-GQu-Ks-Sj-h-EVGflw-q-Em-M-hmr-Rcm-FUZb-GUc.jpg" alt="NFT 3">
                            <div class="artwork-info">
                                <h3>Quantum Realm #3</h3>
                                <p>Limited edition quantum-inspired art</p>
                            </div>
                        </div>
                    </div>

                    <div class="artwork-frame">
                        <div class="artwork">
                            <div class="premium-badge">
                                <i class="fas fa-fire"></i> Trending
                            </div>
                            <div class="price-tag">
                                <i class="fab fa-ethereum"></i> 4.1 ETH
                            </div>
                            <img src="https://i.ibb.co/k51wwwg/an-awe-inspiring-scene-of-mythical-beasts-roaming-E6-Ugt4-g-TAO4r-Pl-Gpra-e-Q-t0tr-Egk6-Sf2r8k-Tr2-I.jpg" alt="NFT 4">
                            <div class="artwork-info">
                                <h3>Neo Tokyo #4</h3>
                                <p>Cyberpunk-inspired digital masterpiece</p>
                            </div>
                        </div>
                    </div>

                    <div class="artwork-frame">
                        <div class="artwork">
                            <div class="premium-badge">
                                <i class="fas fa-diamond"></i> Elite
                            </div>
                            <div class="price-tag">
                                <i class="fab fa-ethereum"></i> 6.3 ETH
                            </div>
                            <img src="https://i.ibb.co/YBXK5Mg/a-striking-3d-illustration-of-a-t-shirt-hanging-on-h1-AIHpnz-TRK-8e-SADc-LFJw-l-Hs-Od-YYj-Sp-Wg6xv-U.jpg" alt="NFT 5">
                            <div class="artwork-info">
                                <h3>Ethereal Visions #5</h3>
                                <p>Elite collection masterwork</p>
                            </div>
                        </div>
                    </div>

                    <div class="artwork-frame">
                        <div class="artwork">
                            <div class="premium-badge">
                                <i class="fas fa-trophy"></i> Featured
                            </div>
                            <div class="price-tag">
                                <i class="fab fa-ethereum"></i> 4.7 ETH
                            </div>
                            <img src="https://i.ibb.co/HKvgVZr/a-vibrant-and-whimsical-image-set-against-a-bright-NSb-Bm-Sj1-Swy1-Ms53f3dacw-s7j1a-TEf-T5ax-R-8wwpn.jpg" alt="NFT 6">
                            <div class="artwork-info">
                                <h3>Crystal Genesis #6</h3>
                                <p>Featured artwork of the month</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="controls">
            <button class="control-btn" onclick="rotate('left')">
                <i class="fas fa-chevron-left"></i> Previous Wall
            </button>
            <button class="control-btn" onclick="rotate('right')">
                Next Wall <i class="fas fa-chevron-right"></i>
            </button>
        </div>
    </div>

    <script>
        let currentRotation = 0;
        const room = document.querySelector('.room');

        function rotate(direction) {
            currentRotation += direction === 'left' ? -90 : 90;
            room.style.transform = `rotateY(${currentRotation}deg)`;
        }

        // Mobile touch controls
        let touchStartX = 0;
        let touchEndX = 0;
        const SWIPE_THRESHOLD = 50;

        document.addEventListener('touchstart', e => {
            touchStartX = e.touches[0].clientX;
        });

        document.addEventListener('touchmove', e => {
            touchEndX = e.touches[0].clientX;
        });

        document.addEventListener('touchend', () => {
            const swipeDistance = touchEndX - touchStartX;
            
            if (Math.abs(swipeDistance) > SWIPE_THRESHOLD) {
                if (swipeDistance > 0) {
                    rotate('left');
                } else {
                    rotate('right');
                }
            }
            
            touchStartX = 0;
            touchEndX = 0;
        });
    </script>
</body>
