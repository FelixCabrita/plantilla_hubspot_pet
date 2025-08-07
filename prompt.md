A continuación tienes un **prompt listo para copiar y pegar en Claude** (u otro LLM) que le indicará exactamente cómo transformar tu archivo `nala_landing_page.html` en una plantilla de HubSpot CMS drag-and-drop, con todo el contenido editable desde el panel. Solo sustituye el bloque `<!-- PEGA AQUÍ TU HTML COMPLETO -->` por el código del archivo que me pasaste.

```txt
### Sistema
Eres un desarrollador experto en HubSpot CMS, HubL y la CLI de HubSpot. Todas tus respuestas deben ser únicamente bloques de código listos para copiar-pegar, sin explicaciones adicionales. Usa buenas prácticas de accesibilidad (atributos alt, jerarquía h1-h6, roles cuando sea útil) y nombra archivos y módulos en inglés sin espacios.

### Usuario
1. **Objetivo:** Convierte el siguiente HTML en un **theme completo** llamado `nala_theme` que incluya una plantilla drag-and-drop `landing_page.dnd.json` basada en ese diseño.
2. **Requisitos de edición en el CMS**
   - Todo el texto (títulos, párrafos, CTA) debe estar en módulos Rich Text o campos `text` dentro de módulos.
   - Cada “tarjeta” (stats, content cards, schedule days) debe ser un **módulo repetible** (`repeater`) para que marketing pueda añadir/quitar elementos sin código.
   - Las imágenes o placeholders usan el módulo estándar de imagen (`@hubspot/image`) y deben poder reemplazarse desde el editor.
   - Define en `theme/fields.json` estas variables globales:
     - `--primary-gradient` (color) → degradao principal (#ff9a9e → #fecfef)
     - `--accent-gradient` (color) → morado (#667eea → #764ba2)
     - `--font-base` (font) → fuente base
     - `--show_card_shadow` (boolean) → activar/desactivar sombras en tarjetas
   - Todos los gradientes y colores del CSS deben referenciar variables con `var(--primary-gradient)` o `var(--accent-gradient)`.
3. **Estructura deseada**
```

nala\_theme/
├─ theme.json
├─ fields.json
├─ templates/
│   └─ landing\_page.dnd.json
├─ modules/
│   ├─ hero\_image.module
│   ├─ stat\_card.module
│   ├─ content\_card.module
│   ├─ day\_card.module
│   └─ cta\_button.module
└─ css/
└─ main.css

````
4. **Instrucción de entrega**
- Devuelve **cada archivo en un bloque de código separado** con la ruta relativa como primer comentario (p. ej. `/* theme.json */`).
- No incluyas comentarios fuera de los bloques de código.
5. **HTML fuente a convertir**  
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vida Perruna con Nala - Amor, Ternura y Aventuras Peluditas</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            background: linear-gradient(135deg, #ffeef8 0%, #f0f8ff 100%);
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 50%, #fecfef 100%);
            padding: 100px 0;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            width: 200px;
            height: 200px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            top: 20%;
            left: 10%;
            animation: float 6s ease-in-out infinite;
        }

        .hero::after {
            content: '';
            position: absolute;
            width: 150px;
            height: 150px;
            background: rgba(255, 255, 255, 0.08);
            border-radius: 50%;
            bottom: 20%;
            right: 15%;
            animation: float 8s ease-in-out infinite reverse;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(180deg); }
        }

        .hero-content {
            position: relative;
            z-index: 2;
        }

        .hero-image {
            width: 200px;
            height: 200px;
            background: linear-gradient(135deg, #fff 0%, #f8f8f8 100%);
            border-radius: 50%;
            margin: 0 auto 30px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 80px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
            animation: bounce 3s ease-in-out infinite;
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }

        .hero h1 {
            font-size: 3rem;
            color: #fff;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
            animation: slideInDown 1s ease-out;
        }

        .hero-subtitle {
            font-size: 1.3rem;
            color: rgba(255, 255, 255, 0.9);
            margin-bottom: 40px;
            font-weight: 300;
            animation: slideInUp 1s ease-out 0.3s both;
        }

        @keyframes slideInDown {
            from { opacity: 0; transform: translateY(-50px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @keyframes slideInUp {
            from { opacity: 0; transform: translateY(50px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .btn-primary {
            display: inline-block;
            background: linear-gradient(135deg, #ff69b4 0%, #ff1493 100%);
            color: white;
            padding: 15px 40px;
            text-decoration: none;
            border-radius: 50px;
            font-weight: 600;
            font-size: 1.1rem;
            box-shadow: 0 10px 25px rgba(255, 105, 180, 0.4);
            transition: all 0.3s ease;
            animation: slideInUp 1s ease-out 0.6s both;
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 35px rgba(255, 105, 180, 0.5);
            background: linear-gradient(135deg, #ff1493 0%, #dc143c 100%);
        }

        /* About Nala Section */
        .about-nala {
            padding: 100px 0;
            background: #fff;
        }

        .section-title {
            text-align: center;
            font-size: 2.5rem;
            color: #333;
            margin-bottom: 60px;
            position: relative;
        }

        .section-title::after {
            content: '';
            width: 60px;
            height: 4px;
            background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 100%);
            position: absolute;
            bottom: -15px;
            left: 50%;
            transform: translateX(-50%);
            border-radius: 2px;
        }

        .nala-grid {
            display: grid;
            grid-template-columns: 1fr 2fr;
            gap: 60px;
            align-items: center;
            margin-bottom: 60px;
        }

        .nala-stats {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 25px;
        }

        .stat-card {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 30px 20px;
            border-radius: 20px;
            text-align: center;
            box-shadow: 0 10px 25px rgba(102, 126, 234, 0.2);
            transition: transform 0.3s ease;
        }

        .stat-card:hover {
            transform: translateY(-5px);
        }

        .stat-emoji {
            font-size: 2rem;
            margin-bottom: 10px;
            display: block;
        }

        .stat-label {
            font-size: 0.9rem;
            opacity: 0.8;
            margin-bottom: 5px;
        }

        .stat-value {
            font-size: 1.2rem;
            font-weight: 600;
        }

        .nala-description {
            background: linear-gradient(135deg, #ffeef8 0%, #f0f8ff 100%);
            padding: 40px;
            border-radius: 25px;
            font-size: 1.2rem;
            line-height: 1.8;
            color: #555;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
        }

        /* Gallery Styles */
        .photo-gallery {
            margin-top: 80px;
        }

        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
            margin-top: 40px;
        }

        .gallery-item {
            position: relative;
            overflow: hidden;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
        }

        .gallery-item:hover {
            transform: translateY(-8px) scale(1.02);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15);
        }

        .photo-placeholder {
            background: linear-gradient(135deg, #ffeef8 0%, #f0f8ff 100%);
            height: 250px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
        }

        .photo-placeholder::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(45deg, rgba(255, 105, 180, 0.1) 0%, rgba(255, 182, 193, 0.1) 100%);
            z-index: 1;
        }

        .photo-placeholder span {
            font-size: 4rem;
            margin-bottom: 15px;
            z-index: 2;
            position: relative;
        }

        .photo-placeholder p {
            color: #666;
            font-weight: 500;
            font-size: 1.1rem;
            z-index: 2;
            position: relative;
            text-align: center;
            margin: 0 20px;
        }
        .content-section {
            padding: 100px 0;
            background: linear-gradient(135deg, #ffeef8 0%, #f0f8ff 100%);
        }

        .content-intro {
            text-align: center;
            font-size: 1.3rem;
            color: #666;
            margin-bottom: 60px;
            max-width: 800px;
            margin-left: auto;
            margin-right: auto;
        }

        .content-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
        }

        .content-card {
            background: white;
            padding: 40px 30px;
            border-radius: 20px;
            text-align: center;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .content-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 100%);
        }

        .content-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.12);
        }

        .content-emoji {
            font-size: 2.5rem;
            margin-bottom: 20px;
            display: block;
        }

        .content-text {
            font-size: 1.1rem;
            color: #555;
            line-height: 1.6;
        }

        /* Schedule Section */
        .schedule {
            padding: 100px 0;
            background: #fff;
        }

        .schedule-content {
            text-align: center;
            max-width: 600px;
            margin: 0 auto;
        }

        .schedule-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 20px;
            margin-top: 40px;
        }

        .day-card {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 25px 15px;
            border-radius: 15px;
            text-align: center;
            font-weight: 600;
            box-shadow: 0 8px 20px rgba(102, 126, 234, 0.2);
        }

        /* CTA Section */
        .cta-section {
            padding: 100px 0;
            background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 100%);
            text-align: center;
        }

        .cta-content h2 {
            color: white;
            font-size: 2.5rem;
            margin-bottom: 30px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
        }

        .cta-content p {
            color: rgba(255, 255, 255, 0.9);
            font-size: 1.3rem;
            margin-bottom: 40px;
        }

        /* Footer */
        .footer {
            background: #333;
            color: white;
            padding: 50px 0 30px;
            text-align: center;
        }

        .footer-content {
            margin-bottom: 30px;
        }

        .social-links {
            margin: 30px 0;
        }

        .social-link {
            display: inline-block;
            width: 50px;
            height: 50px;
            background: linear-gradient(135deg, #ff69b4 0%, #ff1493 100%);
            color: white;
            border-radius: 50%;
            line-height: 50px;
            margin: 0 10px;
            text-decoration: none;
            font-size: 1.2rem;
            transition: all 0.3s ease;
        }

        .social-link:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(255, 105, 180, 0.4);
        }

        .copyright {
            border-top: 1px solid #555;
            padding-top: 20px;
            color: #999;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 2rem;
            }
            
            .hero-subtitle {
                font-size: 1.1rem;
            }
            
            .nala-grid {
                grid-template-columns: 1fr;
                gap: 40px;
            }
            
            .nala-stats {
                grid-template-columns: 1fr;
            }
            
            .schedule-grid {
                grid-template-columns: repeat(2, 1fr);
            }
            
            .section-title {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <!-- Hero Section -->
    <section class="hero">
        <div class="container">
            <div class="hero-content">
                <div class="hero-image">
                    🐕
                </div>
                <h1>Vida Perruna con Nala</h1>
                <p class="hero-subtitle">Amor, ternura y aventuras peluditas</p>
                <a href="#" class="btn-primary">Sigue a Nala en Instagram</a>
            </div>
        </div>
    </section>

    <!-- About Nala Section -->
    <section class="about-nala">
        <div class="container">
            <h2 class="section-title">¿Quién es Nala?</h2>
            
            <div class="nala-grid">
                <div class="nala-stats">
                    <div class="stat-card">
                        <span class="stat-emoji">🐶</span>
                        <div class="stat-label">Edad</div>
                        <div class="stat-value">2 años</div>
                    </div>
                    <div class="stat-card">
                        <span class="stat-emoji">🧬</span>
                        <div class="stat-label">Raza</div>
                        <div class="stat-value">Maltés</div>
                    </div>
                    <div class="stat-card">
                        <span class="stat-emoji">🎨</span>
                        <div class="stat-label">Color</div>
                        <div class="stat-value">Blanca</div>
                    </div>
                    <div class="stat-card">
                        <span class="stat-emoji">💖</span>
                        <div class="stat-label">Nariz</div>
                        <div class="stat-value">Rosadita</div>
                    </div>
                </div>

                <div class="nala-description">
                    <p>Nala es una perrita maltés curiosa, cariñosa y un poquito traviesa. Siempre lista para descubrir el mundo y compartir momentos mágicos con su comunidad perruna. Su personalidad dulce y aventurera la convierte en la compañera perfecta para crear contenido lleno de amor y ternura.</p>
                </div>
            </div>

            <!-- Gallery Section -->
            <div class="photo-gallery">
                <h3 style="text-align: center; font-size: 2rem; margin: 60px 0 40px; color: #333;">Galería de Nala</h3>
                <div class="gallery-grid">
                    <div class="gallery-item">
                        <div class="photo-placeholder">
                            <span>📸</span>
                            <p>Foto de Nala jugando</p>
                        </div>
                    </div>
                    <div class="gallery-item">
                        <div class="photo-placeholder">
                            <span>📸</span>
                            <p>Nala en el parque</p>
                        </div>
                    </div>
                    <div class="gallery-item">
                        <div class="photo-placeholder">
                            <span>📸</span>
                            <p>Momento de ternura</p>
                        </div>
                    </div>
                    <div class="gallery-item">
                        <div class="photo-placeholder">
                            <span>📸</span>
                            <p>Nala descansando</p>
                        </div>
                    </div>
                    <div class="gallery-item">
                        <div class="photo-placeholder">
                            <span>📸</span>
                            <p>Aventuras peludas</p>
                        </div>
                    </div>
                    <div class="gallery-item">
                        <div class="photo-placeholder">
                            <span>📸</span>
                            <p>Nala siendo tierna</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Content Section -->
    <section class="content-section">
        <div class="container">
            <h2 class="section-title">¿Qué encontrarás en esta cuenta?</h2>
            
            <p class="content-intro">
                Vida Perruna con Nala es una cuenta tierna, educativa e inspiradora pensada para quienes aman a los perritos tanto como nosotros.
            </p>

            <div class="content-grid">
                <div class="content-card">
                    <span class="content-emoji">🌸</span>
                    <p class="content-text">Frases bonitas con ilustraciones suaves</p>
                </div>
                <div class="content-card">
                    <span class="content-emoji">🐾</span>
                    <p class="content-text">Tips de cuidado y bienestar</p>
                </div>
                <div class="content-card">
                    <span class="content-emoji">📚</span>
                    <p class="content-text">Curiosidades y datos peludos</p>
                </div>
                <div class="content-card">
                    <span class="content-emoji">🎨</span>
                    <p class="content-text">Imágenes animadas generadas por IA</p>
                </div>
                <div class="content-card">
                    <span class="content-emoji">❤️</span>
                    <p class="content-text">Historias emotivas protagonizadas por Nala</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Schedule Section -->
    <section class="schedule">
        <div class="container">
            <h2 class="section-title">¿Cuándo publica Nala?</h2>
            
            <div class="schedule-content">
                <p style="font-size: 1.2rem; color: #666; margin-bottom: 20px;">
                    Publicamos 4 veces por semana, y también compartimos historias durante la semana con frases, datos y encuestas.
                </p>

                <div class="schedule-grid">
                    <div class="day-card">Lunes</div>
                    <div class="day-card">Miércoles</div>
                    <div class="day-card">Viernes</div>
                    <div class="day-card">Sábado</div>
                </div>
            </div>
        </div>
    </section>

    <!-- CTA Section -->
    <section class="cta-section">
        <div class="container">
            <div class="cta-content">
                <h2>¿Listo para llenarte de ternura cada semana?</h2>
                <p>¡Acompaña a Nala en su aventura perruna!</p>
                <a href="#" class="btn-primary">Síguela en Instagram</a>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
        <div class="container">
            <div class="footer-content">
                <h3 style="margin-bottom: 20px; font-size: 1.8rem;">Vida Perruna con Nala</h3>
                
                <div class="social-links">
                    <a href="#" class="social-link">📷</a>
                </div>
            </div>
            
            <div class="copyright">
                <p>&copy; 2025 Vida Perruna con Nala. Todos los derechos reservados.</p>
            </div>
        </div>
    </footer>

    <script>
        // Smooth scrolling for anchor links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        // Add scroll animations
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, observerOptions);

        // Observe elements for animation
        document.querySelectorAll('.stat-card, .content-card, .day-card').forEach(el => {
            el.style.opacity = '0';
            el.style.transform = 'translateY(30px)';
            el.style.transition = 'all 0.6s ease';
            observer.observe(el);
        });
    </script>
</body>
</html>
````

> Cuando termines, recibiré un conjunto de archivos que puedo subir con `hs upload nala_theme` y funcionarán sin advertencias.

````
 