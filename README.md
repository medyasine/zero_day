drop database if exists mydatabase2;
CREATE DATABASE IF NOT EXISTS mydatabase2 collate utf8mb4_general_ci;

USE mydatabase2;

CREATE TABLE DEPARTEMENT (
    ID_DEP INT AUTO_INCREMENT PRIMARY KEY,
    NOM_DEP VARCHAR(255) NOT NULL,
    Ville VARCHAR(255)
);

CREATE TABLE EMPLOYE (
    ID_EMP INT AUTO_INCREMENT PRIMARY KEY,
    NOM_EMP VARCHAR(255) NOT NULL,
    PRENOM_EMP VARCHAR(255),
    DATE_NAIS_EMP DATE,
    SALAIRE DECIMAL(10, 2),
    ID_DEP INT,
    FOREIGN KEY (ID_DEP) REFERENCES DEPARTEMENT(ID_DEP)
);

INSERT INTO DEPARTEMENT (NOM_DEP, Ville) VALUES
    ('HR Department', 'New York'),
    ('Finance Department', 'Los Angeles'),
    ('IT Department', 'San Francisco'),
    ('Marketing Department', 'Chicago'),
    ('Sales Department', 'Houston');

INSERT INTO EMPLOYE (NOM_EMP, PRENOM_EMP, DATE_NAIS_EMP, SALAIRE, ID_DEP) VALUES
    ('Smith', 'John', '1985-03-15', 55000.00, 1), 
    ('Johnson', 'Sarah', '1990-08-22', 60000.00, 1), 
    ('Williams', 'Michael', '1988-11-10', 70000.00, 2), 
    ('Brown', 'Emily', '1993-05-25', 62000.00, 3),
    ('Davis', 'Robert', '1980-09-30', 58000.00, 4);

alter table EMPLOYE 
add column salaire_moyen  int default 0;
