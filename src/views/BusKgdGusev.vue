<template>
  <div class="bus-kgd-gusev">

    <!-- Breadcrumb -->
    <section class="gs-container gs-container_center">
        <ol class="gs-breadcrumb">
            <li class="gs-breadcrumb__list-item">
                <router-link class="gs-breadcrumb__link"
                    :to="{ path: '/'+$route.params.city, params: { city: $route.params.city } }">
                    GS Гусев
                </router-link>
            </li>
            <li class="gs-breadcrumb__list-item gs-breadcrumb__list-item_active"> Калининград-Гусев </li>
        </ol>
    </section>

    <!-- Well -->
    <transition name="fade" appear>
        <section class="gs-container gs-container_center">
            <div class="gs-well">
                <p>
                    Автобусы в Гусев ходят часто. Расписание приведено в таблице ниже.
                </p>
                <p>
                    <b>Внимание!</b> Внезапный приток пассажиров. На кассах очереди. Введены дополнительные рейсы.
                </p>
                <hr>
                <p class="gs-well_text-center">
                    У вас есть возможность <br>
                    <a href="http://avtovokzal39.ru/xml2/search.php">купить билет онлайн</a>* <br>
                </p>
                <small>
                    <ul>
                        <li> билет обязательно распечатать </li>
                        <li> печать на автовокзале стоит 10 <i class="gs-icon-rouble"></i></li>
                        <li> на доп. рейсы билеты не продаются</li>
                    </ul>
                </small>
            </div>
        </section>
    </transition>

    <!-- Table -->
    <transition name="fade" appear>
        <section class="gs-container gs-container_center gs-container_padding-bottom">
            <div class="gs-well">
                <table class="gs-table gs-table-fixed-header" id="gs-table-fixed">
                    <thead>
                        <tr>
                            <th class="gs-table_text-center">
                                <span class="gs-table__thead_hidden-small-text">Номер автобуса</span>
                                <span class="gs-table__thead_visible-small-text">Автобус</span>
                            </th>
                            <th class="gs-table_text-center">
                                <span class="gs-table__thead_hidden-small-text">Отправление</span>
                                <span class="gs-table__thead_visible-small-text">Отпр.</span>
                            </th>
                            <th class="gs-table_text-center">
                                <span class="gs-table__thead_hidden-small-text">Прибытие</span>
                                <span class="gs-table__thead_visible-small-text">Приб.</span>
                            </th>
                            <th class="gs-table_text-center">
                                <span class="gs-table__thead_hidden-small-text">Цена, <i class="gs-icon-rouble"></i></span>
                                <span class="gs-table__thead_visible-small-text">Цена</span>
                            </th>
                        </tr>
                    </thead>
                    <tfoot>
                        <tr>
                            <td colspan="4"> ** - большой и, возможно, комфортный </td>
                        </tr>
                    </tfoot>
                    <tbody>
                        <tr class="gs-table_text-center" v-for="record in schedule">
                            <td> {{ record.busNo }} </td>
                            <td> {{ record.departure }} </td>
                            <td> {{ record.arrival }} </td>
                            <td> {{ record.price }} </td>
                        </tr>
                    </tbody>
                </table>
                <TableFixedTHead/>
            </div>
        </section>
    </transition>

  </div>
</template>

<script>

import busKgdGusev from '../../static/data/busGusevKgd.json'
import TableFixedTHead from '../components/TableFixedTHead'

export default {
  name: 'BusKgdGusev',
  data: function () {
    return {
      schedule: busKgdGusev
    }
  },
  components: {
    TableFixedTHead
  }
}
</script>

<style lang="scss" scoped>

@import '../assets/scss/bus-kgd-gusev.scss';

.fade-enter-active, .fade-leave-active {
  transition: opacity .3s;
}

.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

</style>
