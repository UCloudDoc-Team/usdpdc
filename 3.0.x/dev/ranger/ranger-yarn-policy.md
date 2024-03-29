# 添加 YARN 的 Ranger 访问权限策略

## 操作场景

Ranger 管理员可通过 Ranger 为 YARN 用户配置 YARN 管理员权限以及 YARN
队列资源管理权限。

## 前提条件

- 已安装 Ranger 服务且服务运行正常。
- 已创建或通过 RangerUserSync 同步需要配置权限的用户、用户组或 Role。

## 操作步骤

1. 使用 Ranger 管理员用户登录 Ranger 管理页面

2. 在首页中单击"YARN"区域的策略服务名称如"ranger-yarn-service"。

3. 单击"Add New Policy"，添加 YARN 权限控制策略。

4. 根据业务需求配置相关参数。

   | 参数名称                | 描述                                                         |
   | ----------------------- | ------------------------------------------------------------ |
   | Policy Name             | 策略名称，可自定义，不能与本服务内其他策略名称重复。         |
   | Policy Label            | 为当前策略指定一个标签，可以根据这些标签搜索报告和筛选策略。 |
   | Queue                   | 队列名称，支持通配符“\*”。<br/>如需子队列继承上级队列权限，可打开递归开关按钮。<br/>● Non-recursive：关闭递归 <br/>● Recursive：打开递归 |
   | Description             | 策略描述信息。                                               |
   | Audit Logging           | 是否审计此策略。                                             |
   | Allow Conditions        | 策略允许条件，配置本策略内允许的权限及例外。<br/>在“Select Role”、“Select Group”、“Select User”列选择已创建好的需要授予权限的 Role、用户组或用户，单击“Add Conditions”，添加策略适用的 IP 地址范围，单击“Add Permissions”，添加对应权限。<br/>● submit-app：提交队列任务权限<br/>● admin-queue：管理队列任务权限<br/>● Select/Deselect All：全选/取消全选<br/>如需让当前条件中的用户或用户组管理本条策略，可勾选“Delegate Admin”使这些用户成为受委托的管理员。被委托的管理员可以更新、删除本策略，它还可以基于原始策略创建子策略。<br/>如需添加多条权限控制规则，可单击 ➕ 按钮添加。如需删除权限控制规则，可单击 ❌ 按钮删除。<br/>Exclude from Allow Conditions：配置策略例外条件。 |
   | Deny All Other Accesses | 是否拒绝其它所有访问。<br/>● True：拒绝其它所有访问 <br/>● False：设置为 False，可配置 Deny Conditions。 |
   | Deny Conditions         | 策略拒绝条件，配置本策略内拒绝的权限及例外，配置方法与“Allow Conditions”类似。拒绝条件的优先级高于“Allow Conditions”中配置的允许条件。<br/>Exclude from Deny Conditions：配置排除在拒绝条件之外的例外规则。 |

   表 2 设置权限
   | 任务场景 | 角色授权操作 |
   | -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | 设置 YARN 管理员权限 | 1. 在首页中单击“YARN”区域的组件插件名称，例如“YARN”。<br/>2. 选择“Policy Name”为“all - queue”的策略，单击 ✏️ 按钮编辑策略。<br/>3. 在“Allow Conditions”区域，单击“Select User”下选择框选择用户。 |
   | 设置用户在指定 YARN 队列提交任务的权限 | 1. 在“Queue”配置队列名。<br/>2. 在“Allow Conditions”区域，单击“Select User”下选择框选择用户。<br/>3. 单击“Add Permissions”，勾选“submit-app”。 |
   | 设置用户在指定 YARN 队列管理任务的权限 | 1. 在“Queue”配置队列名。<br/>2. 在“Allow Conditions”区域，单击“Select User”下选择框选择用户。<br/>3. 单击“Add Permissions”，勾选“admin-queue”。 |

5. （可选）添加策略有效期。在页面右上角单击"Add Validity period"，设置"Start Time"和"End Time"，选择"Time Zone"。单击"Save"保存。如需添加多条策略有效期，可单击 ➕ 按钮添加。如需删除策略有效期，可单击 ❌ 按钮删除。

6. 单击"Add"，在策略列表可查看策略的基本信息。等待策略生效后，验证相关权限是否正常。

   如需禁用某条策略，可单击 ✏️ 按钮编辑策略，设置策略开关为"Disabled"。

   如果不再使用策略，可单击 🗑️ 按钮删除策略。

> 💡 说明：
>
> Ranger YARN 上面各个权限之间相互独立，没有语义上的包含与被包含关系。当前支持下面两种权限：
> 
>- submit-app：提交队列任务权限
> - admin-queue：管理队列任务权限
> 
>虽然 admin-queue 也有提交任务的权限，但和 submit-app 权限之间并没有包含关系。
