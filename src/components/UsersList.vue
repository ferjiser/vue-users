
    <template>
    <div>
        <slot></slot>
        <ul id="user-list" class="loaded">
            <li v-for="user in users"  :key="user.username">
                <img :src="user.image" :alt="`${user.name.first} ${user.name.last}`">
                <div>
                    <slot name="title" :user="user">
                         <span class="name">
                              {{user.name.first}} {{user.name.last}}
                        </span>
                    </slot>
                    <slot name="subtitle" :user="user">
                        <span class="fa fa-user">
                            {{user.username}}
                        </span>
                    </slot>
                    <slot name="address" :user="user">
                        <span class="fa fa-map-marker loc">
                            {{user.address}}
                        </span>
                    </slot>
                </div>
            </li>
        </ul>
    </div>
    </template>
    

    <script>
    export default {
        name: 'UsersList',
  data(){
    return{
      users: []
    }
  },
  created(){
   fetch("https://randomuser.me/api/?results=10")
                    .then(response => response.json())
                    .then(data => {
                      this.users = data.results.map(user => ({
                          name: user.name,
                          username: user.login.username,
                          address: user.location.street,
                          image: user.picture.thumbnail
                      }))
                    }
                )
  }
        
    }
    </script>

    <style lang="scss">
      @import url("https://fonts.googleapis.com/css?family=Oxygen:400,700,300");
      @import url("https://maxcdn.bootstrapcdn.com/font-awesome/4.3.0/css/font-awesome.min.css");
     
       #user-list {
        max-width: 550px;
        margin: 2em auto;
        padding: 0;
      }
      #user-list > li {
        margin: .2rem auto;
        cursor: pointer;
        list-style: none;
        padding: .25rem;
        width: 100%;
      }
      #user-list > li div {
        display: inline-block;
        vertical-align: middle;
      }
      #user-list > li span {
        clear: both;
        display: block;
        padding: .1rem .2rem;
        font-size: 1rem;
      }
      #user-list > li span.name {
        text-transform: capitalize;
        font-size: 1.6rem;
        font-weight: 200;
        margin-bottom: .25rem;
        border-bottom: 1px solid rgba(0, 0, 0, 0.25);
      }
      #user-list > li span.loc {
        text-transform: capitalize;
      }
      #user-list > li span:after, #user-list > li span:before {
        opacity: .75;
        margin-right: .25rem;
      }
      #user-list > li img {
        vertical-align: middle;
        border-radius: 50%;
        margin: 0 1rem;
        border: 1px solid rgba(0, 0, 0, 0.25);
      }
      #user-list > li:hover .name, #user-list > li.active .name {
        text-shadow: 1px 1px 3px rgba(10, 10, 10, 0.2);
        font-weight: 600;
      }
      #user-list > li:hover img, #user-list > li.active img {
        -webkit-transform: scale(1.15);
                transform: scale(1.15);
        box-shadow: 0 0 5px rgba(0, 0, 0, 0.5);
      }
      #user-list > li.active img {
        border-color: #333;
        box-shadow: 0 0 10px rgba(10, 10, 10, 0.75);
      }
      #user-list > li.active:after {
        content: '\f00c';
        font-family: FontAwesome;
        position: relative;
        display: inline-block;
        font-size: 2rem;
        color: green;
        text-shadow: 0 0 5px rgba(50, 50, 50, 0.25);
        margin: 0 .5rem;
      }

</style>

    
