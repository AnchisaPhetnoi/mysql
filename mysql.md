create database lab;
create database if not exists lab;
create database if not exists lab character set utf8 collate utf8_unicode_ci


use lab;
drop database lab;
create table vendor(v_code int not null,v_company char(25) not null,
c_iname char(12) unique, v_address varchar(150), primary key(v_code)
);

create table vendor(v_code int not null,v_company char(25) not null,
c_iname char(12) unique, v_address varchar(150));


create table emp (eid int primary key, ename varchar(50) not null,salary bigint,
CONSTRAINT ct_salary check(salary >=10000 and salary<=1000000) ); 

insert into emp(eid,ename,salary) values(1,'A',12000);
alter table emp drop constraint ct_salary;
insert into emp(eid,ename,salary) values(2,'B',9000);
alter table emp drop constraint ct_salary;


drop table vendor;
alter table emp drop salary;
alter table emp add salary int,add email varchar(20),add tel varchar (20);
alter table emp change tel telephone varchar(10),drop email,add lineid varchar(20);

rename table emp to employee;
create table invoice(inv_id int primary key auto_increment,inv_date datetime);
insert into invoice(inv_date) valuse(now());
select * from invoice;
set sql_safe_updates=false;
delete from invoice;
