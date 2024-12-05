1 - Contare quanti iscritti ci sono stati ogni anno
SELECT COUNT(*) AS `numero_iscritti`, YEAR(`students`.`enrolment_date`) AS `anno`
FROM `students`
GROUP BY YEAR(`students`.`enrolment_date`);

2 - Contare gli insegnanti che hanno l'ufficio nello stesso edificio
SELECT COUNT(*) AS `numero_insegnanti`, `teachers`.`office_address` AS `indirizzo`
FROM `teachers`
GROUP BY `teachers`.`office_address`;