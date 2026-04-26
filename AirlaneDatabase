CREATE DATABASE airline_database;

USE airline_database;

CREATE TABLE customers (
id INT AUTO_INCREMENT PRIMARY KEY,
name VARCHAR(100),
status VARCHAR(50),
total_mileage INT
);

CREATE TABLE aircrafts (
id INT AUTO_INCREMENT PRIMARY KEY,
name VARCHAR(100),
total_seats INT
);

CREATE TABLE flights (
flight_number VARCHAR(10) PRIMARY KEY,
aircraft_id INT,
mileage INT,
FOREIGN KEY (aircraft_id) REFERENCES aircrafts(id)
);

CREATE TABLE bookings (
id INT AUTO_INCREMENT PRIMARY KEY,
customer_id INT,
flight_number VARCHAR(10),
FOREIGN KEY (customer_id) REFERENCES customers(id),
FOREIGN KEY (flight_number) REFERENCES flights(flight_number)
);

INSERT INTO aircrafts (name, total_seats) VALUES
('Boeing 747', 400),
('Airbus A330', 236),
('Boeing 777', 264);

INSERT INTO flights VALUES
('DL143', 1, 135),
('DL122', 2, 4370),
('DL53', 3, 2078),
('DL222', 3, 1765),
('DL37', 1, 531);

INSERT INTO customers (name, status, total_mileage) VALUES
('Agustine Riviera', 'Silver', 115235),
('Alaina Sepulvida', 'None', 6008),
('Tom Jones', 'Gold', 205767),
('Sam Rio', 'None', 2653),
('Jessica James', 'Silver', 127656),
('Ana Janco', 'Silver', 136773),
('Jennifer Cortez', 'Gold', 300582),
('Christian Janco', 'Silver', 14642);

INSERT INTO bookings (customer_id, flight_number) VALUES
(1, 'DL143'),
(1, 'DL122'),
(2, 'DL122'),
(3, 'DL122'),
(3, 'DL53'),
(3, 'DL222'),
(4, 'DL143'),
(4, 'DL37'),
(5, 'DL143'),
(5, 'DL122'),
(6, 'DL222'),
(7, 'DL222'),
(8, 'DL222');

SELECT COUNT(DISTINCT flt.flight_number)
FROM flights flt;

SELECT AVG(flt.mileage)
FROM flights flt;

SELECT AVG(air.total_seats)
FROM aircrafts air;

SELECT cus.status, AVG(cus.total_mileage)
FROM customers cus
GROUP BY cus.status;

SELECT cus.status, MAX(cus.total_mileage)
FROM customers cus
GROUP BY cus.status;

SELECT COUNT(*)
FROM aircrafts air
WHERE air.name LIKE '%Boeing%';

SELECT *
FROM flights flt
WHERE flt.mileage BETWEEN 300 AND 2000;

SELECT cus.status, AVG(flt.mileage)
FROM bookings bok
JOIN customers cus ON bok.customer_id = cus.id
JOIN flights flt ON bok.flight_number = flt.flight_number
GROUP BY cus.status;

SELECT air.name, COUNT(*) AS total_bookings
FROM bookings bok
JOIN customers cus ON bok.customer_id = cus.id
JOIN flights flt ON bok.flight_number = flt.flight_number
JOIN aircrafts air ON flt.aircraft_id = air.id
WHERE cus.status = 'Gold'
GROUP BY air.name
ORDER BY total_bookings DESC
LIMIT 1;
