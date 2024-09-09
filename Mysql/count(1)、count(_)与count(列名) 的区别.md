<font style="color:rgba(0, 0, 0, 0.82);">在 SQL 中，</font>`<font style="color:rgba(0, 0, 0, 0.82);">COUNT()</font>`<font style="color:rgba(0, 0, 0, 0.82);"> 函数用于统计行的数量。不同的用法 (</font>`<font style="color:rgba(0, 0, 0, 0.82);">COUNT(1)</font>`<font style="color:rgba(0, 0, 0, 0.82);">, </font>`<font style="color:rgba(0, 0, 0, 0.82);">COUNT(*)</font>`<font style="color:rgba(0, 0, 0, 0.82);">, </font>`<font style="color:rgba(0, 0, 0, 0.82);">COUNT(column_name)</font>`<font style="color:rgba(0, 0, 0, 0.82);">) 具有略有不同的行为和性能表现。以下是它们的具体区别：</font>

### <font style="color:rgba(0, 0, 0, 0.82);">1.</font><font style="color:rgba(0, 0, 0, 0.82);"> </font>`<font style="color:rgba(0, 0, 0, 0.82);">COUNT(1)</font>`
+ **<font style="color:rgba(0, 0, 0, 0.82);">功能</font>**<font style="color:rgba(0, 0, 0, 0.82);">：</font>
    - <font style="color:rgba(0, 0, 0, 0.82);">统计表中行的数量，包含所有行，不论行中的值是什么。</font>
+ **<font style="color:rgba(0, 0, 0, 0.82);">工作原理</font>**<font style="color:rgba(0, 0, 0, 0.82);">：</font>
    - <font style="color:rgba(0, 0, 0, 0.82);">每一行以常数</font><font style="color:rgba(0, 0, 0, 0.82);"> </font>`<font style="color:rgba(0, 0, 0, 0.82);">1</font>`<font style="color:rgba(0, 0, 0, 0.82);"> </font><font style="color:rgba(0, 0, 0, 0.82);">进行计算，即对于每一行都会计数一次，因此它的计算与</font><font style="color:rgba(0, 0, 0, 0.82);"> </font>`<font style="color:rgba(0, 0, 0, 0.82);">COUNT(*)</font>`<font style="color:rgba(0, 0, 0, 0.82);"> </font><font style="color:rgba(0, 0, 0, 0.82);">基本相同。</font>
+ **<font style="color:rgba(0, 0, 0, 0.82);">效率</font>**<font style="color:rgba(0, 0, 0, 0.82);">：</font>
    - <font style="color:rgba(0, 0, 0, 0.82);">在某些数据库实现中，</font>`<font style="color:rgba(0, 0, 0, 0.82);">COUNT(1)</font>`<font style="color:rgba(0, 0, 0, 0.82);"> </font><font style="color:rgba(0, 0, 0, 0.82);">的性能可能与</font><font style="color:rgba(0, 0, 0, 0.82);"> </font>`<font style="color:rgba(0, 0, 0, 0.82);">COUNT(*)</font>`<font style="color:rgba(0, 0, 0, 0.82);"> </font><font style="color:rgba(0, 0, 0, 0.82);">相同，因为二者在功能上是等效的。</font>

### <font style="color:rgba(0, 0, 0, 0.82);">2.</font><font style="color:rgba(0, 0, 0, 0.82);"> </font>`<font style="color:rgba(0, 0, 0, 0.82);">COUNT(*)</font>`
+ **<font style="color:rgba(0, 0, 0, 0.82);">功能</font>**<font style="color:rgba(0, 0, 0, 0.82);">：</font>
    - <font style="color:rgba(0, 0, 0, 0.82);">统计表中所有行的数量，包括所有列，无论列的值是否为 NULL。</font>
+ **<font style="color:rgba(0, 0, 0, 0.82);">工作原理</font>**<font style="color:rgba(0, 0, 0, 0.82);">：</font>
    - <font style="color:rgba(0, 0, 0, 0.82);">按行统计时，不考虑列的具体值和数据类型。</font>
+ **<font style="color:rgba(0, 0, 0, 0.82);">效率</font>**<font style="color:rgba(0, 0, 0, 0.82);">：</font>
    - <font style="color:rgba(0, 0, 0, 0.82);">是最常用的方法之一，特别是在 InnoDB 引擎中，</font><font style="color:rgba(0, 0, 0, 0.82);"> </font>`<font style="color:rgba(0, 0, 0, 0.82);">COUNT(*)</font>`<font style="color:rgba(0, 0, 0, 0.82);"> </font><font style="color:rgba(0, 0, 0, 0.82);">通常是最优的计数形式，因为它被优化为直接统计数据页上的数目。</font>

### <font style="color:rgba(0, 0, 0, 0.82);">3.</font><font style="color:rgba(0, 0, 0, 0.82);"> </font>`<font style="color:rgba(0, 0, 0, 0.82);">COUNT(column_name)</font>`
+ **<font style="color:rgba(0, 0, 0, 0.82);">功能</font>**<font style="color:rgba(0, 0, 0, 0.82);">：</font>
    - <font style="color:rgba(0, 0, 0, 0.82);">统计指定列中非 NULL 值的行数。</font>
+ **<font style="color:rgba(0, 0, 0, 0.82);">工作原理</font>**<font style="color:rgba(0, 0, 0, 0.82);">：</font>
    - <font style="color:rgba(0, 0, 0, 0.82);">只计数该列中有非 NULL 值的行。因此，如果某行在</font><font style="color:rgba(0, 0, 0, 0.82);"> </font>`<font style="color:rgba(0, 0, 0, 0.82);">column_name</font>`<font style="color:rgba(0, 0, 0, 0.82);"> </font><font style="color:rgba(0, 0, 0, 0.82);">中的值为 NULL，则不会计入总数。</font>
+ **<font style="color:rgba(0, 0, 0, 0.82);">适用场景</font>**<font style="color:rgba(0, 0, 0, 0.82);">：</font>
    - <font style="color:rgba(0, 0, 0, 0.82);">用于需要过滤掉 NULL 值时，例如，统计某个特定字段有值的记录数。</font>

### <font style="color:rgba(0, 0, 0, 0.82);">性能对比</font>
+ <font style="color:rgba(0, 0, 0, 0.82);">现代数据库通常对</font><font style="color:rgba(0, 0, 0, 0.82);"> </font>`<font style="color:rgba(0, 0, 0, 0.82);">COUNT(*)</font>`<font style="color:rgba(0, 0, 0, 0.82);"> </font><font style="color:rgba(0, 0, 0, 0.82);">和</font><font style="color:rgba(0, 0, 0, 0.82);"> </font>`<font style="color:rgba(0, 0, 0, 0.82);">COUNT(1)</font>`<font style="color:rgba(0, 0, 0, 0.82);"> </font><font style="color:rgba(0, 0, 0, 0.82);">进行了优化，因此二者性能基本相似。</font>
+ `<font style="color:rgba(0, 0, 0, 0.82);">COUNT(column_name)</font>`<font style="color:rgba(0, 0, 0, 0.82);"> </font><font style="color:rgba(0, 0, 0, 0.82);">可能较慢一些，特别是当列中有大量 NULL 值时，因为需要遍历和检查每一个值。</font>

### <font style="color:rgba(0, 0, 0, 0.82);">用法选择</font>
+ **<font style="color:rgba(0, 0, 0, 0.82);">大多数情况下</font>**<font style="color:rgba(0, 0, 0, 0.82);">：</font>`<font style="color:rgba(0, 0, 0, 0.82);">COUNT(*)</font>`<font style="color:rgba(0, 0, 0, 0.82);"> </font><font style="color:rgba(0, 0, 0, 0.82);">是首选，因为它清晰明了并且通常是经过优化的。</font>
+ **<font style="color:rgba(0, 0, 0, 0.82);">特定需求</font>**<font style="color:rgba(0, 0, 0, 0.82);">：当需要统计去除 NULL 值的特定列的值，只用</font><font style="color:rgba(0, 0, 0, 0.82);"> </font>`<font style="color:rgba(0, 0, 0, 0.82);">COUNT(column_name)</font>`<font style="color:rgba(0, 0, 0, 0.82);">。</font>

### <font style="color:rgba(0, 0, 0, 0.82);">小结</font>
<font style="color:rgba(0, 0, 0, 0.82);">选择 </font>`<font style="color:rgba(0, 0, 0, 0.82);">COUNT(*)</font>`<font style="color:rgba(0, 0, 0, 0.82);">、</font>`<font style="color:rgba(0, 0, 0, 0.82);">COUNT(1)</font>`<font style="color:rgba(0, 0, 0, 0.82);"> 或 </font>`<font style="color:rgba(0, 0, 0, 0.82);">COUNT(column_name)</font>`<font style="color:rgba(0, 0, 0, 0.82);"> 应基于具体需求。如果只是需要统计总行数，可以使用 </font>`<font style="color:rgba(0, 0, 0, 0.82);">COUNT(*)</font>`<font style="color:rgba(0, 0, 0, 0.82);">。如果需要忽略某列中的 NULL 值，则需使用 </font>`<font style="color:rgba(0, 0, 0, 0.82);">COUNT(column_name)</font>`<font style="color:rgba(0, 0, 0, 0.82);">。它们之间选取的重要依据在于是否需要忽略 NULL 值及所用数据库的优化情况。</font>

