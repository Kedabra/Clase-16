Crear una base de datos llamada call_list
CREATE DATABASE call_list;
\c call_list;


En la base de datos recien creada, crear la tabla users con los campos id (clave primaria), first_name, email.
CREATE TABLE user(id integer PRIMARY KEY, first_name VARCHAR(20),, email VARCHAR(30));


Ingresar un usuario, llamado Carlos (el resto de los datos deben inventarlos).
INSERT INTO users(id, first_name, email) VALUES(1, 'Carlos', 'carlos@email.com');



Ingresar un usuario, llamada Laura (el resto de los datos deben inventarlos).
INSERT INTO users(id, first_name, last_name, email) VALUES(2, 'Laura', 'laura@email.com');



Crear una tabla llamada calls con los campos id (clave primaria), phone, date, user_id (foreign key relacionado a users).
CREATE TABLE calls (id integer PRIMARY KEY, phone integer, date VARCHAR(8), user_id INT, FOREING KEY (user_id) REFERENCES user(id));


Agregar a la tabla users el campo last_name.
ALTER TABLE users ADD COLUMN last_name VARCHAR(20)


Ingresar el apellido del usuario Carlos.
UPDATE users SET last_name = 'Ramirez' WHERE id = 1;


Ingresar el apellido del usuario Laura.
UPDATE users SET last_name = 'Olarre' WHERE id = 2;

Ingresar 6 llamadas asociadas al usuario Laura.
INSERT INTO calls(id, phone, date, user_id) VALUES(1, 12589751, 32/42/23, 2);
INSERT INTO calls(id, phone, date, user_id) VALUES(2, 12589751, 32/42/23, 2);
INSERT INTO calls(id, phone, date, user_id) VALUES(3, 19876544, 97/26/53, 2);
INSERT INTO calls(id, phone, date, user_id) VALUES(4, 64829465, 41/56/27, 2);
INSERT INTO calls(id, phone, date, user_id) VALUES(5, 98161236, 34/54/65, 2);
INSERT INTO calls(id, phone, date, user_id) VALUES(6, 12467656, 54/737/76, 2);


Ingresar 4 llamadas asociadas al usuario Carlos.
INSERT INTO calls(id, phone, date, user_id) VALUES(7, 12467656, 54/737/76, 1);
INSERT INTO calls(id, phone, date, user_id) VALUES(8, 18765446, 74/717/66, 1);
INSERT INTO calls(id, phone, date, user_id) VALUES(9, 14655776, 13/717/26, 1);
INSERT INTO calls(id, phone, date, user_id) VALUES(10, 1965746, 54/757/36, 1);


Crear un nuevo usuario.
INSERT INTO users(id, first_name, email, last_name) VALUES(3, 'Omar', 'omarelias@gmail.com', 'Ramirez');


Seleccionar la cantidad de llamados de cada uno de los usuarios (nombre de usuario y cantidad de llamadas).
SELECT name, count(call) FROM users FULL JOIN calls ON (user.id = calls.user_id) group by name;


Seleccionar los llamados del usuario llamado Carlos ordenados por fecha en orden descendente.
SELECT users.first_name, count(calls.id) FROM users FULL JOIN calls ON users.id = calls.user_id group by users.first_name;



Nuevos cambios solicitados por cliente.
"Necesito agregar a la base una tabla de auditoría que registre el motivo del borrado de una llamada y el usuario que lo efectuó."

A partir de la base anterior, agregar este requerimiento y modelar la base de datos (agregar print de pantalla [utilizar https://www.draw.io/]).
