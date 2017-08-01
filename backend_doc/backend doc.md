# questionnaire backend document

* ## Database  Definition  

#### 1. 用户表(tbl_user)

|   字段名    |   字段类型   |   可空   |      描述     |
| :---------  | :----------- | :--- ----| :------------ |
|   userId    |      int     |     N    |    用户唯一标识，主键自增   |
|   name      |  varchar(32) |     Y    |    用户名     |
|   layer     |  char(1)     |     N    |    用户级别<br/>1：发起表单用户<br/> 2：填写表单用户|
|   mobile    |  char(11)    |     Y    |    手机号     |
|   email     | varchar(32)  |     Y    |    邮箱       |
|   ext       |  varchar(8)  |     Y    |    保留字段   |

#### 2. 问卷表(tbl_question)

|   字段名   |   字段类型   |   可空   |      描述     |
| :--------- | :----------- | :--- ----| :------------ |
| questionId |      int     |     N    |    问题唯一标识，主键自增   |
|   desc     | varchar(128) |     N    |    问题描述   |
|   type     |  char(1)     |     N    |    问题类型<br/>1：单选<br/> 2：多选<br/>3：填空<br/>4：判断|
|   ext      |  varchar(8)  |     Y    |    保留字段   |


#### 3. 选项表(tbl_option)

|   字段名   |   字段类型   |   可空   |      描述     |
| :--------- | :----------- | :--- ----| :------------ |
| questionId |      int     |     N    |    问题唯一标识   |
|   optIndex |   char(1)    |     N    |    选项索引<br/>选择题：A/B/C/D/E... <br/>填空题：空 <br/>判断题：1/2/3...   |
|   optDesc  |   char(1)    |     N    |    答案描述 <br/>填空题：空|
|   optValue |   char(1)    |     Y    |    是否正确答案 <br/>0：否  <br/>1：是 <br/>不关注是否正确时为空  <br/>非零：代表分值|
|   ext      |  varchar(8)  |     Y    |    保留字段   |

*`optValue`字段除记录答案正确与否外，为兼容类似性格测试的题目，设置了分值*

#### 4. 答案表(tbl_answer)

|   字段名   |   字段类型   |   可空   |      描述     |
| :--------- | :----------- | :--- ----| :------------ |
| userId     |      int     |     N    |    用户标识   |
| questionId |      int     |     N    |    问题表示   |
| selectIndex|   char(1)    |     Y    |    所选答案，对应tbl_option中optIndex|
|   ext      |  varchar(8)  |     Y    |    保留字段   |