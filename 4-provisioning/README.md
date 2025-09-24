# 4-provisioning - Ejemplo SIMPLE de Ansible con Roles

Ejemplo muy básico de cómo usar **2 roles** con Ansible y Vagrant.

## 📋 Qué hace

- **Rol common**: Actualiza paquetes, crea usuario, instala herramientas básicas
- **Rol webserver**: Instala Apache y crea página web simple

## 🏗️ Estructura SIMPLE

```
4-provisioning/
├── Vagrantfile          # VM Ubuntu
├── playbook.yml         # 1 playbook que usa 2 roles
└── roles/
    ├── common/
    │   └── tasks/main.yml    # Tareas básicas del sistema
    └── webserver/
        └── tasks/main.yml    # Instalar Apache
```

## 🚀 Cómo usar

```bash
cd 4-provisioning
vagrant up
```

## 🎯 Qué hacen los roles

### Rol "common"
1. Actualiza paquetes
2. Crea usuario "ejemplo"
3. Instala curl y vim

### Rol "webserver"  
1. Instala Apache
2. Inicia el servicio
3. Crea página web simple

## ✅ Resultado

- Usuario "ejemplo" creado
- Apache funcionando
- Página web básica en Apache

¡Así de simple es usar roles en Ansible!
