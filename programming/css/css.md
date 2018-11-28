# CSS

## 2 div side by site

    <section class="container">
        <div class="one"></div>
        <div class="two"></div>
    </section>
    
<br>

    .container {
        width: 80%;
        height: 200px;
        background: aqua;
        margin: auto;
        padding: 10px;
    }
    .one {
        width: 15%;
        height: 200px;
        background: red;
        float: left;
    }
    .two {
        margin-left: 15%;
        height: 200px;
        background: black;
    }
    
## Remove the pointer cursor on a link

    a {
        cursor: default;
    }
    