---
title: 'Besoin d''aide ?'
template: form
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

# Besoin d'aide ?

<h3>Connectez-vous au salon de support</h3>
<center>
<div class="alert alert-info" markdown="1" style="max-width:750px;">
<strong>ProTips™</strong>
<ul style="text-align:left;">
<li>Pas besoin de demander si vous pouvez poser une question - posez-la directement !</li>
<li><em>Soyez patient</em>, cela peut prendre plusieurs minutes avant que quelqu'un remarque vos messages.</li>
</ul>
</div>
<strong>Pseudonyme</strong> : <input id="nickname" value="foobar" type="text">
</br>
</br>
<button id="joinChatroom" type="button" class="btn btn-success" style="font-weight:bold;">
            <span class="glyphicon glyphicon-comment"></span> Rejoindre le salon
</button>
</br>
</br>
<em>Note : vous pouvez aussi vous connecter via votre client XMPP favori à</br>
support@conference.yunohost.org</em>
</center>

<h3>... ou demandez sur le forum !</h3>

<center>
<button id="goForum" type="button" class="btn btn-success" style="font-weight:bold;">
            <span class="glyphicon glyphicon-comment"></span> Aller sur le forum
          </button>
</center>

<h3>Vous avez trouvé un bug ?</h3>

<center>
<br>
<em>Vous pouvez rapporter le bug sur le bugtracker ou contacter les développeurs</em><br><br>
<button id="goBugtracker" type="button" class="btn btn-warning" style="font-weight:bold;">
            <span class="glyphicon glyphicon-exclamation-sign"></span> Rapporter un bug
          </button>
<button id="goDevroom" type="button" class="btn btn-warning" style="font-weight:bold; margin-left:40px">
            <span class="glyphicon glyphicon-comment"></span> Contacter les développeurs
          </button>
</br>
</br>
<em>Note : vous pouvez aussi vous connecter aux salons de dev, via votre client XMPP favori, à</br>
dev@conference.yunohost.org et apps@conference.yunohost.org</em>
</center>

<script>
document.getElementById("joinChatroom").onclick = function() {
    var nickname = document.getElementById("nickname").value;
    window.location.href = "https://chat.yunohost.org/?nick="+nickname;
}
document.getElementById("goForum").onclick = function() {
    var nickname = document.getElementById("nickname").value;
    window.location.href = "https://forum.yunohost.org/latest";
}
document.getElementById("goBugtracker").onclick = function() {
    window.location.href = "https://dev.yunohost.org/projects/yunohost/issues";
}
document.getElementById("goDevroom").onclick = function() {
    window.location.href = "https://chat.yunohost.org/";
}
</script>


## Formulaire de contact
Merci de remplir tout les champs. Nous vous répondrons dès que possible.
