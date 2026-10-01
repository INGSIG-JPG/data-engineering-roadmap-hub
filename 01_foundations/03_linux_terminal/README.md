# 🐧 Linux y Comandos de Terminal

## Checklist de Competencia (COMP-CS-001)
- [x] Navegación del sistema de archivos (`cd`, `ls`, `pwd`, `tree`)
- [x] Manipulación de archivos (`cp`, `mv`, `rm`, `mkdir`, `cat`, `nano`)
- [ ] Permisos y propietarios (`chmod`, `chown`)
- [ ] Procesos y monitoreo (`ps`, `top`, `htop`, `kill`)
- [ ] Tuberías y redirección (`|`, `>`, `>>`, `grep`, `awk`, `sed`)
- [ ] Variables de entorno y `.bashrc` / `.zshrc`
- [ ] Shell Scripting básico (`.sh`)

## Active Recall Test
<details><summary>🧠 Test Linux — Tuberías y Filtrado</summary>

### Pregunta
¿Cómo filtrarías las líneas de un archivo de log `syslog.log` que contengan la palabra "ERROR" y guardarías el resultado en `errores.txt`?

**Mi respuesta:**
<!-- Escribe tu respuesta aquí -->

<details><summary>🔎 Ver solución</summary>

```bash
grep "ERROR" syslog.log > errores.txt
