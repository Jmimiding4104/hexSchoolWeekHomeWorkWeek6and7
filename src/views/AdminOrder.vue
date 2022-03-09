<template>
    <div class="container">
        <table class="table mt-4">
            <thead>
                <tr>
                    <th>購買時間</th>
                    <th>電子信箱</th>
                    <th>購買款項</th>
                    <th>應付金額</th>
                    <th>是否付款</th>
                    <th>編輯</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="item in products" :key="item.id">
                    <td>{{item.category}}</td>
                    <td>{{item.title}}</td>
                    <td class="text-end">{{item.origin_price}}</td>
                    <td class="text-end">{{item.price}}</td>
                    <td>
                        <span
                        :class="{'text-success' : item.is_enabled , 'text-danger' : !item.is_enabled}"
                        >
                        {{item.is_enabled?'啟用':'未啟用'}}
                        </span>
                    </td>
                    <td>
                        <div class="btn-group">
                            <button
                                type="button"
                                class="btn btn-outline-primary btn-sm"
                                @click="openModal('edit', item)"
                            >
                                編輯
                            </button>
                            <button
                                type="button"
                                class="btn btn-outline-danger btn-sm"
                                @click="openModal('del', item)"
                            >
                                刪除
                            </button>
                        </div>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
  data () {
    return {
      orders: []
    }
  },
  methods: {
    getOrder () {
      const apiUrl = `${process.env.VUE_APP_API}/api/${process.env.VUE_APP_PATH}/admin/orders`
      this.$http.get(apiUrl, this.tempProduct)
        .then((res) => {
          res.data.orders = this.orders
          console.log(res)
        })
        .catch((err) => {
          console.log(err)
        })
    }
  },
  mounted () {
    this.getOrder()
  }
}
</script>
