<template>
  <div class="railway">
    <div class="railway_filter">
      <a-form-model :model="filter" layout="inline">
        <a-form-model-item label="出发" prop="from">
          <a-cascader
            v-model="filter.from"
            :options="cities"
            :show-search="{ onFilter }"
            popupClassName="railway_filter_cascader"
            placeholder="请选择出发站点"
          >
            <template slot="displayRender" slot-scope="{ labels, selectedOptions }">
              <span :data="selectedOptions">{{ labels[labels.length - 1] }}</span>
            </template>
            <template slot="showSearchRender" slot-scope="{ inputValue, path }">
              <span>{{ (path.filter((option) => option.label.toLowerCase().indexOf(inputValue.toLowerCase()) > -1))[0].label }}</span>
            </template>
          </a-cascader>
        </a-form-model-item>
        <a-form-model-item label="到达" prop="to">
          <a-cascader
            v-model="filter.to"
            :options="cities"
            :show-search="{ onFilter }"
            popupClassName="railway_filter_cascader"
            placeholder="请选择到达站点"
          >
            <template slot="displayRender" slot-scope="{ labels, selectedOptions }">
              <span :data="selectedOptions">{{ labels[labels.length - 1] }}</span>
            </template>
            <template slot="showSearchRender" slot-scope="{ inputValue, path }">
              <span>{{ (path.filter((option) => option.label.toLowerCase().indexOf(inputValue.toLowerCase()) > -1))[0].label }}</span>
            </template>
          </a-cascader>
        </a-form-model-item>
        <a-form-model-item label="日期" prop="date">
          <a-date-picker
            v-model="filter.date"
            :disabledDate="disabledDate"
            :locale="locale"
            :allowClear="false"
            format="YYYY-MM-DD"
            placeholder="请选择出发时间"
          />
        </a-form-model-item>
        <a-form-model-item>
          <a-button type="primary" icon="search" :loading="loading" @click="submit">查询</a-button>
        </a-form-model-item>
      </a-form-model>
    </div>
    <div class="railway_main">
      <vue-scroll>
        <div class="railway_list">
          
        </div>
      </vue-scroll>
    </div>
  </div>
</template>

<script src="./index.ts"></script>

<style lang="scss">
  @import './index.scss';
</style>