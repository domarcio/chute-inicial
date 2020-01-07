
# Chute Inicial
Abaixo um check-list de algumas coisas para fazer após instalar o _S.O_. O objetivo é ajudar novos devs com um pequeno guia.

Todos os exemplos são para Linux (Fedora), porém são facilmente adaptáveis para qualquer sistema.

## Resumo
Um rápido resumo do que é preciso para o nosso primeiro chute:

- **Docker**
- **Git**
- **Groovy**
- **Golang**
- **Slack**
- **IntelliJ IDEA Community _(JetBrains Toolbox)_**
- **VS Code**
- **DBeaver Community**
- **Abrir uma tarefa para o Goleiro liberar os acessos**
- **kubectl**
- **Acesso a VPN e AWS**
- **Configurar VPN**

Opcionais:

- *Terminator*
- *ZSH + Oh My ZSH*
- *Insomnia REST Client*

## Iniciar

### :arrow_right: Docker
Fedora **31**:
```console
foo@bar:~ sudo dnf install podman && sudo dnf install podman-compose
```
Caso queira usar o Docker ao invés do Podman (no Fedora,) veja [esse link](https://www.linuxuprising.com/2019/11/how-to-install-and-use-docker-on-fedora.html).

### :arrow_right: Git
Fedora já vem com o Git instalado. :blush:

**Dica: Configurar SSH no Github**

Você pode olhar o tutorial oficial de como [gerar a chave](https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) e depois [adicioná-la ao Github](https://help.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account). Se preferir pode seguir os passos abaixo.

1. Gerar a chave.
```console
foo@bar:~ ssh-keygen -t rsa -b 4096 -C "seuemail@pismo.io"
```
2. Copie a chave.
```console
foo@bar:~ cat ~/.ssh/id_rsa.pub
```
3. Adicione a chave nas [suas configurações](https://github.com/settings/keys).

### :arrow_right: Groovy
```console
foo@bar:~ sudo dnf install groovy
```
### :arrow_right: Golang
```console
foo@bar:~ sudo dnf install go
```
### :arrow_right: Slack
1. Faça o download do arquivo **.rpm**: https://slack.com/intl/en-br/downloads/linux
2. Execute o comando:
```console
foo@bar:~ sudo dnf install /path/to/package/slackfile.rpm
```
### :arrow_right: IntelliJ IDEA Community _(JetBrains Toolbox)_
1. Faça o download do arquivo **.tar.gz**: https://www.jetbrains.com/toolbox-app/
2. Extraia o arquivo:
```console
foo@bar:~ cd Downloads/
foo@bar:~ sudo tar -xzf jetbrains-toolbox.tar.gz -C /opt
```
3. Finalize a instalação:
```console
foo@bar:~ cd /opt/jetbrains-toolbox-VERSION_NUMBER
foo@bar:~ sudo ./jetbrains-toolbox
```
4. Depois é só instalar o que quiser. :+1:
### :arrow_right: VS Code
O **VS Code** é uma boa opção para trabalhar com **Go**, então vale a pena instalar.

```console
foo@bar:~ sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
foo@bar:~ sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'
foo@bar:~ sudo dnf check-update
foo@bar:~ sudo dnf install code
```
Algumas extensões legais:
- [Docker      ](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker)
- [Git History ](https://marketplace.visualstudio.com/items?itemName=donjayamanne.githistory)
- [GitLens     ](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
- [Go          ](https://marketplace.visualstudio.com/items?itemName=ms-vscode.Go)
- [Go Critic   ](https://marketplace.visualstudio.com/items?itemName=neverik.go-critic)
- [Go Doc      ](https://marketplace.visualstudio.com/items?itemName=msyrus.go-doc)
- [Go Outliner ](https://marketplace.visualstudio.com/items?itemName=766b.go-outliner)
- [PlantUML    ](https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml)
### :arrow_right: DBeaver CE
```console
foo@bar:~ cd Downloads/
foo@bar:~ wget https://dbeaver.io/files/dbeaver-ce-latest-stable.x86_64.rpm
foo@bar:~ sudo dnf install dbeaver-ce-latest-stable.x86_64.rpm
```
### :arrow_right: Abrir uma tarefa para o Goleiro liberar os acessos
Leia as [regras para criar uma Task](https://app.gitbook.com/@pismo-docs/s/goleiro/) ao [**#goleiro**](https://pismo.slack.com/archives/CPQT2BGR4).

Agora é preciso abrir 2 tarefas (como nos exemplos abaixo) para pedir os acessos:
- Acesso ao Github: https://pismolabs.atlassian.net/browse/GOL-236
- k8s: https://pismolabs.atlassian.net/browse/GOL-284

*Aqui temos um impasse. Para ler as regras do goleiro é preciso de acesso ao Gitbook. Para pedir acesso ao Gitbook é preciso de uma tarefa no GOL. No meu caso (@domarcio) caso um amiguinho me ajudou e criar a task "nos conformes" sem precisar ler a doc.*
### :arrow_right: kubectl
```console
foo@bar:~ cd Downloads/
foo@bar:~ curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
foo@bar:~ chmod +x ./kubectl
foo@bar:~ sudo mv ./kubectl /usr/local/bin/kubectl
foo@bar:~ kubectl version
```

Após a instalação e com as credenciais de acesso ao k8s (fornecidas pelo goleiro), crie a tua configuração.

1. Copie as configurações fornecidades pelo goleiro para esse arquivo
```console
foo@bar:~ vi .kube/config
```
2. Use vários arquivos kubeconfig ao mesmo tempo
```console
foo@bar:~ KUBECONFIG=~/.kube/config:~/.kube/kubconfig2
```
3. Valide as informações da configuração
```console
foo@bar:~ kubectl config view
```
### :arrow_right: Acesso a VPN e AWS
### :arrow_right: Configurar VPN

## Opcionais

### :arrow_right: *Terminator*
```console
foo@bar:~ sudo dnf install terminator
```

### :arrow_right: *ZSH + Oh My ZSH*

Primeiro é preciso instalar o **ZSH**.
```console
foo@bar:~ sudo dnf install zsh
```
Agora partimos para a instalação manual do **Oh My ZSH**.
```console
foo@bar:~ git clone https://github.com/ohmyzsh/ohmyzsh.git ~/.oh-my-zsh
foo@bar:~ cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
foo@bar:~ chsh -s $(which zsh)
```
### :arrow_right: *Insomnia REST Client*

É preciso instalar o [snap](https://snapcraft.io/docs/installing-snap-on-fedora), caso não tenha.

Com o snap, faça a instalação:
```console
foo@bar:~ sudo snap install insomnia
```
