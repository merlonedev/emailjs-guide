# emailjs-guide

1. instalar o emailjs (se estiver usando React) com `npm i emailjs`
2. criar uma conta no emailjs https://dashboard.emailjs.com/sign-in
3. ao logar, clicar em Add New Service, depois em Gmail (o que eu usei). Conecte sua conta do Gmail e **GUARDAR O ID DO SERVIÇO** ![image](https://user-images.githubusercontent.com/10542075/127533302-5e090513-b537-4061-8327-85a7fa8c2e19.png) ![image2](https://github.com/alestori/emailjs-guide/blob/master/gmailservice.png?raw=true) ![image3](https://github.com/alestori/emailjs-guide/blob/master/connectgmail.png?raw=true)
4. no painel à esquerda, em Integration, ***anotar o User ID que está no final da página*** ![image4](https://github.com/alestori/emailjs-guide/blob/master/userid.png?raw=true)
5. no painel à esquerda, clicar em Email Templates, depois Create New Template ![image5](https://github.com/alestori/emailjs-guide/blob/master/newtemplate.png?raw=true)
6. fazer qualquer mudança no template default e depois salvar (canto direito superior) 
7. **GUARDAR BEM OS NOMES ENTRE CHAVES NO TEMPLATE, ELES SERÃO USADOS NO HTML. O ID DO TEMPLATE TAMBÉM É IMPORTANTE** ![iamge6](https://github.com/alestori/emailjs-guide/blob/master/templatedefault.png?raw=true)
8. criar seu HTML com seu form e inputs
9. se não estiver usando React, utilizar no `head` do seu HTML `<script type="text/javascript" src="https://cdn.jsdelivr.net/npm/emailjs-com@2/dist/email.min.js"></script>`
10. lembra dos nomes entre chaves no template do emailjs? esses nomes vão ser usados agora, pro atributo `name` dos seus inputs. Por exemplo, se você tiver um input onde a pessoa usuária vá colocar o nome dela, o `name` deste input deve ser `from_name` (no template padrão).
11. *se não estiver usando React* adicione uma tag `<script>`com o código 
```
(function () {
  emailjs.init("seu_user_id");
})();

window.onload = function () {
  document.getElementById('contact-form').addEventListener('submit', function (event) {
    event.preventDefault();

    const SERVICE_ID = 'seu_service_id';
    const TEMPLATE_ID = 'seu_template_id';

    emailjs.sendForm(SERVICE_ID, TEMPLATE_ID, this)
      .then(function (response) {
        console.log('SUCCESS!', response.status, response.text);
      }, function (error) {
        console.log('FAILED...', error);
      });
  });
}
```
12. seu_user_id, seu_service_id e seu_template_id todos vem dos passos anteriores

![image7](https://github.com/alestori/emailjs-guide/blob/master/code.png?raw=true)
