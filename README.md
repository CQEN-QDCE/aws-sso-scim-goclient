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