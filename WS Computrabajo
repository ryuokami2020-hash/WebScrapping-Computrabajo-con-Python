from webdriver_manager.chrome import ChromeDriverManager
from selenium import webdriver
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.common.by import By
import time
import os 
import csv

def webscraping():
    service = Service(ChromeDriverManager().install())
    option = Options()
    option.add_argument("--window-size=1920,1080")
    driver = webdriver.Chrome(service=service, options=option)
    listaOfertas = []
    
    print("Accediendo a Computrabajo...")
    driver.get("https://pe.computrabajo.com/trabajo-de-ingeniero-sistemas") #Se coloca /"Trabajo q quieres buscar"
    time.sleep(3) 

    tarjetas = driver.find_elements(By.CSS_SELECTOR, "a.js-o-link")
    listaLinks = []
    for elemento in tarjetas:
        url = elemento.get_attribute("href")
        if url:
            listaLinks.append(url)
            
    print(f"Se han encontrado {len(listaLinks)} ofertas. Iniciando extracción...")

    for i, url in enumerate(listaLinks):
        print(f"\n--- Procesando oferta {i+1} ---")
        driver.get(url)
        time.sleep(3)
        try:
            titulo = driver.find_element(By.CSS_SELECTOR, "h1.fwB.fs24").text.strip()
            empresaUbicacion = driver.find_element(By.XPATH, "/html/body/main/div[1]/p").text.strip()
            partes = empresaUbicacion.split(" - ", 1)
            empresa = partes[0].strip()
            ubicacion = partes[1].strip()
            salario = driver.find_element(By.CSS_SELECTOR, "span.tag.base.mb10").text.strip()
            oferta = {
                "Titulo": titulo,
                "Empresa": empresa,
                "Ubicacion": ubicacion,
                "Salario": salario
            }
            listaOfertas.append(oferta)
            print(oferta)
        except Exception as e:
            print(f"No se pudieron extraer los datos de esta oferta: {e}")
        driver.back()
        time.sleep(3)
        

    print("\nProceso finalizado.")
    print(f"{listaOfertas}")
    driver.quit()
    return listaOfertas
    
    
def archivoTexto(datos_recibidos):
    
    rutaCarpeta = r"C:\Users\(Usuario)\Downloads" #Ruta donde se va a exportar los datos
    nombreArchivo = "ListaTrabajo.csv"
    rutaArchivo = os.path.join(rutaCarpeta, nombreArchivo)
    
    if not os.path.exists(rutaCarpeta):
        os.makedirs(rutaCarpeta)
    
    with open(rutaArchivo, 'w',newline='', encoding='utf-8-sig') as archivoSalida:
        writer = csv.writer(archivoSalida)
        writer.writerow(["Titulo", "Empresa", "Ubicacion", "Salario"])
        for oferta in datos_recibidos: 
            writer.writerow([oferta["Titulo"], oferta["Empresa"], oferta["Ubicacion"], oferta["Salario"]])
    print(f"Archivo guardado en: {rutaArchivo}")
        
    
    
if __name__ == "__main__":
    print("Iniciando programa...")
    resultado_extraccion = webscraping()
    archivoTexto(resultado_extraccion)
    print("Programa finalizado.")
