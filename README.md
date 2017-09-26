# FINT test utils

## Installation
```groovy
repositories {
    maven {
        url  "http://dl.bintray.com/fint/maven" 
    }
}

testCompile('no.fint:fint-test-utils:0.0.4')
```

## MockMvcSpecification

Simplifies the setup required to create `MockMvc` tests with [spock](http://spockframework.org/).

```groovy
@WebMvcTest(TestController)
class TestControllerSpec extends MockMvcSpecification {
    private MockMvc mockMvc
 
    void setup() {
        controller = new TestController()
        mockMvc = standaloneSetup(controller)
    }
 

    def "Return status 200 OK"() {
        when:
        def response = mockMvc.perform(get('/test'))

        then:
        response.andExpect(status().isOk())
            .andExpect(jsonPathSize('$', 1))
            .andExpect(jsonPathEquals('$[0].test', '123'))
    }
}
```
