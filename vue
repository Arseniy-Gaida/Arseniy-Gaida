<template>
  <div>
    <div class="card" v-for="user in users" :key="user.id">
      <div class="okno">
      <p class="anim">{{ user.title }}</p>
      <div class="picture"> <img src="https://object.pscloud.io/cms/cms/Photo/img_0_77_3414_0_1_320.webp">{{ user.image }}</div>
      <p>{{ user.description }}</p>
      </div>
    </div>
  </div>

   

</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      users: [],
    };
  },
  async mounted() {
    const { data } = await axios.get("http://localhost:5000/api/users");
    this.users = data;
  },
};
</script>

<style scoped>
.card {
   background-color: gray;
  margin: 6px 0px;
   
}

.card1 {
   background-color: gray;
  margin: 6px 0px;
   
}

.okno{
  width: 500px; height: 440px;
  border: 1px solid rgb(206, 197, 197);
  margin: 6px 0px; border-radius: 20px;
  background-color: rgb(233, 223, 223);
}
img{border-radius: 20px; box-shadow: 10px 10px 10px black; margin-left: 5px;}

p{color: rgb(51, 48, 48); font-family: arial;}

.anim{animation:shadow1  3s infinite ease-in-out;}
@keyframes shadow1 {
from {text-shadow: 0 0 3px black;}
50% {text-shadow: 0 0 20px black;}
to {text-shadow: 0 0 3px black;}
}
 

</style>









const express = require('express')
const cors = require('cors')
const app = express()
app.use(express.json())
app.use(cors())
const port = 5000
const users = [
   
  {
    id: 1,
  title: "СМАРТФОН SAMSUNG GALAXY S22 ULTRA 128GB WHITE",
  description: "Бесконтактная оплата, Датчик отпечатков пальцев, Поддержка 4G, Поддержка 5G, Пыле/-влагозащита, NFC",
  price: 749890,
  image: ""
  },

  {
    id: 2,
  title: "СМАРТФОН SAMSUNG GALAXY S22 ULTRA 128GB WHITE",
  description: "Бесконтактная оплата, Датчик отпечатков пальцев, Поддержка 4G, Поддержка 5G, Пыле/-влагозащита, NFC",
  price: 749890,
  image: ""
  },

  {
    id: 3,
  title: "СМАРТФОН SAMSUNG GALAXY S22 ULTRA 128GB WHITE",
  description: "Бесконтактная оплата, Датчик отпечатков пальцев, Поддержка 4G, Поддержка 5G, Пыле/-влагозащита, NFC",
  price: 749890,
  image: ""
  },

  {
    id: 3,
  title: "СМАРТФОН SAMSUNG GALAXY S22 ULTRA 128GB WHITE",
  description: "Бесконтактная оплата, Датчик отпечатков пальцев, Поддержка 4G, Поддержка 5G, Пыле/-влагозащита, NFC",
  price: 749890,
  image: ""
  },
]

app.get('/api/users', (req, res) => {
  res.send(users)
});

app.get('/api/users/:id', (req, res) => {
  const id = Number(req.params.id)
  const user = users.filter(x => x.id === id)[0]
  if (user) {
    return res.send(user)
  }
  else {
    return res.status(404).send({ msg: "Not found" })
  }

});

app.post('/api/users', (req, res) => {
  const id = users[users.length - 1].id + 1
  const user = Object.assign({id: id}, req.body);
  users.push(user)
  res.send(user)
});

app.put('/api/users/:id', (req, res) => {
  const id = Number(req.params.id)
  const idx = users.map((x, idx) => x.id === id ? idx:null).filter(x => typeof x === 'number')[0]
  if (typeof idx === 'number') {
    const user = Object.assign({id: users[idx].id}, req.body); 
    users[idx] = user
    return res.send(user) 
  }
  else {
    return res.status(404).send({ msg: "Not found" })
  }
});

app.delete('/api/users/:id', (req, res) => {
  const id = Number(req.params.id)
  const idx = users.map((x, idx) => x.id === id ? idx:null).filter(x => typeof x === 'number')[0]
  if (typeof idx === 'number') {
    const user = users.splice(idx,1)[0]
    return res.send(user)
  }
  else {
    return res.status(404).send({ msg: "Not found" })
  }
});

app.listen(port, () => {
  console.log(`Example app listening on localhost:${port}`)
})
