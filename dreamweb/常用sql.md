修改字段

```mysql
	alter  table fw modify  column column1  decimal(10,1) DEFAULT NULL COMMENT '注释';
```



端口被占用

### step1：通过端口找到PID

打开dos命令行，输入**netstat -ano | find "1099"**，得到下列内容，看到最后一列是9280，就是PID：

### step2：通过PID找到进程

输入：**tasklist | find "9280"**（双引号里面的是PID）

### step3：关闭进程

输入命令关闭进程：taskkill /f /t /im java.exe





查询用户的一级部门和二级部门

```sql
SELECT   guser.*,g1.ID ORG_ID,g1.ORG_NAME_LV1_TEXT,g1.ORG_NAME_LV2_TEXT,gu.IS_MAIN FROM G_ORGANIZE G INNER JOIN G_ORGANIZE G1 ON  G1.STEP LIKE CONCAT(G.STEP,'%')
INNER JOIN g_orguser gu ON gu.org_id=g1.ID INNER JOIN g_userinfo guser ON guser.ID=gu.USER_ID AND guser.user_name LIKE '%戎志平%'
and guser.ROWSTATE<>-1 WHERE ((G.FID='180505162656YILYYOzw1FnE5OzzNxm' AND G1.IS_UNIT=-1 AND G.IS_UNIT=-1) OR (gu.ORG_ID='180505162656YILYYOzw1FnE5OzzNxm'
and G.id= '180505162656YILYYOzw1FnE5OzzNxm') )  AND G1.ROWSTATE<>-1
 AND GUSER.USER_TYPE=0  AND G.ROWSTATE<>-1 ORDER BY gu.SHOWORDER
```

