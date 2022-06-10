
# Installation

```
go get github.com/gitig/awdb-golang
```

# Example


```go
package main

import (
	"fmt"
	"log"
	"net"

	"github.com/gitig/awdb-golang/awdb"
)

func main() {
	db, err := awdb.Open("C:/Users/admin/Desktop/allawdb/IP_city_single_WGS84_awdb.awdb")
	if err != nil {
		log.Fatal(err)
	}

	defer db.Close()

	ip := net.ParseIP("166.111.4.100")

	var record interface{}
	err = db.Lookup(ip, &record)
	if err != nil {
		log.Fatal(err)
	}
	var resMap = record.(map[string]interface{})
	fmt.Printf("accuracy:%s", resMap["accuracy"])
	fmt.Println()
	fmt.Printf("%s", record)
}
```

# awdb-golang
www.ipplus360.com 官方支持的解析awdb格式的Golang代码(Official support for parsing Golang code in AWDB format )
# go版本建议
go version go1.14.4
# 依赖包
https://github.com/golang/sys.git
