GROUP BY:
1 - Contare quanti iscritti ci sono stati ogni anno
SELECT COUNT(*) AS `numero_iscritti`, YEAR(`students`.`enrolment_date`) AS `anno`
FROM `students`
GROUP BY YEAR(`students`.`enrolment_date`);

2 - Contare gli insegnanti che hanno l'ufficio nello stesso edificio
SELECT COUNT(*) AS `numero_insegnanti`, `teachers`.`office_address` AS `indirizzo`
FROM `teachers`
GROUP BY `teachers`.`office_address`;

3 - Calcolare la media dei voti di ogni appello d'esame
SELECT AVG(`exam_student`.`vote`) AS `media_voto`,
`exam_student`.`exam_id` AS `id_esame`
FROM `exam_student`
GROUP BY `exam_student`.`exam_id`;

4 - Contare quanti corsi di laurea ci sono per ogni dipartimento
SELECT COUNT(*) AS `numero_corsi_di_laurea`,
`department_id` AS `id_dipartimento`
FROM `degrees`
GROUP BY `department_id`;


JOINS
1 - Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
SELECT `students`.*
FROM `students`
INNER JOIN `degrees`
ON `students`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = "Corso di Laurea in Economia";

2 - Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
SELECT *
FROM `degrees`
INNER JOIN `departments`
ON `degrees`.`department_id` = `departments`.`id`
WHERE `degrees`.`level` = "magistrale"
AND `departments`.`name` = "Dipartimento di Neuroscienze";

3 - Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
SELECT `courses`.`id` AS `id_corso`,
`courses`.`name` AS `nome_corso`
FROM `courses`
INNER JOIN `course_teacher` ON `course_teacher`.`course_id` = `courses`.`id`
INNER JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`
WHERE `teachers`.`id` = 44;

4 - Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
SELECT `students`.`id` AS `id_studente`,
`students`.`name` AS `nome_ studente`,
`students`.`surname` AS `cognome_studente`,
`degrees`.`name` AS `nome_corso_di_laurea`,
`degrees`.`level` AS `tipo_corso_di_laurea`,
`degrees`.`address` AS `indirizzo`,
`degrees`.`email` AS `email`,
`degrees`.`website` AS `sito`,
`departments`.`name` AS `dipartimento`
FROM `students`
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
ORDER BY `students`.`surname` ASC;



