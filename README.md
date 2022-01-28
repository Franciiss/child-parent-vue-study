
  

# app-parent-child

  

  

## Introdução

Este repositório tem como objetivo servir de estudo para o tópico de componentes do framework Vue.Js. Os tópicos abordados são:

  

1. Componentes

2. Props

3. Eventos e Eventos personalizados (Comunicação entre componentes)

4. Atributos Especiais

  

Este projeto utiliza o framework Vue.js 2x e todos os conceitos e funcionalidades são suportadas no Vue.js 3x.

  

## 1. Componentização

  

Componentes são instâncias reutilizáveis nomeadas e definidas pelo usuário. Este projeto utiliza apenas dois componentes, sendo eles:

  

- App.vue: Raiz/instância principal da aplicação

- DatePicker.vue: componente formado pela junção dos componente v-date-picker e v-text-field (ambos da biblioteca Vuetify).

  

## 2. Props

Em muitos casos componentes só são úteis se for possível passar dados para eles. Desta forma, os props são atributos personalizáveis que, quando recebem valor se tornam uma propriedade na instância do componente. Podemos definir um prop chamado label seguinte maneira:

  

No componente DatePicker.vue:

```

props: ['label']

```

  

ou desta forma, na qual é possível indicar qual é o tipo de prop que deve se passado:

```

props: { label: String}

```

  

E para passar o valor para o componente:
  
  

<DatePicker label="Data Inicio"/>

  

Referência: https://br.vuejs.org/v2/guide/components-props.html

  

## 3. Eventos e Eventos personalizados (Comunicação entre componentes)

A diretiva `v-on:` ou a sintaxe `@` para é utilizada para "ouvir" eventos do DOM e executar instruções quando estes eventos forem chamados.

No exemplo, a mudança do valor do componente v-date-picker através do evento `change` notificará o componente pai através do método de instância `$emit`.

@change="$emit('update:data', $event)"

  

### Modificador .sync

O modificador `sync` é uma forma de criar uma "interligação bidirecional" entre o componente pai e filho. Desta forma, o Vue.Js 2x recomenda que se utilize o padrão `update:nomeDaProp`.

  

Então o componente pai pode ouvir da seguinte forma:

  

<datePicker v-bind:data="dataInicio" v-on:update:data="dataInicio = $event" />

  
  

Por conveniência o Vue.Js utiliza um atalho padrão para o modificador `.sync`:

  

<datePicker ref="dataInicio" label="Data Inicio" :data.sync="dataInicio"/>

  

Referência: https://br.vuejs.org/v2/guide/components-custom-events.html

  

## 4. Atributos Especiais

  

### 1. ref

O atriuto espcial `ref` espera uma string e é utilizado para referenciar um elemento ou um componente filho. Esta referência vai ser armazenada no componente pai no objeto `$refs`.

Uma observação importante sobre o tempo de registro de ref: como as próprias refs são criadas como resultado da função de renderização, você não pode acessá-las na renderização inicial - elas ainda não existem! `$refs` também não é reativo, portanto, você não deve tentar usá-lo em modelos para vinculação de dados.

Referência 1: https://vuejs.org/v2/api/#ref

Referência 2: https://vuejs.org/v2/guide/components-edge-cases.html#Accessing-Child-Component-Instances-amp-Child-Elements

  
  
  

  

## Project setup

  

```

  

yarn install

  

```

  

  

### Compiles and hot-reloads for development

  

```

  

yarn serve

  

```

  

  

### Compiles and minifies for production

  

```

  

yarn build

  

```

  

  

### Lints and fixes files

  

```

  

yarn lint

  

```

  

  

### Customize configuration

  

See [Configuration Reference](https://cli.vuejs.org/config/).