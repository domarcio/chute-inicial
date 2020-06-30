# Chute Inicial
Abaixo um check-list de algumas coisas para fazer após instalar o _S.O_. O objetivo é ajudar novos devs **Backend** com um pequeno guia.

Todos os exemplos são para Linux (Fedora 31 & 32), porém são facilmente adaptáveis para qualquer sistema.

## Resumo
Um rápido resumo do que é preciso para o nosso primeiro chute:

- [**Podman**](#podman)
- [**Git**](#git)
- [**Groovy**](#groovy)
- [**Golang**](#golang)
- [**Slack**](#slack)
- [**IntelliJ IDEA Community _(JetBrains Toolbox)_**](#intelliJ-idea-community-JetBrains-toolbox)
- [**VS Code**](#vs-code)
- [**DBeaver Community**](#dbeaver-community)
- [**Acesso VPN, AWS, k8s, ...**](#acesso-vpn-aws-k8s-)
- [**Kubectl**](#kubectl)
- [**AWS Cli**](#aws-cli)
- [**Configurar VPN**](#configurar-vpn)

Opcionais:

- *Terminator*
- *ZSH + Oh My ZSH*
- *Insomnia REST Client*

## Iniciar

### Podman
Fedora:
```console
foo@bar $ sudo dnf install podman && sudo dnf install podman-compose
```
Caso queira usar o Docker ao invés do Podman (no Fedora,) veja [esse link](https://www.linuxuprising.com/2019/11/how-to-install-and-use-docker-on-fedora.html).

### Git
Fedora já vem com o Git instalado. :blush: Porém nada que um `dnf install` não resolva:
```console
foo@bar $ sudo dnf install git
```

**Dica: Configurar SSH no Github**

Você pode olhar o tutorial oficial de como [gerar a chave](https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) e depois [adicioná-la ao Github](https://help.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account). Se preferir pode seguir os passos abaixo.

1. Gerar a chave.
```console
foo@bar $ ssh-keygen -t rsa -b 4096 -C "seuemail@pismo.io"
```
2. Copie a chave.
```console
foo@bar $ cat ~/.ssh/id_rsa.pub
```
3. Adicione a chave nas [suas configurações](https://github.com/settings/keys).

### Groovy
```console
foo@bar $ sudo dnf install groovy
```

### Golang
```console
foo@bar $ sudo dnf install go
```

### Slack
1. Faça o download do arquivo **.rpm**: https://slack.com/intl/en-br/downloads/linux
2. Execute o comando:
```console
foo@bar $ sudo dnf install /path/to/package/slackfile.rpm
```

### IntelliJ IDEA Community _(JetBrains Toolbox)_
1. Faça o download do arquivo **.tar.gz**: https://www.jetbrains.com/toolbox-app/
2. Extraia o arquivo:
```console
foo@bar $ cd Downloads/
foo@bar $ sudo tar -xzf jetbrains-toolbox.tar.gz -C /opt
```
3. Finalize a instalação:
```console
foo@bar $ cd /opt/jetbrains-toolbox-VERSION_NUMBER
foo@bar $ sudo ./jetbrains-toolbox
```
4. Depois é só instalar o que quiser. :+1:

### VS Code
O **VS Code** é uma boa opção para trabalhar com **Go**, então vale a pena instalar.

```console
foo@bar $ sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
foo@bar $ sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'
foo@bar $ sudo dnf check-update
foo@bar $ sudo dnf install code
```
Algumas extensões legais:
- [Docker         ](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker)
- [Git History    ](https://marketplace.visualstudio.com/items?itemName=donjayamanne.githistory)
- [GitLens        ](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
- [Go             ](https://marketplace.visualstudio.com/items?itemName=ms-vscode.Go)
- [Go Critic      ](https://marketplace.visualstudio.com/items?itemName=neverik.go-critic)
- [Go Doc         ](https://marketplace.visualstudio.com/items?itemName=msyrus.go-doc)
- [Go Outliner    ](https://marketplace.visualstudio.com/items?itemName=766b.go-outliner)
- [PlantUML       ](https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml)
- [vscode-icons   ](https://marketplace.visualstudio.com/items?itemName=vscode-icons-team.vscode-icons)
- [Better Comments](https://marketplace.visualstudio.com/items?itemName=aaron-bond.better-comments)

### DBeaver Community
```console
foo@bar $ cd Downloads/
foo@bar $ wget https://dbeaver.io/files/dbeaver-ce-latest-stable.x86_64.rpm
foo@bar $ sudo dnf install dbeaver-ce-latest-stable.x86_64.rpm
```

### Acesso VPN, AWS, k8s, ...
É preciso solicitar esses acessos ao [**#goleiro**](https://pismo.slack.com/archives/CPQT2BGR4), leia a [FAQ](https://app.gitbook.com/@pismo-docs/s/platform/operational-issues/goleiro-faq) para mais detalhes.

Tarefas de exemplo:
- Acesso ao Github: https://pismolabs.atlassian.net/browse/GOL-236
- k8s: https://pismolabs.atlassian.net/browse/GOL-284

### Kubectl
```console
foo@bar $ cd Downloads/
foo@bar $ curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
foo@bar $ chmod +x ./kubectl
foo@bar $ sudo mv ./kubectl /usr/local/bin/kubectl
foo@bar $ kubectl version
```

Após a instalação e com as credenciais de acesso ao k8s (fornecidas pelo goleiro), crie a tua configuração.

1. Copie as configurações fornecidades pelo goleiro para esse arquivo
```console
foo@bar $ cd ~ && mkdir .kube/ && cd .kube/ && vi config
```
2. Use vários arquivos kubeconfig ao mesmo tempo
```console
foo@bar $ KUBECONFIG=~/.kube/config:~/.kube/kubconfig2
```
3. Valide as informações da configuração
```console
foo@bar $ kubectl config view
```

### AWS Cli
1. Instalar o comando [aws cli](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html).
```console
foo@bar $ sudo dnf install awscli
```
2. [Configurar](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html#cli-configure-quickstart-config) de acordo com as [credenciais fornecidas pelo goleiro](#acesso-vpn-aws-k8s-).

### Configurar VPN
1. Primeiro de tudo, instalaremos o [openfortivpn](https://apps.fedoraproject.org/packages/openfortivpn).
```console
foo@bar $ sudo dnf install openfortivpn
```
2. Após a instalação, criaremos um arquivo que contém nossas [credenciais de acesso](#arrow_right-acesso-a-vpn-e-aws).
```console
foo@bar $ sudo vim /etc/openfortivpn/config
```
No arquivo nós adicionaremos as seguintes informações:
```
host = 
port = 
username = 
password = 
trusted-cert = 
```
3.Assim já é possível se conectar na VPN via linha de comando.
```console
foo@bar $ sudo openfortivpn -c /etc/openfortivpn/config
```

**Aqui nossa VPN já está funcional**, mas uma maneira legal de usá-la é adicionar ao Network do *S.O*.

1. Instale o [fortisslvpn](https://gitlab.gnome.org/GNOME/NetworkManager-fortisslvpn).
```console
foo@bar $ sudo dnf install NetworkManager-fortisslvpn-gnome.x86_64
```
2. Agora procure pela opção *Network*, essa opção está no *Settings* do **Fedora**.
3. Clique no :heavy_plus_sign: e selecione a opção **Fortinet SSLVPN** na área de **VPN**.
4. Na aba *Identity*, preencha com as informações que já temos, são as mesmas usadas para se conectar com a VPN via linha de comando. Atenção ao campo **Gatway**, pois nele é preciso (também) informar a porta: `ec2-123-456-7890.sa-east-1.compute.amazonaws.com:99999`.
6. Agora clique no botão *Advanced...* e preencha o campo *Trusted certificate* com o nosso `trusted-cert`.
5. Depois disso vá até a aba *IPv4* e faça um check da opção *Use this connection only for resources on its network*.

Pronto! Agora é possível conectar-se na VPN com apenas um clique.

## Opcionais

### *Terminator*
```console
foo@bar $ sudo dnf install terminator
```

### *ZSH + Oh My ZSH*

Primeiro é preciso instalar o **ZSH**.
```console
foo@bar $ sudo dnf install zsh
```
Agora partimos para a instalação manual do **Oh My ZSH**.
```console
foo@bar $ git clone git@github.com:ohmyzsh/ohmyzsh.git ~/.oh-my-zsh
foo@bar $ cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
foo@bar $ chsh -s $(which zsh)
```
### *Insomnia REST Client*

É preciso instalar o [snap](https://snapcraft.io/docs/installing-snap-on-fedora), caso não tenha.

Com o snap, faça a instalação:
```console
foo@bar $ sudo snap install insomnia
```
