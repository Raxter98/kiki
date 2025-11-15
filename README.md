README – Estructura de Navegación en Angular (KIKI App)

REQUISITOS CLAVES PARA EJECUTAR ESTE PROYECTO

Node.js (obligatorio) (ULTIMA VERSIÓN ESTABLE)

Ionic CLI (obligatorio) (ULTIMA VERSIÓN ESTABLE)

Angular CLI (solo se usa dentro del proyecto, pero recomendada global)

Git (para clonar y subir el proyecto)

--------------------------------------------------------------------
Este proyecto implementa una estructura de navegación modular y escalable en Angular, basada en buenas prácticas y división por pantallas/áreas, permitiendo un desarrollo más organizado y mantenible.

src/
 └── app/
     ├── app.routes.ts
     ├── app.component.ts
     ├── app.component.html
     ├── dashboard/
     │   ├── dashboard.component.ts
     │   ├── dashboard.component.html
     │   └── dashboard.component.scss
     ├── home/
     │   ├── home.component.ts
     │   ├── home.component.html
     │   └── home.component.scss
     ├── login/
     │   ├── login.component.ts
     │   ├── login.component.html
     │   └── login.component.scss
     ├── register/
         ├── register.component.ts
         ├── register.component.html
         └── register.component.scss
    ...
    ...
    ...

Cada carpeta representa una pantalla independiente con su propio componente y estilos.

Cómo ejecutar el proyecto

1 Situarse en la raiz del proyecto

cd kiki

2 Instalar dependencias

npm install

3 Ejecutar el servidor local

ionic serve

La app se abrirá automáticamente

----------------------------------------------------------

Navegación (Routing)

El archivo app.routes.ts define la navegación principal

import { Routes } from '@angular/router';

export const routes: Routes = [
  {
    path: '',
    redirectTo: 'login',
    pathMatch: 'full',
  },
  {
    path: 'login',
    loadComponent: () => import('./login/login.page').then(m => m.LoginPage)
  },
  {
    path: 'register',
    loadComponent: () => import('./register/register.page').then(m => m.RegisterPage)
  },
  {
    path: 'dashboard',
    loadComponent: () => import('./dashboard/dashboard.page').then(m => m.DashboardPage)
  }...


-------------------------------------------------------------------
Estilos

Cada componente posee su propio archivo .scss, por ejemplo:

/* home.component.scss */
@use '../../theme/variables.scss' as *;

ion-content {
  --background: transparent;
  padding: 18px;
}

.hero {
  display: grid;
  gap: 12px;
}

.banner {
  background: linear-gradient(90deg, var(--ion-color-primary), #8540e0);
  color: #fff;
  padding: 18px;
  border-radius: 14px;
  box-shadow: var(--shadow-base);
  display: flex;
  align-items: center;
  justify-content: space-between;
}

Nota: Los estilos incluidos son básicos y solo cumplen un propósito demostrativo.
No representan el diseño oficial final

-----------------------------------------------------------------------

Cómo agregar nuevas pantallas

1. Crear una carpeta dentro de app/
Ejemplo: products/

2.Generar el componente:
ng generate component products

3.Agregar la ruta en app.routes.ts:
{ path: 'products', component: ProductsComponent }


----------------------------------------------------------------------

✅ Problemas enfrentados

1. Diferencias entre la estructura original y la generada por Ionic

Al crear el proyecto con ionic start, la estructura generada por defecto no coincidía con el diseño planificado en la unidad 2.

Fue necesario reorganizar carpetas, crear componentes y ajustar rutas para que coincidieran conceptualmente con el mapa de navegación.

2. Configuración inicial de Angular CLI

Al ejecutar ionic serve, surgió el error "ng no se reconoce como un comando", porque el proyecto no estaba identificado como workspace.

Esto obligó a crear un proyecto Ionic completamente nuevo y sobre él integrar manualmente la estructura de navegación.

3. Enrutamiento y lazy loading

El sistema de rutas de Ionic utiliza lazy loading para mejorar el rendimiento.

Fue necesario comprender la estructura con módulos independientes por página (home.module.ts, login.module.ts, etc.) para implementar la navegación correctamente.

4. Problemas de compatibilidad entre Angular e Ionic

Algunas importaciones necesarias para los componentes (IonMenu, IonRouterOutlet, IonHeader, etc.) requirieron revisar documentación actualizada.

Fue necesario corregir importaciones duplicadas o incorrectas generadas por defecto.

5. Estilos no aplicados

Los estilos base debían instalarse manualmente porque el proyecto no incluía el CSS global.

Hubo que crear los archivos .scss faltantes y aplicar estilos mínimos para mantener coherencia con el diseño conceptual.

6. Organización del proyecto para que el profesor pueda ejecutarlo

El proyecto debía funcionar sin requerir instalaciones adicionales.

Fue necesario crear un README detallado explicando dependencias, comandos de instalación y estructura de carpetas.

7. Estructura real del diseño vs. prototipo

El diseño visual original no se replicó en esta fase porque la tarea exige solo la “cáscara” de navegación.

Esto obligó a separar funcionalidad de diseño y dejar placeholders en las vistas.

-------------------------------------------------------------------

Conclusión

Este repositorio te entrega:

✔ Una estructura modular y escalable
✔ Navegación configurada y funcionando
✔ Layout base con header / contenido / footer
✔ Carpetas organizadas por pantalla
✔ Archivos listos para expandir


❗ El diseño visual NO está finalizado.
El objetivo de este proyecto es entregar la estructura de navegación funcional, no la apariencia final.