# Elizabeth Figueroa's SQL Portfolio
## Welcome to my SQL Portfolio! This code repository contains examples of SQL I've written. Feel free to take a look and reach out via email you have any quesitons! 
elizabeth.figueroaef83@gmail.com

SELECT COUNT(*)
FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info"
WHERE type='Movie';

SELECT MAX(date(date_added))
FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info";

SELECT title
FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info"
ORDER BY title ASC;

SELECT Director
FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info" titles
LEFT JOIN  "CharlotteChaze/BreakIntoTech"."netflix_people" people
ON titles.show_id=people.show_id
WHERE titles.title='Bright Star'

SELECT title, min(release_year) 
FROM "CharlotteChaze/BreakIntoTech"."netflix_titles_info"
WHERE type='Movie'
GROUP BY title, release_year
ORDER BY release_year ASC
LIMIT 1;
