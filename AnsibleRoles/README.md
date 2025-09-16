# Proyecto Vagrant + Ansible con Roles

Este es un ejemplo más complejo que demuestra el uso de roles de Ansible con Vagrant.

## Estructura del proyecto

```
AnsibleRoles/
├── Vagrantfile
├── site.yml
├── inventory
└── roles/
    ├── common/
    │   └── tasks/
    │       └── main.yml
    ├── nginx/
    │   ├── tasks/
    │   │   └── main.yml
    │   ├── templates/
    │   │   └── webapp.conf.j2
    │   └── handlers/
    │       └── main.yml
    ├── nodejs/
    │   └── tasks/
    │       └── main.yml
    └── webapp/
        ├── tasks/
        │   └── main.yml
        ├── templates/
        │   ├── package.json.j2
        │   ├── app.js.j2
        │   └── webapp.service.j2
        └── handlers/
            └── main.yml
```

## ¿Qué hace este proyecto?

1. **Rol Common**: Actualiza el sistema e instala herramientas básicas
2. **Rol Nginx**: Instala y configura Nginx como proxy reverso
3. **Rol Node.js**: Instala Node.js versión 16
4. **Rol WebApp**: Despliega una aplicación Node.js con Express

## Características

- Aplicación Node.js real con Express
- Nginx configurado como proxy reverso
- Servicio systemd para la aplicación
- API REST básica en `/api/status`
- Templates dinámicos con variables de Ansible
- Handlers para reiniciar servicios automáticamente
- Usuario dedicado para la aplicación

## Cómo usar

1. Navegar al directorio:
   ```bash
   cd AnsibleRoles
   ```

2. Levantar la máquina virtual:
   ```bash
   vagrant up
   ```

3. Acceder a la aplicación:
   - Aplicación web: `http://localhost:8080`
   - API REST: `http://localhost:8080/api/status`

4. Para destruir la VM:
   ```bash
   vagrant destroy -f
   ```

## Puertos

- Puerto 80 (VM) → 8080 (host): Aplicación web vía Nginx
- Puerto 3000 (VM) → 3000 (host): Acceso directo a Node.js

## Variables configurables

En `site.yml` puedes modificar:
- `app_name`: Nombre de la aplicación
- `node_version`: Versión de Node.js a instalar
