# 列表 List

<GlobalElement />

*通用列表*

## 何时使用

- 最基础的列表展示，可承载文字、列表、图片、段落，链接等

<script setup lang="ts">
import { ref, reactive, h } from 'vue'
import { UserOutlined, StarOutlined, LikeOutlined, MessageOutlined } from '@ant-design/icons-vue'
const listData = ref([
  {
    title: 'Vue Amazing UI Title 1',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 2',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 3',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 4',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'content'
  }
])
const bordered = ref(true)
const simpleListData = ref([
  {
    title: 'Vue Amazing UI Title 1',
    description: 'An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 2',
    description: 'An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 3',
    description: 'An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 4',
    description: 'An Amazing Vue3 UI Components Library.',
    content: 'content'
  }
])
const simpleList = ref([
  'Vue Amazing UI is developed using TypeScript',
  'An Amazing Vue3 UI Components Library',
  'Streamline web development with Vue Amazing UI',
  'Incredible Vue components for modern web design',
  'Transform your Vue interface with Vue Amazing UI'
])
const sizeOptions = [
  {
    label: 'small',
    value: 'small'
  },
  {
    label: 'middle',
    value: 'middle'
  },
  {
    label: 'large',
    value: 'large'
  }
]
const size = ref('middle')
const loading = ref(true)
const allListData = ref<any[]>([])
for (let i = 1; i <= 8; i++) {
  allListData.value.push({
    href: 'https://themusecatcher.github.io/vue-amazing-ui/',
    title: `Vue Amazing UI part ${i}`,
    avatar: 'https://cdn.jsdelivr.net/gh/themusecatcher/resources@0.0.5/1.jpg',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content:
      'Vue Amazing UI supplies streamline web development, incredible Vue components for modern web design and transform your Vue interface completely.'
  })
}
const paginationListData = ref<any[]>([])
paginationListData.value = allListData.value.slice(0, 3)
const pagination = {
  page: 1,
  pageSize: 3,
  total: 8,
  onChange: (page: number, pageSize: number) => {
    console.log('change page', page)
    console.log('change pageSize', pageSize)
    const start = (page - 1) * pageSize + 1
    const end = page * pageSize > 8 ? 8 : page * pageSize
    paginationListData.value = allListData.value.slice(start - 1, end)
  }
}
const allConfigListData = ref<any[]>([])
for (let i = 1; i <= 30; i++) {
  allConfigListData.value.push({
    href: 'https://themusecatcher.github.io/vue-amazing-ui/',
    title: `Vue Amazing UI Title ${i}`,
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'Incredible Vue components for modern web design'
  })
}
const configListData = ref<any[]>([])
configListData.value = allConfigListData.value.slice(0, 5)
const state = reactive({
  bordered: true,
  vertical: false,
  split: true,
  size: 'middle',
  loading: false,
  hoverable: true,
  header: 'list header',
  footer: 'list footer',
  extra: 'extra',
  showPagination: true,
  pagination: {
    page: 1,
    pageSize: 5,
    total: 30,
    showTotal: (total: number, range: number[]) => `${range[0]}-${range[1]} of ${total} items`,
    showSizeChanger: true,
    showQuickJumper: true,
    onChange: (page: number, pageSize: number) => {
      console.log('change page', page)
      console.log('change pageSize', pageSize)
      const start = (page - 1) * pageSize + 1
      const end = page * pageSize > state.pagination.total ? state.pagination.total : page * pageSize
      configListData.value = allConfigListData.value.slice(start - 1, end)
    }
  }
})
</script>

## 基本使用

<List>
  <ListItem v-for="(data, index) in listData" :key="index" :title="data.title">
    <template #avatar>
      <Avatar src="https://cdn.jsdelivr.net/gh/themusecatcher/resources@0.0.5/1.jpg" />
    </template>
    <template #description>
      {{ data.description }}
    </template>
  </ListItem>
</List>

::: details Show Code

```vue
<script setup lang="ts">
import { ref } from 'vue'
const listData = ref([
  {
    title: 'Vue Amazing UI Title 1',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 2',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 3',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 4',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'content'
  }
])
</script>
<template>
  <List>
    <ListItem v-for="(data, index) in listData" :key="index" :title="data.title">
      <template #avatar>
        <Avatar src="https://cdn.jsdelivr.net/gh/themusecatcher/resources@0.0.5/1.jpg" />
      </template>
      <template #description>
        {{ data.description }}
      </template>
    </ListItem>
  </List>
</template>
```

:::

## 隐藏分割线

<List :split="false">
  <ListItem v-for="(data, index) in listData" :key="index" :title="data.title">
    <template #avatar>
      <Avatar src="https://cdn.jsdelivr.net/gh/themusecatcher/resources@0.0.5/1.jpg" />
    </template>
    <template #description>
      {{ data.description }}
    </template>
  </ListItem>
</List>

::: details Show Code

```vue
<script setup lang="ts">
import { ref } from 'vue'
const listData = ref([
  {
    title: 'Vue Amazing UI Title 1',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 2',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 3',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 4',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'content'
  }
])
</script>
<template>
  <List :split="false">
    <ListItem v-for="(data, index) in listData" :key="index" :title="data.title">
      <template #avatar>
        <Avatar src="https://cdn.jsdelivr.net/gh/themusecatcher/resources@0.0.5/1.jpg" />
      </template>
      <template #description>
        {{ data.description }}
      </template>
    </ListItem>
  </List>
</template>
```

:::

## 带边框列表

<Flex vertical>
  <Space align="center">
    bordered:<Switch v-model="bordered" />
  </Space>
  <List :bordered="bordered">
    <template #header>
      <div>Header</div>
    </template>
    <ListItem v-for="(data, index) in listData" :key="index" :title="data.title">
      <template #avatar>
        <Avatar src="https://cdn.jsdelivr.net/gh/themusecatcher/resources@0.0.5/1.jpg" />
      </template>
      <template #description>
        {{ data.description }}
      </template>
    </ListItem>
    <template #footer>
      <div>Footer</div>
    </template>
  </List>
</Flex>

::: details Show Code

```vue
<script setup lang="ts">
import { ref } from 'vue'
const listData = ref([
  {
    title: 'Vue Amazing UI Title 1',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 2',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 3',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 4',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'content'
  }
])
const bordered = ref(true)
</script>
<template>
  <Flex vertical>
    <Space align="center">
      bordered:<Switch v-model="bordered" />
    </Space>
    <List :bordered="bordered">
      <template #header>
        <div>Header</div>
      </template>
      <ListItem v-for="(data, index) in listData" :key="index" :title="data.title">
        <template #avatar>
          <Avatar src="https://cdn.jsdelivr.net/gh/themusecatcher/resources@0.0.5/1.jpg" />
        </template>
        <template #description>
          {{ data.description }}
        </template>
      </ListItem>
      <template #footer>
        <div>Footer</div>
      </template>
    </List>
  </Flex>
</template>
```

:::

## 三种尺寸

<Flex vertical>
  <Radio :options="sizeOptions" v-model:value="size" button button-style="solid" />
  <Row :gutter="32">
    <Col :span="12">
      <List bordered :size="size">
        <ListItem v-for="(data, index) in simpleListData" :key="index">
          <template #avatar>
            <Avatar src="https://cdn.jsdelivr.net/gh/themusecatcher/resources@0.0.5/1.jpg" />
          </template>
          <template #title>
            <a href="https://themusecatcher.github.io/vue-amazing-ui/">{{ data.title }}</a>
          </template>
          <template #description>
            {{ data.description }}
          </template>
        </ListItem>
      </List>
    </Col>
    <Col :span="12">
      <List bordered :size="size">
        <template #header>
          <div>Header</div>
        </template>
        <ListItem v-for="(data, index) in simpleList" :key="index">
          {{ data }}
        </ListItem>
        <template #footer>
          <div>Footer</div>
        </template>
      </List>
    </Col>
  </Row>
</Flex>

::: details Show Code

```vue
<script setup lang="ts">
import { ref } from 'vue'
const simpleListData = ref([
  {
    title: 'Vue Amazing UI Title 1',
    description: 'An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 2',
    description: 'An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 3',
    description: 'An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 4',
    description: 'An Amazing Vue3 UI Components Library.',
    content: 'content'
  }
])
const simpleList = ref([
  'Vue Amazing UI is developed using TypeScript',
  'An Amazing Vue3 UI Components Library',
  'Streamline web development with Vue Amazing UI',
  'Incredible Vue components for modern web design',
  'Transform your Vue interface with Vue Amazing UI'
])
const sizeOptions = [
  {
    label: 'small',
    value: 'small'
  },
  {
    label: 'middle',
    value: 'middle'
  },
  {
    label: 'large',
    value: 'large'
  }
]
const size = ref('middle')
</script>
<template>
  <Flex vertical>
    <Radio :options="sizeOptions" v-model:value="size" button button-style="solid" />
    <Row :gutter="32">
      <Col :span="12">
        <List bordered :size="size">
          <ListItem v-for="(data, index) in simpleListData" :key="index">
            <template #avatar>
              <Avatar src="https://cdn.jsdelivr.net/gh/themusecatcher/resources@0.0.5/1.jpg" />
            </template>
            <template #title>
              <a href="https://themusecatcher.github.io/vue-amazing-ui/">{{ data.title }}</a>
            </template>
            <template #description>
              {{ data.description }}
            </template>
          </ListItem>
        </List>
      </Col>
      <Col :span="12">
        <List bordered :size="size">
          <template #header>
            <div>Header</div>
          </template>
          <ListItem v-for="(data, index) in simpleList" :key="index">
            {{ data }}
          </ListItem>
          <template #footer>
            <div>Footer</div>
          </template>
        </List>
      </Col>
    </Row>
  </Flex>
</template>
```

:::

## 加载中

<Flex vertical>
  <Space align="center"> Loading state:<Switch v-model="loading" /> </Space>
  <Row :gutter="32">
    <Col :span="12">
      <List bordered :loading="loading">
        <ListItem v-for="(data, index) in simpleListData" :key="index" :title="data.title">
          <template #avatar>
            <Avatar src="https://cdn.jsdelivr.net/gh/themusecatcher/resources@0.0.5/1.jpg" />
          </template>
          <template #description>
            {{ data.description }}
          </template>
        </ListItem>
      </List>
    </Col>
    <Col :span="12">
      <List bordered :loading="loading" :spin-props="{ indicator: 'dynamic-circle' }">
        <template #header>
          <div>Header</div>
        </template>
        <ListItem v-for="(data, index) in simpleList" :key="index">
          {{ data }}
        </ListItem>
        <template #footer>
          <div>Footer</div>
        </template>
      </List>
    </Col>
  </Row>
</Flex>

::: details Show Code

```vue
<script setup lang="ts">
import { ref } from 'vue'
const simpleListData = ref([
  {
    title: 'Vue Amazing UI Title 1',
    description: 'An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 2',
    description: 'An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 3',
    description: 'An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 4',
    description: 'An Amazing Vue3 UI Components Library.',
    content: 'content'
  }
])
const simpleList = ref([
  'Vue Amazing UI is developed using TypeScript',
  'An Amazing Vue3 UI Components Library',
  'Streamline web development with Vue Amazing UI',
  'Incredible Vue components for modern web design',
  'Transform your Vue interface with Vue Amazing UI'
])
const loading = ref(true)
</script>
<template>
  <Flex vertical>
    <Space align="center"> Loading state:<Switch v-model="loading" /> </Space>
    <Row :gutter="32">
      <Col :span="12">
        <List bordered :loading="loading">
          <ListItem v-for="(data, index) in simpleListData" :key="index" :title="data.title">
            <template #avatar>
              <Avatar src="https://cdn.jsdelivr.net/gh/themusecatcher/resources@0.0.5/1.jpg" />
            </template>
            <template #description>
              {{ data.description }}
            </template>
          </ListItem>
        </List>
      </Col>
      <Col :span="12">
        <List bordered :loading="loading" :spin-props="{ indicator: 'dynamic-circle' }">
          <template #header>
            <div>Header</div>
          </template>
          <ListItem v-for="(data, index) in simpleList" :key="index">
            {{ data }}
          </ListItem>
          <template #footer>
            <div>Footer</div>
          </template>
        </List>
      </Col>
    </Row>
  </Flex>
</template>
```

:::

## 暂无数据

<List>
  <ListItem v-for="(data, index) in []" :key="index"></ListItem>
</List>

::: details Show Code

```vue
<template>
  <List>
    <ListItem v-for="(data, index) in []" :key="index"></ListItem>
  </List>
</template>
```

:::

## 显示悬浮样式

<Row :gutter="32">
  <Col :span="12">
    <List bordered hoverable>
      <ListItem v-for="(data, index) in simpleListData" :key="index" :title="data.title">
        <template #avatar>
          <Avatar src="https://cdn.jsdelivr.net/gh/themusecatcher/resources@0.0.5/1.jpg" />
        </template>
        <template #description>
          {{ data.description }}
        </template>
      </ListItem>
    </List>
  </Col>
  <Col :span="12">
    <List bordered hoverable>
      <template #header>
        <div>Header</div>
      </template>
      <ListItem v-for="(data, index) in simpleList" :key="index">
        {{ data }}
      </ListItem>
      <template #footer>
        <div>Footer</div>
      </template>
    </List>
  </Col>
</Row>

::: details Show Code

```vue
<script setup lang="ts">
import { ref } from 'vue'
const simpleListData = ref([
  {
    title: 'Vue Amazing UI Title 1',
    description: 'An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 2',
    description: 'An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 3',
    description: 'An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 4',
    description: 'An Amazing Vue3 UI Components Library.',
    content: 'content'
  }
])
const simpleList = ref([
  'Vue Amazing UI is developed using TypeScript',
  'An Amazing Vue3 UI Components Library',
  'Streamline web development with Vue Amazing UI',
  'Incredible Vue components for modern web design',
  'Transform your Vue interface with Vue Amazing UI'
])
</script>
<template>
  <Row :gutter="32">
    <Col :span="12">
      <List bordered hoverable>
        <ListItem v-for="(data, index) in simpleListData" :key="index" :title="data.title">
          <template #avatar>
            <Avatar src="https://cdn.jsdelivr.net/gh/themusecatcher/resources@0.0.5/1.jpg" />
          </template>
          <template #description>
            {{ data.description }}
          </template>
        </ListItem>
      </List>
    </Col>
    <Col :span="12">
      <List bordered hoverable>
        <template #header>
          <div>Header</div>
        </template>
        <ListItem v-for="(data, index) in simpleList" :key="index">
          {{ data }}
        </ListItem>
        <template #footer>
          <div>Footer</div>
        </template>
      </List>
    </Col>
  </Row>
</template>
```

:::

## 列表添加操作项

<List>
  <ListItem v-for="(data, index) in listData" :key="index" :title="data.title">
    <template #avatar>
      <Avatar src="https://cdn.jsdelivr.net/gh/themusecatcher/resources@0.0.5/1.jpg" />
    </template>
    <template #description>
      {{ data.description }}
    </template>
    {{ data.content }}
    <template #actions>
      <a>edit</a>
      <a>more</a>
    </template>
  </ListItem>
</List>

::: details Show Code

```vue
<script setup lang="ts">
import { ref } from 'vue'
const listData = ref([
  {
    title: 'Vue Amazing UI Title 1',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 2',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 3',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 4',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'content'
  }
])
</script>
<template>
  <List>
    <ListItem v-for="(data, index) in listData" :key="index" :title="data.title">
      <template #avatar>
        <Avatar src="https://cdn.jsdelivr.net/gh/themusecatcher/resources@0.0.5/1.jpg" />
      </template>
      <template #description>
        {{ data.description }}
      </template>
      {{ data.content }}
      <template #actions>
        <a>edit</a>
        <a>more</a>
      </template>
    </ListItem>
  </List>
</template>
```

:::

## 自定义样式

<List>
  <ListItem
    :avatar-props="{
      icon: () => h(UserOutlined),
      size: 56
    }"
    :avatar-style="{ alignSelf: 'center' }"
    :title-style="{ fontSize: '20px' }"
    :description-style="{ fontSize: '16px' }"
    :content-style="{ fontSize: '18px', color: '#f50', marginLeft: '16px' }"
    :extra-style="{ overflow: 'hidden', borderRadius: '12px' }"
    v-for="(data, index) in listData"
    :key="index"
    :title="data.title"
  >
    <template #description>
      {{ data.description }}
    </template>
    {{ data.content }}
    <template #actions>
      <a>edit</a>
      <a>more</a>
    </template>
    <template #extra>
      <img
        class="extra-img"
        width="200"
        alt="extra"
        src="https://cdn.jsdelivr.net/gh/themusecatcher/resources@0.0.5/2.jpg"
      />
    </template>
  </ListItem>
</List>

::: details Show Code

```vue
<script setup lang="ts">
import { ref, h } from 'vue'
import { UserOutlined } from '@ant-design/icons-vue'
const listData = ref([
  {
    title: 'Vue Amazing UI Title 1',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 2',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 3',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'content'
  },
  {
    title: 'Vue Amazing UI Title 4',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'content'
  }
])
</script>
<template>
  <List>
    <ListItem
      :avatar-props="{
        icon: () => h(UserOutlined),
        size: 56
      }"
      :avatar-style="{ alignSelf: 'center' }"
      :title-style="{ fontSize: '20px' }"
      :description-style="{ fontSize: '16px' }"
      :content-style="{ fontSize: '18px', color: '#f50', marginLeft: '16px' }"
      :extra-style="{ overflow: 'hidden', borderRadius: '12px' }"
      v-for="(data, index) in listData"
      :key="index"
      :title="data.title"
    >
      <template #description>
        {{ data.description }}
      </template>
      {{ data.content }}
      <template #actions>
        <a>edit</a>
        <a>more</a>
      </template>
      <template #extra>
        <img
          class="extra-img"
          width="200"
          alt="extra"
          src="https://cdn.jsdelivr.net/gh/themusecatcher/resources@0.0.5/2.jpg"
        />
      </template>
    </ListItem>
  </List>
</template>
```

:::

## 竖排分页列表

<List vertical size="large" show-pagination :pagination="pagination">
  <ListItem v-for="(data, index) in paginationListData" :key="index">
    <template #title>
      <a :href="data.href" target="_blank">{{ data.title }}</a>
    </template>
    <template #avatar>
      <Avatar src="https://cdn.jsdelivr.net/gh/themusecatcher/resources@0.0.5/1.jpg" />
    </template>
    <template #description>
      {{ data.description }}
    </template>
    {{ data.content }}
    <template #actions>
      <span>
        <StarOutlined style="margin-right: 8px" />156
      </span>
      <span>
        <LikeOutlined style="margin-right: 8px" />156
      </span>
      <span>
        <MessageOutlined style="margin-right: 8px" />6
      </span>
    </template>
    <template #extra>
      <img
        class="extra-img"
        width="272"
        alt="extra"
        src="https://gw.alipayobjects.com/zos/rmsportal/mqaQswcyDLcXyDKnZfES.png"
      />
    </template>
  </ListItem>
  <template #footer>
    <div>
      <b>Vue Amazing UI</b>
      footer part
    </div>
  </template>
</List>

<style lang="less" scoped>
.extra-img {
  display: inline-block;
  vertical-align: bottom;
}
</style>

::: details Show Code

```vue
<script setup lang="ts">
import { ref } from 'vue'
import { StarOutlined, LikeOutlined, MessageOutlined } from '@ant-design/icons-vue'
const allListData = ref<any[]>([])
for (let i = 1; i <= 8; i++) {
  allListData.value.push({
    href: 'https://themusecatcher.github.io/vue-amazing-ui/',
    title: `Vue Amazing UI part ${i}`,
    avatar: 'https://cdn.jsdelivr.net/gh/themusecatcher/resources@0.0.5/1.jpg',
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content:
      'Vue Amazing UI supplies streamline web development, incredible Vue components for modern web design and transform your Vue interface completely.'
  })
}
const paginationListData = ref<any[]>([])
paginationListData.value = allListData.value.slice(0, 3)
const pagination = {
  page: 1,
  pageSize: 3,
  total: 8,
  onChange: (page: number, pageSize: number) => {
    console.log('change page', page)
    console.log('change pageSize', pageSize)
    const start = (page - 1) * pageSize + 1
    const end = page * pageSize > 8 ? 8 : page * pageSize
    paginationListData.value = allListData.value.slice(start - 1, end)
  }
}
</script>
<template>
  <List vertical size="large" show-pagination :pagination="pagination">
    <ListItem v-for="(data, index) in paginationListData" :key="index">
      <template #title>
        <a :href="data.href" target="_blank">{{ data.title }}</a>
      </template>
      <template #avatar>
        <Avatar src="https://cdn.jsdelivr.net/gh/themusecatcher/resources@0.0.5/1.jpg" />
      </template>
      <template #description>
        {{ data.description }}
      </template>
      {{ data.content }}
      <template #actions>
        <span>
          <StarOutlined style="margin-right: 8px" />156
        </span>
        <span>
          <LikeOutlined style="margin-right: 8px" />156
        </span>
        <span>
          <MessageOutlined style="margin-right: 8px" />6
        </span>
      </template>
      <template #extra>
        <img
          class="extra-img"
          width="272"
          alt="extra"
          src="https://gw.alipayobjects.com/zos/rmsportal/mqaQswcyDLcXyDKnZfES.png"
        />
      </template>
    </ListItem>
    <template #footer>
      <div>
        <b>Vue Amazing UI</b>
        footer part
      </div>
    </template>
  </List>
</template>
<style lang="less" scoped>
.extra-img {
  display: inline-block;
  vertical-align: bottom;
}
</style>
```

:::

## 列表配置器

<Flex gap="large" vertical>
  <Row :gutter="[24, 12]">
    <Col :span="6">
      <Space gap="small" vertical> bordered:<Switch v-model="state.bordered" /> </Space>
    </Col>
    <Col :span="6">
      <Space gap="small" vertical> vertical:<Switch v-model="state.vertical" /> </Space>
    </Col>
    <Col :span="6">
      <Space gap="small" vertical> split:<Switch v-model="state.split" /> </Space>
    </Col>
    <Col :span="6">
      <Flex gap="small" vertical>
        size:<Select :options="sizeOptions" v-model="state.size" />
      </Flex>
    </Col>
    <Col :span="6">
      <Space gap="small" vertical> loading:<Switch v-model="state.loading" /> </Space>
    </Col>
    <Col :span="6">
      <Space gap="small" vertical> hoverable:<Switch v-model="state.hoverable" /> </Space>
    </Col>
    <Col :span="6">
      <Flex gap="small" vertical> header:<Input v-model:value="state.header" placeholder="header" /> </Flex>
    </Col>
    <Col :span="6">
      <Flex gap="small" vertical> footer:<Input v-model:value="state.footer" placeholder="footer" /> </Flex>
    </Col>
    <Col :span="6">
      <Flex gap="small" vertical> extra:<Input v-model:value="state.extra" placeholder="extra" /> </Flex>
    </Col>
    <Col :span="6">
      <Space gap="small" vertical> showPagination:<Switch v-model="state.showPagination" /> </Space>
    </Col>
    <Col :span="6">
      <Space gap="small" vertical> showSizeChanger:<Switch v-model="state.pagination.showSizeChanger" /> </Space>
    </Col>
    <Col :span="6">
      <Space gap="small" vertical> showQuickJumper:<Switch v-model="state.pagination.showQuickJumper" /> </Space>
    </Col>
  </Row>
  <List
    :bordered="state.bordered"
    :vertical="state.vertical"
    :split="state.split"
    :size="state.size"
    :loading="state.loading"
    :hoverable="state.hoverable"
    :header="state.header"
    :footer="state.footer"
    :showPagination="state.showPagination"
    :pagination="state.pagination"
  >
    <ListItem v-for="(data, index) in configListData" :key="index" :extra="state.extra">
      <template #title>
        <a :href="data.href" target="_blank">{{ data.title }}</a>
      </template>
      <template #avatar>
        <Avatar src="https://cdn.jsdelivr.net/gh/themusecatcher/resources@0.0.5/1.jpg" />
      </template>
      <template #description>
        {{ data.description }}
      </template>
      {{ data.content }}
    </ListItem>
  </List>
</Flex>

::: details Show Code

```vue
<script setup lang="ts">
import { ref, reactive } from 'vue'
const allConfigListData = ref<any[]>([])
for (let i = 1; i <= 30; i++) {
  allConfigListData.value.push({
    href: 'https://themusecatcher.github.io/vue-amazing-ui/',
    title: `Vue Amazing UI Title ${i}`,
    description: 'Vue Amazing UI, An Amazing Vue3 UI Components Library.',
    content: 'Incredible Vue components for modern web design'
  })
}
const configListData = ref<any[]>([])
configListData.value = allConfigListData.value.slice(0, 5)
const state = reactive({
  bordered: true,
  vertical: false,
  split: true,
  size: 'middle',
  loading: false,
  hoverable: true,
  header: 'list header',
  footer: 'list footer',
  extra: 'extra',
  showPagination: true,
  pagination: {
    page: 1,
    pageSize: 5,
    total: 30,
    showTotal: (total: number, range: number[]) => `${range[0]}-${range[1]} of ${total} items`,
    showSizeChanger: true,
    showQuickJumper: true,
    onChange: (page: number, pageSize: number) => {
      console.log('change page', page)
      console.log('change pageSize', pageSize)
      const start = (page - 1) * pageSize + 1
      const end = page * pageSize > state.pagination.total ? state.pagination.total : page * pageSize
      configListData.value = allConfigListData.value.slice(start - 1, end)
    }
  }
})
</script>
<template>
  <Flex gap="large" vertical>
    <Row :gutter="[24, 12]">
      <Col :span="6">
        <Space gap="small" vertical> bordered:<Switch v-model="state.bordered" /> </Space>
      </Col>
      <Col :span="6">
        <Space gap="small" vertical> vertical:<Switch v-model="state.vertical" /> </Space>
      </Col>
      <Col :span="6">
        <Space gap="small" vertical> split:<Switch v-model="state.split" /> </Space>
      </Col>
      <Col :span="6">
        <Flex gap="small" vertical>
          size:<Select :options="sizeOptions" v-model="state.size" />
        </Flex>
      </Col>
      <Col :span="6">
        <Space gap="small" vertical> loading:<Switch v-model="state.loading" /> </Space>
      </Col>
      <Col :span="6">
        <Space gap="small" vertical> hoverable:<Switch v-model="state.hoverable" /> </Space>
      </Col>
      <Col :span="6">
        <Flex gap="small" vertical> header:<Input v-model:value="state.header" placeholder="header" /> </Flex>
      </Col>
      <Col :span="6">
        <Flex gap="small" vertical> footer:<Input v-model:value="state.footer" placeholder="footer" /> </Flex>
      </Col>
      <Col :span="6">
        <Flex gap="small" vertical> extra:<Input v-model:value="state.extra" placeholder="extra" /> </Flex>
      </Col>
      <Col :span="6">
        <Space gap="small" vertical> showPagination:<Switch v-model="state.showPagination" /> </Space>
      </Col>
      <Col :span="6">
        <Space gap="small" vertical> showSizeChanger:<Switch v-model="state.pagination.showSizeChanger" /> </Space>
      </Col>
      <Col :span="6">
        <Space gap="small" vertical> showQuickJumper:<Switch v-model="state.pagination.showQuickJumper" /> </Space>
      </Col>
    </Row>
    <List
      :bordered="state.bordered"
      :vertical="state.vertical"
      :split="state.split"
      :size="state.size"
      :loading="state.loading"
      :hoverable="state.hoverable"
      :header="state.header"
      :footer="state.footer"
      :showPagination="state.showPagination"
      :pagination="state.pagination"
    >
      <ListItem v-for="(data, index) in configListData" :key="index" :extra="state.extra">
        <template #title>
          <a :href="data.href" target="_blank">{{ data.title }}</a>
        </template>
        <template #avatar>
          <Avatar src="https://cdn.jsdelivr.net/gh/themusecatcher/resources@0.0.5/1.jpg" />
        </template>
        <template #description>
          {{ data.description }}
        </template>
        {{ data.content }}
      </ListItem>
    </List>
  </Flex>
</template>
```

:::

## APIs

### List

参数 | 说明 | 类型 | 默认值
:-- | :-- | :-- | :--
bordered | 是否展示边框 | boolean | false
vertical | 是否使用竖直样式 | boolean | false
split | 是否展示分割线 | boolean | true
size | 列表尺寸 | 'small' &#124; 'middle' &#124; 'large' | 'middle'
loading | 是否加载中 | boolean | false
hoverable | 是否显示悬浮样式 | boolean | false
header | 列表头部 | string &#124; slot | undefined
footer | 列表底部 | string &#124; slot | undefined
spinProps | `Spin` 组件属性配置，参考 [Spin Props](https://themusecatcher.github.io/vue-amazing-ui/guide/components/spin.html#spin)，用于配置列表加载中样式 | object | {}
emptyProps | `Empty` 组件属性配置，参考 [Empty Props](https://themusecatcher.github.io/vue-amazing-ui/guide/components/empty.html#empty)，用于配置暂无数据样式 | object | {}
showPagination | 是否显示分页 | boolean | false
pagination | `Pagination` 组件属性配置，参考 [Pagination Props](https://themusecatcher.github.io/vue-amazing-ui/guide/components/pagination.html#pagination)，用于配置分页功能 | object | {}

### ListItem

参数 | 说明 | 类型 | 默认值
:-- | :-- | :-- | :--
avatar | 列表元素的图标 | string &#124; slot | undefined
avatarProps | `Avatar` 组件属性配置，参考 [Avatar Props](https://themusecatcher.github.io/vue-amazing-ui/guide/components/avatar.html#avatar)，用于配置列表图标样式 | object | {}
title | 列表元素的标题 | string &#124; slot | undefined
description | 列表元素的描述内容 | string &#124; slot | undefined
actions | 列表操作组 | slot | undefined
extra | 额外内容，展示在列表右侧 | string &#124; slot | undefined
avatarStyle | 设置图标的样式 | [CSSProperties](https://cn.vuejs.org/api/utility-types.html#cssproperties) | {}
titleStyle | 设置标题的样式 | [CSSProperties](https://cn.vuejs.org/api/utility-types.html#cssproperties) | {}
descriptionStyle | 设置描述内容的样式 | [CSSProperties](https://cn.vuejs.org/api/utility-types.html#cssproperties) | {}
contentStyle | 设置内容的样式 | [CSSProperties](https://cn.vuejs.org/api/utility-types.html#cssproperties) | {}
actionsStyle | 设置操作区域的样式 | [CSSProperties](https://cn.vuejs.org/api/utility-types.html#cssproperties) | {}
extraStyle | 设置额外内容的样式 | [CSSProperties](https://cn.vuejs.org/api/utility-types.html#cssproperties) | {}

## Slots

### List Slots

名称 | 说明 | 类型
:-- | :-- | :--
header | 自定义列表头部 | v-slot:header
default | 自定义内容 | v-slot:default
footer | 自定义列表底部 | v-slot:footer

### ListItem Slots

名称 | 说明 | 类型
:-- | :-- | :--
avatar | 自定义列表元素的图标 | v-slot:avatar
title | 自定义列表元素的标题 | v-slot:title
description | 自定义列表元素的描述内容 | v-slot:description
default | 自定义内容 | v-slot:default
actions | 自定义列表操作组 | v-slot:actions
extra | 自定义额外内容 | v-slot:extra
