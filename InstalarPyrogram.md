O `pyrotgfork` é uma versão modificada do Pyrogram, focada em fornecer funcionalidades relacionadas ao **Telegram**. Vou te guiar no passo a passo para instalar o `pyrotgfork` via `pip` na sua instância EC2.

### Passo 1: Conecte-se à sua instância EC2

Primeiro, se ainda não estiver conectado à sua instância EC2, use o comando SSH para se conectar.

1. Abra o terminal e digite:

	```bash
	ssh -i /path/to/your-key.pem ec2-user@<endereço-ip-publico>
	```

	- **/path/to/your-key.pem**: Caminho para sua chave privada (.pem).
	- **<endereço-ip-publico>**: O endereço IP público da sua instância EC2.

### Passo 2: Atualize os pacotes da sua instância (opcional, mas recomendado)

É sempre bom garantir que sua instância EC2 esteja atualizada. Execute os seguintes comandos, dependendo da distribuição do seu sistema.

#### Para **Amazon Linux 2** ou **Red Hat/CentOS**:

```bash
sudo yum update -y
```

#### Para **Ubuntu**:

```bash
sudo apt update && sudo apt upgrade -y
```

### Passo 3: Verificar se o `pip` está instalado

O `pip` é o gerenciador de pacotes para Python, e você precisa dele para instalar pacotes como o `pyrotgfork`.

1. Verifique se o `pip` já está instalado:

	```bash
	pip3 --version
	```

	Se não estiver instalado, você pode instalá-lo com o seguinte comando:

	- Para **Amazon Linux 2** ou **Red Hat/CentOS**:

  	```bash
  	sudo yum install python3-pip -y
  	```

	- Para **Ubuntu**:

  	```bash
  	sudo apt install python3-pip -y
  	```

### Passo 4: Instalar o `pyrotgfork` via `pip`

Agora que o `pip` está instalado, você pode instalar o `pyrotgfork`. O comando para fazer isso é:

```bash
pip3 install pyrotgfork
```

Isso fará o download e a instalação do `pyrotgfork` diretamente do PyPI (Python Package Index).

### Passo 5: Verificar a instalação

Após a instalação, você pode verificar se o `pyrotgfork` foi instalado corretamente executando o seguinte comando no Python:

1. Abra o Python no terminal:

	```bash
	python3
	```

2. No prompt interativo do Python, tente importar o `pyrotgfork`:

	```python
	import pyrotgfork
	print(pyrotgfork.__version__)
	```

Se não houver erros e a versão do `pyrotgfork` for exibida, a instalação foi bem-sucedida.

### Passo 6: Instalar Dependências Adicionais (se necessário)

Se o `pyrotgfork` tiver dependências adicionais, como bibliotecas para criptografia ou outras funções, o `pip` pode instalar automaticamente essas dependências. Caso contrário, você pode precisar instalar pacotes extras, como o `tgcrypto` (que acelera a criptografia) para melhorar o desempenho da biblioteca.

Para instalar o `tgcrypto`, execute o seguinte comando:

```bash
pip3 install tgcrypto
```

### Passo 7: Testar a instalação do `pyrotgfork` (opcional)

Para garantir que o `pyrotgfork` está funcionando corretamente, você pode escrever um pequeno script para testar sua funcionalidade. Aqui está um exemplo básico de script Python que inicializa um cliente do Telegram com `pyrotgfork`:

1. Crie um arquivo chamado `test_pyrotgfork.py`:

	```bash
	nano test_pyrotgfork.py
	```

2. Adicione o seguinte código:

	```python
	from pyrotgfork import Client

	app = Client("my_account")

	@app.on_message()
	def handle(client, message):
    	print(f"Mensagem recebida: {message.text}")

	app.run()
	```

**Nota:** Para usar a API do Telegram, você precisa fornecer um **API ID** e um **API Hash**. Para isso, crie um aplicativo no [site do Telegram](https://my.telegram.org/auth) para obter essas credenciais.

3. Execute o script:

	```bash
	python3 test_pyrotgfork.py
	```

Se tudo estiver configurado corretamente, o script iniciará o cliente e imprimirá as mensagens recebidas.

### Passo 8: (Opcional) Usar um Ambiente Virtual para Isolamento

Se você deseja isolar o ambiente do Python para evitar conflitos com outros pacotes, você pode criar um ambiente virtual para instalar o `pyrotgfork`.

1. Instale o `virtualenv` (se ainda não o tiver):

	```bash
	pip3 install virtualenv
	```

2. Crie um novo ambiente virtual:

	```bash
	virtualenv myenv
	```

3. Ative o ambiente virtual:

	- Para **Linux/macOS**:

  	```bash
  	source myenv/bin/activate
  	```

	- Para **Windows**:

  	```bash
  	myenv\Scripts\activate
  	```

4. Dentro do ambiente virtual, instale o `pyrotgfork`:

	```bash
	pip install pyrotgfork
	```

5. Quando terminar de usar o ambiente virtual, basta desativá-lo com:

	```bash
	deactivate
	```

---

Agora você tem o `pyrotgfork` instalado e pronto para ser usado na sua instância EC2! Se precisar de mais ajuda para configurar ou usar o `pyrotgfork`, estou à disposição!
