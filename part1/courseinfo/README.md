### **1.1: Información del Curso, paso 1**

Desafortunadamente, toda la aplicación está en el mismo componente. Refactoriza el código para que conste de tres componentes nuevos: *Header*, *Content* y *Total*. Todos los datos aún residen en el componente *App*, que pasa los datos necesarios a cada componente mediante *props*. *Header* se encarga de mostrar el nombre del curso, *Content* muestra las partes y su número de ejercicios y *Total* muestra el número total de ejercicios.

Código Inicial

    const App = () => {
    const course = 'Half Stack application development'
    const part1 = 'Fundamentals of React'
    const exercises1 = 10
    const part2 = 'Using props to pass data'
    const exercises2 = 7
    const part3 = 'State of a component'
    const exercises3 = 14

    return (
        <div>
        <h1>{course}</h1>
        <p>
            {part1} {exercises1}
        </
        <p>
            {part2} {exercises2}
        </p>
        <p>
            {part3} {exercises3}
        </p>
        <p>Number of exercises {exercises1 + exercises2 + exercises3}</p>
        </div>
    )
    }

    export default App