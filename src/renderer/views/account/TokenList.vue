<template>
  <div class="box bplist-box">
    <table class="table data-table">
      <thead>
        <tr>
          <th>{{$t('序号')}}</th>
          <th>{{$t('符号')}}</th>
          <th>{{$t('发行人')}}</th>
          <th class="t_l">{{$t('最大发行量')}}</th>
          <th class="t_l">{{$t('目前发行量')}}</th>
          <th>{{$t('我的余额')}}</th>
          <th>{{$t('操作')}}</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(token, index) in account.tokenList" :key="token.token">
          <td>{{index + 1}}</td>
          <td>({{token.symbol}}, {{token.precision}})</td>
          <td>{{token.issuer}}</td>
          <td class="t_l">{{token.max_supply | formatNumber({showSymbol: true})}}</td>
          <td class="t_l">{{token.supply | formatNumber({showSymbol: true})}}</td>
          <td>{{token.balance | formatNumber({showSymbol: true})}}</td>
          <td>
            <router-link class="button is-small is-outlined" :to="{name: 'tokenTransfer', params: { symbol: token.symbol, precision: token.precision }}">转账</router-link>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import { mapState } from 'vuex';

export default {
  name: 'TokenList',
  computed: {
    ...mapState(['account']),
  },
};
</script>

<style scoped>
.button {
  padding-left: calc(0.625em - 1px);
  padding-right: calc(0.625em - 1px);
}
.is-button span {
  background: #408ee1;
  border-radius: 5px;
  color: #fff;
  border: none;
  padding-left: calc(0.625em - 1px);
  padding-right: calc(0.625em - 1px);
  padding-bottom: calc(0.375em - 1px);
  padding-top: calc(0.375em - 1px);
  text-align: center;
  white-space: nowrap;
  cursor: pointer;
}
/* .bplist-box tbody .is-vote{
  display: none;
} */
.t_l {
  text-align: right !important;
}
</style>
