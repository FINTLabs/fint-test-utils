# FINT test utils

## Installation
```groovy
testCompile('no.fint:fint-test-utils:0.0.1')
```

## MockMvcSpecification

Simplifies the setup required to create `MockMvc` tests with [spock](http://spockframework.org/).

```groovy
class TestControllerSpec extends MockMvcSpecification {
    private TestController controller
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
    }
}
```