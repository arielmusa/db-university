## Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

```
SELECT \* FROM uni.students

INNER JOIN `degrees`
ON `degrees`.`id` = `students`.`degree_id`

WHERE `degrees`.`name` = "Corso di Laurea in Economia"
```

## Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

```
SELECT \* FROM uni.degrees

INNER JOIN `departments`
ON `departments`.`id` = `degrees`.`department_id`

WHERE `level` = "magistrale"
```

## Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

```
SELECT \* FROM uni.course_teacher
INNER JOIN `courses`
ON `courses`.`id` = `course_teacher`.`course_id`

INNER JOIN `teachers`
ON `course_teacher`.`teacher_id` = `teachers`.`id`

WHERE `teacher_id` = 44
```

## Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

```
SELECT \* FROM uni.students
INNER JOIN `degrees`
ON `degrees`.`id` = `students`.`degree_id`

INNER JOIN `departments`
ON `departments`.`id` = `degrees`.`department_id`

ORDER BY `students`.`name`ASC, `students`.`surname` ASC
```

## Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

```
SELECT \* FROM uni.degrees

INNER JOIN `courses`
ON `degrees`.`id` = `courses`.`degree_id`

INNER JOIN `course_teacher`
ON `course_teacher`.`course_id` = `courses`.`id`

INNER JOIN `teachers`
ON `teachers`.`id` = `course_teacher`.`teacher_id`
```

## Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

```
SELECT DISTINCT
`teachers`.`id`,
`teachers`.`name`,
`teachers`.`surname`,
`teachers`.`office_address`,
`departments`.`name`

FROM uni.teachers

INNER JOIN `course_teacher`
ON `teachers`.`id` = `course_teacher`.`teacher_id`

INNER JOIN `courses`
ON `courses`.`id` = `course_teacher`.`course_id`

INNER JOIN `degrees`
ON `degrees`.`id` = `courses`.`degree_id`

INNER JOIN `departments`
ON `departments`.`id` = `degrees`.`department_id`

WHERE `departments`.`name` = "Dipartimento di Matematica"

ORDER BY `teachers`.`name` ASC
```
