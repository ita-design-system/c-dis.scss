# c-dis.scss

[Démo et documentation](https://ita-design-system.github.io/c-dis.scss/)

Composant CSS dédié à la propriété display des éléments. 

## Scope

Liste des propriétés CSS prises en charge par le composant

* align-items
* backface-visibility
* clear
* display
* justify-content
* flex
* flex-basis
* flex-direction
* flex-flow
* flex-shrink
* flex-wrap
* float
* gap
* grid-gap
* grid
* grid-area
* grid-auto-columns
* grid-auto-flow
* grid-auto-rows
* grid-column
* grid-column-end
* grid-column-start
* grid-row
* grid-row-end
* grid-row-start
* grid-template
* grid-template-areas
* grid-template-columns
* grid-template-rows
* row-gap
* place-content
* place-items
* place-self
* table-layout
* visibility
* -webkit-box-orient
* -webkit-line-clamp

## Typologie d'un composant générique

```scss
// SCSS map
$briks-components-generic: ( 
    // SCSS map | Nom du composant
    NOM_DU_COMPOSANT: ( 
        // Boolean | Composant activé true ou false
        enabled: true, 
        // Boolean | Responsive activé true ou false
        responsive: true, 
        // SCSS map | Liste des propriétés du composant par défaut (c-dis seul)
        defaults: (), 
        // SCSS map | Liste des modifieurs
        modifiers: () 
    )
);
```

## Configuration

Organisation et description du fichier de configuration [_sass/_dis_generic.scss](_sass/_dis_generic.scss).

```scss
/*
    C-DIS
    v0.1.0
    Composant générique CSS ITADS
    https://github.com/ita-design-system/c-dis.scss
*/
// SCSS map
$briks-components-generic: ( 
    // Nom du composant
    dis: ( 
        // Composant activé true ou false
        enabled: true, 
        // Responsive activé true ou false
        responsive: true, 
        // Liste des propriétés c-dis par défaut
        defaults: (
            --ita-gap: 0px,
            gap: var(--ita-gap)
        ),
        // Rendu: 
        // c-dis {
        //      --ita-gap: 0px;
        //      gap: var(--ita-gap);
        // }
        // Liste des modifieurs contenant chacun une liste de propriétés qui 
        // soit surchargent les propriétés par défaut
        // soit ajoutent des propriétés
        // soit les deux
        modifiers: ( 
            // c-dis m-none
            none: (
                display: none
            ),
            // c-dis m-inline
            inline: (
                display: inline
            ),
            // c-dis m-block
            block: (
                display: block
            ),
            // c-dis m-inline-block
            inline-block: (
                display: inline-block
            ),
            // c-dis m-flex
            flex: (
                display: flex
            ),
            // c-dis m-inline-flex
            inline-flex: (
                display: inline-flex
            ),
            // c-dis m-grid
            grid: (
                display: grid
            ),
            // c-dis m-inline-grid
            inline-grid: (
                display: inline-grid
            ),
            // c-dis m-webkit-box (utile pour les ellipses à plusieurs lignes)
            webkit-box: (
                display: -webkit-box
            ),
            // FLEX
            // Axe main
            // c-dis m-flex m-main-start
            main-start: ( 
                justify-content: flex-start
            ),
            // c-dis m-flex m-main-center
            main-center: ( 
                justify-content: center
            ),
            // c-dis m-flex m-main-end
            main-end: (
                justify-content: flex-end
            ),
            // c-dis m-flex m-main-space-between
            main-space-between: ( 
                justify-content: space-between
            ),
            // c-dis m-flex m-main-space-around
            main-space-around: ( 
                justify-content: space-around
            ),
            // c-dis m-flex m-main-space-evenly
            main-space-evenly: ( 
                justify-content: space-evenly
            ),
            // Axe cross
            // c-dis m-flex m-cross-center
            cross-center: ( 
                align-items: center
            ),
            // c-dis m-flex m-cross-baseline
            cross-baseline: ( 
                align-items: baseline
            ),
            // c-dis m-flex m-cross-start
            cross-start: ( 
                align-items: flex-start
            ),
            // c-dis m-flex m-cross-end
            cross-end: ( 
                align-items: flex-end
            ),
            // Wrap / retour à la ligne
            // c-dis m-flex m-nowrap
            nowrap: ( 
                flex-wrap: nowrap
            ),
            // c-dis m-flex m-wrap
            wrap: ( 
                flex-wrap: wrap
            ),
            // c-dis m-flex m-wrap-reverse
            wrap-reverse: ( 
                flex-wrap: wrap-reverse
            ),
            // Direction
            // c-dis m-flex m-column
            column: ( 
                flex-direction: column
            ),
            // c-dis m-flex m-column-reverse
            column-reverse: ( 
                flex-direction: column-reverse
            ),
            // c-dis m-flex m-cross-row-reverse
            row-reverse: ( 
                flex-direction: row-reverse
            ),
            // ELLIPSE 2 lignes
            // A utiliser avec c-txt et c-dim
            // c-dis m-webkit-box
            // c-dim m-o-hidden
            // c-txt m-ellipsis-2
            ellipsis-2: (
                '-webkit-box-orient': vertical,
                '-webkit-line-clamp': 2
            ),
            // ELLIPSE 3 lignes
            // A utiliser avec c-txt et c-dim
            // c-dis m-webkit-box
            // c-dim m-o-hidden
            // c-txt m-ellipsis-3
            ellipsis-3: (
                '-webkit-box-orient': vertical,
                '-webkit-line-clamp': 3
            ),
        )
    )
);
``` 

## Extensions

Il est possible d'étendre les fonctionnalités du composant en ajoutant simplement un point d'entrée avec une déclaration `$briks-components-generic` à la typologie identique mais avec des propriétés par défaut et des modifieurs qui surchargent ou ajoutent des propriétés CSS.

L'exemple suivant reprend la logique de l'extension de composant en y ajoutant des gaps disbox.

```scss
/*
    C-DIS EXTENSION
    Extension du composant générique c-dis
    https://github.com/ita-design-system/c-dis.scss
    Ce fichier doit servir à étendre ou surcharger les fonctionnalités
    du composant c-dis selon les besoins du projet
*/
$briks-components-generic: (
    // Nom du composant, obligatoirement dis
    dis: ( 
        // Extension activée true ou false
        enabled: true, 
        // Responsive activée true ou false pour l'extension
        responsive: true, 
        // Valeurs par défaut de l'extension
        defaults: (),
        // Liste des modifieurs contenant chacun une liste de propriétés qui 
        // soit surchargent les propriétés par défaut
        // soit ajoutent des propriétés
        // soit les deux
        modifiers: ( 
            // Gap
            // Surcharge de la variable CSS --ita-gap pour compatibilité avec c-dim
            gap-1: ( // c-dis m-gap-1
                --ita-gap: my-spacing(2)
            ),
            gap-2: ( // c-dis m-gap-2
                --ita-gap: my-spacing(4)
            ),
            gap-3: ( // c-dis m-gap-3
                --ita-gap: my-spacing(8)
            )
        )
    )
);
```
