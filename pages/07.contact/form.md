---
template: form
title: Contact
form:
    name: contact
    classes: 'well col-md-6'
    fields:
        -
            name: name
            label: Nom
            placeholder: 'Saisissez votre nom'
            autofocus: 'on'
            autocomplete: 'on'
            type: text
            classes: 'form-control form-group'
            validate:
                required: true
        -
            name: email
            label: Email
            placeholder: 'Saisissez votre adresse email'
            type: text
            classes: 'form-control form-group'
            validate:
                rule: email
                required: true
        -
            name: website
            type: honeypot
        -
            name: message
            label: Message
            size: long
            placeholder: 'Rédigez votre message'
            type: textarea
            classes: 'form-control form-group'
            rows: '5'
            validate:
                required: true
        -
            name: captcha
            label: 'Combien font 2 fois vingt-et-un ?'
            placeholder: 'Cette question a pour but de vérifier que vous êtes bien un humain'
            type: text
            classes: 'form-control form-group'
            validate:
                pattern: '42'
                required: true
    buttons:
        -
            type: submit
            value: Envoyer
            classes: 'btn btn-primary text-uppercase'
    process:
        -
            email:
                from: '{{ config.plugins.email.from }}'
                to: ['{{ config.plugins.email.from }}', '{{ form.value.email }}']
                subject: '[Message] {{ form.value.name|e }}'
                body: '{% include ''forms/data.html.twig'' %}'
        -
            save:
                fileprefix: feedback-
                dateformat: Ymd-His-u
                extension: txt
                body: '{% include ''forms/data.txt.twig'' %}'
        -
            message: 'Merci pour votre message !'
        -
            display: merci
---

# Nous contacter

## Adresse

12 rue de la liberté  
Bâtiment VI  
69 007 Lyon

## Téléphone / Fax

**Bureau :** 01 23 45 67 89  
**Mobile :** 01 23 45 67 89  
**Fax :** 01 23 45 67 89

## Horaires

Ouvert du **lundi au vendredi** de **13:37 à 14:42**  
Fermé Samedi et Dimanche

## Formulaire de contact
Merci de remplir tout les champs. Nous vous répondrons dès que possible.
