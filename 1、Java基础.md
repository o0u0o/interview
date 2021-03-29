# 面试题：
- 1、请用Iterable实现一个随机产生器？

- 2、Collection和Set的区别？

- 3、Map是不是Collection?

- 4、TreeMap和HashMap的区别？

- 5、HashMap vs Hashtable ？

- 6、实现key-value 的LRU缓存

# 讲解

## 容器（Collection）
### 容纳数据的容器
- 容器可以容纳一组(group)对象，不能容纳非对象，并提供 **增、删、改、、遍历** 操作，如下：使用foreach进行遍历：
```java
for(var c : collections){

}
```
### `Iterable<T>`
如果容器需要遍历，就需要实现`Iterable<T>`接口

> coding
```java
/**
 * 产生一个随机的字符串序列
 * 实现Iterable
 * @author mac
 * @date 2021/3/11 10:48 上午
 */
public class RandomStringGenerator<T> implements Iterable<T> {

    private final List<T> list;

    /**
     * 生成随机数
     * @param list
     */
    public RandomStringGenerator(List<T> list){
        this.list = list;
    }

    @Override
    public Iterator<T> iterator() {
        return new Iterator<T>() {

            /**
             * 是否有下一个
             * @return
             */
            @Override
            public boolean hasNext() {
                return true;
            }

            /***
             * 随机取出一个再返回
             * @return
             */
            @Override
            public T next() {
                return list.get((int)(list.size() * Math.random()));
            }
        };
    }

    public static void main(String[] args) {
        var list  = Arrays.asList("List", "Tree", "Array");

        var gen = new RandomStringGenerator<String>(list);

//        for (var s : gen) {
//            System.out.println(s);
//        }

        var iterator = gen.iterator();
        for (int i = 0; i < 100; i++) {
            System.out.println(iterator.next());
        }

    }
}

```

### Collection接口(源码解读)

### 集合(Set<E>)

## 映射（Map）

# 总结：