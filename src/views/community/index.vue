<template>
  <div class="table-box">
    <ProTable
      ref="proTableRef"
      :columns="columns"
      :request-api="requestApi"
      request-auto
      title="标题"
      :tool-button="['refresh', 'search']"
      row-key="name"
      :data-callback="dataCallback"
    />
  </div>
</template>

<script lang="tsx" setup>
import { ResPage, ResultData } from "@/api/interface";
import ProTable from "@/components/ProTable/index.vue";
import { ColumnProps, ProTableInstance } from "@/components/ProTable/interface";
import { ref } from "vue";

type User = {
  name: string;
  age: number;
};

const proTableRef = ref<ProTableInstance>();

const clickMe = () => {
  console.log(proTableRef.value?.getTableList);
};

const columns: ColumnProps<User>[] = [
  {
    label: "姓名",
    prop: "name",
    width: 100,
    align: "center",
    search: {
      el: "input",
      // label: "姓名"
      props: {
        // placeholder: "请输入姓名"
      },
      key: "username",
      tooltip: "请输入姓名"
    }
  },
  {
    label: "年龄",
    prop: "age",
    type: "radio",
    search: {
      render: () => {
        return (
          <div>
            <input type="text" />
          </div>
        );
      }
    }
  }
];
/**
 * code msg data
 */
type MyRes = ResultData<ResPage<User>>;

// eslint-disable-next-line @typescript-eslint/no-unused-vars
const requestApi = (params: any) => {
  console.log(params);

  return new Promise<MyRes>(resolve => {
    setTimeout(() => {
      resolve({
        code: "200",
        msg: "成功",
        data: {
          list: data,
          total: data.length,
          pageNum: 1,
          pageSize: 10
        }
      });
    }, 1000);
  });
};

const dataCallback = (data: User[]) => {
  console.log(data);

  return data;
};

const data = [
  {
    name: "张三",
    age: 18
  },
  {
    name: "李四",
    age: 20
  },
  {
    name: "王五",
    age: 22
  },
  {
    name: "赵六",
    age: 24
  },
  {
    name: "钱七",
    age: 26
  },
  {
    name: "孙八",
    age: 28
  },
  {
    name: "周九",
    age: 30
  },
  {
    name: "吴十",
    age: 32
  },
  {
    name: "郑十一",
    age: 34
  },
  {
    name: "王十二",
    age: 36
  },
  {
    name: "冯十三",
    age: 38
  },
  {
    name: "陈十四",
    age: 40
  }
];
</script>
