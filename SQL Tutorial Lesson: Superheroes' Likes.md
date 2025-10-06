Here’s how you can write the **Marvel’s Avengers “Likes Category”** problem in the same polished GitHub-style Markdown format you like. You can save this as something like **`problems/Marvel Avengers Likes Category.md`**.

---

````markdown
### Problem Description:
Explore the Marvel Avengers social media dataset and categorize superheroes by their average likes.  
You need to display each actor, character, social media platform, average likes, and their likes category based on the following rules:

- **Super Likes**: average likes ≥ 15,000  
- **Good Likes**: average likes between 5,000 and 14,999 (inclusive)  
- **Low Likes**: average likes < 5,000  

Sort the results by **average likes** (descending).

---

### Input Schema:
Assume a table named `avengers` (or similar) with columns:

| Column Name         | Type             | Description |
|----------------------|------------------|--------------|
| `actor`              | varchar           | Actor name portraying the character |
| `character`          | varchar           | The character name |
| `superhero_alias`    | varchar           | The superhero alias |
| `platform`           | varchar           | Social media platform (e.g. Instagram, Twitter) |
| `followers`          | integer           | Number of followers |
| `posts`               | integer           | Number of posts |
| `engagement_rate`     | decimal(5,2)      | Engagement rate |
| `avg_likes`           | integer            | Average likes on posts |
| `avg_comments`        | integer            | Average comments on posts |

---

### Example Input:

| actor               | character        | superhero_alias | platform   | followers | posts | engagement_rate | avg_likes | avg_comments |
|---------------------|------------------|------------------|------------|-----------|-------|------------------|-----------|--------------|
| Robert Downey Jr.   | Tony Stark        | Iron Man           | Instagram  | 500000    | 200   | 8.20             | 12000     | 800          |
| Chris Evans          | Steve Rogers      | Captain America     | Twitter    | 300000    | 150   | 6.50             | 8000      | 500          |
| Scarlett Johansson  | Natasha Romanoff  | Black Widow         | Instagram  | 700000    | 300   | 7.80             | 15000     | 1000         |
| Chris Hemsworth      | Thor              | Thor                | YouTube    | 400000    | 100   | 9.10             | 20000     | 1200         |
| Mark Ruffalo         | Bruce Banner       | Hulk                | Twitter    | 200000    | 80    | 5.30             | 6000      | 400          |

---

### Desired Output:

| actor                  | character        | platform     | avg_likes | likes_category |
|--------------------------|------------------|----------------|-----------|----------------|
| Chris Hemsworth           | Thor             | YouTube        | 20000     | Super Likes     |
| Scarlett Johansson       | Natasha Romanoff | Instagram      | 15000     | Super Likes     |
| Robert Downey Jr.        | Tony Stark        | Instagram      | 12000     | Good Likes       |
| Mark Ruffalo              | Bruce Banner       | Twitter         | 6000      | Good Likes       |
| Chris Evans               | Steve Rogers      | Twitter         | 8000      | Good Likes       |

*(Rows sorted by `avg_likes` descending; ties broken by default row order or other criteria if needed.)*

---

### Explanation:
- **Super Likes** are assigned when `avg_likes ≥ 15,000`.  
- **Good Likes** apply when `avg_likes` is between 5,000 and 14,999 (inclusive).  
- **Low Likes** apply when `avg_likes < 5,000`.  
- We show actor, character, platform, their average likes, and which category they fall into.  
- The final output is sorted descending by `avg_likes`.

---

### Thought Process:
1. Use a **CASE** expression in the `SELECT` clause to classify each row into **Super Likes**, **Good Likes**, or **Low Likes**.  
2. Simply select the required columns: `actor`, `character`, `platform`, `avg_likes`, and the CASE outcome as `likes_category`.  
3. Sort the result by `avg_likes` in descending order to put the highest averages first.

---

### SQL Query:
```sql
SELECT
    actor,
    character,
    platform,
    avg_likes,
    CASE
        WHEN avg_likes >= 15000 THEN 'Super Likes'
        WHEN avg_likes BETWEEN 5000 AND 14999 THEN 'Good Likes'
        WHEN avg_likes < 5000 THEN 'Low Likes'
    END AS likes_category
FROM marvel_avengers
ORDER BY avg_likes DESC;
````

---

### Output:

This returns a list of actors and their characters, along with the social media platform, average likes, and their category, ordered from highest to lowest average likes.

```

---

If you like, I can also generate a **README-style index file** linking to this and other problems, or create a **template file** you can reuse for all. Do you want me to do that?
::contentReference[oaicite:0]{index=0}
```
