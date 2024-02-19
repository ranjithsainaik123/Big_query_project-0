#Average scores across subjects of students grouped by year group.
select si.year_group ,avg(se.math_score) as avg_maths ,avg(se.reading_score) as avg_reading, avg(se.writing_score) as avg_writing from `midyear-nebula-413114.student_details.student_exam_results`AS se join `midyear-nebula-413114.student_details.student_csv`as si
on se.student_id = si.student_id  
group by si.year_group 
ORDER BY si.year_group  ASC;
#Average scores across subjects of students grouped by gender.
select si.gender ,avg(se.math_score) as avg_maths ,avg(se.reading_score) as avg_reading, avg(se.writing_score) as avg_writing from `midyear-nebula-413114.student_details.student_exam_results`AS se inner join `midyear-nebula-413114.student_details.student_csv`as si
on se.student_id = si.student_id  
group by si.gender;

#How does parental level of education affect student test scores
SELECT
  Parental_Level_of_Education,
  CORR(se.math_score, se.reading_score) AS math_reading_correlation,
  CORR(se.math_score, se.writing_score) AS math_writing_correlation,
  CORR(se.reading_score, se.writing_score) AS reading_writing_correlation
FROM
  `midyear-nebula-413114.student_details.student_exam_survey` as si
join 
  `midyear-nebula-413114.student_details.student_exam_results`AS se
on se.student_id = si.student_id  

GROUP BY
  Parental_Level_of_Education
ORDER BY
  Parental_Level_of_Education;
#How well did the test preparation course help students?
SELECT
  CORR(math_score,si.test_preparation_course) AS math_score_corr,
  CORR(reading_score, si.test_preparation_course) AS reading_score_corr,
  CORR(writing_score, si.test_preparation_course) AS writing_score_corr
FROM
  `midyear-nebula-413114.student_details.student_exam_survey` as si
join 
  `midyear-nebula-413114.student_details.student_exam_results`AS se
on se.student_id = si.student_id ;


