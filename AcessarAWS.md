Para **subir um arquivo** para a sua instância EC2, você pode usar **SCP (Secure Copy Protocol)**, uma ferramenta que permite transferir arquivos de forma segura entre o seu computador local e a instância EC2. O SCP é uma ferramenta de linha de comando que utiliza SSH para transferência de arquivos.


Aqui está o passo a passo para fazer isso:


### Passo 1: Verifique o IP público da sua Instância EC2
1. Acesse o **Console de EC2** na AWS.
2. Na lista de instâncias, encontre sua instância e **anote o IP público** (IPv4) dela. Esse é o IP que você usará para se conectar à instância.


### Passo 2: Garanta que a chave privada (.pem) está configurada corretamente
- Certifique-se de que o arquivo de chave privada (**.pem**) que você usou para criar a instância está acessível no seu computador local. Esse arquivo é necessário para autenticação.


### Passo 3: Conecte-se à sua instância EC2 via SSH
Antes de usar o SCP, verifique se você consegue se conectar à sua instância EC2 usando SSH:


1. Abra o terminal (ou o **Prompt de Comando**, se estiver usando Windows com ferramentas como o **Git Bash** ou **PuTTY**).
2. Use o seguinte comando para conectar à sua instância EC2 via SSH:
   ```bash
   ssh -i /path/to/your-key.pem ec2-user@<endereço-ip-publico>
   ```
   Substitua `/path/to/your-key.pem` pelo caminho para o arquivo de chave privada e `<endereço-ip-publico>` pelo IP público da sua instância EC2.


3. Se a conexão for bem-sucedida, você estará logado na sua instância EC2.


### Passo 4: Subir um arquivo usando SCP
Agora que você está pronto para transferir arquivos, você pode usar o **SCP** para transferir um arquivo local para sua instância EC2.


1. No terminal do seu computador, use o seguinte comando para copiar o arquivo para a instância EC2:
   ```bash
   scp -i /path/to/your-key.pem /path/to/local/file ec2-user@<endereço-ip-publico>:/home/ec2-user/
   ```
   - **`/path/to/your-key.pem`**: O caminho para a sua chave privada (.pem).
   - **`/path/to/local/file`**: O caminho do arquivo no seu computador local que você deseja transferir.
   - **`<endereço-ip-publico>`**: O IP público da sua instância EC2.
   - **`/home/ec2-user/`**: O diretório de destino onde você deseja que o arquivo seja salvo na instância EC2 (geralmente o diretório inicial do usuário `ec2-user`).


### Exemplo:
Suponha que você tem um arquivo chamado `meuarquivo.txt` na pasta `/home/usuario/Documentos` no seu computador local, e você quer copiá-lo para a instância EC2:


```bash
scp -i /home/usuario/.ssh/minha-chave.pem /home/usuario/Documentos/meuarquivo.txt ec2-user@54.123.45.67:/home/ec2-user/
```


### Passo 5: Verifique a transferência na instância EC2
Após a transferência ser concluída, você pode verificar se o arquivo foi enviado corretamente:


1. Acesse a instância EC2 via SSH (caso não esteja conectado ainda):
   ```bash
   ssh -i /path/to/your-key.pem ec2-user@<endereço-ip-publico>
   ```
   
2. Navegue até o diretório onde você enviou o arquivo (por exemplo, `/home/ec2-user/`):
   ```bash
   ls
   ```
   O arquivo que você transferiu deverá aparecer na lista de arquivos.


### Passo 6: Permissões (se necessário)
Se, por algum motivo, você não conseguir acessar o arquivo na instância EC2 (por exemplo, se houver problemas de permissão), você pode corrigir isso alterando as permissões com o comando `chmod`:


1. Na instância EC2, execute o seguinte comando para garantir que o arquivo tenha permissões adequadas:
   ```bash
   chmod 644 /home/ec2-user/meuarquivo.txt
   ```


### Passo 7: Usando o WinSCP (Windows)
Se você estiver no **Windows**, o SCP pode não ser nativamente disponível. Nesse caso, você pode usar uma ferramenta gráfica como o **WinSCP** para transferir arquivos.


1. **Baixe o WinSCP**: Vá até o [site oficial do WinSCP](https://winscp.net/) e faça o download.
2. **Configuração no WinSCP**:
   - **Protocólo**: Escolha **SFTP** (que usa SSH).
   - **Host**: Insira o **IP público** da sua instância EC2.
   - **Nome de usuário**: Use `ec2-user` (para instâncias Amazon Linux) ou `ubuntu` (para instâncias Ubuntu).
   - **Chave privada**: Selecione o arquivo **.pem** da chave privada que você gerou.
   
3. **Conectar**: Clique em **Login** e você poderá arrastar e soltar arquivos entre seu computador local e a instância EC2.


---


Esses são os passos principais para subir arquivos para sua instância EC2. Se precisar de mais detalhes ou enfrentar algum erro específico, é só me avisar!

