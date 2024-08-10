<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Galería de Imágenes</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            margin: 0;
            padding: 20px;
            background-color: #f0f0f0;
        }
        .gallery {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
        }
        .gallery img {
            width: 200px;
            height: 200px;
            object-fit: cover;
            cursor: pointer;
            border-radius: 5px;
            transition: transform 0.3s ease;
        }
        .gallery img:hover {
            transform: scale(1.1);
        }
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            justify-content: center;
            align-items: center;
        }
        .modal img {
            max-width: 80%;
            max-height: 80%;
        }
        .modal.show {
            display: flex;
        }
    </style>
</head>
<body>
    <div class="gallery" id="gallery"></div>

    <div class="modal" id="modal">
        <img id="modalImg" src="" alt="Imagen">
    </div>

    <script>
        // Array de imágenes
        const images = [
            'https://www.nasa.gov/wp-content/uploads/2024/06/as08-14-2383orig.jpg',
            'https://www.nasa.gov/wp-content/uploads/2024/05/pia04234orig.jpg',
            'https://www.nasa.gov/wp-content/uploads/2024/07/ksc-20170504-ph-sww01-0001orig.jpg',
            'https://www.nasa.gov/wp-content/uploads/2024/08/iss065e241659.jpg',
            'https://www.nasa.gov/wp-content/uploads/2024/04/8111969orig.jpg'
        ];

        const gallery = document.getElementById('gallery');
        const modal = document.getElementById('modal');
        const modalImg = document.getElementById('modalImg');

        // Cargar imágenes en la galería
        images.forEach(src => {
            const img = document.createElement('img');
            img.src = src;
            img.alt = 'Imagen de la galería';
            img.addEventListener('click', () => {
                modalImg.src = src;
                modal.classList.add('show');
            });
            gallery.appendChild(img);
        });

        // Cerrar el modal al hacer clic en cualquier parte
        modal.addEventListener('click', () => {
            modal.classList.remove('show');
        });
    </script>
</body>
</html>
