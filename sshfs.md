<header>

# SSH-FS

_Le File System de SSH, expliqué pour pouvoir monter des partages réseaux adhoc, avec n'importe quelles machines disposant de SSHFS, pour faciliter l'exploitation d'une arborescence de travail._

</header>

-   <details>
    <summary><strong>Résumé</strong>
    </summary>

    SSH-FS utilise SFTP, lui-même basé sur SSH. L'idée ici est de monté un lecteur réseau adhoc pour pouvoir travailler sur le répertoire d'une machine distante.

    </details>

-   <details>
    <summary><strong>Installation</strong>
    </summary>

    -   <details>
        <summary><strong>Sous Windows</strong>
        </summary>
        <br>
        <p>Deux paquets sont nécessaires, à installer dans l'ordre:

        1. WinFsp: https://github.com/winfsp/winfsp/releases
        2. SSHFS-Win: https://github.com/winfsp/sshfs-win/releases/
        <br>

        __WinFsp__ permet aux développeurs d'écrire leur propre système de fichier sous Windows.

        __SSHFS-Win__ vous permettra de mapper n'importe quel dossier d'une machine cible à portée de SSH.
        </p>
        </details>

    -   <details>
        <summary><strong>Sous Linux</strong>
        </summary>    
        Installation classique sous repo apt:

        ```
            sudo apt update
            sudo apt install sshfs
        ```
        </details>

    </details>

-   <details>
    <summary><strong>Montage du volume</strong>
    </summary>    

    -   <details>
        <summary><strong>Sous Windows</strong>
        </summary> 

        -   <details>
            <summary><strong>Graphiquement</strong>
            </summary>       
            
            Il est possible de faire le montage en interface graphique.

            Dans l'explorer, clique droit sur ![Ce_PC](images/ce_pc.png)

            Puis, ![Drive](images/connect_drive.png)

            Et enfin renseigner le chemin du montage, avec le nom de l'utilisateur de connexion et la machine cible (IP ou DNS):

            ![Chemin](images/chemin.png)

            Une fenêtre de connexion s'affichera pour renseigner les identifiants.

            Pour les subtilités de l'appel ~~non pas du 18 juin, ni celui de la forêt, ou encore du râteau~~ mais du chemin, cf. infra.
            
            </details>

        -   <details>
            <summary><strong>Par PowerShell</strong>
            </summary> 

            L'outil `net use` est ton ami:
            ```powershell
            net use X: \\sshfs\bob@0.0.0.0\..\..\etc /user:bob
            ```

            L'option `/user:` est optionnelle, elle évite de retaper le login de connexion qui sera demandé par la suite.

            Il est possible de gérer la connexion par clés SSH, comme pour une connexion SSH classique.                
            </details>

    -   <details>
        <summary><strong>Sous Linux</strong>
        </summary>    

        </details>
    
    
    </details>