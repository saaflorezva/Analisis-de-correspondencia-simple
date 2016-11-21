# Seminario
#ANALISIS DE CORREPONDENCIA SIMPLE(AC)
#Paquetes necesarios

     library("FactoMineR")
     library("factoextra")
     library(ca)

#Cargar base de datos
BD = read.csv2("D:/Especialización Estadistica/Semestre II/Seminario de Investigación/Tesis/BD/Bd filtradas/No biopsia/No_biopsia.csv")
 
     str(BD)
     attach(BD)

#Definir variables de interés para el cálculo del AC

    no.mamografia <- table(BD[,c(39,5)])
#Mostrar los primeros 6 datos de las variables seleccionadas para el AC

    head(no.mamografia)
#Generar estadísticos básicos de las variables de interés

    summary(no.mamografia)

#Función del AC

    res.ca <- CA(no.mamografia, graph = FALSE)
    print(res.ca)

#Imprimir un resumen de los resultados del AC

    summary(res.ca, nb.dec = 2, ncp = 2,nbelements = Inf)

#Proporciona las varianzas retenidas por las diferentes dimensiones (ejes)

    eigenvalues <- get_eigenvalue(res.ca)
    head(round(eigenvalues, 2))

#Grafica las coordenadas de filas y columnas presentadas en la salida del AC
     
	 fviz_ca_biplot(res.ca) +   
         theme_minimal()+    
    	  ggtitle("")
      row <- get_ca_row(res.ca)
