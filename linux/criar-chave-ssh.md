### Como Criar e Configurar uma Chave SSH para se Autenticar no GitHub

O uso de chaves SSH é uma prática comum para autenticar e proteger o acesso a serviços online, como o GitHub. Essa autenticação é especialmente útil para desenvolvedores que desejam evitar a inserção contínua de credenciais de login ao interagir com repositórios remotos. Neste artigo, irei mostrar como criar e configurar uma chave SSH para acessar o GitHub de forma simples e prática.

#### 1. Verificando Chaves SSH Existentes
Antes de gerar uma nova chave SSH, é importante verificar se já existem chaves geradas no seu sistema. Para isso, abra um terminal e execute o comando abaixo:

```bash
ls -al ~/.ssh
```

Este comando lista todos os arquivos no diretório `.ssh`, onde as chaves SSH costumam ser armazenadas. Se você já tiver arquivos como `id_rsa` ou `id_ed25519`, isso indica que uma chave SSH já foi criada. Caso contrário, será necessário gerar uma nova chave.

#### 2. Gerando uma Nova Chave SSH
Se você ainda não tem uma chave SSH, pode criar uma nova com o seguinte comando. Certifique-se de substituir `seu-email@exemplo.com` pelo endereço de e-mail associado à sua conta no GitHub:

```bash
ssh-keygen -t ed25519 -C "seu-email@exemplo.com"
```

Se o seu sistema não suportar o algoritmo `ed25519`, você pode optar pelo algoritmo RSA, que também é amplamente suportado:

```bash
ssh-keygen -t rsa -b 4096 -C "seu-email@exemplo.com"
```

Durante o processo, será solicitado um local para salvar a chave. Para seguir as convenções, pressione **Enter** para aceitar o caminho padrão (`~/.ssh/id_ed25519` ou `~/.ssh/id_rsa`). Se desejar, você pode proteger sua chave privada com uma senha, embora isso seja opcional.

#### 3. Adicionando a Chave SSH ao Agente SSH
Após gerar a chave, você precisa carregá-la no agente SSH, que gerencia as suas chaves durante a sessão. Para isso, inicie o agente SSH com o comando:

```bash
eval "$(ssh-agent -s)"
```

Em seguida, adicione a chave recém-gerada ao agente:

```bash
ssh-add ~/.ssh/id_ed25519
```

Se você gerou uma chave RSA, utilize o seguinte comando:

```bash
ssh-add ~/.ssh/id_rsa
```

#### 4. Adicionando a Chave SSH ao GitHub
Agora que a chave SSH foi gerada e está ativa no seu sistema, é necessário adicioná-la à sua conta do GitHub. Primeiro, copie o conteúdo da chave pública com um dos comandos abaixo, dependendo do tipo de chave que você gerou:

Para `ed25519`:

```bash
cat ~/.ssh/id_ed25519.pub
```

Para `rsa`:

```bash
cat ~/.ssh/id_rsa.pub
```

O comando `cat` exibe o conteúdo da chave pública no terminal. Copie o resultado e vá até a página de configurações de chaves SSH no GitHub: [GitHub SSH Keys](https://github.com/settings/keys). Clique em **"New SSH key"**, cole a chave no campo "Key" e forneça um título descritivo para a chave, como **"Minha chave SSH pessoal"**.

#### 5. Testando a Conexão com o GitHub
Agora que a chave foi adicionada à sua conta, é hora de testar a conexão para garantir que tudo está funcionando corretamente. Para isso, execute o seguinte comando:

```bash
ssh -T git@github.com
```

Esse comando tentará se conectar ao GitHub usando a chave SSH configurada. Se a configuração estiver correta, você verá uma mensagem parecida com esta:

```
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```

Essa mensagem indica que a autenticação foi bem-sucedida e que você pode começar a interagir com seus repositórios no GitHub utilizando o SSH.

#### Conclusão
Utilizar uma chave SSH para acessar o GitHub oferece um nível adicional de segurança e praticidade, eliminando a necessidade de digitar seu usuário e senha sempre que você deseja fazer push ou pull de um repositório. Após seguir estes passos, você estará pronto para trabalhar de maneira mais eficiente e segura com o GitHub.

Se você tiver dúvidas ou dificuldades durante o processo, não hesite em consultar a [documentação oficial do GitHub sobre SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/about-ssh) para mais detalhes e orientações.