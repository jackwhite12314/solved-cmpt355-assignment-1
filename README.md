Download Link: https://assignmentchef.com/product/solved-cmpt355-assignment-1
<br>
Description/InstructionsFor this assignment we will be using the idea of a university course database. A university canhave several departments, each of which can have a number of courses, such as CMPT 355.Some of these courses have multiple sections. These sections can be of different types, such asa lecture, lab, or tutorial. Assume that a section can only exist in one term and that each sectionhas only one instructor. Multiple students can be enrolled in multiple sections.There are four scripts included for you to use with this assignment. You can open them inDBVisualizer and run them using the arrow button with the red dot. They need to be run in thefollowing order: assgn1-ddl.sql, assgn1-dml.sql, assgn1-dml2.sql. Running these scripts willcreate the university course data model described above, and populate it with some fake data.This will let you test your queries in part two, and add new tables to the database in part three.After you are done this assignment, you can use the assgn1-dropTables.sql script to removethese tables from your database.As with all assignments in this class, make sure you keep a script of everything you do. We willbe marking the assignments based on the scripts and reports you hand in, as well as what is inyour database. Applying the scripts you hand in should be the equivalent of what is in yourdatabase. For this assignment, you can hand in Part 1 in a .txt file (since you are not applyinganything to the database). Parts 2 and 3 can be handed in as an .sql file. Remember that whenyou have multiple SQL statements in a row, you need to use the ; symbol after each statementas the statement terminator.Part 1 – Analyzing the Data Model /30Review the data model found in Assignment1-Part1.png and use it to answer the followingquestions. Keep in mind that there might be multiple ways to solve a problem. You only need toprovide one approach, unless otherwise stated.1) List all the possible candidate key(s) for the departments table. /2– If we didn’t use a surrogate key for the primary key on the enrollments table, what wouldyou have used as a natural primary key instead and why? /42) We have a gender column on the students table. The type on this column is a CHAR(1), butany single character value could be input into that field right now.a) Name two different approaches you could use to make sure that only the ISO gendercodes (M,F,U,N) are valid values to insert into the gender column. /4b) Write the DDL you would use to implement both of these solutions (but don’t actuallychange anything in the database). /103) Currently in the sections table, it is possible for the num_enrolled to be higher than themax_enrollment. What could you add to make sure this doesn’t happen? Write the codethat would accomplish this. /10Part 2 – Querying the Data Model /40Write queries to return the requested information. Make sure that the results are formatted sothat an outside user could understand what each field means. You can use your choice ofimplicit or explicit joins, except where otherwise specified. Remember that when writingqueries, a good first step is to look at all the information you need to return and identify thetables (or functions you could use) to get that data.1) Return the university name, department name, course code, course name, coursedescription, and credit units of the courses offered at the University of Saskatchewan. /52) We want to check to see if the number of students enrolled in the enrollments tablematches the number of students in sections.num_enrolled. Write a query to return a countof the number of sections that have a matching number of enrollments. /5 (HINT: you’llwant to use a subquery in the WHERE clause to aggregate data.)3) Display all the sections of the CMPT courses. Include the course code, course name, lecturetype, maximum enrollment, number currently enrolled, remaining number of availableenrollments, the name of the instructor of the section, the start and end date of the term,and the start and end time of the section. Write this query twice – once using implicit joinsand again using explicit joins. /10 (5 each)4) With the help of an inline view, return the number of sections for each lecture type of eachcourse. You should return the following information: course code, course name, lecturetype, number of sections. Sort your query first by the course code, and then by the numberof sections. /10 (HINT: try writing the inline view to aggregate the section information firstand then create the rest of the query. See the inline view example in slide set 5 for anexample.)5) We want to report a section status for each section in our database. Based on how manystudents are enrolled in the section, the section status can be one of three values: roomavailable, section full, or section over-filled. With the help of a case statement, write aquery to return the course code, course name, section code, lecture type, and sectionstatus. /10Part 3 – Changing the Data Model /30So far, our data model has a field for the student’s overall grade in the enrollments table.However, there are a lot of factors that go into that final grade. We’re going to add anassessment portion to our structure. See Assignment1-AssessmentModel.png for the updateddata model – note the addition of enrollment_assessments and assessments.1) You’ll notice there are a number of blank spaces in this model, labeled 1-7. Fill in theseblanks with appropriate values. Some of the values are foreign keys, and some are datatypes. Assume it’s possible to receive partial marks on an assessment (such as 75.5/100). /72) Write and apply the DDL statements required to add these tables to the database.Remember to include constraints (such as primary and foreign keys) where appropriate. /103) Using INSERT statements, add records for our five assignments, one midterm, and one finalinto the assessments table for the CMPT 355 lecture section. Remember that eachassignment is worth 10%, the midterm is worth 20%, and the final is worth 30%. You canassume that all assessments have a total_points value of 100, and you can make up yourown due date. /5a) Can you do this using only one insert statement with a SELECT clause? If you can, youonly have to use this one query to get full marks on the whole question. /34) Let’s say that the instructor for lectures of CMPT 355 has suddenly quit. Using theappropriate DML statements, remove the current instructor record from the databasecompletely and assign me (Ellen) to teach the class. Feel free to make up whatever data youneed to make my instructor record. /5