<template>
  <div class="flex flex-col h-full relative">
    <!-- Binary Matrix Background -->
    <div id="matrixBackground" class="matrix-background"></div>
    
    <!-- Background Music Player -->
    <div class="music-player">
      <audio 
        id="backgroundMusic" 
        loop 
        autoplay
        preload="auto"
        src="https://res.cloudinary.com/diqm9d7sx/video/upload/v1753269267/audio/Happy_and_Joyful_Children.mp3"
      >
        Your browser does not support the audio element.
      </audio>
      <button id="musicToggle" class="music-toggle" @click="toggleMusic">
        <i class="bx bx-volume-full" id="musicIcon"></i>
      </button>
    </div>
    <HeroBanner @scrollToSection="scrollToSection" />
    <Introduction @scrollToSection="scrollToSection" />
    <Video @scrollToSection="scrollToSection" />
    <Schedule @scrollToSection="scrollToSection" />
    <Prizes @scrollToSection="scrollToSection" />
    <Rules @scrollToSection="scrollToSection" />
    <Testimonials @scrollToSection="scrollToSection" />
    <Registration @scrollToSection="scrollToSection" />
    <Photos @scrollToSection="scrollToSection" />
    <ProblemsArchive @scrollToSection="scrollToSection" />
    <Contact @scrollToSection="scrollToSection" />
  </div>
</template>

<script>
export default {
  mounted() {
    this.disableScroll();
    this.initMatrixBackground();
    this.initMusicPlayer();
  },
  data() {
    return {
      isPlaying: false,
    };
  },
  methods: {
    disableScroll() {},
    scrollToSection(sectionName) {
      if (process.browser) {
        const section = document.getElementById(sectionName);
        section.scrollIntoView({
          behavior: "smooth",
        });
      }
    },
    initMatrixBackground() {
      if (process.browser) {
        const canvas = document.createElement('canvas');
        const ctx = canvas.getContext('2d');
        const matrixContainer = document.getElementById('matrixBackground');
        
        matrixContainer.appendChild(canvas);
        
        const resizeCanvas = () => {
          canvas.width = window.innerWidth;
          canvas.height = window.innerHeight;
        };
        
        resizeCanvas();
        window.addEventListener('resize', resizeCanvas);
        
        const fontSize = 16;
        const columns = Math.floor(canvas.width / fontSize);
        const drops = Array(columns).fill(0).map(() => Math.floor(Math.random() * canvas.height / fontSize));
        
        const binaryChars = '01';
        const techChars = '!@#$%^&*()_+-=[]{}|;:,.<>?~`';
        const allChars = binaryChars + techChars;
        
        const draw = () => {
          ctx.fillStyle = 'rgba(255, 255, 255, 0.08)';
          ctx.fillRect(0, 0, canvas.width, canvas.height);
          
          ctx.font = `${fontSize}px 'Courier New', monospace`;
          
          for (let i = 0; i < drops.length; i++) {
            const isBinary = Math.random() > 0.3;
            const char = isBinary ? 
              binaryChars[Math.floor(Math.random() * binaryChars.length)] :
              allChars[Math.floor(Math.random() * allChars.length)];
            
            const grayLevel = 20 + Math.random() * 80;
            const alpha = 0.7 + Math.random() * 0.2;
            
            ctx.fillStyle = `rgba(${grayLevel}, ${grayLevel}, ${grayLevel}, ${alpha})`;
            ctx.fillText(char, i * fontSize, drops[i] * fontSize);
            
            if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) {
              drops[i] = 0;
            }
            drops[i]++;
          }
        };
        
        let lastTime = 0;
        const frameDelay = 100; // milliseconds between frames
        
        const animate = (currentTime) => {
          if (currentTime - lastTime >= frameDelay) {
            draw();
            lastTime = currentTime;
          }
          requestAnimationFrame(animate);
        };
        
        animate();
      }
    },
    initMusicPlayer() {
      if (process.browser) {
        const audio = document.getElementById('backgroundMusic');
        const musicIcon = document.getElementById('musicIcon');
        
        // Set volume and ensure looping
        audio.loop = true;
        
        // Force autoplay
        setTimeout(() => {
          const playPromise = audio.play();
          if (playPromise !== undefined) {
            playPromise
              .then(() => {
                this.isPlaying = true;
                musicIcon.className = 'bx bx-volume-full';
              })
              .catch(() => {
                // If autoplay fails, set up click-to-play
                this.isPlaying = false;
                musicIcon.className = 'bx bx-volume-mute';
                
                // Try to play on first user interaction
                const enableAudio = () => {
                  audio.play().then(() => {
                    this.isPlaying = true;
                    musicIcon.className = 'bx bx-volume-full';
                  });
                  document.removeEventListener('click', enableAudio);
                };
                document.addEventListener('click', enableAudio);
              });
          }
        }, 1000);
      }
    },
    toggleMusic() {
      if (process.browser) {
        const audio = document.getElementById('backgroundMusic');
        const musicIcon = document.getElementById('musicIcon');
        
        if (this.isPlaying) {
          audio.pause();
          this.isPlaying = false;
          musicIcon.className = 'bx bx-volume-mute';
        } else {
          audio.play();
          this.isPlaying = true;
          musicIcon.className = 'bx bx-volume-full';
        }
      }
    },
  },
};
</script>
