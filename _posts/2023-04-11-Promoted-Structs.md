---
title: Promoted Structsbundle
date: 2023-04-11 16:00:00 +/-TTTT
categories: [TOP_CATEGORIE, SUB_CATEGORIE]
tags: [golang]     # TAG names should always be lowercase
---

## Promoted Structsbundle

```
package main

import (
	"encoding/json"
	"fmt"
)

func main() {
	u := User{ID: 1, Name: "Matt", Password: "Secret"}
	userView := UserView{User: &u}
	fmt.Printf("Password: %s\n", u.Password)
	fmt.Printf("Password: %s\n", userView.Password)

	json, err := json.Marshal(userView)
	if err != nil {
		fmt.Println(err)
	}
	fmt.Println(string(json))
}

type User struct {
	ID       int    `json:"id" db:"id"`
	Name     string `json:"name" db:"name"`
	Password string `json:"password_hashed" db:"password_hashed"`
}

type UserView struct {
	*User
	Password string `json:"password_hashed,omitempty" db:"password"`
}
```