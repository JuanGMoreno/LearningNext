# Anotaciones de Next.js de el curso de midu

## instalacion

en este caso se usaron parametros extra ya que se iba a tomar como base el de el tutotial :

`npx create-next-app@latest nextjs-dashboard --example "https://github.com/vercel/next-learn/tree/main/dashboard/starter-example" --use-pnpm`

/app: Contiene todas las rutas, componentes y lógica de tu aplicación; aquí es donde trabajarás principalmente.
/app/lib: Contiene las funciones utilizadas en tu aplicación, como las funciones de utilidad reutilizables y las funciones de obtención de datos.
/app/ui: Contiene todos los componentes de la interfaz de usuario de tu aplicación, como tarjetas, tablas y formularios. Para ahorrar tiempo, hemos prediseñado estos componentes.
/public: Contiene todos los recursos estáticos de tu aplicación, como imágenes.
Archivos de configuración: También encontrarás archivos de configuración como next.config.ts en la raíz de tu aplicación. La mayoría de estos archivos se crean y preconfiguran al iniciar un nuevo proyecto con create-next-app. No necesitarás modificarlos en este curso.

## Cargado de css

existen tres metodos principales para cargar css dentro de un proyecto de next de forma nativa:

1. tallwind
2. css global
3. css modules
4. usar una libreria llamada clsx que te permite hacer estilos condicionales mas facilmente

## Optimizacion de letras(Fonts)

se crea una carpeta dentro de la iu que sea fonts.ts

`
import { Inter } from 'next/font/google'

export const inter = Inter({subsets: ['latin'], weight:['400','500','600','700'] })
`
solo basta que en el archivo que estas usando la letra pongas el nombre.clasname

## Optimizacion de imagenes

se usa un componenete llamado Image ya que ya se encuentra optimizado reduciendo las imagenes
y convirtiendolas a una extension optima al usar esto es obligatorio usar width y heigth con
su relacuion de aspecto adecuada ademas es lazy low

`<Image src='/hero-mobile.png' alt='imagen del dashboard mobile' width={560} height={620}
          className='block md:hidden'/>
`

## Rutas ,pages , layout

next trabaja con un eenrrutado teniendo en cuenta el sistema de archivos lo que quiere decir que el primer page sera el / root y las nuevas carpetas que se creeen en la app que tenga un page seran nuevas rutas permitiendo asi hacer rutas anidadas y layouts que envuelven algunas 
rutas especificas 

<img src="./md/rutas.avif" alt="Logo del proyecto" width="500" />

## Navegacion con el Link

este es un compoentne de next que permite navegar entre rutas sin cargar la pagina completa 

`
import Link from 'next/link'

<Link
            key={link.name}
            href={link.href}
            className="flex h-[48px] grow items-center justify-center gap-2 rounded-md bg-gray-50 p-3 text-sm font-medium hover:bg-sky-100 hover:text-blue-600 md:flex-none md:justify-start md:p-2 md:px-3"
          >
            <LinkIcon className="w-6" />
            <p className="hidden md:block">{link.name}</p>
          </Link>
`

### next tiene ya implementado el Automatic code-splitting and prefetching 

1. el code-splitting lo que logra es solo cargar los componentes que estan en uso dentro de la pagina evitando asi sobrecargar con elemetos innecesarios

2. el prefetching lo que hace es que si el link esta dentro de el viewport la ruta se precarga para cuando se de click sea mucho mas rapido 

### Uso de el usePathname 

es un hook de next que te permite saber el nombre de la direccion actual sirve para poner en marcado la barra de navegacion por ejemplo ,para esto se debe poner el componente desde el parte del cliente tambien 

`
'use client'

import {usePathname} from 'next/navegation';
`