# Components compiler

Webpack compiler for creating frontend component. Build on top Twig templates, Scss and ES6 javascript.

## How to start

```
npm install
```

```
npm run server 
```
starts server on port 8001

```
npm run build
```
builds standalone HTML/CSS/JS component

## Creating your own component

All component source files are placed inside src directory. 
Component is loaded with component-loader, which contains all the data and options for component.

Component example (twig template)

```
{% set data = data|default('[{content:"No data"}]') %}
<div class="component">
    {% for item in data %}
        <p class="component_item">{{item.content}}</p>   
    {% endfor %}
</div>  
```

Component-loader example (twig template)

```
{% set data = [
    {
        "content": "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Recusandae illum ipsa in autem voluptatem amet, numquam sunt laudantium ullam magni."
    },
    {
        "content": "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Recusandae repellat, ullam nesciunt doloremque officia accusantium quod provident necessitatibus eaque, obcaecati tempore atque sequi. Modi deleniti quibusdam numquam vero consequuntur iusto quod, architecto ut aperiam soluta sit quis dignissimos delectus officiis laboriosam odit repellendus! Itaque reiciendis, repellat repellendus tempore laboriosam, sint."
    },
    {
        "content": "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Illum ex nam laudantium id at dolore, dolor aspernatur minus eveniet, reprehenderit nulla porro numquam aperiam! Sit, modi omnis harum, quod at vel officiis placeat fugiat a quis cumque asperiores consequuntur pariatur ipsum sapiente minus iure assumenda optio. Molestias dicta ipsa, vitae, nulla aspernatur quos rerum aperiam corporis, nesciunt nam delectus exercitationem dolores tempora repellat aut enim accusamus soluta aliquam reprehenderit libero in, officiis? Consequuntur similique illum aperiam facilis tempore, non dicta ipsum at autem dolorem! Libero reprehenderit minima ipsam sequi perspiciatis beatae dolorem officia, distinctio nisi ducimus adipisci, maxime sed, numquam dolor aut voluptate molestiae cum esse quasi rem. Id consequatur, veritatis animi nobis sunt qui necessitatibus quod dolore molestiae aliquam nihil voluptate explicabo, recusandae at non. Qui officiis libero nisi asperiores sunt nesciunt ex nostrum adipisci reprehenderit, facere aspernatur doloremque earum, aliquam voluptatum. Ex pariatur reprehenderit, fugit deleniti impedit accusantium quaerat ullam quisquam autem molestias soluta, voluptates nulla, beatae magnam nam maiores cupiditate! Deserunt voluptatibus ducimus, earum autem porro dolore modi! Recusandae ducimus laboriosam hic. Nam laboriosam reiciendis impedit consequuntur, iure accusamus nihil hic necessitatibus quaerat, ipsam optio maiores error minima aliquid delectus, voluptatum. Magni atque, veniam impedit perferendis consequatur."
    }
    ] %}

{% include '../src/component.html.twig' with {
    'data': data
} %}
```
CSS and JS files are bundled with webpack during *build/server* tasks.

## Used webpack loaders

- twig-loader
- babel-loader with ES2015 preset
- scss-loader
- css-loader