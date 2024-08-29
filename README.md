# 😁 Projeto de Autenticação e Autorização

## 🚀 Autenticação de Usuários a Único Servidor (Single Server).
````
A autenticação é como verificar o cartão de um membro para garantir que ele tem permissão para entrar em um clube. Em um servidor único, toda a autenticação é gerenciada por um único servidor, o que simplifica a administração.
````
### **Fluxo Básico da Autenticação**:
1. **Registro do Usuário**: O usuário se registra fornecendo suas credenciais, como nome de usuário e senha. Essas informações são armazenadas de forma segura no banco de dados do servidor.
2. **Login**: O usuário insere suas credenciais para acessar o sistema. O servidor confere se essas informações coincidem com as que estão armazenadas.
3. **Verificação**: O servidor compara as credenciais fornecidas com as armazenadas. Se os dados estiverem corretos, o usuário é autenticado e tem acesso ao sistema.
4. **Sessão**: Após a autenticação, o servidor cria uma sessão para o usuário, geralmente usando um identificador de sessão que é armazenado em um cookie. Isso permite que o usuário continue acessando o sistema sem precisar fazer login novamente em cada requisição.

### **Aspectos Técnicos**:
- **Hashing de Senhas**: Para proteger as senhas dos usuários, elas são armazenadas em uma forma criptografada chamada hash. Isso garante que mesmo se o banco de dados for comprometido, as senhas não possam ser facilmente decifradas. Algoritmos comuns de hashing incluem bcrypt, Argon2 e PBKDF2.
- **Gerenciamento de Sessões**: Sessões são gerenciadas com cookies que têm atributos de segurança, como `HttpOnly` e `Secure`. O atributo `HttpOnly` impede que scripts no navegador acessem o cookie, protegendo contra ataques de Cross-Site Scripting (XSS). O atributo `Secure` garante que o cookie só seja enviado sobre conexões HTTPS, protegendo contra ataques de interceptação.

---

## 🔐 Autenticação VS Autorização

Para entender a diferença entre autenticação e autorização, pense em um jogo de tabuleiro:

- **Autenticação**: É como mostrar seu cartão de membro para entrar no jogo. É o processo de verificar se você é quem diz ser.
- **Autorização**: Após entrar no jogo, é sobre o que você pode fazer nele. Define quais partes do jogo você pode acessar e quais regras você deve seguir.

### **Aspectos Técnicos**:
- **Autenticação**:
  - **Mecanismos**: Incluem senhas, biometria (como impressão digital ou reconhecimento facial), e autenticação multifatorial (MFA), que exige mais de um método de verificação (como senha e código enviado por SMS).
  - **Protocolos**: Muitos sistemas usam protocolos como OAuth 2.0 para autenticação, que define padrões para como tokens de acesso são emitidos e validados.
  
- **Autorização**:
  - **Controle de Acesso Baseado em Roles (RBAC)**: Usuários são atribuídos a diferentes papéis (roles) e cada papel tem permissões específicas. Por exemplo, um "administrador" pode ter acesso total, enquanto um "usuário" pode ter acesso restrito.
  - **Controle de Acesso Baseado em Atributos (ABAC)**: Permissões são concedidas com base em atributos dos usuários, recursos e ambiente. Isso é mais flexível e pode considerar contextos mais complexos para determinar o acesso.

---

## 🛡️ Autenticação com Token (JWT)

O JWT (JSON Web Token) é como um passaporte digital que você recebe após se registrar. Ele permite que você prove sua identidade e acesse áreas protegidas sem precisar se autenticar novamente a cada vez.

### **Como Funciona**:
1. **Login**: O usuário se autentica fornecendo suas credenciais.
2. **Geração do Token**: Após uma autenticação bem-sucedida, o servidor gera um JWT. Este token contém informações sobre o usuário (chamadas de "claims") e é assinado com uma chave secreta para garantir que não possa ser alterado.
3. **Envio do Token**: O JWT é enviado ao cliente e pode ser armazenado no navegador (em cookies ou localStorage).
4. **Uso do Token**: Em requisições subsequentes, o cliente inclui o JWT no cabeçalho HTTP. O servidor verifica a validade do token antes de conceder acesso aos recursos.
5. **Validação do Token**: O servidor usa a chave secreta para verificar a assinatura do token e garantir que ele não foi alterado. Se o token for válido, o acesso ao recurso é permitido.

### **Aspectos Técnicos**:
- **Estrutura do JWT**: Um JWT é composto por três partes:
  - **Cabeçalho (Header)**: Especifica o algoritmo de assinatura usado, como HMAC SHA256 ou RSA.
  - **Corpo (Payload)**: Contém as "claims", que são declarações sobre o usuário, como seu ID e permissões. As claims podem ser "registered" (como `sub` para ID do usuário), "public" (definidas pelo usuário), e "private" (específicas do aplicativo).
  - **Assinatura (Signature)**: A assinatura é gerada usando o cabeçalho e o corpo com uma chave secreta. Isso garante que o token não foi modificado.
  
- **Algoritmos de Assinatura**: Os JWTs podem ser assinados usando algoritmos simétricos (HMAC) ou assimétricos (RSA). HMAC usa uma chave secreta compartilhada, enquanto RSA usa um par de chaves (pública e privada) para garantir a segurança.

---

## 📋 Projeto (Objeto de Estudos)

Ao desenvolver um projeto de autenticação e autorização com um servidor único, considere:

1. **Escopo do Projeto**: Defina claramente o que o sistema deve realizar. Isso inclui como os usuários se registrarão, como farão login e como a autorização será gerenciada.
2. **Arquitetura**: Desenhe a arquitetura do sistema, detalhando como a autenticação e a autorização serão implementadas. Considere como o sistema se comunicará com o banco de dados e como as sessões serão gerenciadas.
3. **Segurança**: Implemente práticas de segurança, como criptografia de dados sensíveis e proteção contra ataques comuns (como SQL Injection e Cross-Site Request Forgery).
4. **Interface de Usuário**: Desenvolva uma interface intuitiva para login e registro. Certifique-se de que a experiência do usuário seja clara e eficiente.
5. **Testes e Validação**: Teste o sistema para garantir que a autenticação e a autorização funcionam corretamente. Inclua testes de unidade e integração para verificar a segurança e o desempenho.
6. **Documentação**: Documente detalhadamente o fluxo de autenticação e autorização. Inclua descrições dos tokens (se usar JWT) e os endpoints da API que requerem autenticação.

---
## Obrigado por conferir o projeto! 🚀