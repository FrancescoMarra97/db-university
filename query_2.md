# Group by:
1) Contare quanti iscritti ci sono stati ogni anno:
SELECT 
YEAR(`enrolment_date`) AS anno_iscrizione,
COUNT(*) AS numero_iscritti		
FROM `students`
GROUP BY YEAR(`enrolment_date`)

2) Contare gli insegnanti che hanno l'ufficio nello stesso edificio:

SELECT 
`office_address` AS edificio, 
COUNT(id) 
FROM `teachers`
GROUP BY(`office_address`)

3) Calcolare la media dei voti di ogni appello d'esame:

SELECT 
AVG(vote) AS media_voto,
`exam_id`
FROM `exam_student`
GROUP BY `exam_id`

4) Contare quanti corsi di laurea ci sono per ogni dipartimento

SELECT 
COUNT(id) AS numero_corsi,
`department_id`
FROM `degrees`
GROUP BY `department_id`

# Joins:
1) Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT *
FROM `students`
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name`= "Corso di Laurea in Economia"