### Se requiere crear una consulta para:

- Obtener de manera ordenada la lista de vistas y modulos a los que tiene acceso un rol en estado activo. 

## Forma esperada: 

- role[name=> rol, route => ruta]
- module[name=> modulo, route => paquete]

## Forma SQL: 

```sql
use db_security;

SELECT 
	p.first_name,
    r.name,
    m.name AS modulo,
    v.name AS vista,

FROM person p
INNER JOIN user u ON p.id = u.person_id
INNER JOIN user_role ur ON u.id = ur.user_id
INNER JOIN role r ON ur.role_id = r.id
INNER JOIN role_module rm ON r.id = rm.role_id
INNER JOIN module m ON rm.module_id = m.id
WHERE u.state = true;
```

# RESULTADO
![Consulta completa](IMG/Sinfiltro.png)
![Consulta con filtro](IMG/Confiltro.png)
