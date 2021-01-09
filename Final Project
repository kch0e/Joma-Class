SELECT quiz_type
FROM quiz_metadata
group by quiz_type


SELECT distinct(quiz_id)
FROM quiz_metadata;

SELECT *
FROM quiz_metadata;

\d daily_agg_quiz_metrics


/*  1. Which quiz generated the most views? What type of quiz is it? */

select  a.quiz_id, sum(num_views) as total_views, quiz_type
FROM daily_agg_quiz_metrics a
join quiz_metadata b
on a.quiz_id = b.quiz_id
group by a.quiz_id, quiz_type
order by total_views desc


/* 2. Which quiz has the highest completion rate? What type of quiz is it and when was it
published? */

select  a.quiz_id, (sum(num_completes) /  sum(num_views) ) AS completion_rate , quiz_type, published
FROM daily_agg_quiz_metrics a
join quiz_metadata b
on a.quiz_id = b.quiz_id
group by a.quiz_id, quiz_type, published
order by completion_rate desc; 


/* 3. Which type of quiz generated the most views? What about on average, which type of
quiz generates the most views? */


SELECT a.quiz_id, b.quiz_type, sum(a.num_views) as num_of_views, avg(a.num_views) as Average_views
from daily_agg_quiz_metrics a 
join quiz_metadata b 
on a.quiz_id = b.quiz_id
group by a.quiz_id, b.quiz_type
order by num_of_views desc

/* 4. Which type of quiz has the highest completion rate? */

select  a.quiz_id, (sum(num_completes) /  sum(num_views) ) AS completion_rate , quiz_type
FROM daily_agg_quiz_metrics a
join quiz_metadata b
on a.quiz_id = b.quiz_id
group by quiz_type, a.quiz_id
order by completion_rate desc 


/* 5. Which type of quiz had the highest share rate? */

select  a.quiz_id, (sum(num_shares) /  sum(num_views) ) AS share_rate , quiz_type
FROM daily_agg_quiz_metrics a
join quiz_metadata b
on a.quiz_id = b.quiz_id
group by quiz_type, a.quiz_id
order by share_rate desc 


/*  6. Create a histogram chart where the x-axis is the number of questions and the y-axis is
the number of quizzes. */

select count(num_questions) as number_of_quizzes, num_questions
FROM quiz_metadata 
group by  num_questions
order by number_of_quizzes DESC




/* which type of quizzes perform best */


select  a.quiz_id, (sum(num_completes) /  sum(num_views) ) AS completion_rate , quiz_type
FROM daily_agg_quiz_metrics a
join quiz_metadata b
on a.quiz_id = b.quiz_id
group by quiz_type, a.quiz_id
order by completion_rate desc 


select sum(num_views) as total_views, sum(num_completes) as total_completes, sum(num_shares) as total_shares, quiz_type 
from daily_agg_quiz_metrics a 
join quiz_metadata b 
on a.quiz_id = b.quiz_id
group by quiz_type 



select sum(num_views) as total_views, sum(num_completes) as total_completes, sum(num_shares) as total_shares, published 
from daily_agg_quiz_metrics a 
join quiz_metadata b 
on a.quiz_id = b.quiz_id
group by published 
order by total_views desc 


Select device_type, sum(num_views) as total_views, sum(num_completes) as total_completes, sum(num_shares) as total_shares
from daily_agg_quiz_metrics a 
join quiz_metadata b 
on a.quiz_id = b.quiz_id
GROUP by device_type 

/* When should we publish a quiz?*/

SELECT published,"date", sum(num_views) as total_views, sum(num_completes) as total_completes, sum(num_shares) as total_shares
from daily_agg_quiz_metrics a 
join quiz_metadata b 
on a.quiz_id = b.quiz_id
group by published, "date"
order by total_views DESC

/* What is the optimal length for a quiz? */

select num_questions, num_completes, num_views, num_shares
from quiz_metadata a 
join daily_agg_quiz_metrics b 
on a.quiz_id = b.quiz_id
order by num_completes desc

 /* What are the differences between the device type? Should we focus on one more than the other? */
Select device_type, sum(num_views) as total_views, sum(num_completes) as total_completes, sum(num_shares) as total_shares
from daily_agg_quiz_metrics a 
join quiz_metadata b 
on a.quiz_id = b.quiz_id
GROUP by device_type 
