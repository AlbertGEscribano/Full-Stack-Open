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

Ejercicio resuelto:

    const App = () => {
    const course = 'Half Stack application development'
    const part1 = 'Fundamentals of React'
    const exercises1 = 10
    const part2 = 'Using props to pass data'
    const exercises2 = 7
    const part3 = 'State of a component'
    const exercises3 = 14

    const Header = ({ course }) => {
        return <h1>{course}</h1>}

    export default Header

    const Content = ({ part1, exercises1, part2, exercises2, part3, exercises3 }) => {
        return (
        <>
            <p>{part1} {exercises1}</p>
            <p>{part2} {exercises2}</p>
            <p>{part3} {exercises3}</p>
        </>
        )
    }

    const Total = ({ exercises1, exercises2, exercises3 }) => {
        return <p>Number of exercises {exercises1 + exercises2 + exercises3}</p>
    }

    return (
        <div>
        <Header course={course} />
        <Content 
            part1={part1} exercises1={exercises1} 
            part2={part2} exercises2={exercises2} 
            part3={part3} exercises3={exercises3} 
        />
        <Total exercises1={exercises1} exercises2={exercises2} exercises3={exercises3} />
        </div>
    )
    }


    export default App

### **1.2: Información del Curso, paso 2**

Refactoriza el componente *Content* para que no muestre ningún nombre de partes o su número de ejercicios por sí mismo. En su lugar, solo representa tres componentes *Part* de los cuales cada uno representa el nombre y el número de ejercicios de una parte.

Ejercicio resuelto:

    const App = () => {
    const course = 'Half Stack application development'
    const part1 = 'Fundamentals of React'
    const exercises1 = 10
    const part2 = 'Using props to pass data'
    const exercises2 = 7
    const part3 = 'State of a component'
    const exercises3 = 14

    const Header = ({ course }) => {
        return <h1>{course}</h1>}

    const Part = ({name, exercises}) => {
        return<p>{name} {exercises}</p>}

    const Content = ({part1, exercises1, part2, exercises2, part3, exercises3}) => {
        return (
        <>
            <Part name={part1} exercises={exercises1}/>
            <Part name={part2} exercises={exercises2}/>
            <Part name={part3} exercises={exercises3}/>
        </>
        )
    }

    const Total = ({total}) => {
        return<p>Number of exercises {total}</p>}

    return (
        <div>
        <Header course={course} />
        <Content part1={part1} exercises1={exercises1} part2={part2} exercises2={exercises2} part3={part3} exercises3={exercises3} />
        <Total total={exercises1+exercises2+exercises3}/>
        </div>
    )
    }

    export default App

### **1.3: Información del Curso, paso 3**

Avancemos para usar objetos en nuestra aplicación. Modifica las definiciones de las variables del componente *App* de la siguiente manera y también refactoriza la aplicación para que siga funcionando:

Código:

    const App = () => {
    const course = 'Half Stack application development'
    const part1 = {
        name: 'Fundamentals of React',
        exercises: 10
    }
    const part2 = {
        name: 'Using props to pass data',
        exercises: 7
    }
    const part3 = {
        name: 'State of a component',
        exercises: 14
    }

    return (
        <div>
        ...
        </div>
    )
    }

Ejercicio resuelto:

    const App = () => {
    const course = 'Half Stack application development'
    const part1 = {
        name: 'Fundamentals of React',
        exercises: 10
    }
    const part2 = {
        name: 'Using props to pass data',
        exercises: 7
    }
    const part3 = {
        name: 'State of a component',
        exercises: 14
    }

    const Header = ({ course }) => {
        return <h1>{course}</h1>}

    const Part = ({name, exercises}) => {
        return<p>{name} {exercises}</p>}

    const Content = ({part1, part2, part3}) => {
        return (
        <>
            <Part name={part1.name} exercises={part1.exercises} />
                    <Part name={part2.name} exercises={part2.exercises} />
                    <Part name={part3.name} exercises={part3.exercises} />
        </>
        )
    }

    const Total = ({total}) => {
        return<p>Number of exercises {total}</p>}

    return (
        <div>
        <Header course={course} />
        <Content part1={part1} part2={part2} part3={part3}/>
        <Total total={part1.exercises + part2.exercises + part3.exercises}/>
        </div>
    )
    }

    export default App

### **1.4: Información del Curso paso 4**

Coloca los objetos en un array. Modifica las definiciones de las variables de *App* de la siguiente forma y modifica las otras partes de la aplicación que sean necesarias para que continue funcionando:

Código:

    const App = () => {
    const course = 'Half Stack application development'
    const parts = [
        {
        name: 'Fundamentals of React',
        exercises: 10
        },
        {
        name: 'Using props to pass data',
        exercises: 7
        },
        {
        name: 'State of a component',
        exercises: 14
        }
    ]

    return (
        <div>
        ...
        </div>
    )
    }

**Nota:** en este punto *puedes asumir que siempre hay tres elementos*, por lo que no es necesario pasar por los arrays usando bucles. Volveremos al tema de la renderización de componentes basados en elementos dentro de arrays con una exploración más profunda en la [siguiente parte del curso](https://fullstackopen.com/es/part2).

Sin embargo, no pases diferentes objetos como props separados del componente *App* a los componentes *Content* y *Total*. En su lugar, pásalos directamente como un array:

const App = () => {
  // definiciones de const

  return (
    <div>
      <Header course={course} />
      <Content parts={parts} />
      <Total parts={parts} />
    </div>
  )
}

Ejercicio resuelto: 

const App = () => {
  const course = 'Half Stack application development'
  const parts = [
    {
      name: 'Fundamentals of React',
      exercises: 10
    },
    {
      name: 'Using props to pass data',
      exercises: 7
    },
    {
      name: 'State of a component',
      exercises: 14
    }
  ]
  
  const Header = ({ course }) => {
    return <h1>{course}</h1>
  }

  const Part = ({ part }) => {
    return <p>{part.name} {part.exercises}</p>
  }

  const Content = ({ parts }) => {
    return (
      <>
        <Part part={parts[0]} />
        <Part part={parts[1]} />
        <Part part={parts[2]} />
      </>
    )
  }

  const Total = ({ parts }) => {
    const totalExercises = parts[0].exercises + parts[1].exercises + parts[2].exercises
    return <p>Number of exercises {totalExercises}</p>
  }
  
  return (
    <div>
      <Header course={course} />
      <Content parts={parts} />
      <Total parts={parts} />
    </div>
  )
}

export default App

### **1.5: Información del Curso paso 5**

Llevemos los cambios un paso más allá. Cambia el curso y sus partes a un solo objeto JavaScript. Arregla todo lo que se rompa.

const App = () => {
  const course = {
    name: 'Half Stack application development',
    parts: [
      {
        name: 'Fundamentals of React',
        exercises: 10
      },
      {
        name: 'Using props to pass data',
        exercises: 7
      },
      {
        name: 'State of a component',
        exercises: 14
      }
    ]
  }

  return (
    <div>
      ...
    </div>
  )
}