<script>
    import CodeBlock from "svelte-highlight";
	import Card from "./lib/Card.svelte";
	import Column from "./layouts/Column.svelte";

	import Python from "svelte-highlight/languages/python";
	import Monokai from "svelte-highlight/styles/monokai";
</script>

<svelte:head>
	{@html Monokai}
</svelte:head>

<div class="content">
	<Card>
		<Column padding="20px" justifyContent="flex-start">
		<h2>Variables</h2>
		<CodeBlock language={Python}
			code={`nombre = "Juan"`}
		/>
		<CodeBlock language={Python}
			code={`x = 5
y = 20`}
		/>
		<CodeBlock language={Python}
			code={`ganador = True`}
		/>
		</Column>
	</Card>
	<Card>
		<Column padding="20px" justifyContent="flex-start">
		<h2>Salida</h2>
		<CodeBlock language={Python}
			code={`print("¡Hola Mundo!")`}
		/>
		<CodeBlock language={Python}
			code={`x = 5
y = 20
print(x + y)`}
		/>
		<CodeBlock language={Python}
			code={`nombre = "José"
print(f"¡Hola {nombre}!")`}
		/>
		</Column>
	</Card>
	<Card>
		<Column padding="20px" justifyContent="flex-start">
		<h2>Entrada</h2>
		<CodeBlock language={Python}
			code={`input("Presiona cualquier tecla para continuar. . .")`}
		/>
		<CodeBlock language={Python}
			code={`nombre = input("¿Cuál es tu nombre?")
print(f"¡Hola {nombre}!")`}
		/>
		<CodeBlock language={Python}
			code={`x = int(input("Dime el primer número"))
y = int(input("Dime el segundo número"))
print(x + y)`}
		/>
		</Column>
	</Card>
	<Card>
		<Column padding="20px" justifyContent="flex-start">
		<h2>Condicionales</h2>
		<CodeBlock language={Python}
			code={`contra = input("¿Cuál es la contraseña?")
if contra == "quesito254":
	print("Bienvenido")`}
		/>
		<CodeBlock language={Python}
			code={`nota = int(input("Dime tu nota"))
if nota > 70:
	print("Wow no reprobaste")
else:
	print("Jaja qué tonto")`}
		/>
		<CodeBlock language={Python}
			code={`animal = input("Dime un animal")
if animal == "Vaca":
	print("¡Muuuuuu!")
elif animal == "Gallo":
	print("¡Quiquiriquí!")
else:
	print("¿Qué animal es ese?")
	print("Digo que si no es gallo es gallina :V")`}
		/>
		</Column>
	</Card>
	<Card>
		<Column padding="20px" justifyContent="flex-start">
		<h2>Bucle <code>for</code></h2>
		<CodeBlock language={Python}
			code={`for numero in range(10):
	print(numero)`}
		/>
		<CodeBlock language={Python}
			code={` # Like si entendiste la referencia
for _ in range(10):
    print("ian")`}
		/>
		<CodeBlock language={Python}
			code={`import time

for i in range(500):
    print("La hamburguesa se está haciendo...")
    time.sleep(5)
    print("¡La hamburguesa está lista!")`}
		/>
		</Column>
	</Card>
	<Card>
		<Column padding="20px" justifyContent="flex-start">
		<h2>Bucle <code>while</code></h2>
		<CodeBlock language={Python}
			code={`while True:
    nombre = input("Nombre: ")
    print(f"¡Hola {nombre}!")`}
		/>
		<CodeBlock language={Python}
			code={`numero = 0
while numero < 10:
    print(numero)
    numero += 1`}
		/>
		<CodeBlock language={Python}
			code={`hay_clientes = True
while hay_clientes:
    print("¡Hola! ¿Qué desea ordenar?")
    pedido = input()
    if pedido == "":
        print("Parece que ya no hay más clientes")
        hay_clientes = False
    else:
        print("Su pedido estará listo pronto")`}
		/>
		</Column>
	</Card>
	<Card>
		<Column padding="20px" justifyContent="flex-start">
		<h2><code>break</code> y <code>continue</code></h2>
		<CodeBlock language={Python}
			code={`for numero in range(10):
    if numero == 6 or numero == 7:
        print("Ese número no se dice")
        continue
    print(numero)`}
		/>
		<CodeBlock language={Python}
			code={`numero = 1
while True:
    print(numero)
    numero += 1
    if numero > 100:
        print("Ok ya me harté")
        print("Puedes dejar de contar")
        break`}
		/>
		</Column>
	</Card>
	<Card>
		<Column padding="20px" justifyContent="flex-start">
		<h2>Funciones</h2>
		<CodeBlock language={Python}
			code={`def saludar():
	print("¡Hola mundo!")

saludar()`}
		/>
		<CodeBlock language={Python}
			code={`def funcion_secreta(numero):
	return (2 * numero) + 1

entrada = int(input())
print(funcion_secreta(entrada))`}
		/>
		<CodeBlock language={Python}
			code={`def mayor_o_menor(a, b):
	if a > b:
		return f"{a} es mayor a {b}"
	elif a == b:
		return f"{a} es igual a {b}"
	else a < b:
		return f"{a} es menor a {b}"
	
print(mayor_o_menor(2, 8))`}
		/>
		</Column>
	</Card>
</div>