# ML_Coches-de-segunda-mano

## Descripción
Debido a los cambios actuales en el mercado automovilístico en España, este proyecto trata de establecer el precio de coches de segunda mano según sus características y estado de desgaste, proporcionando una guía sobre la que estimar el coste.


Los datos han sido obtenidos de DataMarket, contando con los anuncios de las principales páginas de venta de coches de segunda mano. Los datos son principalmente del año 2023, e incluyen la siguiente información:
- color: Color del vehículo.
- currency: Moneda en la que está definido el precio del vehículo.
- date: Fecha de extracción de la información.
- dealer_address: Dirección del anunciante.
- dealer_city: Ciudad del anunciante.
- dealer_country_code: Código de país del anunciante
- dealer_description: Descripción del anunciante.
- dealer_is_professional: Determina si el anunciante es o no profesional.
- dealer_name: Vendedor del vehículo. En el caso de vendedores particulares (no concesionarios), esta información está encriptada en el dataset para cumplir con la GDPR.
- dealer_registered_at: Fecha de registro del anunciante en la plataforma.
- dealer_website: Página web del anunciante.
- dealer_zip_code: Código postal del anunciante.
- description: Descripción presente en el anuncio del vehículo.
- doors: Número de puertas del vehículo.
- fuel: Tipo de combustible del vehículo (diésel, gasolina, eléctrico, híbrido).
- is_professional: Indica si el vendedor es profesional (un concesionario).
- kms: Kilometraje del vehículo.
- location: Ciudad en la que se ha publicado el anuncio.
- make: Marca del vehículo.
- model: Modelo del vehículo.
- photos: Número de fotos del vehículo disponibles en el anuncio.
- power: Potencia del vehículo.
- price: Precio de venta del vehículo.
- publish_date: Fecha de publicación del anuncio.
- shift: Tipo de cambio (Automático/Manual).
- update_date: Fecha de actualización del anuncio.
- vehicle_type: Tipo de vehículo: coche, moto...
- version: Versión del vehículo.
- year: Año de fabricación del vehículo.


Utiliza Machine Learning para predecir el valor. Se ha implementado un modelo de regresión basado en **RandomForestRegressor**, ya que proporcionó los mejores resultados en pruebas, aunque se sigue intentando mejorar el resultado de sus predicciones.

## Estructura del Proyecto
```
/
|-- src/data_sample/              # Contiene los datos crudos y procesados
|-- src/notebooks/                # Jupyter Notebooks con el análisis y entrenamientos de diferentes modelos
|-- src/results_notebooks/        
|   |-- results_notebook.ipynb    # Script que explica el proceso de preparado de las variables y entrena el modelo definitivo
|   |-- train.ipynb               # Script para hacer predicciones
|   |-- predict.ipynb             # Script para hacer predicciones
|-- src/models/                   # Modelos entrenados guardados
|-- src/utils/                    # Contiene archivos de utilidad (funciones de visualización, etc.)
|-- requirements.txt              # Librerías necesarias para el proyecto
|-- README.md                     # Documentación
```

## Instalación
Para ejecutar el proyecto, asegúrese de tener instalado Python (>=3.8) y las siguientes librerías:

```bash
pip install -r requirements.txt
```

## Uso
1. Clonar el repositorio:

```bash
git clone https://github.com/tu_usuario/tu_repositorio.git
cd tu_repositorio
git lfs install
git lfs pull
```

2. Ejecutar el Jupyter Notebook para el entrenamiento y la predicción:

```bash
jupyter notebook
```

Abrir `notebooks/model_training.ipynb` y seguir las instrucciones.


## Modelo
Se ha utilizado un **RandomForestRegressor** de `scikit-learn`.
Las principales características del modelo son:
- Entrenado con un dataset de coches de segunda mano con atributos como: marca, modelo, año, kilometraje, combustible, cambio, etc.
- Se han ajustado hiperparámetros mediante `GridSearchCV` para mejorar el rendimiento.

## Ejemplo de Uso
Puedes hacer predicciones con el modelo guardado ejecutando:

```python
from src.predict import load_model, predict_price

model = load_model("models/random_forest.pkl")
car_features = {
    "year": 2018,
    "mileage": 50000,
    "fuel": "Gasoline",
    "transmission": "Automatic",
    "brand": "Toyota",
    "model": "Corolla"
}

price = predict_price(model, car_features)
print(f"Precio estimado: ${price:.2f}")
```

## Contribuciones
Si deseas contribuir, puedes abrir un **pull request** o reportar problemas en la sección de **issues**.

## Licencia
Este proyecto está bajo la licencia MIT.

