# React

## ¿Qué es React?

React es una librería de JavaScript desarrollada por Facebook para construir interfaces de usuario (UI) de forma declarativa, basada en componentes reutilizables.

- Basado en componentes: piezas independientes y reutilizables.

- Declarativo: describes qué quieres ver en la pantalla, y React se encarga de actualizarlo de forma eficiente.

- Virtual DOM: mejora el rendimiento actualizando solo lo necesario.

## Crear un Proyecto React con Vite

[Vite](https://vitejs.dev/) es una herramienta moderna de desarrollo frontend que ofrece arranques rápidos y recargas instantáneas. Es mucho más rápido que `create-react-app`.

Podemos crear un nuevo proyecto con el siguiente comando:

```bash
npm create vite@latest
```

## Estructura Básica de un Componente

``` jsx
function MiComponente() {
  return (
    <div>
      <h1>Hola, mundo</h1>
    </div>
  );
}
```

Para usarlo:

``` jsx
<MiComponente />
```

## JSX

JSX es una extensión de JavaScript que permite escribir HTML dentro de JS:

``` jsx
const saludo = <h1>Hola, JSX</h1>;
```

## Hooks de React

React introdujo los hooks para usar estado y otras funcionalidades sin escribir clases.

1. useState()

    Permite manejar el estado en componentes funcionales.

    ``` jsx
    const [contador, setContador] = useState(0);
    ```

2. useEffect()

    Permite ejecutar efectos secundarios (side effects) como peticiones fetch, suscripciones, etc.

    ``` jsx
    useEffect(() => {
    console.log("Componente montado o actualizado");

    return () => {
        console.log("Componente desmontado");
    };
    }, [dependencias]);
    ```

    - Si []: se ejecuta solo al montar
    - Si [x]: se ejecuta al cambiar x
    - Sin array: se ejecuta en cada render

3. useContext()

    Accede a un contexto global sin necesidad de pasar props manualmente.

    ``` jsx
    const valor = useContext(MiContexto);
    ```

4. useRef()

    Crea una referencia mutable que no causa renderizados cuando cambia.

    ``` jsx
    const inputRef = useRef(null);

    <input ref={inputRef} />
    ```

5. useMemo() y useCallback()

    - useMemo: memoriza un valor computado.

    ``` jsx
    const resultado = useMemo(() => calcularAlgo(dato), [dato]);
    ```

    - useCallback: memoriza una función.

    ``` jsx
    const funcionMemo = useCallback(() => hacerAlgo(valor), [valor]);
    ```

6. useReducer()

    Alternativa a useState, útil para estados más complejos.

    ``` jsx
    const [estado, dispatch] = useReducer(reducer, estadoInicial);
    ```

7. useLayoutEffect()

    Como useEffect pero se ejecuta sincrónicamente después del DOM renderizado. ⚠️ Usar con cuidado.

8. useImperativeHandle()

    Personaliza la instancia expuesta por un componente con ref.

9. useId()

    Genera un ID único para usar en elementos HTML (útil para accesibilidad y formularios).

## Ejemplo completo

``` jsx
import React, { useState, useEffect } from "react";

function Contador() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `Has hecho clic ${count} veces`;
  }, [count]);

  return (
    <button onClick={() => setCount(count + 1)}>
      Haz clic ({count})
    </button>
  );
}
```

## Recomendaciones

- Usar useEffect para peticiones a APIs
- Mantener componentes pequeños y reutilizables
- Vitar useState excesivo si puedes usar useReducer o context
- Usa custom hooks para reutilizar lógica
