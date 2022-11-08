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
