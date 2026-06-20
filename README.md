## Executar uma Instância EC2 pelo console

<img width="2553" height="978" alt="image" src="https://github.com/user-attachments/assets/85775d06-11a2-4c91-adc3-667102d9a8ed" />

1.  Iremos iniciar uma instância através do console de gerenciamento, que será um servidor web de teste. Depois iremos testar a conectividade desse servidor web. No canto superior esquerdo, na barra de pesquisa, pesquise pelo serviço EC2.
<img width="2558" height="974" alt="image" src="https://github.com/user-attachments/assets/30dcfb69-0bd7-4048-a41d-dfc55f169cbc" />
<img width="2558" height="974" alt="image" src="https://github.com/user-attachments/assets/04d34b11-e35e-4fed-8a31-b49517bcad40" />

2.  Clique em **“Executar instância”**. Se não aparecer o botão laranja, você pode ir no menu esquerdo, em Instâncias e depois em **"Executar instância"**.
   <img width="2558" height="974" alt="image" src="https://github.com/user-attachments/assets/53d79676-ef28-439f-accd-1fbbaa0f81b7" />
   

3.  Preencha as informações conforme abaixo. Os campos que não forem mencionados, deixe no valor padrão:

a.  **Nome**: webserver-<seu nome e sobrenome>. Não digite espaço, nem os sinais <>. Por exemplo, se seu nome for Jeff Bezos, digite webserver-JeffBezos.
b.  **Imagem de máquina da Amazon (AMI):** Amazon Linux 2023
c.  **Tipo de instância:** t2.micro
d.  **Par de chaves (login):** no canto direito há a opção azul “Criar novo par de chaves”. Clique nela, para criar um par de chaves. Crie com o nome parchave-<seu nome e sobrenome>. Não digite espaço, nem os sinais <>. Por exemplo, se seu nome for Jeff Bezos, digite parchave-JeffBezos.
e.  **Tipo de par de chaves**: RSA
f.  **Formato de arquivo de chave privada:** .pem
g.  Clique em **“Criar par de chaves”**. Irá aparecer uma tela para salvar o arquivo .pem. Salve-o em uma pasta de fácil localização, pois o utilizaremos em breve.
h.  Depois volte à tela do console da AWS e selecione o par de chaves com o seu nome.
i.  **Configurações de rede > Firewall (grupos de segurança):** Criar grupo de segurança. Marque a opção “Permitir tráfego HTTP”.
j.  **Detalhes avançados:** clique nessa opção, depois vá até o final, em **“Dados de usuário (opcional)”** e insira o scrip abaixo. Com estes dados de usuário, iremos instalar e iniciar um componente, para subirmos um servidor web. E então é criada uma página web simples. Após isso, clique em **“Executar instância.”**


  
  

    #!/bin/bash
    
    dnf install -y httpd
    
    systemctl enable  --now httpd
    
    echo  '<html><h1>Olá do seu servidor web!</h1></html>'  > /var/www/html/index.html

  

4.  Caso precisar, anote o nome da instância que você utilizou, pois iremos precisar em breve. Após clicar para executar a instância, irá mostrar uma mensagem de **“Êxito”**. Você pode clicar em cima do ID da instância (**geralmente começa com  i- e terão várias letras e números**) ou volte para o serviço EC2 e no menu esquerdo, clique em **“Instâncias”**.
5.  Após abrir a tela de Instâncias, localize a instância pelo seu nome e clique em cima do ID da instância e aguarde a verificação de status mostrar **“2/2 verificações aprovadas”**.
6.  Após isso, clique em cima do ID da sua instância, para mostrar todos os detalhes. Logo no início, irá mostrar o Endereço IPv4 público. Copie-o e deixe-o salvo em algum editor de texto. Usaremos este IP em breve.
7.  Abra outra aba no seu navegador e digite **“http://”** e então o Endereço IPv4 público da sua instância. Por exemplo, se o IP da sua instância for 8.8.8.8, digite **“http://8.8.8.8”**. Ao acessar pelo navegador, alguém vai te dar um oi!
8.  O servidor de teste está iniciado! Se apareceu a mensagem corretamente, pode fechar a aba da mensagem. Agora iremos iniciar outra instância pelo CloudShell.


