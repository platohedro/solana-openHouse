# Solana Open house

Sesiones dirigidas por Alex ramírez 

Instalar solana y el cli en linux:

* usar terminal bash "recomendado"

~~~
sh -c "$(curl -sSfL https://release.solana.com/v1.16.4/install)"
~~~

luego creamos un alias para activar el comando solana en la terminal 

~~~
nano ~/.bashrc
~~~

al final de documento agregamos la sigueinte linea

~~~
alias neas='export PATH="/home/noisk8/.local/share/solana/install/active_release/bin:$PATH"'
~~~

con esto podemos escribir neas y se activara el comando solana 


luego instalamos el  cli, para esto debemos de tener rust instalado 

instalando rust 
~~~
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
~~~

instlando spl token cli 

~~~
cargo install spl-token-cli
~~~


Luego de tener esto instalado pasamos a ver la configuración de solana 

~~~
solana config get 
~~~

el resulatdo es algo cómo esto 

~~~
Config File: /home/noisk8/.config/solana/cli/config.yml
RPC URL: https://api.mainnet-beta.solana.com 
WebSocket URL: wss://api.mainnet-beta.solana.com/ (computed)
Keypair Path: /home/noisk8/.config/solana/id.json 
Commitment: confirmed 
~~~

Esto nos indica que: la configuración está apuntando al mainet, pero para este ejercicio queremos trabajar sobre la dev net pero antes debemos de generar una llave publica y una privada

~~~
solana-keygen  new --outfile /home/noisk8/.config/solana/id.json 
~~~
esto nos arrojara las 12 palanras que debemos de guardar

para saber nuestra public key 

~~~
solana-keygen pubkey
~~~

para saber la llaver privada 

~~~
cat /home/noisk8/.config/solana/id.json
~~~


para cambiar nuestro entorno a la dev net 

~~~
solana config set --url https://api.devnet.solana.com
~~~

## ¡Creemos programas en Solana!

Primero, deberemos descargar "Anchor". Anchor es un framework para crear contratos inteligentes (programas) en Solana.

También tenemos "Seahorse". Seahorse es un framework que permite crear contratos inteligentes (programas) usando el lenguaje de programación Python.

Para instalar Anchor con cargo, ejecuta el siguiente comando:

~~~
cargo install --git https://github.com/coral-xyz/anchor avm --locked --force
~~~

Te pedirá que actualices Anchor a la versión más reciente, puedes hacerlo a través de este comando:

~~~
avm install 0.28.0
~~~

Luego, ¡Estaremos listxs para crear un nuevo proyecto con Anchor!

~~~
anchor init my_project
~~~

Este comando te creará un nuevo proyecto de Rust llamado my_project

Luego, estaremos listos para compilar nuestro proyecto. Ejecute el siguiente comando:

~~~
anchor build
~~~

Luego, inicia un nodo local de Solana con:

~~~
solana-test-validator
~~~

Ahora, vamos a desplegar nuestro contrato inteligente en nuestro nodo local:

~~~
anchor deploy
~~~

¡Listo, ya tendremos nuestro contrato inteligente en nuestro nodo local!
