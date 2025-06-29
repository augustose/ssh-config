# SSH Configuration Manager

Una colección de scripts para gestionar fácilmente las conexiones SSH desde la línea de comandos.

## 📋 Descripción

Este proyecto incluye dos scripts principales:

- **`ssh-config`**: Gestor de configuraciones SSH para agregar, editar, listar y comentar conexiones
- **`ssh-connect`**: Conectador SSH interactivo con filtros y selección visual

## 🚀 Características

### ssh-config
- ✅ Agregar nuevas configuraciones SSH
- ✅ Editar configuraciones existentes
- ✅ Listar todas las configuraciones
- ✅ Comentar/descomentar configuraciones
- ✅ Editar el archivo de configuración directamente
- ✅ Interfaz de línea de comandos intuitiva

### ssh-connect
- ✅ Modo interactivo con interfaz colorida
- ✅ Filtrado de conexiones por nombre
- ✅ Selección numérica de servidores
- ✅ Visualización de detalles de conexión
- ✅ Búsqueda en tiempo real
- ✅ Modo de solo listado

## 📦 Instalación

### macOS

1. **Clona o descarga los scripts:**
```bash
# Opción 1: Clonar desde Git
git clone https://github.com/augustose/ssh-config.git
cd ssh-config

# Opción 2: Descargar directamente
curl -O https://raw.githubusercontent.com/augustose/ssh-config/main/ssh-config
curl -O https://raw.githubusercontent.com/augustose/ssh-config/main/ssh-connect
```

2. **Hacer ejecutables los scripts:**
```bash
chmod +x ssh-config ssh-connect
```

3. **Instalar en el PATH (opcional):**
```bash
# Opción A: Mover a /usr/local/bin (recomendado)
sudo cp ssh-config ssh-connect /usr/local/bin/

# Opción B: Crear enlaces simbólicos
sudo ln -s $(pwd)/ssh-config /usr/local/bin/ssh-config
sudo ln -s $(pwd)/ssh-connect /usr/local/bin/ssh-connect

# Opción C: Agregar al PATH del usuario
echo 'export PATH="$HOME/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

### Linux

1. **Descargar los scripts:**
```bash
# Opción 1: Clonar desde Git
git clone https://github.com/augustose/ssh-config.git
cd ssh-config

# Opción 2: Descargar directamente
wget https://raw.githubusercontent.com/augustose/ssh-config/main/ssh-config
wget https://raw.githubusercontent.com/augustose/ssh-config/main/ssh-connect
```

2. **Hacer ejecutables los scripts:**
```bash
chmod +x ssh-config ssh-connect
```

3. **Instalar en el PATH:**
```bash
# Opción A: Mover a /usr/local/bin
sudo cp ssh-config ssh-connect /usr/local/bin/

# Opción B: Crear enlaces simbólicos
sudo ln -s $(pwd)/ssh-config /usr/local/bin/ssh-config
sudo ln -s $(pwd)/ssh-connect /usr/local/bin/ssh-connect

# Opción C: Agregar al PATH del usuario
echo 'export PATH="$HOME/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

## 📖 Uso

### ssh-config

#### Comandos disponibles:
```bash
ssh-config [OPTION]
```

#### Opciones:
- `add, -a` - Agregar nueva configuración SSH
- `comment, -c` - Comentar configuración existente
- `list, -l` - Listar todas las configuraciones
- `edit, -e` - Editar archivo de configuración con VI
- `update, -u` - Actualizar configuración existente
- `help, -h` - Mostrar ayuda

#### Ejemplos:
```bash
# Agregar nueva configuración
ssh-config -a

# Listar configuraciones
ssh-config -l

# Comentar configuración 'server'
ssh-config -c server

# Editar archivo de configuración
ssh-config -e

# Actualizar configuración existente
ssh-config -u
```

### ssh-connect

#### Modos de uso:
```bash
ssh-connect [OPTION] [SEARCH_TERM]
```

#### Opciones:
- `-h, --help` - Mostrar ayuda
- `-i, --interactive` - Modo interactivo (por defecto)
- `-l, --list` - Solo listar conexiones
- `-f, --filter` - Aplicar filtro a nombres de conexión

#### Ejemplos:
```bash
# Modo interactivo
ssh-connect

# Listar todas las conexiones
ssh-connect -l

# Filtrar conexiones que contengan 'production'
ssh-connect production

# Aplicar filtro específico
ssh-connect -f staging
```

#### Comandos en modo interactivo:
- `[número]` - Conectar al servidor seleccionado
- `f <término>` - Filtrar conexiones por término
- `c` - Limpiar filtro
- `l` - Listar conexiones
- `h` - Mostrar ayuda
- `q` - Salir

## 🔧 Configuración

### Archivo de configuración SSH

Los scripts utilizan el archivo de configuración SSH estándar ubicado en:
- **macOS/Linux**: `~/.ssh/config`

Si el archivo no existe, se creará automáticamente con los permisos correctos.

### Configuración inicial

Para comenzar rápidamente, puedes usar el archivo de ejemplo incluido:

```bash
# Copiar el archivo de ejemplo
cp ssh-config.example ~/.ssh/config

# Editar con tus configuraciones reales
ssh-config -e
```

### Estructura del archivo de configuración

```bash
Host nombre-servidor
    HostName example.com
    User usuario
    Port 22
    IdentityFile ~/.ssh/id_rsa
    ForwardAgent yes
    ServerAliveInterval 60
```

## 🎨 Características visuales

### ssh-connect
- **Interfaz colorida** para mejor legibilidad
- **Números de selección** para conexiones
- **Detalles de configuración** mostrados con colores
- **Mensajes informativos** con códigos de color

### Colores utilizados:
- 🔵 **Azul**: Nombres de servidores
- 🟢 **Verde**: Números de selección y mensajes de éxito
- 🟡 **Amarillo**: Advertencias y filtros activos
- 🔴 **Rojo**: Errores
- 🟣 **Púrpura**: Detalles de configuración
- 🔵 **Cian**: Títulos y encabezados

## 📝 Ejemplos de uso

### Agregar una nueva conexión SSH
```bash
$ ssh-config -a
Adding new SSH configuration...
Host name (alias): mi-servidor
Server address (hostname/IP): example.com
SSH user: admin
SSH port [22]: 2222
Use a specific key file? (y/n): y
Path to private key file: ~/.ssh/id_rsa
Add additional options? (y/n): y
Use ForwardAgent? (y/n): y
Use ServerAliveInterval? (y/n): y

Configuration added successfully.
You can now connect using: ssh mi-servidor
```

### Conectar usando ssh-connect
```bash
$ ssh-connect
SSH Connect - Interactive Mode
Type 'h' for help, 'q' to quit

Available SSH connections:
----------------------------------------
[1] prod-server
    HostName example.com
    User admin
    Port 22
    IdentityFile ~/.ssh/id_rsa
    ForwardAgent yes
    ServerAliveInterval 60

[2] staging-server
    HostName staging.example.com
    User deploy
    Port 2222
    IdentityFile ~/.ssh/staging_key
    ForwardAgent yes

Commands:
  [number] - Connect to server
  f <term> - Filter connections
  c        - Clear filter
  l        - List connections
  h        - Show help
  q        - Quit

Enter command: 1
Connecting to prod-server...
Press Ctrl+C to cancel
```

## 🔒 Seguridad

- Los scripts respetan los permisos del archivo de configuración SSH
- El archivo `~/.ssh/config` se crea con permisos `600` (solo lectura para el propietario)
- El directorio `~/.ssh` se crea con permisos `700` si no existe
- No se almacenan contraseñas ni información sensible
- **Importante**: Nunca compartas tu archivo `~/.ssh/config` real, ya que puede contener información sensible

## 🐛 Solución de problemas

### Error: "Permission denied"
```bash
# Verificar permisos del archivo de configuración
ls -la ~/.ssh/config

# Corregir permisos si es necesario
chmod 600 ~/.ssh/config
chmod 700 ~/.ssh
```

### Error: "No SSH configurations defined"
- Verificar que el archivo `~/.ssh/config` existe
- Verificar que contiene configuraciones válidas
- Usar `ssh-config -a` para agregar la primera configuración
- Usar el archivo de ejemplo: `cp ssh-config.example ~/.ssh/config`

### Error: "Command not found"
- Verificar que los scripts están en el PATH
- Verificar que tienen permisos de ejecución (`chmod +x`)
- Usar rutas absolutas si es necesario

## 📄 Licencia

Este proyecto está licenciado bajo la Licencia Apache 2.0. Ver el archivo [LICENSE](LICENSE) para más detalles.

## 👨‍💻 Autor

**Augusto Sosa Escalada** - [augustose@gmail.com](mailto:augustose@gmail.com)

## 🤝 Contribuciones

Las contribuciones son bienvenidas. Por favor:

1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

## 📞 Soporte

Si encuentras algún problema o tienes alguna pregunta:

- Abre un issue en GitHub
- Contacta al autor: [augustose@gmail.com](mailto:augustose@gmail.com)

---

⭐ **¡Si este proyecto te es útil, considera darle una estrella en GitHub!** 