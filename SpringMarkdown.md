# Spring_Markdown

## spring

- GetMapping
- RequestMapping ( Get, Post, Delete, Put, Patch)
- 입력 방식 (PathVariable),(RequestParam)
- Requestbody

''' java

```java
package com.example.demo.ex01.d0512;

import org.springframework.web.bind.annotation.*;

import java.util.List;
import java.util.Map;

@RestController
@RequestMapping("/wine/a01")
public class P01 {
    @GetMapping("/getmapping/{id}")
    public List<Map<String, String>> GetMapping(@PathVariable String id) {
        return List.of(
                Map.of("GetMapping", "사용자가 Get 요청을 보냈을때 실행"),
                Map.of("get 요청", "데이터 조회 요청 방식"),
                Map.of("PathVariable", id)
        );
    }

    @RequestMapping(method = RequestMethod.GET, value = "get/{id}")
    public List<Map<String, String>> R_Get(@PathVariable String id) {
        return List.of(
                Map.of("RequestMapping", "주소를 공통으로 묶어주는 Mapping"),
                Map.of("RequestMapping_get", "RequestMapping Get 방식"),
                Map.of("PathVariable", id)
        );
    }

    @RequestMapping(method = RequestMethod.POST, value = "post")
    public List<Map<String, String>> R_Post(
            @RequestParam String id,
            @RequestBody @RequestParam String password
    ) {
        return List.of(
                Map.of("RequestMapping", "주소를 공통으로 묶어주는 mapping"),
                Map.of("RequestMapping_Post", "RequestMapping post 방식"),
                Map.of("RequestPram", id),
                Map.of("RequestBody", password)
        );
    }

    @RequestMapping(method = RequestMethod.DELETE, value = "delete")
    public List<Map<String, String>> R_Delete(
            @RequestParam String id
    ) {
        return List.of(
                Map.of("RequestMapping_Delete", "데이터 삭제할 때 사용하는 요청 방식"),
                Map.of("result", id + "삭제")
        );
    }

    @RequestMapping(method = RequestMethod.PUT, value = "put")
    public List<Map<String, String>> R_Put(
            @RequestParam(required = false, defaultValue = "전체 수정") String id
    ){
        if (id.equals("전체 수정")){
            return List.of(
                    Map.of("put","데이터를 수정할 때 사용하는 요청"),
                    Map.of("id",id+"완료")
            );
        }
        else{
            return List.of(
                    Map.of("put","데이터를 수정할 때 사용하는 요청"),
                    Map.of("id",id+"번 수정 완료")
            );
        }
    }

    @RequestMapping(method = RequestMethod.PATCH, value = "patch")
    public List<Map<String, String>> R_Patch(
            @RequestParam String id
    ){
        return List.of(
                Map.of("patch","데이터를 일부 수정할 때 사용하는 요청"),
                Map.of("id",id+"번 수정")
        );

    }
}
```

'''