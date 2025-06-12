## Selezionare tutti gli studenti nati nel 1990

SELECT \* FROM uni.students
WHERE YEAR(`date_of_birth`) = 1990

## Selezionare tutti i corsi che valgono più di 10 crediti

SELECT \* FROM uni.courses
WHERE `cfu` > 10;

## Selezionare tutti gli studenti che hanno più di 30 anni

SELECT \* FROM uni.students
WHERE 2025 - YEAR(`date_of_birth`) > 30;

## Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea

SELECT \* FROM uni.courses
WHERE `period`= "I semestre" AND `year` = 1;

## Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020

SELECT \* FROM uni.exams
WHERE DATE(`date`) = "2020-06-20" AND HOUR(`hour`) > "14:00:00"

## Selezionare tutti i corsi di laurea magistrale

SELECT \* FROM uni.degrees
WHERE `level` = "magistrale"

## Da quanti dipartimenti è composta l'università?

SELECT COUNT(`id`) FROM uni.departments

## Quanti sono gli insegnanti che non hanno un numero di telefono?

SELECT COUNT(\*) FROM uni.teachers
WHERE `phone` IS NULL
