# Tienda
actividad grupal

import ipywidgets as widgets
from IPython.display import display, clear_output

# Título del formulario
titulo = widgets.HTML("<h2>REGISTRO DE PRODUCTOS</h2>")

# Campos de entrada
txt_producto = widgets.Text(
    description="Producto:",
    placeholder="Escriba el nombre"
)

txt_precio = widgets.FloatText(
    description="Precio (Bs):",
    value=0.0
)

txt_cantidad = widgets.IntText(
    description="Cantidad:",
    value=1
)

# Botón para registrar
btn_registrar = widgets.Button(
    description="Registrar",
    button_style="success",
    icon="check"
)

# Área de resultados
salida = widgets.Output()

# Función para registrar el producto
def registrar_producto(b):
    with salida:
        clear_output(wait=True)

        producto = txt_producto.value.strip()
        precio = txt_precio.value
        cantidad = txt_cantidad.value

        if not producto:
            print("Error: escriba el nombre del producto.")
            return

        if precio < 0 or cantidad <= 0:
            print("Error: revise el precio y la cantidad.")
            return

        total = precio * cantidad

        print("PRODUCTO REGISTRADO")
        print("------------------------------")
        print(f"Producto: {producto}")
        print(f"Precio unitario: {precio:.2f} Bs")
        print(f"Cantidad: {cantidad}")
        print(f"Total: {total:.2f} Bs")

# Asociar el botón con la función
btn_registrar.on_click(registrar_producto)

# Mostrar el formulario
display(
    titulo,
    txt_producto,
    txt_precio,
    txt_cantidad,
    btn_registrar,
    salida
)
