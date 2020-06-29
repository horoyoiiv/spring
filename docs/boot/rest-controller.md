
1. @RestController

* 예제 코드  
```java
@RestController
@RequestMapping("/api/v1")
public class ProfileController {

    @GetMapping("hello")
    public String hello(){
        return "Hello me!";
    }
}
```

* 요청 URI  
```
http://domain.com/context-path/api/v1/hello
```

2. @Request






