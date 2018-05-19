<template>
  <section class="container">
    <div>
      <h1>All dogs</h1>
    </div>
  </section>
</template>

<script>
    import Rehive from 'rehive';

    const rehive = new Rehive({storageMethod: 'local'});
    export default {
        data: function() {
            return {
                dogs: [],
            }
        },
        methods: {
            getDogs: function() {
                rehive.admin.users.get({
                    filters: {
                        metadata__type: 'dog'
                    }
                }).then((res) => {
                    this.dogs = res.results;
                    console.log('res is', res);
                }, function (err) {
                    console.log('an error occured', err);
                });
            },
            tipDog: function() {
                rehive.transactions.createTransfer(
                {
                    amount: 100,
                    recipient: "7660da2d-097a-410a-9089-bfbf72629fd9",
                    currency: "ZAR"
                }).then(function(res){
                    console.log('tip successful');
                },(err) => {
                    console.log('an error occured doing the transfer', err);
                    alert('An error occured');
                })
            }
        },
        created() {
            console.log('hello');
            this.getDogs();
            // this.tipDog();
        }
    }
</script>

<style>
.test{
  height: 400px;
  width: 400px;
}
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; /* 1 */
  display: block;
  font-weight: 300;
  font-size: 50px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 30px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
