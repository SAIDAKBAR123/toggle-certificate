<template>
  <div id="print_bill" style="width: 300px; padding: 5px; font-family: sans-serif!important">
    <div style="display: flex; justify-content: center; margin: 20px">
      <span>Заказ № 2</span>
    </div>
    <div style="margin-bottom: 10px">
      <span style="margin-top: 10px; font-size: 14px; font-weight: 500"><b>Клиент:</b> Nodirbek Ergashev</span><br>
      <span style="margin-top: 10px; font-size: 14px; font-weight: 500"><b>Тел номер:</b> +998998998877</span><br>
      <span style="margin-top: 10px; font-size: 14px; font-weight: 500"><b>Адрес:</b> Toshkent shah, Yunusobod tum, 23 uy</span><br>
      <span style="margin-top: 10px; font-size: 14px; font-weight: 500"><b>Заказ принят:</b> 2/03/2020 21:32</span><br>
      <span style="margin-top: 10px; font-size: 14px; font-weight: 500"><b>Тип оплаты:</b> CASH</span><br>
      <!-- <span style="margin-top: 10px; font-size: 12px; font-weight: 500"><b>Тип оплаты:</b> client of dummy</span><br> -->
    </div>
    <hr style="width: 100%; border-top: 1px dashed black; margin-top: 5px">
    <div style="color: black; display: flex; width: 300px">
      <table style="width: 100%">
            <tr style="padding: 10px 0px">
            <th style="font-size: 13px; text-align:start">Наименование</th>
            <th style="font-size: 13px; text-align:start">К-во</th>
            <th style="font-size: 13px; text-align:start">Цена</th>
            <th style="font-size: 13px; text-align:start">Сумма</th>
          </tr>
          <tr v-for="item in parseInt(itemLength.count)" :key="item">
            <td style="font-size: 14px">посуда</td>
            <td style="font-size: 14px">X1</td>
            <td style="font-size: 14px">12 000</td>
            <td style="font-size: 14px">12 000</td>
          </tr>
      </table>
    </div>
    <hr style="width: 100%; border-top: 1px dashed black;">
    <div style="padding: 0px 10px; display: flex; justify-content: start;">
      <span style="margin-top: 10px; font-size: 15px">Общее кол-во: {{ itemLength.count }}</span>
    </div>
    <div style="padding: 0px 10px; display: flex; justify-content: space-between;">
      <span style="margin-top: 10px; font-size: 15px">Подитог</span>
      <span style="margin-top: 10px; font-size: 15px">32 300 сум</span>
    </div>
    <div style="padding: 0px 10px; display: flex; justify-content: space-between;">
      <span style="margin-top: 10px; font-size: 15px">Сумма доставки</span>
      <span style="margin-top: 10px; font-size: 15px">23 000 сум</span>
    </div>
    <div style=" padding: 0px 10px; display: flex; justify-content: space-between;">
      <span style="margin-top: 10px; font-size: 15px; font-weight: 500"><b>Итого к оплате</b></span>
      <span style="margin-top: 10px; font-size: 15px; font-weight: 500"><b>32 300 сум</b></span>
    </div>
    <div style="display: flex; justify-content: space-between; margin-top: 20px">
      <span style="margin-top: 10px; font-size: 15px; font-weight: 500">
        <b>Комментарии к заказу:</b> Lorem ipsum dolor sit, amet consectetur adipisicing elit. Nulla qui, fuga ea quae id ipsa possimus corrupti accusantium! Deserunt, non magnam? Earum dolore aperiam corrupti excepturi porro illo incidunt culpa.
      </span>
    </div>
    <div style="display: flex; justify-content: center; margin-top: 20px;">
      <h4>Спасибо за заказ ;)</h4>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    itemLength: {
      type: Object,
      required: true
    }
  },
  data () {
    return {
    }
  }
}
</script>

<style scoped>
table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

td, th {
  text-align: left;
  padding: 8px;
}

/* tr:nth-child(even) {
  background-color: #dddddd;
} */

</style>
