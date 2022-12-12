<!-- ENTETE -->
[![img](https://img.shields.io/badge/Cycle%20de%20Vie-Phase%20D%C3%A9couverte-339999)](https://www.quebec.ca/gouv/politiques-orientations/vitrine-numeriqc/accompagnement-des-organismes-publics/demarche-conception-services-numeriques)
[![License](https://img.shields.io/badge/License-LiLiQ--P-blue)](LICENSE)

---

<div>
    <a target="_blank" href="https://www.quebec.ca/gouvernement/ministere/cybersecurite-numerique">
      <img src="https://github.com/CQEN-QDCE/.github/blob/main/images/mcn.png" alt="Logo du Ministère de la cybersécurité et du numérique" />
    </a>
</div>
<!-- FIN ENTETE -->

<!-- PROJET -->
# Client Go pour approvisionnement SCIM du service AWS Single Sign-On

Client SCIM extrait du projet https://github.com/awslabs/ssosync pour importation en module Go.

## 1.0 Objectifs

Le service AWS Single Sign-On expose un API d'approvisionnement d'usagers basé sur le standard SCIM. Ce module Go implémente un client permettant d'exploiter cet API.

## 2.0 Installation

```
go get github.com/CQEN-QDCE/aws-sso-scim-goclient
```

## 3.0 Exemple
```
import (
	"fmt"
	scim "github.com/CQEN-QDCE/aws-sso-scim-goclient"
)

const SCIM_ENDPOINT = "*YOUR_ENDPOINT*"
const SCIM_TOKEN = "*YOUR_TOKEN*"

awsClient, err := scim.NewClient(
    &http.Client{},
    &scim.Config{
        Endpoint: SCIM_ENDPOINT,
        Token:    SCIM_TOKEN,
    })

if err != nil {
    //return err
}

listUsers, err := awsClient.GetUsers()

if err != nil {
    //return err
}

for _, user := range listUsers {
    println(user.Username)
}
```


## 4.0 Licence