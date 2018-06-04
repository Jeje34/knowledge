- Client header :  Accept: application/json


@RestController
public class TestRestController {

	@RequestMapping(value = "/getTest", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
	BeanTest readBookmarks() {
		return new BeanTest(1L, "dsejsd");
	}
}