## Les principales commandes Ansible

Ansible est livré avec un certain nombre de commandes permettant soit de lancer des actions ou, soit d'obtenir de l'information sur l'environnement d'exécution Ansible :

`ansible` : Permet d'exécuter un simple module ansible sur un inventaire. Vu ci-dessus dans le premier test.
`ansible-console` : Ouvre une console interactive permettant de lancer plusieurs actions sur un inventaire.
`ansible-config` : Affiche l'ensemble des paramètres Ansible. ansible-config [list|dump|view].
    list : affiche la liste complète des options d'Ansible à disposition.
    dump : affiche la configuration dans le contexte actuel.
    view : affiche le contenu d'un fichier de configuration Ansible
`ansible-playbook` : Exécute un playbook Ansible sur un inventaire. La plus connue.
`ansible-vault` : Permet de chiffrer des données qui ne doivent être divulgué.
`ansible-inventory` : Affiche l'ensemble des données d'un inventaire Ansible.
`ansible-galaxy` : permet d'installer des roles et des collections Ansible
`ansible-doc` : Permet de lister l'ensemble des composants Ansible à disposition sur le nœud d'execution ansible-doc -l -t [type] type parmi: become, cache, callback, cliconf, connection,httpapi, inventory, lookup, netconf, shell, vars, module, strategy.


# REFERENCES

Si vous voulez continuer votre apprentissage d'ansible, je conseille de lire les billets suivants :

    Joel Seguillon : Ansible, une meilleure expérience est possible !
    L’écriture de playbooks Ansible plus évolués permettant de configurer et d’installer une application. Mais nous y arborerons aussi d'autres notions comme les variables Ansible, les boucles et conditions Ansible et les templates Ansible.
    Pour vous assister dans l'écriture de playbooks, je vous conseille d'utiliser l'outil Ansible-Lint et l'extension vscode Ansible
    Pour améliorer la qualité de votre code, je conseille l'outil spotter.
    Pour écrire correctement des playbooks Ansible, il faut le faire avec du TDD (Test-Driven Development) qui consistent à écrire un playbook par itération, en écrivant chaque test avant d'écrire la solution.
    Dans certains cas vous pouvez être obligé de recourir aux modules de commandes comme shell et command. Comment les utiliser correctement ?
    Pour éviter de vous répéter sans cesse, il faut développer des rôles. Voyons comment écrire vos propres rôles Ansible
    Un billet expliquant comment structurer ses developpements Ansible
    Pour éviter de subir une attaque, protégez vos secrets avec Ansible Vault
    Pour tester les résultats de vos rôles, vous pouvez utiliser molecule
    Maintenant que vous connaissez une grande partie des concepts important d'Ansible, il est temps de lire mes bonnes pratiques.
    La suite sur les tips avec au menu tous les moyens pour optimiser les temps d'exécution des playbooks
    La sécurité est notre priorité et il ne faut pas l'oublier quand on code avec Ansible. C'est pourquoi je vous propose un environnement de développement ansible intégrant OpenScap.
    Si vous avez besoin de variables dynamiques dans vos inventaires, vous pouvez utiliser des customs facts
    Pour manipuler vos variables, vous avez à votre disposition les filtres Ansible. 1, 2 et 3
    Pour générer des fichiers de configurations, des lignes de commandes, vous pouvez recourir aux templates Jinja.
    Pour vous aider à comprendre le fonctionnement des principaux modules Ansible :
        Gérer les packages des distributions linux avec les modules Ansible
        Gérer le contenu de fichiers avec les modules LineInfile et BlockInfile
        Gérer les services avec les modules service et service_facts
        Les principaux modules pour gérer les fichiers
        Checker les prérequis avec le module assert
    Ansible est un gestionnaire de configuration, on se doit de gérer ses inventaires. Mais cela demande de comprendre la précédence d'Ansible.
    Parfois les inventaires statiques ne suffisent plus et c'est qu'interviennent les inventaires dynamiques d'ansible
    Pour simplifier le décryptage de la sortie des commandes avec le filtre jc
    Ansible et les taches asynchrones
    Comment distribuer tout ce qui compose un environnement Ansible avec les collections Ansible
    Ansible ne permet pas que de piloter la configuration de machines Linux ! On peut également gérer des machines tournant sous Windows avec Ansible
    Pour répondre à vos questions.


# ansible-vagrant-terraform-kitchen-inspec

KVM : https://www.cyberciti.biz/faq/install-kvm-server-debian-linux-9-headless-server/
