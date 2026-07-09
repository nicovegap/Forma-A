NOTA_MINIMA_APROBACION = 4.0


def validar_nombre(nombre):
    return len(nombre.strip()) > 0


def validar_edad(valor):
    try:
        edad = int(valor)
        return edad > 0
    except ValueError:
        return False


def validar_nota(valor):
    try:
        nota = float(valor)
        return 1.0 <= nota <= 7.0
    except ValueError:
        return False


def mostrar_menu():
    print()
    print("========== MENU PRINCIPAL ==========")
    print("1. Agregar estudiante")
    print("2. Buscar estudiante")
    print("3. Eliminar estudiante")
    print("4. Actualizar estados")
    print("5. Mostrar estudiantes")
    print("6. Salir")
    print("=====================================")


def leer_opcion():
    while True:
        entrada = input("Ingrese una opcion (1-6): ").strip()
        if entrada.isdigit():
            opcion = int(entrada)
            if 1 <= opcion <= 6:
                return opcion
        print("Opcion invalida. Ingrese un numero del 1 al 6.")


def agregar_estudiante(lista):
    print("\n--- Agregar Estudiante ---")

    nombre = input("Ingrese el nombre: ")
    if not validar_nombre(nombre):
        print("Error: el nombre no puede estar vacio ni contener solo espacios.")
        return

    edad = input("Ingrese la edad: ")
    if not validar_edad(edad):
        print("Error: la edad debe ser un numero entero mayor que cero.")
        return

    nota = input("Ingrese la nota (1.0 - 7.0): ")
    if not validar_nota(nota):
        print("Error: la nota debe ser un numero decimal entre 1.0 y 7.0.")
        return

    estudiante = {
        "nombre": nombre.strip(),
        "edad": int(edad),
        "nota": float(nota),
        "aprobado": False
    }

    lista.append(estudiante)
    print("Estudiante agregado correctamente.")


def buscar_posicion(lista, nombre):
    for i in range(len(lista)):
        if lista[i]["nombre"] == nombre:
            return i
    return -1


def buscar_estudiante(lista):
    print("\n--- Buscar Estudiante ---")
    nombre = input("Ingrese el nombre a buscar: ")
    posicion = buscar_posicion(lista, nombre)

    if posicion != -1:
        estudiante = lista[posicion]
        print(f"Estudiante encontrado en la posicion {posicion}.")
        print(f"Nombre: {estudiante['nombre']}")
        print(f"Edad: {estudiante['edad']}")
        print(f"Nota: {estudiante['nota']}")
        estado = "APROBADO" if estudiante["aprobado"] else "REPROBADO"
        print(f"Estado: {estado}")
    else:
        print(f"El estudiante '{nombre}' no se encuentra registrado.")


def eliminar_estudiante(lista):
    print("\n--- Eliminar Estudiante ---")
    nombre = input("Ingrese el nombre del estudiante a eliminar: ")
    posicion = buscar_posicion(lista, nombre)

    if posicion != -1:
        lista.pop(posicion)
        print(f"El estudiante '{nombre}' ha sido eliminado.")
    else:
        print(f"El estudiante '{nombre}' no se encuentra registrado.")


def actualizar_estados(lista):
    for estudiante in lista:
        if estudiante["nota"] >= NOTA_MINIMA_APROBACION:
            estudiante["aprobado"] = True
        else:
            estudiante["aprobado"] = False


def mostrar_estudiantes(lista):
    actualizar_estados(lista)

    if len(lista) == 0:
        print("\nNo hay estudiantes registrados.")
        return

    print("\n=== LISTA DE ESTUDIANTES ===")
    for estudiante in lista:
        estado = "APROBADO" if estudiante["aprobado"] else "REPROBADO"
        print(f"Nombre: {estudiante['nombre']}")
        print(f"Edad: {estudiante['edad']}")
        print(f"Nota: {estudiante['nota']}")
        print(f"Estado: {estado}")
        print("********************************************")


def main():
    estudiantes = []

    while True:
        mostrar_menu()
        opcion = leer_opcion()

        if opcion == 1:
            agregar_estudiante(estudiantes)
        elif opcion == 2:
            buscar_estudiante(estudiantes)
        elif opcion == 3:
            eliminar_estudiante(estudiantes)
        elif opcion == 4:
            actualizar_estados(estudiantes)
            print("Estados actualizados correctamente.")
        elif opcion == 5:
            mostrar_estudiantes(estudiantes)
        elif opcion == 6:
            print("Gracias por usar el sistema. Vuelva Pronto")
            break


if __name__ == "__main__":
    main()
