# Exercicio_Pratico_SQL

NOTA: Para pegar os dados Vc pode fazer clic no botãon de editar README.

YOUTUBE CLONE

![I am Front-end Web Developer](https://github.com/Cherry-2023/Exercicio_Pratico_SQL/blob/main/Youtube.png)

DIAGRAMA DO BANCO DE DADOS

![I am Front-end Web Developer](https://github.com/Cherry-2023/Exercicio_Pratico_SQL/blob/main/Diagrama_BD.png)

# --DDL  -  Criando tabelas

CREATE TABLE IF NOT EXISTS Users (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    firstName TEXT NOT NULL,
    lastName TEXT NOT NULL,
    email TEXT NOT NULL UNIQUE,
    profile_foto TEXT,
    mypassword TEXT NOT NULL UNIQUE,
    has_channel BOOLEAN DEFAULT FALSE,
    is_Verified BOOLEAN DEFAULT FALSE,
   createdAt DATETIME NOT NULL DEFAULT (datetime('now','localtime')),
   updatedAt DATETIME NOT NULL DEFAULT (datetime('now','localtime'))
);

CREATE TABLE IF NOT EXISTS Channels (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    user_id INTEGER REFERENCES Users(id),
    name TEXT NOT NULL UNIQUE,
    description TEXT,
    createdAt DATETIME NOT NULL DEFAULT (datetime('now','localtime')),
    updatedAt DATETIME NOT NULL DEFAULT (datetime('now','localtime'))
);

CREATE TABLE IF NOT EXISTS Videos (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    user_id INTEGER REFERENCES Users(id),
    channel_id INTEGER REFERENCES Channels(id),
    streaming_url TEXT,
    thumbnail_url TEXT,
    clave_key TEXT NOT NULL UNIQUE,
    processed BOOLEAN DEFAULT FALSE,
    title TEXT NOT NULL,
    description TEXT,
    createdAt DATETIME NOT NULL DEFAULT (datetime('now','localtime')),
    updatedAt DATETIME NOT NULL DEFAULT (datetime('now','localtime'))
);

CREATE TABLE IF NOT EXISTS Comments (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    user_id INTEGER REFERENCES Users(id),
    video_id INTEGER REFERENCES Videos(id),
    reply TEXT NOT NULL,   
    createdAt DATETIME NOT NULL DEFAULT (datetime('now','localtime')),
    updatedAt DATETIME NOT NULL DEFAULT (datetime('now','localtime'))
);

# --DDL  -  Adicionando cargas iniciais

INSERT INTO Users (firstName, lastName, email, profile_foto, mypassword, has_channel, is_Verified, createdAt, updatedAt)
VALUES 

('Alejandro Dario', 'Centeno', 'alejandro@gmail.com', 'alejandro.png', '8i775GT1', true, true,'1223389346048', '1223389346048'),
('Andrea', 'Montoya', 'andrea205@gmail.com', 'andrea.png', '5y775EJ8', false, false, '1223389346048', '1223389346048'),
('Danilson Nunes', 'Dos Reis', 'danilson5645@gmail.com', 'danilson.jpg', '9w565GJ8', true, false, '1223389346048', '1223389346048'),
('Edwin Alexander', 'Sanchez Delgado', 'edwinsanchez5@hotmail.com', 'edwinsan.png', 'W7y44GTA', false, true, '1223389346048', '1223389346048'),
('Elluz', 'Roriguez', 'elluzrodriguez@gmail.com', 'elluzrodri.jpg', 'R92n46LQA', true, true, '1223389346048', '1223389346048');

INSERT INTO Channels (user_id, name, description, createdAt, updatedAt)
VALUES 
('1', 'Canal de Alejandro', 'Este canal es para mostrar mis desarrollos web', '1223389346048', '1223389346048'),
('1', 'Canal de Video Juegos', 'Este canal es para mostrar mis Video Juegos', '1223389346048', '1223389346048'),
('1', 'Canal de Ventas', 'Este canal es para mostrar mis ventas desde casa', '1223389346048', '1223389346048'),
('2', 'Canal de Andrea', 'Este canal es para mostrar mis muñecas', '1223389346048', '1223389346048'),
('2', 'Canal de Refrescos', 'Este canal es para promocionar mis refrescos', '1223389346048', '1223389346048'),
('3', 'Canal de Danilson', 'Este canal es para mis cosas personales', '1223389346048', '1223389346048'),
('3', 'Canal de Carritos', 'Este canal es para mostrar mis Carritos de Hierro', '1223389346048', '1223389346048'),
('3', 'Canal de Platos', 'Este canal es para mostrar mis Platos favoritos', '1223389346048', '1223389346048'),
('3', 'Canal de Bicicletas', 'Este canal es para mostrar mis Bicicletas favoritas', '1223389346048', '1223389346048'),
('3', 'Canal de Yucas', 'Este canal es para mostrar mis Yucas favoritas de Perú', '1223389346048', '1223389346048'),
('4', 'Canal de Edwin Alexander', 'Este canal es para mostrar mis proyectos', '1223389346048', '1223389346048'),
('4', 'Canal de Trofeos', 'Este canal es para mostrar mis todos mis trofeos', '1223389346048', '1223389346048'),
('4', 'Canal de Música', 'Este canal es para mostrar mis canciones favoritas', '1223389346048', '1223389346048'),
('4', 'Canal de Casas Alquiladas', 'Este canal es para mostrar mis casas alquiladas', '1223389346048', '1223389346048'),
('5', 'Canal de Elluz Rodríguez', 'Este canal es para promocionar mis éxitos de los 80 y 90', '1223389346048', '1223389346048'),
('5', 'Canal de Hombres', 'Este canal es para mostrar los hombres más fuertes', '1223389346048', '1223389346048'),
('5', 'Canal de Estrellas del Rock', 'Este canal es para mostrar las estrellas de Rock', '1223389346048', '1223389346048');

INSERT INTO Videos (user_id, channel_id, streaming_url, thumbnail_url, clave_key, processed, title, description, createdAt, updatedAt)
VALUES 

('1', '1', 'https://www.youtube.com/watch?v=1Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7920', false, 'El resplandor', 'Jack Torrance, un escritor ex-alcoholico, acepta un puesto como vigilante de invierno en un solitario hotel.', '1223389346048', '1223389346048'),
('1', '1', 'https://www.youtube.com/watch?v=1Ibr_zStertU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7921', false, 'El Caza Fantasma', 'Rafael Linares, un poeta argentino ex-alcoholico, acepta un puesto como mesonero de un restaurante de lujo.', '1223389346048', '1223389346048'),
('2', '1', 'https://www.youtube.com/watch?v=2Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7922', false, 'The Adventure', 'Join us on an epic adventure across the world!', '1223389346048', '1223389346048'),
('2', '2', 'https://www.youtube.com/watch?v=3Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7923', false, 'Amazing Nature', 'Discover the beauty of nature in this breathtaking video.', '1223389346048', '1223389346048'),
('3', '1', 'https://www.youtube.com/watch?v=4Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7924', false, 'Cooking Masterclass', 'Learn how to cook delicious dishes from around the world.', '1223389346048', '1223389346048'),
('3', '2', 'https://www.youtube.com/watch?v=5Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7925', false, 'Space Exploration', 'Embark on a journey to explore the mysteries of the universe.', '1223389346048', '1223389346048'),
('3', '3', 'https://www.youtube.com/watch?v=6Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7926', false, 'Artistic Creations', 'Witness the creation of stunning art pieces from scratch.', '1223389346048', '1223389346048'),
('3', '4', 'https://www.youtube.com/watch?v=7Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7927', false, 'Science Breakthroughs', 'Stay updated on the latest scientific discoveries and breakthroughs.', '1223389346048', '1223389346048'),
('3', '5', 'https://www.youtube.com/watch?v=8Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7928', false, 'Travel Diaries', 'Explore the world through the eyes of avid travelers.', '1223389346048', '1223389346048'),
('4', '1', 'https://www.youtube.com/watch?v=9Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7929', false, 'Gaming Fun', 'Join us for exciting gaming adventures and challenges.', '1223389346048', '1223389346048'),
('4', '2', 'https://www.youtube.com/watch?v=10Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7930', false, 'Tech Unboxing', 'Get a firsthand look at the latest tech gadgets and innovations.', '1223389346048', '1223389346048'),
('4', '3', 'https://www.youtube.com/watch?v=11Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7931', false, 'Fitness Journey', 'Follow our fitness journey and stay motivated.', '1223389346048', '1223389346048'),
('4', '4', 'https://www.youtube.com/watch?v=12Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7932', false, 'Wildlife Encounters', 'Witness the wonders of the animal kingdom up close.', '1223389346048', '1223389346048'),
('5', '1', 'https://www.youtube.com/watch?v=13Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7933', false, 'Historical Mysteries', 'Delve into the mysteries and secrets of history.', '1223389346048', '1223389346048'),
('5', '2', 'https://www.youtube.com/watch?v=14Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7934', false, 'DIY Projects', 'Learn how to create amazing DIY projects at home.', '1223389346048', '1223389346048'),
('5', '3', 'https://www.youtube.com/watch?v=15Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7935', false, 'Fashion Trends', 'Stay fashionable and up-to-date with the latest trends.', '1223389346048', '1223389346048'),
('1', '2', 'https://www.youtube.com/watch?v=16Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7936', false, 'Music Vibes', 'Experience the magic of music in our music sessions.', '1223389346048', '1223389346048'),
('2', '2', 'https://www.youtube.com/watch?v=17Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7937', false, 'Cooking Adventures', 'Join us in the kitchen for exciting culinary adventures.', '1223389346048', '1223389346048'),
('3', '4', 'https://www.youtube.com/watch?v=18Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7938', false, 'Travel Stories', 'Hear captivating travel stories from around the world.', '1223389346048', '1223389346048'),
('4', '2', 'https://www.youtube.com/watch?v=19Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7939', false, 'Gaming Challenges', 'Take on challenging gaming missions and win.', '1223389346048', '1223389346048'),
('5', '1', 'https://www.youtube.com/watch?v=20Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7940', false, 'Tech Reviews', 'Get in-depth reviews of the latest tech products.', '1223389346048', '1223389346048'), 
('1', '2', 'https://www.youtube.com/watch?v=21Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7941', false, 'Natures Beauty', 'Explore the wonders of the natural world.', '1223389346048', '1223389346048'),
('1', '2', 'https://www.youtube.com/watch?v=22Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7942', false, 'Cooking Delights', 'Discover delicious recipes and cooking tips.', '1223389346048', '1223389346048'),
('2', '1', 'https://www.youtube.com/watch?v=23Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7943', false, 'Space Odyssey', 'Embark on a journey through the cosmos.', '1223389346048', '1223389346048'),
('2', '2', 'https://www.youtube.com/watch?v=24Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7944', false, 'Artistic Expressions', 'Witness the creation of stunning artworks.', '1223389346048', '1223389346048'),
('3', '1', 'https://www.youtube.com/watch?v=25Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7945', false, 'Science Wonders', 'Explore the frontiers of science and technology.', '1223389346048', '1223389346048'),
('3', '2', 'https://www.youtube.com/watch?v=26Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7946', false, 'Wanderlust', 'Travel to exotic destinations around the world.', '1223389346048', '1223389346048'),
('3', '3', 'https://www.youtube.com/watch?v=27Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7947', false, 'Gaming Thrills', 'Experience the adrenaline of intense gaming.', '1223389346048', '1223389346048'),
('3', '4', 'https://www.youtube.com/watch?v=28Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7948', false, 'Tech Gadgets Galore', 'Reviewing the latest tech gadgets and innovations.', '1223389346048', '1223389346048'),
('3', '5', 'https://www.youtube.com/watch?v=29Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7949', false, 'Fitness Goals', 'Stay fit and healthy with our fitness tips.', '1223389346048', '1223389346048'),
('4', '1', 'https://www.youtube.com/watch?v=30Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7950', false, 'Wildlife Adventures', 'Discover the fascinating world of wildlife.', '1223389346048', '1223389346048'),
('4', '2', 'https://www.youtube.com/watch?v=31Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7951', false, 'Historical Enigmas', 'Unravel the mysteries of the past.', '1223389346048', '1223389346048'),
('4', '3', 'https://www.youtube.com/watch?v=32Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7952', false, 'DIY Creations', 'Get creative with our DIY project tutorials.', '1223389346048', '1223389346048'),
('4', '4', 'https://www.youtube.com/watch?v=33Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7953', false, 'Fashion Insights', 'Stay trendy with our fashion tips and trends.', '1223389346048', '1223389346048'),
('5', '1', 'https://www.youtube.com/watch?v=34Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7954', false, 'Musical Harmonies', 'Enjoy the melodies and rhythms of music.', '1223389346048', '1223389346048'),
('5', '2', 'https://www.youtube.com/watch?v=35Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7955', false, 'Culinary Delights', 'Savor the flavors of exquisite cuisine.', '1223389346048', '1223389346048'),
('5', '3', 'https://www.youtube.com/watch?v=36Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7956', false, 'Journey through History', 'Learn about historical events and figures.', '1223389346048', '1223389346048'),
('1', '1', 'https://www.youtube.com/watch?v=37Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7957', false, 'Home Improvement', 'Upgrade your home with our DIY home improvement guides.', '1223389346048', '1223389346048'),
('4', '3', 'https://www.youtube.com/watch?v=38Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7958', false, 'Beauty and Style', 'Discover beauty and style tips for a glamorous you.', '1223389346048', '1223389346048'),
('3', '3', 'https://www.youtube.com/watch?v=39Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7959', false, 'Mellow Music', 'Relax to the soothing tunes of mellow music.', '1223389346048', '1223389346048'),
('5', '1', 'https://www.youtube.com/watch?v=40Ibr_zStmfU', 'https://yt3.ggpht.com/ytc/AOPolaSKQnVS0PWsb1jwg2XOzWrHFGLJjw2sQy7xUY6D=s48-c-k-c0x00ffffff-no-rj', 'U78o7960', false, 'International Cuisine', 'Explore the diverse world of international cuisine.', '1223389346048', '1223389346048');

INSERT INTO Comments (user_id, video_id, reply, createdAt, updatedAt) 
VALUES

('1', '1', 'Great movie. I really enjoyed it.', '1223389346048', '1223389346048'),
('1', '2', 'One of the best films Ive seen in a while.', '1223389346048', '1223389346048'),
('1', '3', 'Amazing storyline and fantastic acting.', '1223389346048', '1223389346048'),
('2', '4', 'This movie is a must-watch!', '1223389346048', '1223389346048'),
('2', '5', 'I couldnt take my eyes off the screen.', '1223389346048', '1223389346048'),
('3', '6', 'A true cinematic masterpiece.', '1223389346048', '1223389346048'),
('3', '7', 'Incredible performance by the cast.', '1223389346048', '1223389346048'),
('3', '8', 'The plot twists kept me hooked.', '1223389346048', '1223389346048'),
('3', '9', 'I cant stop thinking about this film.', '1223389346048', '1223389346048'),
('3', '10', 'Bravo! Well done, filmmakers.', '1223389346048', '1223389346048'),
('4', '11', 'Absolutely loved every minute of it.', '1223389346048', '1223389346048'),
('4', '12', 'This movie exceeded my expectations.', '1223389346048', '1223389346048'),
('4', '13', 'An emotional rollercoaster.', '1223389346048', '1223389346048'),
('4', '14', 'Outstanding cinematography.', '1223389346048', '1223389346048'),
('5', '15', 'I want to watch it again and again.', '1223389346048', '1223389346048'),
('5', '16', 'This deserves all the awards.', '1223389346048', '1223389346048'),
('5', '17', 'A true work of art.', '1223389346048', '1223389346048'),
('1', '18', 'The soundtrack was perfect.', '1223389346048', '1223389346048'),
('2', '19', 'I cant get enough of this movie.', '1223389346048', '1223389346048'),
('3', '20', 'Im recommending it to everyone I know.', '1223389346048', '1223389346048'),
('4', '21', 'A cinematic gem.', '1223389346048', '1223389346048'),
('5', '22', 'I was on the edge of my seat throughout.', '1223389346048', '1223389346048'),
('1', '23', 'The character development was superb.', '1223389346048', '1223389346048'),
('1', '24', 'This film will stay with me forever.', '1223389346048', '1223389346048'),
('2', '25', 'Breathtaking visuals.', '1223389346048', '1223389346048'),
('2', '26', 'I was completely immersed in the story.', '1223389346048', '1223389346048'),
('3', '27', 'A powerful and moving experience.', '1223389346048', '1223389346048'),
('3', '28', 'I laughed, I cried, and I was amazed.', '1223389346048', '1223389346048'),
('3', '29', '10/10 would watch again.', '1223389346048', '1223389346048'),
('3', '30', 'I am  speechless. What a film!', '1223389346048', '1223389346048'),
('3', '31', 'I am recommending it to all my friends.', '1223389346048', '1223389346048'),
('4', '32', 'This is why I love cinema.', '1223389346048', '1223389346048'),
('4', '33', 'I am a fan for life after this.', '1223389346048', '1223389346048'),
('4', '34', 'This movie is pure magic.', '1223389346048', '1223389346048'),
('4', '35', 'I couldnt ask for a better film.', '1223389346048', '1223389346048'),
('5', '36', 'It left me wanting more.', '1223389346048', '1223389346048'),
('5', '37', 'A must-see for everyone.', '1223389346048', '1223389346048'),
('5', '38', 'I am still processing how good it was.', '1223389346048', '1223389346048'),
('1', '39', 'This film left me in awe.', '1223389346048', '1223389346048'),
('4', '40', 'I am in love with the characters.', '1223389346048', '1223389346048'),
('3', '41', 'I am in love with the characters.', '1223389346048', '1223389346048');

# --DQLs de Exemplo BancoYOUTUBE.sql

1) Para conhecer todos os videos que tem os usuarios em cada canal.
   
SELECT Users.firstName AS Nome, Users.lastName AS Sobre_Nome, Channels.name AS Canal, Videos.title AS Titulo_Video  
FROM Videos
JOIN Channels ON Videos.channel_id = Channels.id
JOIN Users ON Videos.user_id = Users.id
ORDER BY (Users.firstName);

2) Para conhecer os comentários dos Videos em cada canal.

SELECT c1.name AS Canal, v.title AS Titulo, c.reply AS Comentario  
FROM Comments AS c 
INNER JOIN Videos AS v ON ( c.video_id = v.id  )  
INNER JOIN Channels AS c1 ON ( v.channel_id = c1.id  )
ORDER BY (c1.name);

3) Para conhecer a quantidade de Videos que tem cada canal.

SELECT Channels.id AS ChannelID, Channels.name AS ChannelName, COUNT(Videos.title) AS VideoCount
FROM Channels
LEFT JOIN Videos ON Channels.id = Videos.channel_id
GROUP BY Channels.id, Channels.name
ORDER BY (Channels.id);

4) Para conhecer a quantidade de comentários que tem cada Video.

SELECT Videos.id AS Video_ID, Videos.title AS Titulo_Video, COUNT(Comments.reply) AS Comentarios
FROM Videos
LEFT JOIN Comments ON Videos.id = Comments.video_id
GROUP BY Videos.id, Videos.title;

5) Para conhecer o canal com mais Videos em orden descendente.

SELECT Channels.name AS ChannelName, COUNT(Videos.title) AS VideoCount
FROM Channels
LEFT JOIN Videos ON Channels.id = Videos.channel_id
GROUP BY Channels.id, Channels.name
ORDER BY VideoCount DESC;

