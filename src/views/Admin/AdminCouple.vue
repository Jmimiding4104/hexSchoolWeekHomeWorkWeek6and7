<template>
    <div class="container">
        <div class="text-end mt-4">
            <button class="btn btn-primary">
                建立新的折扣券
            </button>
        </div>
        <table class="table mt-4">
            <thead>
                <tr>
                    <th>名稱</th>
                    <th>折扣百分比</th>
                    <th>到期日</th>
                    <th>是否啟用</th>
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
