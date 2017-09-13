# Stored Procedures com MySQL

```sql
CREATE PROCEDURE GetAllEstados()
begin
	declare num_estados int default 0;
	select count(*) into num_estados from tabela_estados;
	select * from tabela_estados where reg_uf < num_estados;
end;

call GetAllEstados;

--

CREATE PROCEDURE GetEstado(in estado char(2))
begin
	select * from tabela_estados where codi_uf = estado;
end;

call GetEstado('RJ');

--

CREATE PROCEDURE GetNumEstadosRegiao(in regiao varchar(12), out num_estados int)
begin
	select count(*) into num_estados from tabela_estados where regi_uf = regiao;
end;

call GetNumEstadosRegiao('Sudeste', @num_estados);
select @num_estados;

--

create procedure PegaEstados(inout estados_list varchar(4000))
BEGIN
	declare finished int default 0;
	declare estado varchar(2) default "";
	declare regiao varchar(12) default "";
	declare cur cursor for 
		select codi_uf, regi_uf from tabela_estados;
	declare continue handler for not found set finished = 1;
	open cur;
	drop temporary table if exists resumo_estados; 
	create temporary table resumo_estados (estado char(2), regiao varchar(12)); 
	get_estados: LOOP
		fetch cur into estado, regiao;
		if finished = 1 then
			leave get_estados;
		end if;
		set estados_list = concat(estado, " - ", regiao, ";",estados_list);
		insert into resumo_estados values (estado, regiao);
	END LOOP get_estados;
	close cur;
	select * from resumo_estados;
END;

set @estados_list = "";
call PegaEstados(@estados_list);
select @estados_list;
select * from resumo_estados; // a tabela temporária existe até a conexão terminar
```

---

*keywords: mysql, stored procedures, database, banco de dados*
