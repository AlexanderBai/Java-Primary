#Comparable和Comparator区别

###1、Comparable

> Comparable是**内部比较器**（即用于实现了Comparable接口的类与自身进行比较），称自然排序；
>
> 至于一个类与实现了Comparable接口的另一个类的比较则依赖于CompareTo方法的实现。

```java 
/**
 * @Author AlexanderBai
 * @data 2019/3/14 15:20
 */
public class Domain implements Comparable<Domain> {
    private String str;

    public Domain(String str) {
        this.str = str;
    }

    @Override
    public int compareTo(Domain domain) {
        if (this.str.compareTo(domain.str)>0) {
            return 1;
        }
        else if (this.str.compareTo(domain.str) == 0) {
            return 0;
        }
        else
            return -1;
    }

    public static void main(String[] args) {
        Domain domain = new Domain("a");
        Domain domain1 = new Domain("a");
        Domain domain2 = new Domain("B");
        Domain domain3 = new Domain("c");
        System.out.println("domain.compareTo(domain1) = " + domain.compareTo(domain1));
        System.out.println("domain.compareTo(domain2) = " + domain.compareTo(domain2));
        System.out.println("domain2.compareTo(domain3) = " + domain2.compareTo(domain3));
    }
}
```

> 运行结果：
>
> domain.compareTo(domain1) = 0
> domain.compareTo(domain2) = 1
> domain2.compareTo(domain3) = -1

#### 1.1、基于Comparable实现的二叉树操作

Comparable比较器的排序过程是**二叉树**的排序方法，再利用中序遍历依次读取

```java
package testfile;

/**
 * @Author AlexanderBai
 * @data 2019/3/14 15:52
 */
class BinaryTree{
    class Node{
        private Comparable data;
        private Node left;
        private Node right;

        /**
         * 添加子节点
         * @param newNode
         */
        public void addNode(Node newNode) {
            if (newNode.data.compareTo(this.data)<0) {
                if (this.left == null) {
                    this.left=newNode;
                }else {
                    this.left.addNode(newNode);
                }
            }
            if (newNode.data.compareTo(this.data)>=0){
                if (this.right == null) {
                    this.right = newNode;
                }else {
                    this.right.addNode(newNode);
                }
            }
        }

        //中序遍历输出
        public void printNode() {
            if (this.left != null) {
                this.left.printNode();
            }
            System.out.println(this.data+"\t");
            if (this.right != null) {
                this.right.printNode();
            }
        }
    }
    private Node root;

    /**
     * 添加根节点
     * @param data
     */
    public void add(Comparable data) {
        Node newNode=new Node();
        newNode.data=data;
        if (root == null) {
            root=newNode;
        }else {
            root.addNode(newNode);
        }
    }

    public void print() {
        this.root.printNode();
    }
}

public class Test {
    public static void main(String[] args) {
        BinaryTree binaryTree=new BinaryTree();
        binaryTree.add(8);
        binaryTree.add(87);
        binaryTree.add(2456);
        binaryTree.add(76);
        binaryTree.add(1);
        binaryTree.add(44);
        System.out.println("排序之后的结果是：");
        binaryTree.print();
    }
}
```

>运行结果：
>
>![1552555189479](C:\Users\AlexanderBai\AppData\Roaming\Typora\typora-user-images\1552555189479.png)

### 2、Comparator

