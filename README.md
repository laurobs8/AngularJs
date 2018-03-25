# AngularJs
Estudo de AngularJS


Este documento, é resultado de um inicio de uma sequência de estudos em AngularJS. Através de pesquisar a respeito do assunto, achei uma vídeo-aula feita por Rodrigo Branas. Esta é a AULA 2 que é a elaboração de uma Lista Telefonica com cunho totalmente voltado ao aprendizado do Angular.

# ng-app

<code> html ng-app="ListaTelefonica" </code>

Nome do modulo principal da aplicação, neste caso  usaremos ListaTelefonica” aconselhável colocar em níveis altos, nesse documento, se encontra na tag <html >

Ao salvar este documento no browser, ele da um erro, nos informando que a lista telefônica não está disponível, portanto precisa-se criar um modulo.

# Criando um modulo 

<code> angular.module("ListaTelefonica", []);//[]nome do modulo(ListaTelefonica). [] conjunto de modulos que quer importar(bootstrap, ngtable, nggrid etc...) </code>

# ng-controller 

Ele faz o vínculo entre a view e o controller de onde vai nascer o scope
<code> body ng-controller="ListaTelefonicaCtrl" </code>
Pode-se colocar o ng-controller em divs também por exemplo

Ao salvar o arquivo e exibir-lo no browser, ele fala que o ng-controller não existe, então tem que definir o modulo.

# Definir o modulo

<code> angular.module("ListaTelefonica").controller("ListaTelefonicaCtrl", function($scope) </code>
$scope é o que faz a ponte entre a view e o controller

Após isso, não há mais problemas no browser.




# ng-bind

ngBind substitui um elemento por uma expressão

exemplo:
dentro da function $scope, vamos colocar 
<code> $scope.app = "Lista Telefonica" </code>


E para “vincular” essa string para aparecer na tela, colocamos num h4 dentro de uma div no body.
<code> h4 ng-bind='app'> </code>

Automaticamente vai vincular o h4 no $scope. Ou seja, no browser vai aparecer a string “Lista Telefônica”.

Outro jeito de mostrar essa string, é a chamada interpolação da expressão representada dentro das chaves duplas

<code> <h4>{{app + ' ' + "Teste " + 20*20}} </h4> </code>

Alem de só mostrar a expressão no app, também pode-se fazer concatenação, operações dentro das chaves duplas


# rg-repeat

Serve para iterar, - “loop” - numa array como um for in em JavaScript
Usando ng-repeat ele verifica um a um elementos dentro de uma array. Nesse exemplo, o array fica dentro do $scope e nomeamos de contatos.

<code> $scope.contatos = [ 
            {nome: 'Antonio', telefone: "22334455"},
            {nome: 'Ana', telefone: "211445566"},
            {nome: 'Cesar', telefone: "26688555"},
            {nome: 'Marcia', telefone: "123234345"}
          ];
</code>

Para mostrar no browser de forma ordenada, no exemplo usamos a tag table

<table class='table table-striped'>
            <tr>
                <th>Nome</th>
                <th>Telefone</th>
            </tr>

            <tr ng-repeat='contato in contatos'>
                <td>{{contato.nome}}</td>
                <td>{{contato.telefone}}</td>
            </tr>
        <hr>

        </table>

Na tag tr colocamos o ng-repeat como no exemplo acima e passamos para verificar contato in contatos
A tag td serve para alinha em colunas



# ng-model

Pega algo na view e define no scope. É o oposto do ngRepeat. Aplica-se na maioria das vezes nos inputs, selects e no texts áreas.

Nesse exemplo, usamos:
 
<code> input class="form-control" type="text" ng-model="contato.nome" placeholder=" Nome"/>
 <input class="form-control" type="text" ng-model="contato.telefone" placeholder="Telefone"
</code>


# ng-click

Faz atribuições através do evento Click ou dubbleClick
<code> <button class="btn btn-primary" ng-click="adicionarContato(contato)">Adicionar contato</button> </code>

Desta vez, após o ng-click, passamos uma função chamado ”contato”. Portanto, essa função tem que está OBRIGATORIAMENTE no $scope.

<code>
$scope.adicionarContato = function(contato){
            $scope.contatos.push(angular.copy(contato));
          }
          </code>
