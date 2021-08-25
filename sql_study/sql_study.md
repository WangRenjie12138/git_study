#### 简单的基础查询

world表格

| name | continent | area | population | gdp  |
| :--: | :-------: | :--: | :--------: | :--: |
|      |           |      |            |      |
|      |           |      |            |      |
|      |           |      |            |      |
|      |           |      |            |      |
|      |           |      |            |      |
|      |           |      |            |      |

1. 查询德国的人口

   ```sql
   SELECT population FROM world WHERE name = 'Germany';
   ```

2. 查询面积为 5 000 000 以上平方公里的国家，展示每个国家的名字和人均国民生产总值

   ```sql
   SELECT name, gdp/population FROM world WHERE area > 5000000;
   ```

3. 展示爱尔兰、冰岛、丹麦的国家名称和人口

   ```sql
   select name, population from world where name in ('Ireland','iceland','denmark');
   ```

4. 展示面积在 200000 和 250000 之间的国家名称和土地面积

   ```sql
   select name, area from world where area > 200000 and area < 2500000;
   select name, area from world where area between 200000 and 2500000;
   ```



#### 文字样式匹配查询

| name | continent |
| :--: | :-------: |
|      |           |



1. 查询以 Y 字母开头的国家

   ```sql
   select name from world where name like 'y%';
   ```

2. 查询以 Y 字母结尾的国家

   ```sql
   select name from world where name like '%y';
   ```

3. 查询包含字母 x 的国家

   ```sql
   select name from world where name like '%x%';
   ```

4. 查询以 land 结尾的国家

   ```sql
   select name from world where name like '%land';
   ```

5. 找出以 C 开头，以 ia 结尾的国家

   ```sql
   select name from world where name like 'C%ia';
   ```

6. 找出包括 oo 的国家

   ```sql
   select name from world where name like '%oo%';
   ```

7. 找出包含三个及以上 a 的国家

   ```sql
   select name from world where name like '%a%a%a%';
   ```

8. 找出以 t 作为第二个字母的国家

   ```sql
   select name from world where name like '_t%';
   ```

9. 找出包含两个 o，而且被另外两个字母隔着的国家

   ```sql
   select name from world where name like '%o__o%';
   ```

10. 找出四个字母名字的国家

    ```sql
    select name from world where name like '____' order by name;
    ```

11. 找出首都和国家名字相同的国家

    ```sql
    select name from world where name = capital;
    ```

12. 找出首都是国家名字+city的国家

    ```sql
    select name from world where capital = concat(name,'City');
    ```

13. 查询首都名称有国家名称出现的国家的首都名和国名

    ```sql
    select capital, name from world where capital like concat('%',concat(name,'%'));
    ```

14. 找出所有首都和其国家名字，而首都是国家名字的延伸

    ```sql
    select capital, name from world where capital like concat(name,'_%');
    ```

15. 显示国家名字和延伸词，如首都是国家名字的延伸

    ```sql
    select name, replace(capital,name,'') from world where capital like concat(name,'_%');
    ```

    

`concat(a,b)`,`raplace(A,B,C)` `_`  `%`

#### 查询练习

`nobel`

|  yr  | subject | winner |
| :--: | :-----: | :----: |
|      |         |        |

1. 查询 1950 年的诺贝尔奖项资料

   ```sql
   select yr, subject, winner from nobel where yr = 1950;
   ```

   

2. 查询谁赢得了 1962 年文学奖（Literature）

   ```sql
   select winner from nobel where yr = 1962 and subject = 'Literature';
   ```

   

3. 查询爱因斯坦（'Albert Einstein'）的获奖年份和奖项

   ```sql
   select yr, subject from nobel where winner = 'Albert Einstein';
   ```

   

4. 查询 2000 年及以后的和平奖（Peace）得奖者

   ```sql
   select winner from nobel where yr >= 2000 and subject = 'Peace';
   ```

   

5. 查询 1980 年至 1989 年（包含首尾）的文学奖（Literature）获奖者的细节

   ```sql
   select yr, subject, winner from nobel where subject = 'Literature' and yr between 1980 and 1989; 
   ```

   

6. 查询总统获奖者的所有细节

   - 西奧多・羅斯福 Theodore Roosevelt
   - 伍德羅・威爾遜 Woodrow Wilson
   - 吉米・卡特 Jimmy Carter

   ```sql
   select yr, subject, winner from nobel where winner in ('Theodore Roosevelt', 'Woodrow Wilson', 'Jimmy Carter');
   ```

   

7. 查询名字为 john 的获奖者（ps，外国人名前姓后）

   ```sql
   select winner from nobel where name like 'john%';
   ```

   

8. 查询 1980 年物理学获奖者和 1984 年化学奖获奖者

   ```sql
   select yr, subject, winner from nobel where (yr = 1980 and subject = 'physics') or (yr = 1984 and subject = 'chemistry');
   ```

   

9. 查询 1980 年除了化学家（chemistry）和医学奖（medicine）的获奖者

   ```sql
   select yr, subject, winner from nobel where subject not in ('chemistry', 'medicine') and yr = 1980;
   ```

   

10. 查询早期医学奖（medicine）得奖者（1910 之前，不包括 1910），以及近年文学奖（literature）得奖者（2004年以后，包括2004）

    ```sql
    select yr, subject, winner from nobel where (subject = 'medicine' and yr < 1910) or (subject = 'literature' and yr >= 2004);
    ```

    

11. Find all details of the prize won by PETER GRÜNBERG

    ```sql
    关于 non-ASCII 字符的查询
    ```

    

12. Find all details of the prize won by EUGENE O'NEILL

    ```sql
    select yr, subject, winner from nobel where winner = 'EUGENE O''NEILL';    使用''代替查询中遇到的'
    ```

    

13. Knights in order 

    List the winners, year and subject where the winner starts with **Sir**. Show the the most recent first, then by name order

    ```sql
    select winner, yr, subject from nobel where winner like 'Sir%' order by yr DESC, winner ASC;
    ```

14. The expression **subject IN ('Chemistry','Physics')** can be used as a value - it will be **0** or **1**.

    Show the 1984 winners and subject ordered by subject and winner name; but list Chemistry and Physics last.

    ```sql
    select winner, subject from nobel where yr = 1984 order by subject in ('Chemistry','Physics'), subject, winner;
    ```

**总结**：

+ order by 默认按字母顺序，数字升序来排列，可选择多个列，按照前后顺序的优先级来排列。
+ in 表达式可以用作参数，如果在其中则为 1，不在的话为 1
+ 查询的参数中有 ' 的话，使用 '' 表示



#### 嵌套查询

**总结**

+ select 查询的结果可以当作一个值或者一组值，用在另一个查询中
+ 某些 SQL 系统中需要别名，用`AS 别名`在嵌套查询的括号之后
+ 有时候会多于一个结果，用 in 比 = 安全
+ 如果子查询只有一个结果，则可以在 SELECT 语句中使用子查询
+ 如果查询的结果是集合，而且还想用 = > < 等运算符，则使用 ALL 或者 ANY 关键字
  + all表示每一个
  + any表示存在任意一个即可
+ 可以在`from 表名`的后面加上 x 或 y，这样可以用于区分嵌套内和嵌套外的两个表格

world表

| name | continent | area | population | gdp  |
| ---- | --------- | ---- | ---------- | ---- |
|      |           |      |            |      |

1. 查询人口比俄罗斯多的国家

   ```sql
   select name from world where population > (select population from world where name = 'russia');
   ```

   

2. 查询欧洲人均 GDP 比英国高的国家的人均 gdp

   ```sql
   select name from world where gdp/population > (select gdp/population from world where name = 'United Kingdom') and continent = 'Europe';
   ```

   

3. 查询和阿根廷 Argentina 及澳大利亚 Australia 同一洲的国家 name 和 continent， 并按照国家名字顺序排列

   ```sql
   select name, continent from world where continent in (select continent from world where name in ('Argentina', 'Australia')) order by name;
   ```

   

4. 查询人口比加拿大 Canada 多但是比波兰 Poland少的国家的 name 和 population

   ```sql
   select name, population from world where population > (select population from world where name = 'Canada') and  population < (select population from world where name = 'Poland');
   ```

   

5. 显示欧洲国家名称 name 和每个国家的人口 population，以德国的人口的百分比作为人口展示

   ```sql
   select name, concat(ROUND(population * 100 / (select population from world where name = 'Germany'),0),'%') from world where continent = 'Europe';
   ```

   

6. 查询比欧洲所有国家 gdp 都高的国家

   ```sql
   select name from world where gdp > all(select gdp from world where continent = 'Europe' and gdp > 0);
   ```

   

7. 查询每个洲面积最大的国家，列出 continent name 和 area

   ```sql
   select continent, name, area from world x where area >= all(select area from world y where y.continent = x.continent and area >0);
   ```

   

8. 列出洲名，和每洲中国家按字母序排首位的国家名

   ```sql
   select continent, name from world x where name <= all(select name from world y where x.continent = y.continent);
   ```

   

9. 找出洲份，其中所有国家都有少于等于 25000000 人口。在这些洲份中，列出国家名字 name，continent 和 population。

   ```sql
   select name, continent, population from world where continent in (select continent from world x where population >= all(select population from world y where x.continent = y.continent) and population <= 25000000 );
   ```

   

10. 有些国家的人口是同洲其他国家的 3 倍及以上，列出 name 和 continent

    ```sql
    select name, continent from world x where population > any(select 3*population from world y where x.continent = y.continent and population > 0);
    ```

    

#### 合计函数

**表同上**

**总结**

+ SUM() 求和
+ DISTINCT  去重
+ COUNT()  计数
+ AVG()  平均数
+ GROUP BY 相同的项归为一行，常与SUM，AVG等一起使用
+ HAVING 使用它只是因为where无法和合计函数一起使用    `HAVING SUM(column) < 200`



1. 查询世界总人口

   ```sql
   select SUM(population) from world where population > 0;
   ```

   

2. 列举所有的洲

   ```sql
   select DISTINCT continent from world;
   ```

   

3. 查询非洲( Africa )的GDP总和

   ```sql
   select SUM(gdp) from world where continent = 'Africa';
   ```

   

4. 查询百万平方公里面积以上的国家

   ```sql
   select COUNT(*) from world where area > 1000000;
   ```

   

5. 查法德西三国总人口

   ```sql
   select SUM(population) from world where name in ('France', 'Germany', 'Spain');
   ```

   

6. 查询每个洲的国家数量

   ```sql
   select continent, count(name) from world group by continent;
   ```

   

7. 查询每个洲至少有一千万人国家的数目

   ```sql
   select continent, count(name) from world where population >= 10000000 group by continent;
   ```

   

8. 查询至少有一亿人口的洲

   ```sql
   select continent from world group by continent having SUM(population) > 100000000;
   ```



#### JOIN 操作

