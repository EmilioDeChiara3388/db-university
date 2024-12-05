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
