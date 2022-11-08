# Change citycode

| |	原本 | 新 |
| :---: |	:---: | :---: |
| 臺北市 |	1 |	2 |
| 基隆市 |	2 |	1 |
| 新北市 |	3 |	3 |
| 宜蘭縣 |	4 |	19 |
| 新竹市 |	5 |	5 |
| 新竹縣 |	6 |	6 |
| 桃園市 |	7 |	4 |
| 苗栗縣 |	8 |	7 |
| 臺中市 |	9 |	8 |
| 彰化縣 |	10 |	9 |
| 南投縣 |	11 |	10 |
| 嘉義市 |	12 |	12 |
| 嘉義縣 |	13 |	13 |
| 雲林縣 |	14 |	11 |
| 臺南市 |	15 |	14 |
| 高雄市 |	16 |	15 |
| 屏東縣 |	17 |	16 |
| 臺東縣 |	18 |	17 |
| 花蓮縣 |	19 |	18 |
| 澎湖縣 |	20 |	20 |
| 金門縣 |	21 |	21 |
| 連江縣 |	22 |	22 |
| 釣魚臺 |	23 |	23 |
| 南海島 |	24 |	24 |


```sql
DECLARE
  new_citycode NUMBER;

BEGIN
  FOR row_data IN (SELECT * FROM profile)
  LOOP
    CASE row_data.citycode
      WHEN 1 THEN
        new_citycode := 2;
      WHEN 2 THEN
        new_citycode := 1;
      WHEN 4 THEN
        new_citycode := 19;
      WHEN 7 THEN
        new_citycode := 4;
      WHEN 8 THEN
        new_citycode := 7;
      WHEN 9 THEN
        new_citycode := 8;
      WHEN 10 THEN
        new_citycode := 9;
      WHEN 11 THEN
        new_citycode := 10;
      WHEN 14 THEN
        new_citycode := 11;
      WHEN 15 THEN
        new_citycode := 14;
      WHEN 16 THEN
        new_citycode := 15;
      WHEN 17 THEN
        new_citycode := 16;
      WHEN 18 THEN
        new_citycode := 17;
      WHEN 19 THEN
        new_citycode := 18;
      ELSE
        CONTINUE;
    END CASE;
    UPDATE profile
    SET citycode = new_citycode
    WHERE id = row_data.id;
  END LOOP;
END;
```
