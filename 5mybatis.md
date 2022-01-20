# mybatis优缺点

>优点：
>
>* 简单易学，基于sql编程
>* JDBC相比，消除了JDBC大量冗余的代码，不需要手动开关连接。
>* 很好地与数据库兼容，使用JDBC连接数据库，所以只要jdbc支持的，都可以直接使用，并且有可扩展性，引入jar包即可，开发人员不需要考虑数据库的差异性。
>* 提供了很多第三方插件，分页插件，逆向工程。
>* 能够与spring很好地集成。
>* SQL写在xml里，从程序中分离，解耦操作，并且可以服用。
>* 提供XML标签，支持编写动态sql语句（for each, if ）
>* 提供映射标签，支持对象与数据库的ORM字段关系映射



> 缺点：
>
> * sql语句编写工作量大，字段多，关联表多
> * sql语句过于依赖数据库，导致数据库移植性差，不能随意更换数据库。





# mybatis与hibernate区别

> 相同点：
>
> 都是通过sessionFactoryBuilder由XML配置文件生成sessionFactory，然后由sessionFactory生成session，最后由session 来开启执行事务和sql语句。
>
> 都支持JDBC和JTA事务处理。



> 不同点：
>
> * Hibernate是全自动，mybatis是半自动，Hibernate完全可以通过对象关系模型实现对数据库的操作，而mybatis仅有基本的字段映射，对象数据以及对象关系仍然需要通过手写sql来实现和管理。
> * Hibernate数据库移植性远大于mybatis，可以将Hibernate看做一个黑盒，通过强大的hql语言和映射关系，大大降低了与数据库的耦合性，而mybatis需要手写sql，耦合性直接取决于程序sql语句。
> * Hibernate具有完整的日志系统，mybatis缺点意思。
> * mybatis相比Hibernate需要关心很多细节，Hibernate配置要比前者复杂多，学习成本高，所以mybatis很容易上手开发，但会导致前期bug较多，后期需要debug注意细节。
> * sql优化上，mybatis要比Hibernate方便很多，因为Hibernate的hql很多都是自动生成的，遇到一些别的需求时，有局限性。
> * 缓存机制上，hibernate要比mybatis好一些。因为hibernate对查询对象有着良好的管理机制，用户无需关心sql，如果出现脏数据，系统汇报出错误并提示。





## mybatis 中#{} 和 ${} 区别

* #{} 是预编译处理，而后者则是字符串替换
* mybatis在处理#{}时，会将sql中的#{} 替换为？号，调用prepareStatement的set方法来赋值
* mybatis在处理${}时，就是把${}替换成变量的值
* 使用#{} 可以有效的防止sql注入，提高系统安全性





## mysql的隔离级别有哪些

有四种隔离级别，用于限定事务内外哪些改变是可见的，哪些改变是不可见的，低级别的隔离一般支持更高的并发处理，并且拥有更低的系统开销。
