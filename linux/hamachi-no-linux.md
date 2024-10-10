
## Hamachi VPN no Linux: Guia Completo de Instalação e Configuração

O **Hamachi** é um software de rede privada virtual (VPN) que permite criar conexões seguras entre dispositivos de diferentes redes locais. Embora o Hamachi seja popular em sistemas Windows, ele também pode ser instalado e configurado em distribuições Linux. Neste tutorial, você aprenderá como instalar o Hamachi no Linux, utilizando comandos simples.

### Passo 1: Baixar o Hamachi

Primeiramente, você deve baixar o Hamachi para Linux. A LogMeIn, empresa responsável pelo Hamachi, oferece uma versão para Linux no formato `.deb`, compatível com distribuições baseadas no Debian, como Ubuntu.

Abra o terminal e use o `wget` para baixar o pacote:

```bash
wget https://vpn.net/installers/logmein-hamachi_2.1.0.203-1_amd64.deb
```

Se você estiver usando uma versão de 32 bits, substitua o link acima pelo pacote correto para sua arquitetura.

### Passo 2: Instalar o Hamachi

Após o download, você pode usar o `dpkg` para instalar o Hamachi:

```bash
sudo dpkg -i logmein-hamachi_2.1.0.203-1_amd64.deb
```

Se houver dependências não satisfeitas, execute o seguinte comando para corrigir:

```bash
sudo apt install -f
```

### Passo 3: Iniciar o Hamachi

Para iniciar o daemon do Hamachi no Linux, você precisará do comando:

```bash
sudo hamachi login
```

Isso faz o login no Hamachi e inicializa o daemon. Caso seja a primeira vez que você está usando o Hamachi, ele também irá registrar seu cliente.

### Passo 4: Associar a sua conta LogMeIn Hamachi

Para associar a instalação do Hamachi ao seu **LogMeIn Account**, use o comando abaixo:

```bash
sudo hamachi attach seu_email@example.com
```

Substitua `seu_email@example.com` pelo email que você usa na sua conta LogMeIn. Isso irá associar o Hamachi à sua conta LogMeIn Hamachi.

Será necessário acessar sua conta e confirmar o ingresso do novo dispositivo. 

### Passo 5: Confirmar a associação

Após isso, você pode verificar o estado de login com:

```bash
sudo hamachi
```

Isso irá mostrar o estado atual do cliente Hamachi, incluindo o ID associado à sua conta.

### Passo 4: Criar ou juntar-se a uma rede

- Para **criar** uma nova rede, use o comando:

   ```bash
   sudo hamachi create nome_da_rede senha
   ```

- Para **juntar-se** a uma rede existente:

   ```bash
   sudo hamachi join nome_da_rede senha
   ```

### Passo 5: Verificar o status da conexão

Use o seguinte comando para ver o status da conexão e as redes às quais você está conectado:

```bash
sudo hamachi list
```

### Dicas adicionais:

- Se você já configurou sua conta Hamachi em outro dispositivo, pode acessar sua conta diretamente no [LogMeIn Central](https://central.logmein.com/), onde você gerencia suas redes.

### Conclusão

Agora você tem o Hamachi instalado e funcionando no seu sistema Linux. Ele permite que você crie redes privadas, compartilhe arquivos, jogue em rede com seus amigos e até mesmo acesse dispositivos remotamente de maneira segura.


