### Documentação da Função: `loadCookies`

#### Visão Geral
A função `loadCookies` gerencia um mecanismo simples de consentimento de cookies usando o `localStorage` para verificar se o usuário aceitou os cookies. Ela exibe uma mensagem de consentimento de cookies e a oculta quando o usuário clica para aceitar.

#### Sintaxe
```javascript
function loadCookies();
```

#### Descrição
Essa função verifica se o usuário já aceitou a política de cookies recuperando um valor do `localStorage`. Caso os cookies não tenham sido aceitos, ela exibe uma mensagem de consentimento de cookies e oferece ao usuário a opção de aceitá-los. Após a aceitação, o status de consentimento é salvo no `localStorage` e a mensagem de consentimento é oculta em futuras visitas.

#### Parâmetros
Esta função não aceita nenhum parâmetro.

#### Variáveis Locais
- `cookiesAccepted`: Um booleano que indica se o usuário aceitou os cookies. Ele verifica o valor armazenado no `localStorage` com a chave `"cookiesAccepted"`.
- `acceptBtn`: Uma referência ao botão que permite ao usuário aceitar os cookies. O elemento é selecionado pela classe `.cookies-accept-button`.
- `container`: Uma referência ao contêiner que contém a mensagem de consentimento de cookies. O elemento é selecionado pela classe `.cookies-container`.

#### Lógica e Fluxo

1. **Verificar Consentimento Armazenado:**
   A função recupera o status de `cookiesAccepted` do `localStorage`. Se `"cookiesAccepted"` estiver definido como `"true"`, o usuário já aceitou os cookies e nenhuma outra ação é necessária.

2. **Exibir a Mensagem de Consentimento de Cookies:**
   Se `cookiesAccepted` não for `true`, a mensagem de consentimento de cookies (`container`) é exibida, definindo `container.style.display` como `"block"`.

3. **Adicionar Event Listener:**
   Um listener de evento é adicionado ao botão de aceitar cookies (`acceptBtn`). Quando o usuário clica no botão:
   - A função armazena o valor `"true"` no `localStorage` sob a chave `"cookiesAccepted"`.
   - A mensagem de consentimento é oculta definindo `container.style.display` como `"none"`.

4. **Carregar ao Invocar a Função:**
   A função é invocada imediatamente após sua definição com `loadCookies();`, garantindo que a verificação de consentimento de cookies seja executada assim que a página carregar.

#### Exemplo de Uso
Esta função pode ser usada em qualquer site que necessite exibir uma mensagem de consentimento de cookies e armazenar o consentimento do usuário no `localStorage` do navegador.

Estrutura HTML para Consentimento de Cookies:
```html
<div class="cookies-container" style="display: none;">
  <p>Este site utiliza cookies para garantir a melhor experiência possível.</p>
  <button class="cookies-accept-button">Aceitar Cookies</button>
</div>
```

#### Valor Retornado
Esta função não retorna nenhum valor.

#### Observações
- A informação de consentimento é armazenada de forma persistente usando o `localStorage`, ou seja, o usuário não verá a mensagem de consentimento novamente após aceitá-la, a menos que limpe os dados do navegador.
- Certifique-se de que os elementos com as classes `.cookies-container` e `.cookies-accept-button` existam no HTML para que a função funcione corretamente.