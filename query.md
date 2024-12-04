1) select * from `students` where year(date_of_birth) = 1990 LIMIT 0, 1000	160 row(s) returned	0,032 sec / 0,000 sec
2) select * from `courses` where cfu > 10 LIMIT 0, 1000	479 row(s) returned	0,000 sec / 0,016 sec
3) select * from `students` where (year(current_date()) - year(date_of_birth)) > 30	3646 row(s) returned	0,000 sec / 0,016 sec
4) select * from `courses` where `period` = "I semestre" AND `year` = 1	286 row(s) returned	0,000 sec / 0,000 sec
5) select * from `exams` where date = "2020-06-20" AND hour > "14:00:00"	21 row(s) returned	0,016 sec / 0,000 sec
6) select * from `degrees` where `level` = "magistrale"	38 row(s) returned	0,000 sec / 0,000 sec



