link de la imagen:docker pull javp013/lab_neo4j:latest
para levantar en contenedor : docker run -d --name rutas-api -p 3000:3000 node-rutas   


```SQL
//Sucursales:
CREATE (s1:Sucursal {clave: "s1112", nombre: "Sucursal Centro", direccion: "Av. Principal 123", ciudad: "Tepic", capacidad: "15"}),
       (s2:Sucursal {clave: "s1113", nombre: "Sucursal Norte", direccion: "Calle Norte 45", ciudad: "Tepic", capacidad: "20"}),
       (s3:Sucursal {clave: "s1114", nombre: "Sucursal Sur", direccion: "Boulevard Sur 89", ciudad: "Tepic", capacidad: "18"}),
       (s4:Sucursal {clave: "s1115", nombre: "Sucursal Este", direccion: "Calle Oriente 33", ciudad: "Tepic", capacidad: "12"}),
       (s5:Sucursal {clave: "s1116", nombre: "Sucursal Oeste", direccion: "Calle Poniente 56", ciudad: "Tepic", capacidad: "22"})
RETURN s1, s2, s3, s4, s5;



//-----------------------------------------------------------------------




//Empleados , sucursale 

// Crear empleados y relaciones con sucursales
MATCH (s1:Sucursal {clave: "s1112"}), (s2:Sucursal {clave: "s1113"}), (s3:Sucursal {clave: "s1114"}),
      (s4:Sucursal {clave: "s1115"}), (s5:Sucursal {clave: "s1116"})

// Crear los empleados y sus relaciones
CREATE (e1:Empleado {id:"j12345", nombre:"Jose Alberto", curp:"abc123", telefono:"1234567", num_cuent_ban:"1234567890", fech_contra:"20-10-2020", puesto:"gerente", area_gest:"Recursos Humanos"}),
       (e1)-[:Trabaja_en]->(s1),
       (e2:Empleado {id:"j12346", nombre:"Maria Gomez", curp:"def456", telefono:"7654321", num_cuent_ban:"0987654321", fech_contra:"15-08-2021", puesto:"gerente", area_gest:"Ventas"}),
       (e2)-[:Trabaja_en]->(s2),
       (e3:Empleado {id:"j12347", nombre:"Carlos Ruiz", curp:"ghi789", telefono:"5555555", num_cuent_ban:"1234567890", feBrinda_soporte_ench_contra:"01-12-2022", puesto:"gerente", area_gest:"Operaciones"}),
       (e3)-[:Trabaja_en]->(s3),
       (e4:Empleado {id:"j12348", nombre:"Ana Martinez", curp:"jkl012", telefono:"4444444", num_cuent_ban:"2345678901", fech_contra:"10-03-2019", puesto:"gerente", area_gest:"Finanzas"}),
       (e4)-[:Trabaja_en]->(s4),
       (e5:Empleado {id:"j12349", nombre:"Luis Perez", curp:"mno345", telefono:"3333333", num_cuent_ban:"3456789012", fech_contra:"22-06-2020", puesto:"gerente", area_gest:"Marketing"}),
       (e5)-[:Trabaja_en]->(s5)

// Devolver todos los empleados
RETURN e1, e2, e3, e4, e5;



//----------------------------------------------------------------


// Crear desarrolladores y relaciones con sucursales
MATCH (s1:Sucursal {clave: "s1112"}), (s2:Sucursal {clave: "s1113"}), (s3:Sucursal {clave: "s1114"}),(s4:Sucursal {clave: "s1115"}), (s5:Sucursal {clave: "s1116"})

// Crear los desarrolladores y sus relaciones
CREATE (dev1:Empleado {id:"d12345", nombre:"Juan Perez", curp:"ABC123456HDFRJN00", telefono:"1234567890", num_cuent_ban:"1234567890", fech_contra:"2020-10-20", especializacion:"Back-end", lenguaje_principal:"Java",
puesto:"desarrollador",proyectos_activos:5}),
       (dev1)-[:Trabaja_en]->(s1),
       (dev2:Empleado {id:"d12346", nombre:"Laura Sanchez", curp:"DEF123456HDFRJN01", telefono:"0987654321", num_cuent_ban:"0987654321", fech_contra:"2021-08-15", especializacion:"Front-end", lenguaje_principal:"JavaScript",puesto:"desarrollador", proyectos_activos:3}),
       (dev2)-[:Trabaja_en]->(s1),
       (dev3:Empleado  {id:"d12347", nombre:"Carlos Torres", curp:"GHI123456HDFRJN02", telefono:"5555555555", num_cuent_ban:"1234567891", fech_contra:"2022-12-01", especializacion:"Full-stack", lenguaje_principal:"Python",puesto:"desarrollador", proyectos_activos:4}),
       (dev3)-[:Trabaja_en]->(s1),

       (dev4:Empleado  {id:"d12348", nombre:"Maria Gomez", curp:"JKL123456HDFRJN03", telefono:"4444444444", num_cuent_ban:"2345678901", fech_contra:"2019-03-10", especializacion:"Back-end", lenguaje_principal:"Node.js",puesto:"desarrollador", proyectos_activos:2}),
       (dev4)-[:Trabaja_en]->(s2),
       (dev5:Empleado  {id:"d12349", nombre:"Miguel Ramirez", curp:"MNO123456HDFRJN04", telefono:"3333333333", num_cuent_ban:"3456789012", fech_contra:"2020-06-22", especializacion:"Front-end", lenguaje_principal:"React",puesto:"desarrollador", proyectos_activos:6}),
       (dev5)-[:Trabaja_en]->(s2),
       (dev6:Empleado  {id:"d12350", nombre:"Sofia Lopez", curp:"PQR123456HDFRJN05", telefono:"2222222222", num_cuent_ban:"4567890123", fech_contra:"2021-07-15", especializacion:"Full-stack", lenguaje_principal:"Ruby", puesto:"desarrollador",proyectos_activos:1}),
       (dev6)-[:Trabaja_en]->(s2),

       (dev7:Empleado  {id:"d12351", nombre:"Luis Martin", curp:"STU123456HDFRJN06", telefono:"1111111111", num_cuent_ban:"5678901234", fech_contra:"2022-09-30", especializacion:"Back-end", lenguaje_principal:"C#", puesto:"desarrollador",proyectos_activos:8}),
       (dev7)-[:Trabaja_en]->(s3),
       (dev8:Empleado  {id:"d12352", nombre:"Ana Torres", curp:"VWX123456HDFRJN07", telefono:"8888888888", num_cuent_ban:"6789012345", fech_contra:"2022-11-01", especializacion:"Front-end", lenguaje_principal:"Vue.js", puesto:"desarrollador",proyectos_activos:4}),
       (dev8)-[:Trabaja_en]->(s3),
       (dev9:Empleado  {id:"d12353", nombre:"Javier Ortega", curp:"YZA123456HDFRJN08", telefono:"7777777777", num_cuent_ban:"7890123456", fech_contra:"2022-10-15", especializacion:"Full-stack", lenguaje_principal:"PHP", puesto:"desarrollador",proyectos_activos:5}),
       (dev9)-[:Trabaja_en]->(s3),

       (dev10:Empleado  {id:"d12354", nombre:"Estela Ruiz", curp:"BCD123456HDFRJN09", telefono:"6666666666", num_cuent_ban:"8901234567", fech_contra:"2020-03-20", especializacion:"Back-end", lenguaje_principal:"Go", puesto:"desarrollador",proyectos_activos:2}),
       (dev10)-[:Trabaja_en]->(s4),
       (dev11:Empleado  {id:"d12355", nombre:"Felipe Cruz", curp:"EFG123456HDFRJN10", telefono:"5555555555", num_cuent_ban:"9012345678", fech_contra:"2021-02-18", especializacion:"Front-end", lenguaje_principal:"Angular",puesto:"desarrollador", proyectos_activos:3}),
       (dev11)-[:Trabaja_en]->(s4),
       (dev12:Empleado  {id:"d12356", nombre:"Veronica Morales", curp:"HIJ123456HDFRJN11", telefono:"4444444444", num_cuent_ban:"0123456789", fech_contra:"2021-12-30", especializacion:"Full-stack", lenguaje_principal:"Swift",puesto:"desarrollador", proyectos_activos:7}),
       (dev12)-[:Trabaja_en]->(s4),

       (dev13:Empleado  {id:"d12357", nombre:"Ricardo Salas", curp:"KLM123456HDFRJN12", telefono:"3333333333", num_cuent_ban:"1234567892", fech_contra:"2021-04-25", especializacion:"Back-end", lenguaje_principal:"Scala",puesto:"desarrollador", proyectos_activos:1}),
       (dev13)-[:Trabaja_en]->(s5),
       (dev14:Empleado  {id:"d12358", nombre:"Claudia Salinas", curp:"NOP123456HDFRJN13", telefono:"2222222222", num_cuent_ban:"2345678902", fech_contra:"2020-06-10", especializacion:"Front-end", lenguaje_principal:"HTML/CSS",puesto:"desarrollador", proyectos_activos:4}),
       (dev14)-[:Trabaja_en]->(s5),
       (dev15:Empleado  {id:"d12359", nombre:"Gonzalo Jimenez", curp:"QRS123456HDFRJN14", telefono:"1111111111", num_cuent_ban:"3456789013", fech_contra:"2021-03-15", especializacion:"Full-stack", lenguaje_principal:"Kotlin", puesto:"desarrollador",proyectos_activos:2}),
       (dev15)-[:Trabaja_en]->(s5)

// Devolver todos los desarrolladores
RETURN dev1, dev2, dev3, dev4, dev5, dev6, dev7, dev8, dev9, dev10, dev11, dev12, dev13, dev14, dev15;


//-----------------------------------------------------------------


// Crear soporte técnico y relaciones con sucursales 
MATCH (s1:Sucursal {clave: "s1112"}), (s2:Sucursal {clave: "s1113"}), (s3:Sucursal {clave: "s1114"}), (s4:Sucursal {clave: "s1115"}), (s5:Sucursal {clave: "s1116"})

// Crear los soportes técnicos y sus relaciones
CREATE (st1:Empleado  {id:"st12345", nombre:"Fernando Lopez", curp:"FL123456789", telefono:"5551234567", num_cuent_ban:"1234567890", fech_contra:"15-01-2020", tipo_soporte:"Infraestructura", puesto:"soporte tecnico",contacto_interno:"101"}),
       (st1)-[:Trabaja_en]->(s1),
       (st2:Empleado  {id:"st12346", nombre:"Camila Martinez", curp:"CM123456789", telefono:"5552345678", num_cuent_ban:"0987654321", fech_contra:"20-02-2021", tipo_soporte:"Software",puesto:"soporte tecnico", contacto_interno:"102"}),
       (st2)-[:Trabaja_en]->(s1),
       (st3:Empleado  {id:"st12347", nombre:"Pedro Gomez", curp:"PG123456789", telefono:"5553456789", num_cuent_ban:"1357924680", fech_contra:"10-03-2021", tipo_soporte:"Hardware",puesto:"soporte tecnico", contacto_interno:"103"}),
       (st3)-[:Trabaja_en]->(s1),

       (st4:Empleado  {id:"st12348", nombre:"Elena Ruiz", curp:"ER123456789", telefono:"5554567890", num_cuent_ban:"2468135790", fech_contra:"25-01-2020", tipo_soporte:"Infraestructura",puesto:"soporte tecnico", contacto_interno:"201"}),
       (st4)-[:Trabaja_en]->(s2),
       (st5:Empleado  {id:"st12349", nombre:"Sofia Ramirez", curp:"SR123456789", telefono:"5555678901", num_cuent_ban:"3579246801", fech_contra:"30-06-2021", tipo_soporte:"Software",puesto:"soporte tecnico", contacto_interno:"202"}),
       (st5)-[:Trabaja_en]->(s2),
       (st6:Empleado  {id:"st12350", nombre:"Luis Torres", curp:"LT123456789", telefono:"5556789012", num_cuent_ban:"4681357902", fech_contra:"05-07-2021", tipo_soporte:"Hardware",puesto:"soporte tecnico", contacto_interno:"203"}),
       (st6)-[:Trabaja_en]->(s2),

       (st7:Empleado  {id:"st12351", nombre:"Javier Salas", curp:"JS123456789", telefono:"5557890123", num_cuent_ban:"5792468013", fech_contra:"11-09-2020", tipo_soporte:"Infraestructura", puesto:"soporte tecnico",contacto_interno:"301"}),
       (st7)-[:Trabaja_en]->(s3),
       (st8:Empleado  {id:"st12352", nombre:"Maria Garcia", curp:"MG123456789", telefono:"5558901234", num_cuent_ban:"6803579124", fech_contra:"15-12-2020", tipo_soporte:"Software",puesto:"soporte tecnico", contacto_interno:"302"}),
       (st8)-[:Trabaja_en]->(s3),
       (st9:Empleado  {id:"st12353", nombre:"Angela Fernandez", curp:"AF123456789", telefono:"5559012345", num_cuent_ban:"7914682035", fech_contra:"25-11-2020", tipo_soporte:"Hardware",puesto:"soporte tecnico", contacto_interno:"303"}),
       (st9)-[:Trabaja_en]->(s3),

       (st10:Empleado  {id:"st12354", nombre:"Raul Mendoza", curp:"RM123456789", telefono:"5550123456", num_cuent_ban:"8025793146", fech_contra:"01-05-2020", tipo_soporte:"Infraestructura",puesto:"soporte tecnico", contacto_interno:"401"}),
       (st10)-[:Trabaja_en]->(s4),
       (st11:Empleado  {id:"st12355", nombre:"Lucia Morales", curp:"LM123456789", telefono:"5551234560", num_cuent_ban:"9136804257", fech_contra:"10-08-2020", tipo_soporte:"Software",puesto:"soporte tecnico", contacto_interno:"402"}),
       (st11)-[:Trabaja_en]->(s4),
       (st12:Empleado  {id:"st12356", nombre:"Carlos Jimenez", curp:"CJ123456789", telefono:"5552345601", num_cuent_ban:"0247916385", fech_contra:"15-04-2020", tipo_soporte:"Hardware", puesto:"soporte tecnico",contacto_interno:"403"}),
       (st12)-[:Trabaja_en]->(s4),

       (st13:Empleado  {id:"st12357", nombre:"Estela Rojas", curp:"ER123456789", telefono:"5553456702", num_cuent_ban:"1358024684", fech_contra:"20-06-2020", tipo_soporte:"Infraestructura",puesto:"soporte tecnico", contacto_interno:"501"}),
       (st13)-[:Trabaja_en]->(s5),
       (st14:Empleado  {id:"st12358", nombre:"Diego Quiroz", curp:"DQ123456789", telefono:"5554567812", num_cuent_ban:"2469135780", fech_contra:"30-10-2020", tipo_soporte:"Software",puesto:"soporte tecnico", contacto_interno:"502"}),
       (st14)-[:Trabaja_en]->(s5),
       (st15:Empleado  {id:"st12359", nombre:"Claudia Salinas", curp:"CS123456789", telefono:"5555678923", num_cuent_ban:"3570246819", fech_contra:"05-11-2020", tipo_soporte:"Hardware",puesto:"soporte tecnico", contacto_interno:"503"}),
       (st15)-[:Trabaja_en]->(s5);



//-------------------------------------------------------------------------------



// Crear proyectos
CREATE (p1:Proyecto {
    codigo: "p1alb",
    nombre: "Sistema de Gestión de Recursos Humanos",
    descripcion: "Proyecto para la gestión eficiente de recursos humanos en la empresa.",
    fenc_in: "2023-11-05",
    fenc_fin: "2024-11-01",
    presu_asig: 2000000
}),
(p2:Proyecto {
    codigo: "p2nord",
    nombre: "Aplicación de Ventas",
    descripcion: "Desarrollo de una aplicación para mejorar las ventas en línea.",
    fenc_in: "2023-12-01",
    fenc_fin: "2024-05-01",
    presu_asig: 1500000
}),
(p3:Proyecto {
    codigo: "p3sur",
    nombre: "Plataforma de Operaciones",
    descripcion: "Creación de una plataforma para optimizar las operaciones de la empresa.",
    fenc_in: "2024-01-10",
    fenc_fin: "2024-07-10",
    presu_asig: 500000
}),
(p4:Proyecto {
    codigo: "p4este",
    nombre: "Sistema Financiero",
    descripcion: "Desarrollo de un sistema financiero integrado.",
    fenc_in: "2024-02-15",
    fenc_fin: "2024-08-15",
    presu_asig: 3000000
}),
(p5:Proyecto {
    codigo: "p5oeste",
    nombre: "Portal de Marketing Digital",
    descripcion: "Desarrollo de un portal para estrategias de marketing digital.",
    fenc_in: "2024-03-01",
    fenc_fin: "2024-09-01",
    presu_asig: 1800000
})


//-----------------------------------------------------------------






//Match de proyectos
// Coincidir con las sucursales, empleados y desarrolladores
MATCH (s1:Sucursal {clave: "s1112"}), 
      (s2:Sucursal {clave: "s1113"}), 
      (s3:Sucursal {clave: "s1114"}), 
      (s4:Sucursal {clave: "s1115"}), 
      (s5:Sucursal {clave: "s1116"}),
      (e1:Empleado {id: "j12345"}), 
      (e2:Empleado {id: "j12346"}), 
      (e3:Empleado {id: "j12347"}), 
      (e4:Empleado {id: "j12348"}), 
      (e5:Empleado {id: "j12349"}), 
      (dev1:Empleado  {id: "d12345"}), 
      (dev2:Empleado  {id: "d12346"}), 
      (dev3:Empleado  {id: "d12347"}), 
      (dev4:Empleado  {id: "d12348"}), 
      (dev5:Empleado  {id: "d12349"}), 
      (dev6:Empleado  {id: "d12350"}), 
      (dev7:Empleado  {id: "d12351"}), 
      (dev8:Empleado  {id: "d12352"}), 
      (dev9:Empleado  {id: "d12353"}), 
      (dev10:Empleado  {id: "d12354"}), 
      (dev11:Empleado  {id: "d12355"}), 
      (dev12:Empleado  {id: "d12356"}), 
      (dev13:Empleado  {id: "d12357"}), 
      (dev14:Empleado  {id: "d12358"}), 
      (dev15:Empleado  {id: "d12359"}),
      (p1:Proyecto {codigo: "p1alb"}),
      (p2:Proyecto {codigo: "p2nord"}),
      (p3:Proyecto {codigo: "p3sur"}),
      (p4:Proyecto {codigo: "p4este"}),
      (p5:Proyecto {codigo: "p5oeste"})
      
      
      
      

// Crear relaciones para el primer proyecto
CREATE (p1)-[:Desarrollado_en]->(s1),
       (p1)-[:Gestionado_por]->(e1),
       (p1)-[:Involucrado_en]->(dev1),
       (p1)-[:Involucrado_en]->(dev3),
       (p1)-[:Involucrado_en]->(dev13),
       (p1)-[:Involucrado_en]->(dev3),
// Crear relaciones para el segundo proyecto
       (p2)-[:Desarrollado_en]->(s2),
       (p2)-[:Gestionado_por]->(e2),
       (p2)-[:Involucrado_en]->(dev4),
       (p2)-[:Involucrado_en]->(dev15),
       (p2)-[:Involucrado_en]->(dev1),
       (p2)-[:Involucrado_en]->(dev6),
// Crear relaciones para el tercer proyecto
	   (p3)-[:Desarrollado_en]->(s3),
       (p3)-[:Gestionado_por]->(e3),
       (p3)-[:Involucrado_en]->(dev4),
       (p3)-[:Involucrado_en]->(dev2),
       (p3)-[:Involucrado_en]->(dev7),
       (p3)-[:Involucrado_en]->(dev9),
// Crear relaciones para el cuarto proyecto
       (p4)-[:Desarrollado_en]->(s4),
       (p4)-[:Gestionado_por]->(e4),
       (p4)-[:Involucrado_en]->(dev10),
       (p4)-[:Involucrado_en]->(dev11),
       (p4)-[:Involucrado_en]->(dev8),
       (p4)-[:Involucrado_en]->(dev3),
       (p4)-[:Involucrado_en]->(dev12),
// Crear relaciones para el quinto proyecto
       (p5)-[:Desarrollado_en]->(s5),
       (p5)-[:Gestionado_por]->(e5),
       (p5)-[:Involucrado_en]->(dev13),
       (p5)-[:Involucrado_en]->(dev14),
       (p4)-[:Involucrado_en]->(dev11),
       (p4)-[:Involucrado_en]->(dev1),
       (p4)-[:Involucrado_en]->(dev5),
       (p4)-[:Involucrado_en]->(dev7),
       (p5)-[:Involucrado_en]->(dev15);




//----------------------------------------------------------------------





MATCH  (p1:Proyecto {codigo: "p1alb"}),
      (p2:Proyecto {codigo: "p2nord"}),
      (p3:Proyecto {codigo: "p3sur"}),
      (p4:Proyecto {codigo: "p4este"}),
      (p5:Proyecto {codigo: "p5oeste"})
      

// Crear 3 clientes
CREATE (c1:Cliente {nombre: "Cliente 1", empresa: "Empresa A", telefono: "1111111", correo: "cliente1@gmail.com"}),
       (c1)-[:Pertenece_a]->(p1),
       (c1)-[:Pertenece_a]->(p2),

       (c2:Cliente {nombre: "Cliente 2", empresa: "Empresa B", telefono: "2222222", correo: "cliente2@gmail.com"}),
       (c2)-[:Pertenece_a]->(p3),
       (c2)-[:Pertenece_a]->(p4),

       (c3:Cliente {nombre: "Cliente 3", empresa: "Empresa C", telefono: "3333333", correo: "cliente3@gmail.com"}),
       (c3)-[:Pertenece_a]->(p5)

RETURN c1, c2, c3;




//------------------------------------------------------------




MATCH (s1:Sucursal {clave: "s1112"}), 
      (s2:Sucursal {clave: "s1113"}), 
      (s3:Sucursal {clave: "s1114"}), 
      (s4:Sucursal {clave: "s1115"}), 
      (s5:Sucursal {clave: "s1116"}),
      (c1:Cliente {nombre: "Cliente 1"}),
      (c2:Cliente {nombre: "Cliente 2"}),
      (c3:Cliente {nombre: "Cliente 3"}),
      (e1:Empleado {id: "j12345"}), 
      (e2:Empleado {id: "j12346"}), 
      (e3:Empleado {id: "j12347"}), 
      (e4:Empleado {id: "j12348"}), 
      (e5:Empleado {id: "j12349"}), 
      (dev1:Empleado  {id: "d12345"}), 
      (dev2:Empleado  {id: "d12346"}), 
      (dev3:Empleado  {id: "d12347"}), 
      (dev4:Empleado  {id: "d12348"}), 
      (dev5:Empleado  {id: "d12349"}), 
      (dev6:Empleado  {id: "d12350"}), 
      (dev7:Empleado  {id: "d12351"}), 
      (dev8:Empleado  {id: "d12352"}), 
      (dev9:Empleado  {id: "d12353"}), 
      (dev10:Empleado  {id: "d12354"}), 
      (dev11:Empleado  {id: "d12355"}), 
      (dev12:Empleado  {id: "d12356"}), 
      (dev13:Empleado  {id: "d12357"}), 
      (dev14:Empleado  {id: "d12358"}), 
      (dev15:Empleado  {id: "d12359"})






// Crear reuniones
CREATE 
     (r1:Reunion {nombre:"Reunion 1", fecha: "2024-10-30", hora_reun: "15:00"}),
      (s1) - [:REALIZA] -> (r1),
      (c1) - [:PARTICIPA_EN] -> (r1),
      (e1) - [:ASISTE_A] -> (r1),
      (dev1) - [:ASISTE_A] -> (r1),

      (r2:Reunion {nombre:"Reunion 2", fecha: "2024-10-31", hora_reun:"10:00"}),
      (s2) - [:REALIZA] -> (r2),
      (c2) - [:PARTICIPA_EN] -> (r2),
      (e2) - [:ASISTE_A] -> (r2),
      (dev3) - [:ASISTE_A] -> (r2),

      (r3:Reunion {nombre:"Reunion 3", fecha: "2024-11-01", hora_reun:"11:30"}),
      (s3) - [:REALIZA] -> (r3),
      (c3) - [:PARTICIPA_EN] -> (r3),
      (e3) - [:ASISTE_A] -> (r3),
      (dev5) - [:ASISTE_A] -> (r3),

      (r4:Reunion {nombre:"Reunion 4",fecha: "2024-11-02", hora_reun: "09:00"}),
      (s1) - [:REALIZA] -> (r4),
      (c1) - [:PARTICIPA_EN] -> (r4),
      (e4) - [:ASISTE_A] -> (r4),
      (dev2) - [:ASISTE_A] -> (r4),

      (r5:Reunion {nombre:"Reunion 5",fecha: "2024-11-03", hora_reun: "14:00"}),
      (s2) - [:REALIZA] -> (r5),
      (c2) - [:PARTICIPA_EN] -> (r5),
      (e5) - [:ASISTE_A] -> (r5),
      (dev6) - [:ASISTE_A] -> (r5),

      (r6:Reunion {nombre:"Reunion 6",fecha: "2024-11-04", hora_reun: "16:00"}),
      (s3) - [:REALIZA] -> (r6),
      (c3) - [:PARTICIPA_EN] -> (r6),
      (e1) - [:ASISTE_A] -> (r6),
      (dev4) - [:ASISTE_A] -> (r6)


RETURN r1, r2, r3, r4, r5, r6;


//-------------------------------------------------------------------------------




MATCH (s1:Sucursal {clave: "s1112"}), 
      (s2:Sucursal {clave: "s1113"}), 
      (s3:Sucursal {clave: "s1114"}), 
      (c1:Cliente {nombre: "Cliente 1"}),
      (c2:Cliente {nombre: "Cliente 2"}),
      (c3:Cliente {nombre: "Cliente 3"})

// Crear visitas
CREATE 
      (v1:Visita {nombre:"Visita 1",fecha: "2024-10-30", hora: "09:00", motivo: "Reunión de seguimiento"}),
      (s1) - [:RECIBE] -> (v1),
      (c1) - [:REALIZA] -> (v1),

      (v2:Visita {nombre:"Visita 2",fecha: "2024-10-31", hora: "14:00", motivo: "Presentación de proyecto"}),
      (s2) - [:RECIBE] -> (v2),
      (c2) - [:REALIZA] -> (v2),

      (v3:Visita {nombre:"Visita 3",fecha: "2024-11-01", hora: "11:30", motivo: "Revisión de contrato"}),
      (s3) - [:RECIBE] -> (v3),
      (c3) - [:REALIZA] -> (v3)

RETURN v1, v2, v3;

```


# Querys

1. Obtener la lista de sucursales que tienen más de 5 empleados.
	1. MATCH (e:Empleado)-[:Trabaja_en]->(s:Sucursal) 
WITH s,count(e) AS nuEmpl 
WHERE nuEmpl >5
RETURN s

2.  Encontrar los gerentes que gestionan más de 3 proyectos simultáneamente.
	1. MATCH (p:Proyecto)-[:Gestionado_por]->(e:Empleado {puesto: "gerente"})
WITH e, COUNT(p) AS proyectos_gestionados
WHERE proyectos_gestionados > 3
RETURN e

3. 1. Q03. Obtener la lista de desarrolladores con especialización en back-end que están trabajando en más de 2 proyectos.
	1. MATCH (p:Proyecto)-[:Involucrado_en]->(e:Empleado {especializacion:"Back-end"})
WITH e, COUNT(p) AS proyectos_invo
WHERE proyectos_invo  = 2
RETURN e

4. 1. Q04. Obtener la lista de proyectos que tienen un presupuesto mayor a $1,000,000.
	1. MATCH (p:Proyecto) where p.presu_asig >1000000 return p

 5. Listar los empleados de soporte técnico de todas las sucursales
	 1. MATCH (e:Empleado {puesto:"soporte tecnico"})-[:Trabaja_en]-> (s:Sucursal)
RETURN s,e

6. 1. Q06. Encontrar los proyectos que corresponden a un cliente en específico.
	1. MATCH (c:Cliente) --> (p:Proyecto)
WHERE c.nombre = "Cliente 1"
RETURN c,p

7.  Obtener la lista de sucursales que han recibido visitas de más de 5 clientes diferentes.
	1. MATCH (c:Cliente) --> (p:Proyecto) , (p:Proyecto) --> (s:Sucursal)
WITH s,count(DISTINCT c) as cliVis
WHERE cliVis > 5
RETURN s

8. Q08. Encontrar a los desarrolladores que han trabajado en proyectos con un presupuesto total mayor a $500,000.
	1. MATCH (p:Proyecto)-[:Involucrado_en]-> (e:Empleado)                            
	WHERE p.presu_asig > 500000 RETURN e,p 

9. Obtener la lista de clientes que han contratado más de 3 proyectos en diferentes sucursales.
	1. MATCH (c:Cliente) --> (p:Proyecto) , (p:Proyecto) --> (s:Sucursal)
WITH c,count(DISTINCT s) as sucDif 
WHERE sucDif > 3
RETURN c

10.  Encontrar las sucursales que tienen más de 5 desarrolladores especializados en full-stack.
	1. MATCH (e:Empleado {especializacion:"Full-stack"})-[:Trabaja_en]->(s:Sucursal) WITH s,count(e) as  numDeFullSatck                         
        WHERE numDeFullSatck > 5 
        return s
    

11. Transferir todos los empleados de soporte técnico de una sucursal en específico hacia otra sucursal.
	1. MATCH (e:Empleado {puesto:"soporte tecnico"}) -[r:Trabaja_en]->(s:Sucursal{clave:"s1112"}) DELETE r WITH e MATCH (n:Sucursal {clave:"s1113"}) CREATE (e)-[:Trabaja_en]->(n)
	2. Comprobación: MATCH (e:Empleado{puesto:"soporte tecnico"})-[:Trabaja_en]->(s:Sucursal{clave:"s1112"}) return e,s
	    MATCH (e:Empleado{puesto:"soporte tecnico"})-[:Trabaja_en]->(s:Sucursal{clave:"s1113"}) return e,s
	
12.  Reemplaza al gerente de una sucursal en específico..
	1. MATCH (e:Empleado{id:"j12345"})-[r:Trabaja_en]->(s:Sucursal {clave:"s1112"})  DELETE r WITH s MATCH (ne:Empleado{id:"j12346"}) CREATE (ne)-[:Trabaja_en]->(s)
	2. Comprobacion : MATCH  (e:Empleado{id:"j12345"})-[Trabaja_en]->(s:Sucursal {clave:"s1112"})  return e,s
	3.  MATCH  (e:Empleado{id:"j12346"})-[Trabaja_en]->(s:Sucursal {clave:"s1112"})  return e,s

13. Cambie un proyecto en específico a otra sucursal, incluyendo la totalidad de participantes en el proyecto .
	1. MATCH (p:Proyecto{codigo:"p4este"}) -[r:Desarrollado_en]->(s:Sucursal) DELETE r WITH p MATCH (sn:Sucursal{clave:"s1112"}) CREATE (p)-[:Desarrollado_en]->(sn)
	2. Comprabacion: MATCH (p:Proyecto{codigo:"p4este"}) -[:Desarrollado_en]->(s:Sucursal) return p,s

14. Obtener la lista de clientes que nunca han realizado visitas a las sucursales.
	1. MATCH (c:Cliente) --> (p:Proyecto) ,(p:Proyecto) -->(s:Sucursal) WITH c,count(s) as sucVis WHERE sucVis =0  RETURN c

15. Todos los empleados de una sucursal determinada son transferidos a otra sucursal por cierre de sucursal de origen.
	1. MATCH (e:Empleado) -[r:Trabaja_en]-> (s:Sucursal{clave: "s1114"}) DELETE r WITH e MATCH (sn:Sucursal{clave: "s1113"}) CREATE (e)-[:Trabaja_en]->(sn)
	2. Comprobacion:  MATCH (e:Empleado) -[:Trabaja_en]-> (s:Sucursal{clave: "s1114"}) return e,s
	3.  MATCH (e:Empleado) -[:Trabaja_en]-> (s:Sucursal{clave: "s1113"} ) return e,s
	