# 😁 Projeto de Autenticação e Autorização

## 🚀 Autenticação de Usuários a Único Servidor (Single Server).

A **autenticação** é como verificar o cartão de um membro para garantir que ele tem permissão para entrar em um clube. Em um servidor único, toda a autenticação é gerenciada por um único servidor, o que simplifica a administração.

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

## 🛡️ Não utilizaremos a autenticação com Token (JWT)

Mas aqui está uma breve explicação para você ficar informado sobre o que é o **JWT (JSON Web Token)**, é um formato de token compacto e seguro para transmitir informações entre partes como um objeto JSON. Ele é frequentemente utilizado em sistemas de autenticação e autorização.

**Como Funciona:**

**Estrutura:** Um JWT é composto por três partes: header (cabeçalho), payload (corpo) e signature (assinatura). O cabeçalho define o algoritmo de assinatura, o corpo contém as informações ou claims (como ID do usuário e permissões), e a assinatura garante que o token não foi alterado.

**Geração e Validação:** O servidor gera o JWT ao autenticar um usuário e o envia ao cliente. O cliente armazena o token e o inclui em requisições subsequentes. O servidor valida a assinatura do token para verificar sua integridade e autenticidade antes de processar a requisição.
**Benefícios:**

**Compacto:** Ideal para transmissão em cabeçalhos HTTP e URLs.
Auto-Suficiente: Contém todas as informações necessárias para autenticação e autorização, reduzindo a necessidade de consultas adicionais ao banco de dados.

**Segurança:** Permite garantir a integridade dos dados com uma assinatura digital, e pode ser criptografado para maior proteção.
JWT é útil para sistemas distribuídos e APIs, proporcionando uma maneira eficiente e segura de gerenciar sessões e permissões de usuários.

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
