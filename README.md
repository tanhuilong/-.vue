
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://cdn.staticfile.org/vue/2.4.2/vue.min.js"></script>
    <style>
        [v-cloak] {
            display: none;
        }
        *{
            margin: 0;
            padding: 0;
        }
        body{
            font:15px/1.3 'Open Sans',sans-serif;
            color:#5e5b64;
            text-align: center;
        }
        a,a:visited{
            outline:none;
            color: #389dc1;
        }
        a:hover{
            text-decoration: none;
        }
        section,aside,header,footer,nav{
            display: block;
        }
        #main{
            background-color: #61a1bc;
            width:400px;
            border-radius: 3px;
            box-shadow: 0 1px 2px #ccc;
            padding:35px 50px;
            margin: 50px auto;
            
        }
        #main h1{
            color: #fff;
            font-size: 64px;
            font-family: 'Cookie',cursive;
            font-weight: normal;
            line-height: 1;
            text-shadow: 0 1px 2px #ccc;
        }

        #main ul li{
            color: #fff;
            font-size: 22px;
            padding: 20px 30px;
            background-color:#8ec16d;
            margin-bottom: 8px;
            box-shadow: 0 1px 2px #ccc;
            cursor: pointer;
            list-style: none;      
        }
        #main ul li span{
            float: right;
        }
       .red{background-color:  #e35885 !important;}
    </style>
</head>
<body>
    <div id="main">
        <h1>Services</h1>
        <ul>
            <li v-for="(service,index) in services" :class="service.active?'red':' '" :key="index" 
            @click="handlecolor(service)">{{service.name}} <span>{{service.price}}</span></li>
        </ul>
        <p>Total:{{nn}}</p>
    </div>
    <script>
        vue.filter('currency',function(value) {
            return '$'+value.toFixed(2)
        })
        var demo= new Vue ({
            el:'#main',
            data:{
               nn:0,
               services:[{
               name:'Web Development',
               price:300,
               active:true
             },{
               name:'Design',
               price:400,
               active:false
             },{
              name:'Integration',
              price:250,
              active:false
             },{
              name:'Training',
              price:220,
              active:false
             }]
            },
            methods:{
                handlecolor (service) {
                   service.active = !service.active;
                 this.getNN();
                },
                getNN() {
                    this.nn = 0;
                   this.services.forEach(item => {
                       if(item.active) {
                           this.nn += item.price;
                       }
                   });
                   console.log(this.nn);
                },
            },
            mounted(){
               this.getNN();
            },
        })
    </script>
</body>
</html>
