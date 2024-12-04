1) select * from `students`
 where year(date_of_birth) = 1990 
 LIMIT 0, 1000	
 160 row(s) returned	0,032 sec / 0,000 sec

2) select * from `courses` 
where cfu > 10 LIMIT 0, 1000	
479 row(s) returned	0,000 sec / 0,016 sec

3) select * from `students`
where (year(current_date()) - year(date_of_birth)) > 30	
3646 row(s) returned	0,000 sec / 0,016 sec

4) select * from `courses` 
where `period` = "I semestre" AND `year` = 1	
286 row(s) returned	0,000 sec / 0,000 sec

5) select * from `exams`
 where date = "2020-06-20" AND hour > "14:00:00"	
 21 row(s) returned	0,016 sec / 0,000 sec

6) select * from `degrees` 
where `level` = "magistrale"	
38 row(s) returned	0,000 sec / 0,000 sec

7) select count(*)
from departments
count = 12;

8) select * from `teachers`
 where `phone` is null	
 50 row(s) returned	0,000 sec / 0,000 sec

9) INSERT INTO `students` (`id`, `degree_id`, `name`, `surname`, `date_of_birth`, `fiscal_code`, `enrolment_date`, `registration_number`, `email`)
 values (null, 43, "Francesco" , "Booleano", "1990-05-14", "ABCDEF12G34H567I", "2020-09-01", "123456", "francesco.booleano@libero.it")	
 1 row(s) affected	0.031 sec

10) select * 
from teachers 
where name = "Pietro" AND surname = "Rizzo" 
LIMIT 0, 1000	1 row(s) returned	0.000 sec / 0.000 sec
	(id: 58 name:Pietro	surname:Rizzo	phone:+21 6710 0964205	email:sanna.michele@negri.it	office_address:Contrada Santoro 17 Appartamento 30	office_number: 125)

update teachers 
set office_number = "126" 
where id = 58	
1 row(s) affected Rows matched: 1  Changed: 1  Warnings: 0	0.031 sec


11) select *
from students
where name="Francesco" and surname= "Booleano"
(	id:5001	degree_id:43	name:Francesco	surname:Booleano	date_of_birth:1990-05-14	fiscal_code:ABCDEF12G34H567I	enrolment_date:2020-09-01	registration_number:123456	email:francesco.booleano@libero.it)

delete from students
where id = "5001"
1 row(s) affected	0.063 sec



