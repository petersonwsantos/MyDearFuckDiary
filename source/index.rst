############################
Amazon Web Services
############################


AWS Compute
*************

AWS Security, Identity & Compliance
**************************************

Identity Access Management (IAM)
====================================

Gerencia usuários grupos, roles e policies. Algumas de suas features são:

* Controle de segurança para o acesso individual e em grupo aos recursos da AWS.
* Suporte nativo para autenticação com MFA.
* Acesso compartilhado à sua conta AWS.
* Permissões granulares
* Acesso seguro aos recursos da AWS para aplicativos executados no EC2
* Identity federation(federação): para conceder permissões para usuários fora da AWS (FB, Google ..)
* Conformidade com o padrão de segurança de dados (DSS) da indústria de cartões de pagamento (PCI)
* Auditoria de registros de acesso usando CloudTrail
* Eventually Consistent

Password Policy
------------------------

* Definição de comprimento mínimo de senha
* Complexidade
* Permitir/Obrigar que todos os usuários IAM alterem suas próprias senhas.
* Expiração de senha
* Impedir que os usuários reutilizem senhas anteriores
* Forçar os usuários a entrar em contato com um administrador de conta quando a senha expirar


Características
------------------------

User-Based
^^^^^^^^^^^^^^

IAM Policies
""""""""""""""

1. IAM policies podem se atachadas em:

* **IAM user** ou **Group**. ("Principal" é considerado o Usuário ou Grupo)
* **Resources AWS** Ex: S3. ("Principal" precisa ser especificado. Can be ARNs of User, Roles, AWS service)
* **Role**

    * Especifique "Principal" atachando uma "Trust Policy(Política de confiança)" que diz quem pode assumir a Role.
    * Anexe as políticas de permissão normais, SEM um principal, "QUEM" é determinado pela Trust Policy.

2. Especifique as ações que são permitidas e o recurso pode ser acessado.

* EC2
* RDS

.. note:: Atenção: Não é possível com IAM permitir ou negar acesso ao sistema operacional de um EC2 específico. Para isso use: SSH Keys, Windows Passwords e Security Group.


Resource Based Policies
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Atachado a um Resource e está disponível apenas para:

* S3
* Glacier
* SNS
* SQS
* AWS KMS

Management Console
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Includes
------------------------

User
^^^^^^^^^^^^^^^

Quando o usuário é criado ele recebe "Access Key ID" e "Secret Access Key".

Group
^^^^^^^^^^^^^^^

Grups são coleções de IAM Users.
É permitido 100 Groups por account.
Os usuários podem pertencer a vários grupos.


Role
^^^^^^^^^^^^^^^

Quando anexo um usuário a varias roles é possível qual papel desejo. Ex: Role de desenvolvimento ou Role de produção.
( IAM User + (RolePROD(+Policy2) + RoleDEV(Policy1+Policy2)

Posso dar permissão para uma instância usar um recurso AWS
( EC2(cli que faz snapshot)+(Role(Policy1+Policy2)) )


* Permitir que instâncias EC2 acessem outros recursos AWS
* Usado por aplicativos rodando na EC2, sem uso de credenciais
* Defina as permissões que podem ser assumidas por IAM Users ou Resources.
* Conceda acesso aos seus Resources a usuários de outra conta da AWS.
* Pode ser usado para permitir que os usuários assumam temporariamente uma Role com menos privilégios de acesso a recursos críticos.
* podem ter permissões específicas em uma região.

Policy
^^^^^^^^^^^^^^^

O que o usuário ou grupo pode fazer.

* Quando adicionamos um usuário ao grupo ele ira herdar as permissões Ex: ( IAM User + (Group + Policy) )
* Quando o usuário pertencer a mais de um grupo não poderá, selecionar no login, a qual grupo prefere trabalhar/ receber as permissões.
* As politicas são descritas em um formato JSON.
* não são específicos da região.

Tipos:

* inline policies: política só para um usuário e não possível reutilizar. (No user clicar em "add inline policy")
* geral: Builtin e Custom (menu esquerda "Policy"). As etapas são:

    * seleciona serviço:
    * seleciona ações: (list, read, tagging. write. permission Management)
    * selecionar resource:  posibilidade de bloqueio por regioão. account, intanceId
    * Request condition: (mfa, horário, etc ...)

Exemplos:

* EC2
    * Ligar instâncias
    * Desligar instãncias
* RD
    * Fazer querys
    * Criar bancos

Identity Federation
------------------------

* A IAM Role pode ser usada para especificar permissões para usuários identificados externamente.
* Max 5000 IAM users per account
* Ativa credenciais temporárias ILIMITADAS
* Identificado por sua organização ou um provedor terceirizado
* Methods:

    * Provedores de serviços de identidade pública ou OpenID (FB, Google ..) Web Identity Federation
    * Provedores compatíveis com SAML 2.0 (Security Assertion Markup Language 2.0)
    * Custom identity broken application (serviço LDAP ou Active Directory)
    * AWS Directory Service for AD and use it for Enterprise
    * AWS Cognito (guest access, public identity..)


Best Pratices
------------------------

* Enable MFA and Reduce root access keys
* Create Individual IAM users

    * Individual credentials, permissions and credentials rotation.
    * Create using console, CLI or API
    * CloudTrail effectiveness. (teste de eficácia)

* Usar grupos para atribuir permissões a IAM users
* Conceda o menor privilégio.

    * Evite atribuir políticas com curinga *. *
    * Default deny

* Apply IAM password policy
* Usar Roles para apliacações que rodan em uma EC2.

    * onde possível, não use credenciais de segurança.
    * nunca compartilhe credenciais de segurança.
    * casos de uso.

        * Cross account access:

            *  Trust Policy
            *  Access Policy

        * Intra-account delegation
        * Federated Users (external users)

* Delegar usando Roles em vez de compartilhar credenciais.
* Rotate credentials regularly
* Remova credenciais desnecessárias
* Usar Policy condicionais para segurança extra.



AWS Management Tools
**************************************

