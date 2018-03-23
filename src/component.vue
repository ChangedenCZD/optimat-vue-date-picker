<template>
    <section class="component-layout ui-picker-date-layout rel">
        <div class="date-input-layout">
            <input class="date-input w100 h100 pdl5 pr5 bg-white" contenteditable="false" :placeholder="placeholder"
                   v-model="mergeDate" @click="toggleDatePickLayout"/>
            <img class="abs rt0" v-if="mergeDate" :src="icons.clear" @click="clearDate"/>
            <img class="abs rt0" v-else :src="icons.calendar" @click="toggleDatePickLayout"/>
        </div>
        <div class="date-pick-layout bg-white shadow abs over-hidden" :style="{left:pickerLeft+'px'}"
             v-show="isShowDatePickLayout">
            <table>
                <tr>
                    <th class="year-item pdl10 pdr10" v-if="leftMonthDateInfo.date">
                        <div class="abs lt0 w100 h100">{{format(leftMonthDateInfo.date[4],'yyyy - mm')}}</div>
                        <img class="year-select-btn last-year-btn left" :src="icons.left" @click="lastMonth"
                             v-if="isDoubleMode&&!isCurrentMonth(currentLeftMonth)"/>
                        <img class="year-select-btn last-year-btn left" :src="icons.left" @click="lastMonth"
                             v-if="isSingleMode&&!isCurrentMonth(currentLeftMonth)"/>
                        <img class="year-select-btn last-year-btn right" :src="icons.right" @click="nextMonth"
                             v-if="isSingleMode"/>
                    </th>
                    <th class="pdl10 pdr10" v-if="isDoubleMode"></th>
                    <th class="year-item pdl10 pdr10 rel" v-if="isDoubleMode&&rightMonthDateInfo.date">
                        <div class="abs lt0 w100 h100">{{format(rightMonthDateInfo.date[4],'yyyy - mm')}}</div>
                        <img class="year-select-btn next-year-btn right" :src="icons.right" @click="nextMonth"/>
                    </th>
                </tr>
                <tr>
                    <td>
                        <table class="month-layout left-month pdl10 pdr10 pdb10">
                            <tr class="day-of-week-description">
                                <th class="date-item invalid-item" v-for="day in defaultDayOfWeek">{{day}}</th>
                            </tr>
                            <tr v-for="row in leftMonthDateInfo.mergeList">
                                <td class="date-item"
                                    :class="[day.invalid?'invalid-item':(day.preview?'preview-item':'active-item'),isStartDate(day),isEndDate(day),isMiddleDate(day)]"
                                    v-for="day in row" :date-index="day.index" :date-time="day.time"
                                    @click="select(day)">{{day.day}}
                                </td>
                            </tr>
                        </table>
                    </td>
                    <td class="pdl10 pdr10" v-if="isDoubleMode"></td>
                    <td v-if="isDoubleMode">
                        <table class="month-layout right-month pdl10 pdr10 pdb10">
                            <tr class="day-of-week-description">
                                <th class="date-item invalid-item" v-for="day in defaultDayOfWeek">{{day}}</th>
                            </tr>
                            <tr v-for="row in rightMonthDateInfo.mergeList">
                                <td class="date-item"
                                    :class="[day.invalid?'preview-item':(day.preview?'preview-item':'active-item'),isStartDate(day),isEndDate(day),isMiddleDate(day)]"
                                    v-for="day in row" :date-index="day.index" :date-time="day.time"
                                    @click="select(day)">{{day.day}}
                                </td>
                            </tr>
                        </table>
                    </td>
                </tr>
            </table>
        </div>
    </section>
</template>

<script>
    const Component = require('./component');
    export default new Component();
</script>

<style lang="scss" scoped="true">
    @import "./component.scss";
</style>