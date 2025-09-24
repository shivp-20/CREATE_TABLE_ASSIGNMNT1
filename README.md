# CREATE_TABLE_ASSIGNMNT1
create table countries(
country_id int ,
country_name varchar(50),
region_id int);

create table dup_countries like countries;

create table dup_countries as select * from countries;

desc dup_countries;

create table jobs(
job_id varchar(50) primary key,
job_title varchar(50),
min_salary decimal(6,2),
max_salary decimal(6,2)
 check(max <= 25000)
);

create table countries(
country_id varchar(50) primary key,
country_name varchar (50) not null 
check(country_name in ('italy','india','china')),
region_id int(10)
);

create table job_history (
employee_id int primary key,
start_date date,
end_date date,
job_id int ,
department_id int 
);
insert into job_history values(101,'2024-05-25',str_to_date('25/09/2025', '%d%m%y'), 20, 1);
select * from job_history;


create table countries(
country_id int(10),
country_name varchar(50),
region_id int,
unique(country_id,region_id)
);

create table jobs(
job_id varchar(10) primary key unique not null,
job_title varchar(35) default null  ,
MIN_SALARY decimal(6,0) default null,
MAX_SALARY decimal(6,0) default null
);
desc jobs;
create table job_history(
employee_id int unique,
start_date date ,
end_date date ,
job_id varchar(10) ,
department_id int,
foreign key(job_id) references jobs(job_id)
);

create table employees(
employee_id int unique,
first_name varchar(50) not null ,
last_name varchar(50) not null ,
email varchar(50),
phone_number int(10) ,
hire_date date,
job_id int unique,
salary int ,
commission decimal(4,2),
manager_id decimal(6,0) ,
department_id decimal(4,0) unique,
foreign key(department_id,manager_id) references departments(department_id,manager_id)
);


CREATE TABLE employees (
    employee_id   DECIMAL(6,0) NOT NULL,
    first_name    VARCHAR(20),
    last_name     VARCHAR(25) NOT NULL,
    email         VARCHAR(50) NOT NULL,
    phone_number  VARCHAR(20),
    hire_date     DATE NOT NULL,
    job_id        VARCHAR(10) NOT NULL,
    salary        DECIMAL(8,2),
    commission    DECIMAL(2,2),
    manager_id    DECIMAL(6,0),
    department_id DECIMAL(4,0),
    PRIMARY KEY (employee_id),
    FOREIGN KEY (department_id) REFERENCES departments(DEPARTMENT_ID),
    FOREIGN KEY (job_id) REFERENCES jobs(JOB_ID)
) ENGINE=InnoDB;


CREATE TABLE employees (
    employee_id INT NOT NULL PRIMARY KEY,
    first_name  VARCHAR(30),
    last_name   VARCHAR(30),
    job_id      INT NOT NULL,
    salary      DECIMAL(8,2),
    FOREIGN KEY (job_id)
        REFERENCES jobs(JOB_ID)
        ON UPDATE CASCADE
        ON DELETE RESTRICT
) ENGINE=InnoDB;


CREATE TABLE employees (
    employee_id INT NOT NULL PRIMARY KEY,
    first_name  VARCHAR(30),
    last_name   VARCHAR(30),
    job_id      INT NOT NULL,
    salary      DECIMAL(8,2),
    FOREIGN KEY (job_id)
        REFERENCES jobs(JOB_ID)
        ON DELETE CASCADE
        ON UPDATE RESTRICT
) ENGINE=InnoDB;

CREATE TABLE employees (
    employee_id INT NOT NULL PRIMARY KEY,
    first_name  VARCHAR(30),
    last_name   VARCHAR(30),
    job_id      INT NULL,
    salary      DECIMAL(8,2),
    FOREIGN KEY (job_id)
        REFERENCES jobs(JOB_ID)
        ON DELETE SET NULL
        ON UPDATE SET NULL
) ENGINE=InnoDB;



CREATE TABLE employees (
    employee_id INT NOT NULL PRIMARY KEY,
    first_name  VARCHAR(30),
    last_name   VARCHAR(30),
    job_id      INT NOT NULL,
    salary      DECIMAL(8,2),
    FOREIGN KEY (job_id)
        REFERENCES jobs(JOB_ID)
        ON DELETE NO ACTION
        ON UPDATE NO ACTION
) ENGINE=InnoDB;
