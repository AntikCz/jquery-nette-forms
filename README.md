# Client-side pro Nette forms

## Instalace

```html
<script src="{$basePath}/js/jquery.js"></script>
<script src="{$basePath}/js/netteForms.js"></script>
<script src="{$basePath}/js/jquery.nette.forms.js"></script>
<script>
    $.form.init();
</script>
```

## Konfigurace

```html
    $.form.liveValidationUrl = {link validate!}; // Optional - Glob�ln� nastaven� pro live validaci
    $.form.useLabels = true; // V�choz� true - P�i hodnot� true a p�i renderu chyb u formul��e bere label pole a p�id� k chybov� zpr�v�
```

Pro dynamicky p�idan� formul��e m��eme p�i�adit validaci za pomoc�:

```html
    $.form.refresh();
```

## Nastaven� formul��e p�es data atributy

### data-novalidate

Vynech� validaci cel�ho formul��e.

```html
    <form n:name="name" data-novalidate>
```

### data-novalidatelive

Vynech� live validaci cel�ho formul��e.

```html
    <form n:name="name" data-novalidatelive>
```

### data-error-container

Nastav� vlastn� container pro chybov� hl�ky

```html
    <div id="myContainer"></div>
    
    <form n:name="name" data-error-container="#myContainer">
```

### data-error-type

Nastav� container pro jednu chybovou hl�ku.

```html
    <form n:name="name" data-error-type="strong class='input-error'">
```

Vygeneruje:

```html
    <div class="form-error-container">
        <strong class="input-error">Tato polo�ka je povinn�.</strong>
    </div>
```

### data-renderer 

Nastav� renderer.

```html
    <form n:name="name" data-renderer="myRenderer">
```

### data-nolabel

Vynech� chybovou hl�ku s label.

```html
    <form n:name="name" data-nolabel>
```

## Nastaven� pole p�es data atributy

### data-validatelive-url

Na danou url adresu se po�lou �daje k vyhodnocen�.

```html
    <input n:name="name" data-validatelive-url="{link validateName!}">
```

### data-novalidatelive

Live validace se u tohoto pole neprovede

```html
    <input n:name="name" data-novalidatelive>
```

### data-error-container

Nastav� vlastn� container pro chybov� hl�ky

```html
    <input n:name="name" data-error-container="#customContainer">
    
    <div id="customContainer"></div>
```

### data-error-type

Nastav� container pro jednu chybovou hl�ku.

```html
    <input n:name="name" data-error-type="strong class='input-error'">
```

Vygeneruje:

```html
    <div class="form-error-container">
        <strong class="input-error">Tato polo�ka je povinn�.</strong>
    </div>
```

### data-novalidate

Pole bude p�esko�eno p�i validaci.

```html
    <input n:name="name" data-novalidate>
```

### data-label

Nastav� label pro chybovou hl�ku.

```html
    <input n:name="name" data-label="U�ivatelsk� jm�no">
```

### data-nolabel

Vynech� chybovou hl�ku s label.

```html
    <input n:name="name" data-nolabel>
```

## Nastaven� odes�lac�ch tla��tek p�es data atributy

### data-novalidate

Vynech� validaci formul��e po kliknut� na dan� tla��tko.

```html
    <input n:name="back" data-novalidate>
```

## Vlastn� renderery

```javascript

$.form.addRenderer('render', {
    /**
     * Error at control
     *
     * @param {string} message
     * @param {SingleControl} ctrl
     */
    controlError: function (message, ctrl) {
        // Odstran�n� chyby u pole
    },
    /**
     * Errors at form
     *
     * @param {string} message
     * @param {SingleControl} ctrl
     */
    formError: function (message, ctrl) {
        // P�id�n� chyby u formul��e
    },
    /**
     * Base method for adding error message
     *
     * @param {string} message
     * @param $container
     * @param {SingleControl} ctrl
     * @param {string} type
     */
    addError: function (message, $container, ctrl, type) {
        // P�id�n� chyby
    },
    /**
     * Base method for removing error message
     *
     * @param $container
     * @param {SingleControl} ctrl
     */
    removeCustomError: function ($container, ctrl) {
        // Odstran�n� chyby 
    },
    /**
     * Method which removes error message at control
     *
     * @param {SingleControl} ctrl
     */
    removeError: function (ctrl) {
        // Odstran�n� chyby u pole
    },
    /**
     * Method which removes error message at form
     *
     * @param {SingleControl} ctrl
     */
    removeFormError: function (ctrl) {
        // Odstran�n� chyby u formul��e
    }
});

```