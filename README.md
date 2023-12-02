//Programa Creado por: Cristian Jesus Garcia Tapia
import Foundation

struct Producto {
    var nombre: String
    var cantidad: Int
}

class Inventario {
    var productos: [Producto] = []

    func mostrarMenu() {
        print("Menú:")
        print("1. Registrar un artículo")
        print("2. Ver la lista de artículos")
        print("3. Consultar los artículos en existencia")
        print("4. Salir")

        if let opcion = readLine() {
            switch opcion {
            case "1":
                registrarArticulo()
            case "2":
                verListaArticulos()
            case "3":
                consultarArticulos()
            case "4":
                print("¡Hasta luego!")
            default:
                print("Opción inválida")
                mostrarMenu()
            }
        }
    }

    func registrarArticulo() {
        print("Por favor, ingrese la cantidad de artículos que desea ingresar:")
        if let cantidadString = readLine(), let cantidad = Int(cantidadString) {
            for _ in 1...cantidad {
                print("Ingrese el nombre del artículo:")
                if let nombre = readLine() {
                    print("Ingrese la cantidad del artículo:")
                    if let cantidadString = readLine(), let cantidad = Int(cantidadString) {
                        let producto = Producto(nombre: nombre, cantidad: cantidad)
                        productos.append(producto)
                    } else {
                        print("Cantidad inválida")
                    }
                } else {
                    print("Nombre inválido")
                }
            }
        } else {
            print("Cantidad inválida")
        }

        mostrarMenu()
    }

    func verListaArticulos() {
        print("Listado de Productos:")
        for producto in productos {
            print("\(producto.nombre) - Cantidad: \(producto.cantidad)")
        }

        mostrarMenu()
    }

    func consultarArticulos() {
        print("Artículos registrados:")
        for producto in productos {
            print("\(producto.nombre)")
        }

        mostrarMenu()
    }
}

let inventario = Inventario()
inventario.mostrarMenu()
