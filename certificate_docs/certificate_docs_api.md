# AliOS Things API 兼容性认证规范

## 1. 内存管理
### 1.1 动态内存分配与释放
<table border=1 width=100%>
    <tr>
        <td width=100>测试用例编号</td>
        <td>AOS-1-1</td>
    </tr>
    <tr>
        <td>测试用例名称</td>
        <td>验证aos_malloc/aos_free能否正常分配与释放堆内存</td>
    </tr>
    <tr>
        <td>测试属性</td>
        <td>必选 | P0 | 功能用例</td>
    </tr>
    <tr>
        <td>测试步骤</td>
        <td><ol>
            <li>调用aos_malloc分配堆内存 512字节</li>
            <li>读写该512字节堆内存</li>
            <li>调用aos_free释放该512字节内存></li>
        </ol></td>
    </tr>
    <tr>
        <td>通过标准</td>
        <td><ol>
            <li>分配和释放堆内存成功</li>
            <li>读写分配的堆内存成功</li>
            <li>系统无crash，fail，error，assert，abort，内存泄漏，阻塞等异常</li>
        </ol></td>
    </tr>
</table>

### 1.2 动态内存分配与释放并初始化为0
<table border=1 width=100%>
    <tr>
        <td width=100>测试用例编号</td>
        <td>AOS-1-2</td>
    </tr>
    <tr>
        <td>测试用例名称</td>
        <td>验证aos_zalloc能否正常分配与释放堆内存并将分配的内存初始化为0</td>
    </tr>
    <tr>
        <td>测试属性</td>
        <td>必选 | P0 | 功能用例</td>
    </tr>
    <tr>
        <td>测试步骤</td>
        <td><ol>
            <li>调用aos_zalloc分配堆内存512 Bytes节</li>
            <li>读该512 Bytes堆内存，判断是否为0</li>
            <li>调用aos_free释放该内存</li>
        </ol></td>
    </tr>
    <tr>
        <td>通过标准</td>
        <td><ol>
            <li>分配和释放堆内存成功</li>
            <li>读写分配的堆内存成功</li>
            <li>系统无crash，fail，error，assert，abort，内存泄漏，阻塞等异常</li>
        </ol></td>
    </tr>
</table>
## 2. 任务管理
## 3. 多任务同行
## 4. 定时器
