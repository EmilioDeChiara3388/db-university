1 - Contare quanti iscritti ci sono stati ogni anno
SELECT COUNT(*) AS `numero_iscritti`, YEAR(`students`.`enrolment_date`) AS `anno`
FROM `students`
GROUP BY YEAR(`students`.`enrolment_date`);