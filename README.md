-- 1. Очищаем старые таблицы, чтобы не было дублей и ошибок
DROP TABLE IF EXISTS Bilety;
DROP TABLE IF EXISTS Reysy;
DROP TABLE IF EXISTS Passazhiry;
DROP TABLE IF EXISTS Samolety;

-- 2. Создаем структуру заново
CREATE TABLE Samolety (
    samolet_id INTEGER PRIMARY KEY AUTOINCREMENT,
    model TEXT NOT NULL,
    vmestimost INTEGER NOT NULL
);

CREATE TABLE Reysy (
    reys_id INTEGER PRIMARY KEY AUTOINCREMENT,
    nomer_reysa TEXT NOT NULL UNIQUE,
    gorod_vyleta TEXT NOT NULL,
    gorod_pribytiya TEXT NOT NULL,
    vremya_vyleta TEXT NOT NULL,
    vremya_pribytiya TEXT NOT NULL,
    samolet_id INTEGER,
    FOREIGN KEY (samolet_id) REFERENCES Samolety(samolet_id)
);

CREATE TABLE Passazhiry (
    passazhir_id INTEGER PRIMARY KEY AUTOINCREMENT,
    imya TEXT NOT NULL,
    familiya TEXT NOT NULL,
    pasport TEXT NOT NULL UNIQUE,
    telefon TEXT,
    pochta TEXT
);

CREATE TABLE Bilety (
    bilet_id INTEGER PRIMARY KEY AUTOINCREMENT,
    reys_id INTEGER,
    passazhir_id INTEGER,
    nomer_mesta TEXT NOT NULL,
    cena REAL NOT NULL,
    data_broni TEXT NOT NULL,
    FOREIGN KEY (reys_id) REFERENCES Reysy(reys_id),
    FOREIGN KEY (passazhir_id) REFERENCES Passazhiry(passazhir_id)
);

-- 3. Заполняем Самолеты (7 штук)
INSERT INTO Samolety (model, vmestimost) VALUES ('Boeing 737-800', 189);
INSERT INTO Samolety (model, vmestimost) VALUES ('Airbus A320', 158);
INSERT INTO Samolety (model, vmestimost) VALUES ('Sukhoi Superjet 100', 98);
INSERT INTO Samolety (model, vmestimost) VALUES ('Airbus A321', 220);
INSERT INTO Samolety (model, vmestimost) VALUES ('Boeing 777-300ER', 402);
INSERT INTO Samolety (model, vmestimost) VALUES ('Embraer E190', 110);
INSERT INTO Samolety (model, vmestimost) VALUES ('MC-21-300', 163);

-- 4. Заполняем Рейсы (8 штук)
INSERT INTO Reysy (nomer_reysa, gorod_vyleta, gorod_pribytiya, vremya_vyleta, vremya_pribytiya, samolet_id) 
VALUES ('SU-100', 'Moskva', 'Sankt-Peterburg', '2026-11-15 08:00', '2026-11-15 09:30', 1);
INSERT INTO Reysy (nomer_reysa, gorod_vyleta, gorod_pribytiya, vremya_vyleta, vremya_pribytiya, samolet_id) 
VALUES ('S7-250', 'Novosibirsk', 'Moskva', '2026-11-15 12:00', '2026-11-15 16:15', 2);
INSERT INTO Reysy (nomer_reysa, gorod_vyleta, gorod_pribytiya, vremya_vyleta, vremya_pribytiya, samolet_id) 
VALUES ('DP-402', 'Moskva', 'Sochi', '2026-11-16 10:00', '2026-11-16 13:45', 4);
INSERT INTO Reysy (nomer_reysa, gorod_vyleta, gorod_pribytiya, vremya_vyleta, vremya_pribytiya, samolet_id) 
VALUES ('SU-1700', 'Moskva', 'Vladivostok', '2026-11-16 18:30', '2026-11-17 03:00', 5);
INSERT INTO Reysy (nomer_reysa, gorod_vyleta, gorod_pribytiya, vremya_vyleta, vremya_pribytiya, samolet_id) 
VALUES ('U6-214', 'Ekaterinburg', 'Kazan', '2026-11-17 09:15', '2026-11-17 10:40', 3);
INSERT INTO Reysy (nomer_reysa, gorod_vyleta, gorod_pribytiya, vremya_vyleta, vremya_pribytiya, samolet_id) 
VALUES ('N4-512', 'Kazan', 'Sochi', '2026-11-18 14:20', '2026-11-18 17:10', 1);
INSERT INTO Reysy (nomer_reysa, gorod_vyleta, gorod_pribytiya, vremya_vyleta, vremya_pribytiya, samolet_id) 
VALUES ('SU-2130', 'Moskva', 'Stambul', '2026-11-19 11:00', '2026-11-19 15:50', 4);
INSERT INTO Reysy (nomer_reysa, gorod_vyleta, gorod_pribytiya, vremya_vyleta, vremya_pribytiya, samolet_id) 
VALUES ('S7-3011', 'Sankt-Peterburg', 'Kaliningrad', '2026-11-20 07:45', '2026-11-20 09:15', 6);

-- 5. Заполняем Пассажиров (10 человек)
INSERT INTO Passazhiry (imya, familiya, pasport, telefon, pochta) 
VALUES ('Ivan', 'Ivanov', '4510 123456', '+79991112233', 'ivan@mail.ru');
INSERT INTO Passazhiry (imya, familiya, pasport, telefon, pochta) 
VALUES ('Anna', 'Petrova', '4012 654321', '+79994445566', 'anna@yandex.ru');
INSERT INTO Passazhiry (imya, familiya, pasport, telefon, pochta) 
VALUES ('Sergey', 'Sidorov', '5015 987654', '+79997778899', 'serg@gmail.com');
INSERT INTO Passazhiry (imya, familiya, pasport, telefon, pochta) 
VALUES ('Elena', 'Smirnova', '4511 223344', '+79161234567', 'elena_s@mail.ru');
INSERT INTO Passazhiry (imya, familiya, pasport, telefon, pochta) 
VALUES ('Dmitriy', 'Kuznetsov', '6514 556677', '+79039876543', 'dima.kuz@yandex.ru');
INSERT INTO Passazhiry (imya, familiya, pasport, telefon, pochta) 
VALUES ('Olga', 'Popova', '9218 889900', '+79265554433', 'olga.popova@gmail.com');
INSERT INTO Passazhiry (imya, familiya, pasport, telefon, pochta) 
VALUES ('Aleksey', 'Vasiliev', '4519 334455', '+79156667788', 'alex_v@mail.ru');
INSERT INTO Passazhiry (imya, familiya, pasport, telefon, pochta) 
VALUES ('Mariya', 'Sokolova', '4018 778899', '+79851110022', 'masha.sok@yandex.ru');
INSERT INTO Passazhiry (imya, familiya, pasport, telefon, pochta) 
VALUES ('Maksim', 'Morozov', '2715 445566', '+79052223344', 'maks_moroz@mail.ru');
INSERT INTO Passazhiry (imya, familiya, pasport, telefon, pochta) 
VALUES ('Ekaterina', 'Novikova', '4520 990011', '+79653334455', 'katya.nov@gmail.com');

-- 6. Заполняем Билеты (12 штук)
INSERT INTO Bilety (reys_id, passazhir_id, nomer_mesta, cena, data_broni) 
VALUES (1, 1, '12A', 5500.00, '2026-11-01');
INSERT INTO Bilety (reys_id, passazhir_id, nomer_mesta, cena, data_broni) 
VALUES (2, 2, '05C', 11200.00, '2026-11-02');
INSERT INTO Bilety (reys_id, passazhir_id, nomer_mesta, cena, data_broni) 
VALUES (3, 3, '21B', 6800.00, '2026-11-03');
INSERT INTO Bilety (reys_id, passazhir_id, nomer_mesta, cena, data_broni) 
VALUES (4, 4, '02A', 28500.00, '2026-11-04');
INSERT INTO Bilety (reys_id, passazhir_id, nomer_mesta, cena, data_broni) 
VALUES (4, 5, '02B', 28500.00, '2026-11-04');
INSERT INTO Bilety (reys_id, passazhir_id, nomer_mesta, cena, data_broni) 
VALUES (5, 6, '14F', 4200.00, '2026-11-05');
INSERT INTO Bilety (reys_id, passazhir_id, nomer_mesta, cena, data_broni) 
VALUES (6, 7, '09D', 7900.00, '2026-11-06');
INSERT INTO Bilety (reys_id, passazhir_id, nomer_mesta, cena, data_broni) 
VALUES (7, 8, '18A', 19400.00, '2026-11-07');
INSERT INTO Bilety (reys_id, passazhir_id, nomer_mesta, cena, data_broni) 
VALUES (7, 9, '18B', 19400.00, '2026-11-07');
INSERT INTO Bilety (reys_id, passazhir_id, nomer_mesta, cena, data_broni) 
VALUES (8, 10, '04A', 4900.00, '2026-11-08');
INSERT INTO Bilety (reys_id, passazhir_id, nomer_mesta, cena, data_broni) 
VALUES (1, 2, '12B', 5500.00, '2026-11-09');
INSERT INTO Bilety (reys_id, passazhir_id, nomer_mesta, cena, data_broni) 
VALUES (3, 1, '15C', 7100.00, '2026-11-10');
