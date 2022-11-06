# Composition API

![img](https://velog.velcdn.com/images%2Fsian%2Fpost%2F8cf4efb6-f4a0-4e93-83e8-ac671ae37f95%2Fimage.png)

Composition API란 컴포넌트 로직을 유연하게 구성할 수 있는 API 모음으로 로직의 **재사용성과 가독성**을 높여준다.
위의 그림과 같이 기존에는 data, methods, computed에 각각 로직이 흩어져 있었는데 Composition API를 활용하면 로직이 모아지는 것을 알 수 있다.

Composition API의 가장 큰 특징 중 하나는 \*\*Setup이다. 기존 Vue2의 Life Cycle과 비교하자면,

**beforeCreate -> setup()
created -> setup()**
beforeMount -> **on**BeforeMount
mounted -> **on**Mounted
beforeUpdate -> **on**BeforeUpdate
updated -> **on**Updated
beforeDestroy -> **on**BeforeUnmount
destroyed -> **on**Unmounted
activated -> **on**Activated
deactivated -> **on**Deactivated
errorCaptured -> **on**ErrorCaptured

위와 같이 beforeCreate나 created는 모두 setup() 안으로 들어가고, 나머지 life cycle은 onXXX function들로 적용할 수 있다.
즉, setup()이라는 일종의 훅에서 초기화를 진행한다.
setup에서 반응형 데이터를 바인딩해주고, 기존에는 computed에 따로 명시되어 있던 computed 속성들을 정의해줄 수 있다.

#### Composition API 예시

- 기존 방식

```vue
<template>
  <div>
    <h1>Count: {{ count }}</h1>
    <h1>Double: {{ double }}</h1>
    <button @click="increase">increase</button>
    <button @click="decrease">decrease</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: 0,
    };
  },
  computed: {
    double() {
      return this.count * 2;
    },
  },
  methods: {
    increase() {
      ++this.count;
    },
    decrease() {
      --this.count;
    },
  },
};
</script>
```

딱히 별 기능 없이 간단한 카운트 기능을 하는 Component에 비슷한 기능을 가진 로직들이 data, methods, computed로 각각 분리되어 있다.

- Composition API 방식

```vue
<template>
  <div>
    <h1>Count: {{ count }}</h1>
    <h1>Double: {{ double }}</h1>
    <button @click="increase">increase</button>
    <button @click="decrease">decrease</button>
  </div>
</template>

<script>
import { reactive, computed } from "@vue/composition-api";

const useCount = () => {
  const count = ref(0);
  const double = computed(() => count.value * 2);

  const increase = () => ++count.value;
  const decrease = () => --count.value;

  return { count, double, increase, decrease };
};

export default {
  setup() {
    const { count, double, increase, decrease } = useCount();

    return {
      count,
      double,
      increase,
      decrease,
    };
  },
};
</script>
```

관련된 것들을 한 부분에서 해결하고 있기 때문에 추후 Component를 나눌 때도 편해지고 가독성도 좋아진다.
