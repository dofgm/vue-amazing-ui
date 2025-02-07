# 徽标 Badge

<GlobalElement />

*图标右上角的圆形徽标数字或文本前的状态小圆点*

## 何时使用

- 一般出现在通知图标或头像的右上角，用于显示需要处理的消息条数，通过醒目视觉形式吸引用户处理

<script setup lang="ts">
import { ref } from 'vue'
import { ClockCircleOutlined, MinusOutlined, PlusOutlined } from '@ant-design/icons-vue'
const value = ref(5)
const dot = ref(true)
const colors = [
  'pink',
  'red',
  'yellow',
  'orange',
  'cyan',
  'green',
  'blue',
  'purple',
  'geekblue',
  'magenta',
  'volcano',
  'gold',
  'lime'
]
function decline() {
  if (value.value >= 1) {
    value.value--
  }
}
function increase() {
  value.value++
}
</script>

## 基本使用

<Space>
  <Badge :value="5">
    <Avatar shape="square" size="large" />
  </Badge>
  <Badge :value="0" show-zero>
    <Avatar shape="square" size="large" />
  </Badge>
  <Badge>
    <template #value>
      <ClockCircleOutlined style="color: #f5222d" />
    </template>
    <Avatar shape="square" size="large" />
  </Badge>
</Space>

::: details Show Code

```vue
<script setup lang="ts">
import { ClockCircleOutlined } from '@ant-design/icons-vue'
</script>
<template>
  <Space>
    <Badge :value="5">
      <Avatar shape="square" size="large" />
    </Badge>
    <Badge :value="0" show-zero>
      <Avatar shape="square" size="large" />
    </Badge>
    <Badge>
      <template #value>
        <ClockCircleOutlined style="color: #f5222d" />
      </template>
      <Avatar shape="square" size="large" />
    </Badge>
  </Space>
</template>
```

:::

## 独立使用

<Space>
  <Badge :value="25" />
  <Badge
    :value="4"
    :value-style="{
      backgroundColor: '#fff',
      color: '#999',
      boxShadow: '0 0 0 1px #d9d9d9 inset'
    }"
  />
  <Badge :value="109" :value-style="{ backgroundColor: '#52c41a' }" />
</Space>

::: details Show Code

```vue
<template>
  <Space>
    <Badge :value="25" />
    <Badge
      :value="4"
      :value-style="{
        backgroundColor: '#fff',
        color: '#999',
        boxShadow: '0 0 0 1px #d9d9d9 inset'
      }"
    />
    <Badge :value="109" :value-style="{ backgroundColor: '#52c41a' }" />
  </Space>
</template>
```

:::

## 封顶数字

<Space gap="large">
  <Badge :value="99">
    <Avatar shape="square" size="large" />
  </Badge>
  <Badge :value="100">
    <Avatar shape="square" size="large" />
  </Badge>
  <Badge :value="99" :max="10">
    <Avatar shape="square" size="large" />
  </Badge>
  <Badge :value="1000" :max="999">
    <Avatar shape="square" size="large" />
  </Badge>
</Space>

::: details Show Code

```vue
<template>
  <Space gap="large">
    <Badge :value="99">
      <Avatar shape="square" size="large" />
    </Badge>
    <Badge :value="100">
      <Avatar shape="square" size="large" />
    </Badge>
    <Badge :value="99" :max="10">
      <Avatar shape="square" size="large" />
    </Badge>
    <Badge :value="1000" :max="999">
      <Avatar shape="square" size="large" />
    </Badge>
  </Space>
</template>
```

:::

## 自定义内容

<Space gap="large">
  <Badge value="hello" :value-style="{ backgroundColor: '#1677FF' }">
    <Avatar shape="square" size="large" />
  </Badge>
  <Badge>
    <template #value>
      <span class="u-value">world</span>
    </template>
    <Avatar shape="square" size="large" />
  </Badge>
</Space>

::: details Show Code

```vue
<template>
  <Space gap="large">
    <Badge value="hello" :value-style="{ backgroundColor: '#1677FF' }">
      <Avatar shape="square" size="large" />
    </Badge>
    <Badge>
      <template #value>
        <span class="u-value">world</span>
      </template>
      <Avatar shape="square" size="large" />
    </Badge>
  </Space>
</template>
<style lang="less" scoped>
.u-value {
  display: inline-block;
  line-height: 20px;
  padding: 0 6px;
  background-color: #FAAD14;
  color: #FFF;
  border-radius: 10px;
  box-shadow: 0 0 0 1px #ffffff;
}
</style>
```

:::

## 自定义徽标样式

<Space gap="large">
  <Badge :value="99" :value-style="{ backgroundColor: 'magenta' }">
    <Avatar shape="square" size="large" />
  </Badge>
  <Badge value="hello" :value-style="{ backgroundColor: 'gold' }">
    <Avatar shape="square" size="large" />
  </Badge>
  <Badge dot :value-style="{ width: '10px', height: '10px', backgroundColor: 'purple' }">
    <Avatar shape="square" size="large" />
  </Badge>
</Space>

::: details Show Code

```vue
<template>
  <Space gap="large">
    <Badge :value="99" :value-style="{ backgroundColor: 'magenta' }">
      <Avatar shape="square" size="large" />
    </Badge>
    <Badge value="hello" :value-style="{ backgroundColor: 'gold' }">
      <Avatar shape="square" size="large" />
    </Badge>
    <Badge dot :value-style="{ width: '10px', height: '10px', backgroundColor: 'purple' }">
      <Avatar shape="square" size="large" />
    </Badge>
  </Space>
</template>
```

:::

## 徽标偏移

<Space gap="large">
  <Badge value="9" :offset="[-20, 10]">
    <Avatar shape="square" size="large" />
  </Badge>
  <Badge dot :offset="[-15, 10]">
    <Avatar shape="square" size="large" />
  </Badge>
  <Badge dot status="success" :offset="['-50%', '30%']">
    <Avatar shape="square" size="large" />
  </Badge>
</Space>

::: details Show Code

```vue
<template>
  <Space gap="large">
    <Badge value="9" :offset="[-20, 10]">
      <Avatar shape="square" size="large" />
    </Badge>
    <Badge dot :offset="[-15, 10]">
      <Avatar shape="square" size="large" />
    </Badge>
    <Badge dot status="success" :offset="['-50%', '30%']">
      <Avatar shape="square" size="large" />
    </Badge>
  </Space>
</template>
```

:::

## 小红点

<Badge dot>
  <a href="#">Link something</a>
</Badge>

::: details Show Code

```vue
<template>
  <Badge dot>
    <a href="#">Link something</a>
  </Badge>
</template>
```

:::

## 状态点

<Space>
  <Badge status="success" />
  <Badge status="error" />
  <Badge status="default" />
  <Badge status="processing" />
  <Badge status="warning" />
</Space>
<br/>
<Space style="margin-top: 10px;" vertical>
  <Badge status="success" text="Success" />
  <Badge status="error" text="Error" />
  <Badge status="default" text="Default" />
  <Badge status="processing" text="Processing" />
  <Badge status="warning" text="warning" />
</Space>

::: details Show Code

```vue
<template>
  <Space>
    <Badge status="success" />
    <Badge status="error" />
    <Badge status="default" />
    <Badge status="processing" />
    <Badge status="warning" />
  </Space>
  <br/>
  <Space style="margin-top: 10px;" vertical>
    <Badge status="success" text="Success" />
    <Badge status="error" text="Error" />
    <Badge status="default" text="Default" />
    <Badge status="processing" text="Processing" />
    <Badge status="warning" text="warning" />
  </Space>
</template>
```

:::

## 动态

<Flex vertical>
  <Space gap="large" align="center">
    <Badge :value="value">
      <Avatar shape="square" size="large" />
    </Badge>
    <Button @click="decline">
      <MinusOutlined />
    </Button>
    <Button @click="increase">
      <PlusOutlined />
    </Button>
  </Space>
  <Space gap="large" align="center">
    <Badge :dot="dot">
      <Avatar shape="square" size="large" />
    </Badge>
    <Switch v-model="dot" />
  </Space>
</Flex>

::: details Show Code

```vue
<script setup lang="ts">
import { MinusOutlined, PlusOutlined } from '@ant-design/icons-vue'
const value = ref(5)
const dot = ref(true)
function decline () {
  if (count.value >= 1) {
    count.value--
  }
}
function increase () {
  count.value++
}
</script>
<template>
  <Flex vertical>
    <Space gap="large" align="center">
      <Badge :value="value">
        <Avatar shape="square" size="large" />
      </Badge>
      <Button @click="decline">
        <MinusOutlined />
      </Button>
      <Button @click="increase">
        <PlusOutlined />
      </Button>
    </Space>
    <Space gap="large" align="center">
      <Badge :dot="dot">
        <Avatar shape="square" size="large" />
      </Badge>
      <Switch v-model="dot" />
    </Space>
  </Flex>
</template>
```

:::

## 自定义悬浮状态点的显示文字

<Badge :value="5" title="Custom hover text">
  <Avatar shape="square" size="large" />
</Badge>

::: details Show Code

```vue
<template>
  <Badge :value="5" title="Custom hover text">
    <Avatar shape="square" size="large" />
  </Badge>
</template>
```

:::

## 多彩徽标

### Presets

<Space>
  <Badge v-for="color in colors" :key="color" :color="color" :text="color" />
</Space>

::: details Show Code

```vue
<script setup lang="ts">
const colors = [
  'pink',
  'red',
  'yellow',
  'orange',
  'cyan',
  'green',
  'blue',
  'purple',
  'geekblue',
  'magenta',
  'volcano',
  'gold',
  'lime'
]
</script>
<template>
  <Space>
    <Badge v-for="color in colors" :key="color" :color="color" :text="color" />
  </Space>
</template>
```

:::

### Custom

<Space>
  <Badge color="#f50" text="#f50" />
  <Badge color="#2db7f5" text="#2db7f5" />
  <Badge color="#87d068" text="#87d068" />
  <Badge color="#108ee9" text="#108ee9" />
</Space>

::: details Show Code

```vue
<template>
  <Space>
    <Badge color="#f50" text="#f50" />
    <Badge color="#2db7f5" text="#2db7f5" />
    <Badge color="#87d068" text="#87d068" />
    <Badge color="#108ee9" text="#108ee9" />
  </Space>
</template>
```

:::

<style lang="less" scoped>
.u-value {
  display: inline-block;
  line-height: 20px;
  padding: 0 6px;
  background-color: #FAAD14;
  color: #FFF;
  border-radius: 10px;
  box-shadow: 0 0 0 1px #ffffff;
}
</style>

## APIs

### Badge

参数 | 说明 | 类型 | 默认值
:-- | :-- | :-- | :--
color | 自定义小圆点的颜色，优先级高于 `status` | [PresetColor](#presetcolor-type) &#124; string | undefined
value | 展示的数字或文字，为数字时大于 `max` 显示为 `max+`，为 `0` 时隐藏 | number &#124; string &#124; slot | undefined
max | 展示封顶的数字值 | number | 99
showZero | 当数值为 `0` 时，是否展示 `Badge` | boolean | false
dot | 不展示数字，只有一个小红点 | boolean | false
offset | 设置状态点的位置偏移，距默认位置左侧、上方的偏移量 `[x, y]: [水平偏移, 垂直偏移]` | [number &#124; string, number &#124; string] | undefined
status | 设置 `Badge` 为状态点 | [Status](#status-type) | undefined
text | 在设置了 `status` 的前提下有效，设置状态点的文本 | string &#124; slot | undefined
valueStyle | 设置徽标的样式 | [CSSProperties](https://cn.vuejs.org/api/utility-types.html#cssproperties) | {}
zIndex | 设置徽标的 `z-index` | number | 9
title | 设置鼠标放在状态点上时显示的文字 | string | undefined
ripple | 是否开启涟漪动画效果 | boolean | false

### PresetColor Type

名称 | 值
:-- | :--
PresetColor | 'pink' &#124; 'red' &#124; 'yellow' &#124; 'orange' &#124; 'cyan' &#124; 'green' &#124; 'blue' &#124; 'purple' &#124; 'geekblue' &#124; 'magenta' &#124; 'volcano' &#124; 'gold' &#124; 'lime'

### Status Type

名称 | 值
:-- | :--
Status | 'success' &#124; 'processing' &#124; 'default' &#124; 'error' &#124; 'warning'

## Slots

名称 | 说明 | 类型
:-- | :-- | :--
default | 自定义内容元素 | v-slot:default
value | 自定义徽标数字或文字 | v-slot:value
