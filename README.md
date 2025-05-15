CREATE TABLE disasters (
 id INT AUTO_INCREMENT PRIMARY KEY,
name VARCHAR(255),
 type VARCHAR(255),
 date DATE,
 location VARCHAR(255),
 severity VARCHAR(50)
);
CREATE TABLE donations (
 id INT AUTO_INCREMENT PRIMARY KEY,
 user_id INT,
 amount DECIMAL(10, 2),
 date DATE,
 FOREIGN KEY (user_id) REFERENCES users(id)
);
CREATE TABLE event_logs (
 id INT AUTO_INCREMENT PRIMARY KEY,
 event_type VARCHAR(255),
 description TEXT,
 date DATE
);
CREATE TABLE logistics (
 id INT AUTO_INCREMENT PRIMARY KEY,
 resource_id INT,
 quantity INT,
 status VARCHAR(50),
 date DATE,
 FOREIGN KEY (resource_id) REFERENCES resources(id)
);
CREATE TABLE messages (
 id INT AUTO_INCREMENT PRIMARY KEY,
 user_id INT,
 message TEXT,
 date DATE,

FOREIGN KEY (user_id) REFERENCES users(id)
);
CREATE TABLE relief_terms (
 id INT AUTO_INCREMENT PRIMARY KEY,
 term VARCHAR(255),
 definition TEXT
);
CREATE TABLE resources (
 id INT AUTO_INCREMENT PRIMARY KEY,
 name VARCHAR(255),
 type VARCHAR(255),
 quantity INT
);
CREATE TABLE users (
 id INT AUTO_INCREMENT PRIMARY KEY,
 name VARCHAR(255),
 email VARCHAR(255),
 password VARCHAR(255)
);
CREATE TABLE volunteers (
 id INT AUTO_INCREMENT PRIMARY KEY,
 name VARCHAR(255),
 contact VARCHAR(255),
 availability VARCHAR(255)
);
CREATE TABLE volunteer_tasks (
 id INT AUTO_INCREMENT PRIMARY KEY,
 volunteer_id INT,
 task_description TEXT,
 status VARCHAR(50),
 date DATE,

FOREIGN KEY (volunteer_id) REFERENCES volunteers(id)
);

INSERT INTO disasters (name, type, date, location, severity) 
VALUES
('Flood', 'Natural', '2023-01-15', 'City A', 'High'),
('Earthquake', 'Natural', '2023-02-20', 'City B', 'Severe'),
('Fire', 'Accidental', '2023-03-12', 'City C', 'Moderate')
INSERT INTO users (name, email, password) VALUES
('Emran', 'emran@example.com', 'password1'),
('Talha', 'talha@example.com', 'password2'),
('Ruhin', 'ruhin@example.com', 'password3')

INSERT INTO donations (user_id, amount, date) VALUES
(1, 100.00, '2023-01-01'),
(2, 200.00, '2023-01-15'),
(3, 150.00, '2023-02-10')

INSERT INTO event_logs (event_type, description, date) 
VALUES
('Disaster Declared', 'A disaster has been declared in City A due to flooding.', '2023-01-
15'),
('Evacuation', 'Evacuation orders issued for City B after earthquake.', '2023-02-20'),
('Fire Contained', 'Fire in City C has been contained.', '2023-03-12')

INSERT INTO logistics (resource_id, quantity, status, date) 
VALUES
(1, 50, 'Delivered', '2023-01-02'),
(2, 100, 'In Transit', '2023-01-16'),
(3, 70, 'Delivered', '2023-02-11')

INSERT INTO messages (user_id, message, date)
VALUES
(1, 'We need more volunteers.', '2023-01-01'),
(2, 'Donation received, thank you!', '2023-01-15'),
(3, 'Relief materials dispatched.', '2023-02-10')

INSERT INTO relief_terms (term, definition) 
VALUES
('Evacuation', 'The process of moving people from a dangerous place to safety.'),
('Shelter', 'A place providing temporary protection from bad weather or danger.'),
('Rescue', 'To save someone from a dangerous or distressing situation.')

INSERT INTO resources (name, type, quantity) 
VALUES
('Water Bottles', 'Consumable', 500),
('Blankets', 'Non-Consumable', 200),
('Medical Kits', 'Medical', 150)

INSERT INTO volunteers (name, contact, availability) VALUES
('Shanto', 'shanto@example.com', 'Weekends'),
('Fardin', 'fardin@example.com', 'Weekdays'),
('Tanvir', 'tanvir@example.com', 'Weekends')

