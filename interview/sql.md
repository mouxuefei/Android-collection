 1. create table t_user(_id integer primary key autoincrement,c_name varchar(20),c_age integer,c_phone varchar(20) );
4. 插入数据(记录)
 1.insert into t_user(name, age,phone) values('张三',23,'13111111111');
5. 删除表全部数据
 1. delete from t_user;
6. 带条件的删除
 1. delete from t_user where c_age>28 and c_age<31;
7. 修改数据
 1. update t_user set c_name='磁性' where _id=16;
8. 查询数据
 1. select c_name,c_age,c_phone,_id from t_user;
 2. select c_name,c_age,c_phone,_id from t_user where c_age<30;
 3. select c_name,c_age,c_phone,_id from t_user where c_age<30; 限制最大400条
 4. select c_name,c_age,c_phone,_id from t_user order by c_age desc; 按照c_age的倒序排序
9. 修改表结构(一般是数据库更新的时候)
 1. alter table t_user add c_money float;
9. CRUD:C(Create)R(Retrieve)U(update)D(delete)