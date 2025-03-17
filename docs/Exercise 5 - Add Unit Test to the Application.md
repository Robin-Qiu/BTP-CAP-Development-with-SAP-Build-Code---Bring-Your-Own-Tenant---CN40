<div class="draftWatermark"></div>

# 练习 5 - 在应用程序中添加单元测试
---

在本练习中，我们将为自动紧急程度确定增加一个单元测试。该单元测试会检查根据事件标题是否将紧急程度提升到 **高**。

## 创建针对基于事件标题更新紧急程度的测试

从**Storyboard**中选择**Processor**，然后点击**Open in Graphical Modeler**。CDS 图形建模器将打开。

选择 **Incidents** 实体，然后点击实体标题旁边的**Add Logic**图标。

![](vx_images/391565065667596.png)

点击"取消"按钮

![](vx_images/79335569886493.png)

在**Application Logic Editor**中选择 **changeUrgencyDueToSubject**，然后点击 **Open Code Editor > Unit Test**。

![](vx_images/110284422840203.png)

点击**是**按钮以激活测试环境。
![](vx_images/222644465484670.png)

在**'test-changeUrgencyDueToSubject.js'** 文件中，在**Your code here**注释之后添加以下内容：

```
  let draftId, incidentId;

  // 创建一个事件
  const createIncident = await POST(`/service/Processor/Incidents`, {
    title: '需要紧急关注!',
  });

  draftId = createIncident.data.ID;
  expect(createIncident.status).to.equal(201);
  expect(createIncident.statusText).to.equal('Created');

  const responseActivate = await POST(
    `/service/Processor/Incidents(ID=${draftId},IsActiveEntity=false)/Processor.draftActivate`
  );
  expect(responseActivate.status).to.eql(201);
  incidentId = responseActivate.data.ID;
  // 测试紧急程度
  expect(responseActivate.data.urgency_code).to.eql('H');

  const getIncident = await GET(`/service/Processor/Incidents(ID=${incidentId},IsActiveEntity=true)`);

  expect(getIncident.status).to.eql(200);
  expect(getIncident.data.urgency_code).to.eql('H');

  // 清理
  const responseDelete = await DELETE(`/service/Processor/Incidents(ID=${incidentId},IsActiveEntity=true)`);
  expect(responseDelete.status).to.eql(204);
```

![](vx_images/551631733116477.png)

现在我们将从终端运行测试。

从活动栏中选择汉堡图标，然后选择**Terminal > New Terminal**。

![](vx_images/46536896297919.png)

终端打开。 

**使用chai需要在项目中添加以下依赖：**

```

npm add -D chai@4 chai-as-promised chai-subset jest
```


![](vx_images/70522811455857.png)


复制以下命令，将其粘贴到终端中并通过按下**Enter**来运行测试。

```
basctl --command lcap.applicationLogic.runTest
```

![](vx_images/286081878431436.png)

测试开始运行，并且终端中应该显示以下**PASS**指示：

![](vx_images/72222060292062.png)

## 总结
我们现在为应用程序添加了一个单元测试。