# Estudo de Brute Force - Santander Cybersecurity Bootcamp

Este repositório documenta meu processo de aprendizagem no curso de Cybersegurança Santander na plataforma DIO, especificamente sobre técnicas de Brute Force.

---

## 1. Brute Force no FTP

Em primeira instância, realizei um scan de portas para a verificação dos serviços que foram utilizados ao longo do laboratório (FTP, SMB, HTTP).

![Scan de Portas](/images/Captura%20de%20tela%202025-11-29%20190206.png)

Depois disso, criei duas pequenas wordlists — uma para usuários e outra para senhas — e com elas realizei um ataque de força bruta no FTP utilizando a ferramenta **Medusa**.

![Wordlists](/images/Captura%20de%20tela%202025-11-29%20190258.png)
![Execução Medusa](/images/Captura%20de%20tela%202025-11-29%20190317.png)

**O comando do ataque:**

![Comando](/images/Captura%20de%20tela%202025-11-29%20190937.png)

**Login realizado com a senha descoberta:**

![Login Sucesso](/images/Captura%20de%20tela%202025-11-29%20192858.png)

---

## 2. Brute Force no Formulário DVWA

No formulário web, utilizei as mesmas wordlists criadas para o FTP. Porém, antes de iniciar, verifiquei qual seria a resposta do site ao inserir um usuário e senha aleatórios. Identificar essa resposta de erro é chave para configurar a ferramenta Medusa corretamente.

![Erro de Login](/images/Captura%20de%20tela%202025-11-29%20191145.png)

Após identificar a mensagem "Login Failed", montei o comando conforme os ensinamentos do curso:

![Comando Web](/images/Captura%20de%20tela%202025-11-29%20193622.png)

Ao rodar o comando e testar as possibilidades, consegui identificar o acesso com o usuário **"admin"** e a senha **"password"**. Inserindo esses dados no campo de login, o acesso foi concedido.

![Acesso DVWA](/images/Captura%20de%20tela%202025-11-29%20191403.png)

---

## 3. Enumeração de Usuários + Password Spraying

Para aplicar a técnica de *Password Spraying*, iniciei enumerando os usuários do sistema alvo com o seguinte comando:

![Enumeração](/images/Captura%20de%20tela%202025-11-29%20191454.png)

Analisando a lista retornada, filtrei os usuários mais comuns/vazados e criei uma nova wordlist. Fiz o mesmo processo para criar uma lista com as senhas mais comuns utilizadas em serviços SMB.

![Lista Users](/images/Captura%20de%20tela%202025-11-29%20191525.png)
![Lista Pass](/images/Captura%20de%20tela%202025-11-29%20191600.png)
![Edição](/images/Captura%20de%20tela%202025-11-29%20191553.png)

Com as duas wordlists salvas, executei o **Medusa** configurado para *password spraying*, utilizando duas threads por usuário e testando múltiplos hosts paralelamente.

![Execução Spraying](/images/Captura%20de%20tela%202025-11-29%20191655.png)

Após encontrar a senha correta, testei o acesso no serviço SMB e obtive sucesso.

![Acesso SMB](/images/Captura%20de%20tela%202025-11-29%20191724.png)

---

**Fim da documentação.**
