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
   select winner from nobel where yr = 1950 and subject = 'Literature';
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
   select 
   ```

   

6. 查询总统获奖者的所有细节

   - 西奧多・羅斯福 Theodore Roosevelt
   - 伍德羅・威爾遜 Woodrow Wilson
   - 吉米・卡特 Jimmy Carter

7. 查询名字为 john 的获奖者（ps，外国人名前姓后）

8. 查询 1980 年物理学获奖者和 1984 年化学奖获奖者

9. 查询 1980 年除了化学家（chemistry）和医学奖（medicine）的获奖者

10. 查询早期医学奖（medicine）得奖者（1910 之前，不包括 1910），以及近年文学奖（literature）得奖者（2004年以后，包括2004）

11. Find all details of the prize won by PETER GRÜNBERG

12. Find all details of the prize won by EUGENE O'NEILL

13. Knights in order

    List the winners, year and subject where the winner starts with **Sir**. Show the the most recent first, then by name order.

    







