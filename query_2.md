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

2) Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

SELECT *
FROM `degrees`
JOIN `departments` ON `degrees`.`department_id`= `departments`.`id`
WHERE `degrees`.`level`= "Magistrale" AND `departments`.`name` = "Dipartimento di Neuroscienze"

3) Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT *
FROM `course_teacher`
JOIN `courses` ON `course_teacher`.`course_id`= `courses`.`id`
WHERE `teacher_id` = 44

4) Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome:

SELECT `students`.*,
`degrees`.`name` AS `nome_corso`,
`departments`.`name` AS `nome_dipartimento`
FROM `students`
JOIN `degrees` ON `degrees`.`department_id` = `degrees`.`id`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
ORDER BY `students`.`surname`, `students`.`name`

5) Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

SELECT 
`degrees`.`name` AS `nome_corso_laurea`,
`courses`.`name` AS `nome_corsi`,
`teachers`.`name`, `teachers`.`surname`
FROM `degrees`
JOIN `courses` ON `degrees`.`id`=`courses`.`degree_id`
JOIN `course_teacher` ON `courses`.`id`= `course_teacher`.`course_id`
JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`

6) Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica 

SELECT `teachers`.*
FROM `teachers`
JOIN `course_teacher` ON `teachers`.`id`= `course_teacher`.`teacher_id`
JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
WHERE `departments`.`name` = 'Dipartimento di Matematica'