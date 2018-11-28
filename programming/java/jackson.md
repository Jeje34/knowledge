# Jackson

## Mapping Object or List depending on JSON input

    public class CustomerDetailsResponse {
        @JsonFormat(with = JsonFormat.Feature.ACCEPT_SINGLE_VALUE_AS_ARRAY)
        @JsonProperty("WET_CUST")
        private List<WetCust> listCustomers;
    }
    
If JSON input is a JSON Object instead of a JSON Array, allows to avoid following Exception :

    com.fasterxml.jackson.databind.JsonMappingException: Can not deserialize instance of java.util.ArrayList out of START_OBJECT token_ at

when 

    CustomerDetailsResponse response = mapper.readValue(json, CustomerDetailsResponse.class);
    	    
## Ignore any unknown properties in JSON input

    @JsonIgnoreProperties(ignoreUnknown = true)
    public class Foo {
        ...
    }