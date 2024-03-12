1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

```sql
    SELECT
        `students`.`name`,
        `students`.`surname`,
        `degrees`.`name` AS `degree`
    FROM `students`
    INNER JOIN `degrees`
    ON `degrees`.`id` = `students`.`degree_id`
    WHERE `degrees`.`name` = 'Corso di Laurea in Economia';
```

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
   Neuroscienze

```sql
    SELECT
        `degrees`.`name`,
        `degrees`.`level`,
        `departments`.`name`
    FROM `degrees`
    INNER JOIN `departments`
    ON `degrees`.`department_id` = `departments`.`id`

    WHERE
        `departments`.`name` = 'Dipartimento di Neuroscienze' AND
        `degrees`.`level` = 'magistrale';
```

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

```sql
    SELECT
        `teachers`.`id`,
        `teachers`.`name`,
        `teachers`.`surname`,
        `courses`.`name`
    FROM `teachers`

    INNER JOIN `course_teacher`
    ON `teachers`.`id` = `course_teacher`.`teacher_id`

    INNER JOIN `courses`
    ON `course_teacher`.`course_id` = `courses`.`id`
    WHERE `teachers`.`id` = 44;
```

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
   sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
   nome

```sql
    SELECT
        `students`.`name`,
        `students`.`surname`,
        `degrees`.`name` AS `degree`,
        `departments`.`name` AS `department`
    FROM `students`

    INNER JOIN `degrees`
    ON `students`.`degree_id` = `degrees`.`id`

    INNER JOIN `departments`
    ON `departments`.`id` = `degrees`.`department_id`

    ORDER BY `students`.`surname` ASC;
```

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

```sql
    SELECT
        `degrees`.`name` AS `degree`,
        `courses`.`name` AS `course`,
        `teachers`.`name` AS `teachers_name`,
        `teachers`.`surname` AS `teachers_surname`
    FROM `degrees`

    INNER JOIN `courses`
    ON `degrees`.`id` = `courses`.`degree_id`

    INNER JOIN `course_teacher`
    ON `course_teacher`.`course_id` = `courses`.`id`

    INNER JOIN `teachers`
    ON `course_teacher`.`teacher_id` = `teachers`.`id`;
```

6. Selezionare tutti i docenti che insegnano nel Dipartimento di
   Matematica (54)

```sql
    SELECT
        `teachers`.`name` AS `teachers_name`,
        `teachers`.`surname` AS `teachers_surname`,
        `departments`.`name` AS `department`
    FROM `teachers`

    INNER JOIN `course_teacher`
    ON `teachers`.`id` = `course_teacher`.`teacher_id`

    INNER JOIN `courses`
    ON `courses`.`id` = `course_teacher`.`course_id`

    INNER JOIN `degrees`
    ON `courses`.`degree_id` = `degrees`.`id`

    INNER JOIN `departments`
    ON `departments`.`id` = `degrees`.`department_id`

    WHERE `departments`.`name` = 'Dipartimento di Matematica';
```

7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
   per ogni esame, stampando anche il voto massimo. Successivamente,
   filtrare i tentativi con voto minimo 18.

```sql

```
