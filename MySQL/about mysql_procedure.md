***
<br>

# 1. 테이블 데이터를 가져와 처리하는 루프

> notebooks_spec 테이블에서 제조사에 "LG"가 포함된 레코드의 개수를 구하는 프로시저

```SQL
CREATE DEFINER=`division`@`%` PROCEDURE `test_proc`()
BEGIN
	DECLARE result_count INT;
	DECLARE manu_data VARCHAR(1024);
	DECLARE name_data VARCHAR(1024);

	DECLARE done INT DEFAULT FALSE;
	
	DECLARE cur CURSOR FOR SELECT `제조사`, `이름` FROM notebooks_spec;
	DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = TRUE;
	
	OPEN cur;
	
	SET result_count = 0;
	read_loop: LOOP
			FETCH cur INTO manu_data, name_data;

			IF done THEN
					LEAVE read_loop;
			END IF;
			
			IF (manu_data LIKE "%LG%") THEN
				SET result_count = result_count + 1;
			END IF;
	END LOOP;
	
	SELECT result_count;
END
```

![사진](https://media.discordapp.net/attachments/1196215613144703076/1199965273063694388/image.png?ex=65c475bf&is=65b200bf&hm=7613806c960ced9b8efc41bbeae59f84a7847598193fee9f211e2375631d2d51&=&format=webp&quality=lossless&width=393&height=180)

<br>

> 같은 기능을 수행하는 SQL문의 결과
```SQL
SELECT count(*) FROM notebooks_spec WHERE `제조사` LIKE "%LG%";
```

![사진](https://media.discordapp.net/attachments/1196215613144703076/1199965538764476467/image.png?ex=65c475fe&is=65b200fe&hm=18fe918c57cc26e89321fb26a24046ca0404e812bec1d02507405d584dc0a4c5&=&format=webp&quality=lossless&width=874&height=404)

<br><br>
***