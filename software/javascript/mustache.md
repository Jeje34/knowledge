# Mustache

## Instructions if/else

    <span>
        {{#like}}
            Like <!-- If {like: true} --->
        {{/like}}
        {{^like}}
            Unlike <!-- If {like: false} --->
        {{/like}}
    </span>