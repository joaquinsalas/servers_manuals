# Procedimiento para crear un usuario en Ubuntu (con Conda)

## 1. Crear credenciales seguras
Generar el nombre de usuario y contraseña en un administrador de contraseñas (por ejemplo, Bitwarden).  
La contraseña debe tener 16 o 20 caracteres.

## 2. Verificar UID disponible
```bash
cat /etc/group
````

El UID debe ser único para evitar conflictos en el sistema.

---

## 3. Crear el usuario

```bash
sudo adduser --uid 1036 username
```

* Crea el usuario con un identificador único (UID).
* Genera automáticamente `/home/username`.

---

## 4. Asignar contraseña y configurar datos

Durante la creación, el sistema solicitará:

* contraseña
* nombre completo
* teléfono (opcional)

Estos datos son informativos y pueden dejarse en blanco.

---

## 5. Agregar usuario al grupo de Conda

```bash
sudo usermod -aG conda3 username
```

Permite acceso a Conda instalado en `/opt/conda3`.

---

## 6. Verificar que se agregó al grupo

```bash
groups username
```

Confirma que pertenece al grupo `conda3`.

---

## 7. Crear directorio de almacenamiento

```bash
mkdir /mnt/data-r1/EmilioBadillo
```

Crea un espacio de trabajo para datos.

---

## 8. Verificar que se creó

```bash
ls -l /mnt/data-r1
```

Confirma que la carpeta existe.

---

## 9. Asignar permisos (MUY IMPORTANTE)

```bash
chown emiliobadillo:emiliobadillo /mnt/data-r1/EmilioBadillo
```

Otorga propiedad total de la carpeta al usuario.
Sin esto, no podrá escribir en esa ruta.

---

## 10. Entrar con el usuario creado

```bash
su emiliobadillo
```

Cambia a la sesión del nuevo usuario.

---

## 11. Inicializar Conda

```bash
/opt/conda3/bin/conda init
```

Configura la terminal para usar Conda.




