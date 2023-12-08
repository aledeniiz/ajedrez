# ajedrez
https://github.com/aledeniiz/ajedrez
def guardar_tablero(tablero, nombre_archivo, primera_vez):
    if primera_vez==True:
        with open(nombre_archivo, 'w') as archivo:
            for fila in tablero:
                fila_str = '\t'.join(fila)  
                archivo.write(fila_str + '\n')
            archivo.write('\n')
    else:
        with open(nombre_archivo, 'a') as archivo:
            for fila in tablero:
                fila_str = '\t'.join(fila) 
                archivo.write(fila_str + '\n')
            archivo.write('\n')    
    



def mostrar_tablero(tablero):
    print(tablero)


def construir_tablero(tablero):
    tablero= [["Torreblanca1", "Caballoblanco1", "Alfilblanco1", "Reinablanca", "Reyblanco", "Alfilblanco2", "Caballoblanco2", "Torreblanca2"], 
              ["Peonblanco1", "Peonblanco2", "Peonblanco3", "Peonblanco4", "Peonblanco5", "Peonblanco6", "Peonblanco7", "Peonblanco8"], 
              ["", "", "", "", "", "", "", ""], 
              ["", "", "", "", "", "", "", ""], 
              ["", "", "", "", "", "", "", ""], 
              ["", "", "", "", "", "", "", ""], 
              ["Peonnegro1", "Peonnegro2", "Peonnegro3", "Peonnegro4", "Peonnegro5", "Peonnegro6", "Peonnegro7", "Peonnegro8"], 
              ["Torrenegra1", "Caballonegro1", "Alfilnegro1", "Reinanegra", "Reynegro", "Alfilnegro2", "Caballonegro2", "Torrenegra2"]]

    return tablero

def realizar_movimiento(tablero, fila_origen, col_origen, fila_destino, col_destino):
    
    nuevo_tablero = tablero
    pieza = nuevo_tablero[fila_origen][col_origen]
    nuevo_tablero[fila_origen][col_origen]=""
    nuevo_tablero[fila_destino][col_destino]=pieza
    return nuevo_tablero


def pedirdato(texto):
    dato=-1
    while dato<0 or dato>7:
        dato = int(input(texto))
    return dato

def preguntar_movimiento(movimientos):
    respuesta=-1
    pregunta="¿Qué movimiento desea ver? (0-" +str(movimientos)+ "): "        
    while respuesta<1 or respuesta>movimientos:
        respuesta = int(input(pregunta))
    return respuesta

def main():
    tablero=[];
    movimientos=0
    nombre_archivo = input("Introduce el nombre del archivo para guardar la partida: ")
    tablero = construir_tablero(tablero)
    guardar_tablero(tablero, nombre_archivo, True)

    continuar_partida = True
    while continuar_partida:
        mostrar_tablero(tablero)

        fila_origen = pedirdato("Introduce la fila de la pieza que quieres mover: ")
        col_origen = pedirdato("Introduce la columna de la pieza que quieres mover: ")
        fila_destino = pedirdato("Introduce la fila a la que quieres mover la pieza: ")
        col_destino = pedirdato("Introduce la columna a la que quieres mover la pieza: ")


        tablero = realizar_movimiento(tablero, fila_origen, col_origen, fila_destino, col_destino)
        movimientos+=1
        guardar_tablero(tablero, nombre_archivo, False)

        respuesta = input("¿Quieres hacer otro movimiento? (Sí/No): ")
        if respuesta.lower() != 'si':
            continuar_partida = False
    movimiento_a_mostrar=preguntar_movimiento(movimientos)

    #mostrar_movimiento(nombre_archivo, movimiento_a_mostrar)
    


if __name__ == "__main__":
    main()
    


#Intenté hacer una función que mostrara el movimiento guardado pero no me salió.
