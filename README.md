# SyP-DEV_Ansible_Vagrant

## 📁 Estructura del Proyecto

```
SyP-DEV_Ansible_Vagrant/
├── 1-vagrant/           # Vagrant básico
├── 2-ansible/           # Ansible básico con múltiples VMs
├── 3-vagrant-ansible/   # Integración Vagrant + Ansible
├── 4-provisioning/      # Ansible con Roles (SIMPLE)
└── 5-roles-galaxy/      # Roles de Ansible Galaxy
```

## 🎯 Progresión de Aprendizaje

Cada carpeta representa un nivel de complejidad creciente:

1. **Básico**: Solo Vagrant
2. **Intermedio**: Ansible independiente
3. **Integración**: Vagrant + Ansible
4. **Roles propios**: Ansible con roles personalizados
5. **Avanzado**: Roles de la comunidad (Galaxy)

---

## 📂 1-vagrant - Vagrant Básico

### 🎯 Objetivo
Crear una máquina virtual simple con Vagrant.

### 📋 Contenido
- `Vagrantfile`: Configuración básica de VM Ubuntu

### 🚀 Cómo ejecutar
```bash
cd 1-vagrant
vagrant up
```

### ✅ Cómo verificar
```bash
# Ver estado de la VM
vagrant status

# Conectarse por SSH
vagrant ssh

# Dentro de la VM
uname -a
exit

# Destruir VM
vagrant destroy
```

### 📖 Qué aprenderás
- Configuración básica de Vagrant
- Creación y gestión de VMs
- Comandos básicos de Vagrant

---

## 📂 2-ansible - Ansible Básico

### 🎯 Objetivo
Usar Ansible para configurar múltiples VMs desde el host.

### 📋 Contenido
- `Vagrantfile`: Crea 2 VMs (vm1, vm2)
- `inventory.yaml`: Inventario de servidores
- `playbook.yaml`: Playbook básico de Ansible

### 🚀 Cómo ejecutar
```bash
cd 2-ansible

# Levantar las VMs
vagrant up

# Ejecutar Ansible desde el host
ansible-playbook -i inventory.yaml playbook.yaml
```

### ✅ Cómo verificar
```bash
# Ver VMs corriendo
vagrant status

# Conectarse a cada VM
vagrant ssh vm1
# (verificar cambios realizados por Ansible)
exit

vagrant ssh vm2
# (verificar cambios realizados por Ansible)
exit
```

### 📖 Qué aprenderás
- Inventarios de Ansible
- Playbooks básicos
- Gestión de múltiples hosts
- Ejecución de Ansible desde el host

---

## 📂 3-vagrant-ansible - Integración

### 🎯 Objetivo
Integrar Vagrant con Ansible para provisionamiento automático.

### 📋 Contenido
- `Vagrantfile`: VM con provisionador Ansible
- `inventory`: Inventario simple
- `playbook.yml`: Playbook ejecutado automáticamente

### 🚀 Cómo ejecutar
```bash
cd 3-vagrant-ansible

# Vagrant automáticamente ejecuta Ansible
vagrant up
```

### ✅ Cómo verificar
```bash
# Conectarse a la VM
vagrant ssh
exit
```

### 📖 Qué aprenderás
- Integración Vagrant + Ansible
- Provisionamiento automático
- Configuración en tiempo de creación de VM

---

## 📂 4-provisioning - Ansible con Roles (SIMPLE)

### 🎯 Objetivo
**Ejemplo educativo SIMPLE** de cómo usar roles personalizados en Ansible.

### 📋 Contenido
```
4-provisioning/
├── Vagrantfile          # VM con provisionamiento
├── playbook.yml         # Playbook que usa 2 roles
└── roles/
    ├── common/          # Rol 1: Tareas básicas
    │   └── tasks/main.yml
    └── webserver/       # Rol 2: Servidor web
        └── tasks/main.yml
```

### 🚀 Cómo ejecutar
```bash
cd 4-provisioning
vagrant up
```

### ✅ Cómo verificar

#### Conectarse a la VM:
```bash
vagrant ssh
```

#### Verificar ROL "common":
```bash
# Usuario "ejemplo" creado
grep ejemplo /etc/passwd

# Paquetes instalados
curl --version
vim --version
```

#### Verificar ROL "webserver":
```bash
# Apache funcionando
sudo systemctl status apache2

# Página web creada
cat /var/www/html/index.html

# Probar página web
curl http://localhost
```

#### Salir:
```bash
exit
```

### 📊 Resultado esperado
- ✅ Usuario "ejemplo" creado
- ✅ Curl y Vim instalados
- ✅ Apache corriendo
- ✅ Página web personalizada

### 📖 Qué aprenderás
- **Estructura de roles** de Ansible
- **Organización modular** del código
- **Reutilización** de roles
- **Separación de responsabilidades**

---

## 📂 5-roles-galaxy - Roles de la Comunidad

### 🎯 Objetivo
Usar roles externos de Ansible Galaxy para configuraciones avanzadas.

### 📋 Contenido
- `requirements.yaml`: Roles de Galaxy a instalar
- `playbook.yml`: Playbook usando roles externos
- `inventory`: Inventario de hosts

### 🚀 Cómo ejecutar
```bash
cd 5-roles-galaxy

# Instalar roles de Galaxy
ansible-galaxy install -r requirements.yaml

# Ejecutar playbook con roles externos
ansible-playbook -i inventory playbook.yml
```

### ✅ Cómo verificar
```bash
# Verificar roles instalados
ansible-galaxy list

# Verificar funcionalidad según roles usados
# (depende de los roles específicos en requirements.yaml)
```

### 📖 Qué aprenderás
- Ansible Galaxy
- Instalación de roles externos
- Gestión de dependencias
- Roles de la comunidad

---

## 🎓 Orden de Aprendizaje Recomendado

1. **Comenzar con `1-vagrant`** - Entender Vagrant básico
2. **Continuar con `2-ansible`** - Aprender Ansible independiente
3. **Seguir con `3-vagrant-ansible`** - Ver la integración
4. **Practicar con `4-provisioning`** - **⭐ ROLES SIMPLES** (ideal para aprender)
5. **Avanzar a `5-roles-galaxy`** - Roles avanzados de la comunidad

## 🔧 Comandos Útiles Globales

### Vagrant:
```bash
vagrant up        # Crear y arrancar VM
vagrant status    # Ver estado
vagrant ssh       # Conectar por SSH
vagrant provision # Solo re-ejecutar provisionadores
vagrant halt      # Parar VM
vagrant destroy   # Eliminar VM
```

### Ansible:
```bash
ansible-playbook -i inventory playbook.yml    # Ejecutar playbook
ansible-galaxy install -r requirements.yaml   # Instalar roles
ansible-galaxy list                           # Ver roles instalados
```

## 🎯 Proyecto Recomendado para Aprender Roles

**La carpeta `4-provisioning`** es perfecta para entender roles porque:

✅ **Estructura simple** - Solo lo esencial  
✅ **2 roles básicos** - Fácil de seguir  
✅ **Ejemplo funcional** - Resultado visible  
✅ **Bien documentado** - Explicación clara  