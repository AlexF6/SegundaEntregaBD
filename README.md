# SegundaEntregaBD

CREATE DATABASE hotel;

USE hotel;

CREATE TABLE habitaciones(
	id INT IDENTITY(1,1) PRIMARY KEY,
	tipo VARCHAR(30) NOT NULL
);

CREATE TABLE empleados(
	id INT IDENTITY(1,1) PRIMARY KEY,
	nombre VARCHAR(50) NOT NULL
);

CREATE TABLE opiniones(
	id INT IDENTITY(1,1) PRIMARY KEY,
	opinion VARCHAR(30) NOT NULL
);

CREATE TABLE hoteles(
	id INT IDENTITY(1,1) PRIMARY KEY,
	nombre VARCHAR(30) NOT NULL
);

CREATE TABLE clientes(
	id INT IDENTITY(1,1) PRIMARY KEY,
	primer_nombre VARCHAR(30) NOT NULL,
	primer_apellido VARCHAR(30) NOT NULL
);

CREATE TABLE correos(
	id INT IDENTITY(1,1) PRIMARY KEY,
	cliente_id INT NOT NULL,
	correo VARCHAR(30) NOT NULL,
	FOREIGN KEY (cliente_id) REFERENCES clientes(id)
);

CREATE TABLE servicios(
	id INT IDENTITY(1,1) PRIMARY KEY,
	servicio VARCHAR(30) NOT NULL
);

CREATE TABLE reservas(
	id INT IDENTITY(1,1) PRIMARY KEY,
	cliente_id INT NOT NULL,
	habitacion_id INT NOT NULL,
	hotel_id INT NOT NULL,
	empleado_id INT NOT NULL,
	opinion_id INT NOT NULL,
	FOREIGN KEY (cliente_id) REFERENCES clientes(id),
	FOREIGN KEY (habitacion_id) REFERENCES habitaciones(id),
	FOREIGN KEY (hotel_id) REFERENCES hoteles(id),
	FOREIGN KEY (empleado_id) REFERENCES empleados(id),
	FOREIGN KEY (opinion_id) REFERENCES opiniones(id)
);

CREATE TABLE detalle_servicios(
	reserva_id INT NOT NULL,
	servicio_id INT NOT NULL,
	PRIMARY KEY (reserva_id, servicio_id),
	FOREIGN KEY (reserva_id) REFERENCES reservas(id),
	FOREIGN KEY (servicio_id) REFERENCES servicios(id)
);
