# TIA Portal Openness学习笔记_从零开发openness应用-CSDN博客
**目录**

[一、准备工作](#t0)

[１、学习手册](#t1)

[２、软件](#t2)

[（１）开发软件](#t3)

[（２）辅助工具](#t4)

[３、学习方法](#t5)

[（１）对Openness中的对象模型整体框架有个基本认识](#t6)

[（２）先整体，后局部](#t7)

[（３）编写代码测试](#t8)

[二、学习TiaPortal　Openness中的对象　](#t9)

[一、TiaPortal类](#t10)

[１、属性](#t11)

[（１）GlobalLibraries](#%EF%BC%88%EF%BC%91%EF%BC%89GlobalLibraries)

[（２）HardwareCatalog](#%EF%BC%88%EF%BC%92%EF%BC%89HardwareCatalog)

[（３）LocalSessions](#%EF%BC%88%EF%BC%93%EF%BC%89LocalSessions)

[（４）Projects](#%EF%BC%88%EF%BC%94%EF%BC%89Projects)

[（５）ProjectServers](#%EF%BC%88%EF%BC%95%EF%BC%89ProjectServers)

[（６）SettingsFolders](#%EF%BC%88%EF%BC%96%EF%BC%89SettingsFolders)

[二、Project类](#t12)

[1、属性](#t13)

[2、方法](#t14)

[(1)创建项目](#%281%29%E5%88%9B%E5%BB%BA%E9%A1%B9%E7%9B%AE)

[(2)打开项目](#%282%29%E6%89%93%E5%BC%80%E9%A1%B9%E7%9B%AE)

[(3)修改项目属性](#%283%29%E4%BF%AE%E6%94%B9%E9%A1%B9%E7%9B%AE%E5%B1%9E%E6%80%A7)

[(4)保存项目](#%284%29%E4%BF%9D%E5%AD%98%E9%A1%B9%E7%9B%AE)

[(5)另存为项目](#%285%29%E5%8F%A6%E5%AD%98%E4%B8%BA%E9%A1%B9%E7%9B%AE)

[(6)关闭项目](#%286%29%E5%85%B3%E9%97%AD%E9%A1%B9%E7%9B%AE)

[3、示例](#t15)

[4、运行效果](#t16)

[三、Device类](#t17)

[1、属性](#t18)

[2、方法](#t19)

[(1)创建设备](#%281%29%E5%88%9B%E5%BB%BA%E8%AE%BE%E5%A4%87)

[a、仅创建设备](#a%E3%80%81%E4%BB%85%E5%88%9B%E5%BB%BA%E8%AE%BE%E5%A4%87)

[b、通过设备项类型标识符创建设备对象](#b%E3%80%81%E9%80%9A%E8%BF%87%E8%AE%BE%E5%A4%87%E9%A1%B9%E7%B1%BB%E5%9E%8B%E6%A0%87%E8%AF%86%E7%AC%A6%E5%88%9B%E5%BB%BA%E8%AE%BE%E5%A4%87%E5%AF%B9%E8%B1%A1)

[c、两种创建设备方法的区别](#c%E3%80%81%E4%B8%A4%E7%A7%8D%E5%88%9B%E5%BB%BA%E8%AE%BE%E5%A4%87%E6%96%B9%E6%B3%95%E7%9A%84%E5%8C%BA%E5%88%AB)

[(2)删除设备](#%282%29%E5%88%A0%E9%99%A4%E8%AE%BE%E5%A4%87)

[(3)枚举设备](#%283%29%E6%9E%9A%E4%B8%BE%E8%AE%BE%E5%A4%87)

[a、枚举根节点下的设备](#a%E3%80%81%E6%9E%9A%E4%B8%BE%E6%A0%B9%E8%8A%82%E7%82%B9%E4%B8%8B%E7%9A%84%E8%AE%BE%E5%A4%87)

[b、枚举“未分组设备”下的设备](#b%E3%80%81%E6%9E%9A%E4%B8%BE%E2%80%9C%E6%9C%AA%E5%88%86%E7%BB%84%E8%AE%BE%E5%A4%87%E2%80%9D%E4%B8%8B%E7%9A%84%E8%AE%BE%E5%A4%87)

[(4)访问设备](#%284%29%E8%AE%BF%E9%97%AE%E8%AE%BE%E5%A4%87)

[四、DeviceItem类](#t20)

[1、属性](#t21)

[2、方法](#t22)

[(1)创建设备项](#%281%29%E5%88%9B%E5%BB%BA%E8%AE%BE%E5%A4%87%E9%A1%B9)

[(2)插入设备项](#%282%29%E6%8F%92%E5%85%A5%E8%AE%BE%E5%A4%87%E9%A1%B9)

[(3)移动](#%283%29%E7%A7%BB%E5%8A%A8)

[(4)复制](#%284%29%E5%A4%8D%E5%88%B6)

[(5)删除](#%285%29%E5%88%A0%E9%99%A4)

[(6)枚举](#%286%29%E6%9E%9A%E4%B8%BE)

[(7)访问](#%287%29%E8%AE%BF%E9%97%AE)

[五、Subnet类](#t23)

[(1)属性](#t24)

[(2)方法](#t25)

[1、创建子网](#1%E3%80%81%E5%88%9B%E5%BB%BA%E5%AD%90%E7%BD%91)

[2、删除子网](#2%E3%80%81%E5%88%A0%E9%99%A4%E5%AD%90%E7%BD%91)

[(3)如何让Device能联接子网](#t26)

[六、Sivarc类](#t27)

[1、属性](#t28)

[2、方法](#t29)

[(1)访问Sivarc服务](#%281%29%E8%AE%BF%E9%97%AESivarc%E6%9C%8D%E5%8A%A1)

[(2)创建画面规则](#%282%29%E5%88%9B%E5%BB%BA%E7%94%BB%E9%9D%A2%E8%A7%84%E5%88%99)

[(3)查找规则表](#%283%29%E6%9F%A5%E6%89%BE%E8%A7%84%E5%88%99%E8%A1%A8)

[(4)查找规则组](#%284%29%E6%9F%A5%E6%89%BE%E8%A7%84%E5%88%99%E7%BB%84)

[(5)查找规则](#%285%29%E6%9F%A5%E6%89%BE%E8%A7%84%E5%88%99)

[七、ProjectLibrary类](#t30)

[1、模板副本文件夹](#t31)

[(1)获取模板副本中的FB块](#%281%29%E8%8E%B7%E5%8F%96%E6%A8%A1%E6%9D%BF%E5%89%AF%E6%9C%AC%E4%B8%AD%E7%9A%84FB%E5%9D%97)

[(2)获取模板副本中的画面模板](#%282%29%E8%8E%B7%E5%8F%96%E6%A8%A1%E6%9D%BF%E5%89%AF%E6%9C%AC%E4%B8%AD%E7%9A%84%E7%94%BB%E9%9D%A2%E6%A8%A1%E6%9D%BF)

[2、类型文件夹](#t32)

[(1)获取类型中的面板实例](#%281%29%E8%8E%B7%E5%8F%96%E7%B1%BB%E5%9E%8B%E4%B8%AD%E7%9A%84%E9%9D%A2%E6%9D%BF%E5%AE%9E%E4%BE%8B)

[三、学习TiaPortal Openness对象模型框架中的节点](#t33)

[一、TiaPortal节点](#t34)

[(1)GlobalLibraries](#t35)

[(2)HardwareCatalog](#t36)

[(3)LocalSessions](#t37)

[(4)ProjectServers](#t38)

[(5)Projects](#t39)

[(6)SettingsFolders](#t40)

[二、Project节点](#t41)

[(1)Comment](#t42)

[(2)DeviceGroups](#t43)

[(3)Devices](#t44)

[(4)Graphics](#t45)

[(5)HistoryEntries](#t46)

[(6)HwUtilities](#t47)

[(7)LanguageSettings](#t48)

[(8)PlantViews](#t49)

[(9)ProjectLibrary](#t50)

[(10)Subnets](#t51)

[(11)UngroupedDeviceGroup](#t52)

[(12)UsedProducts](#t53)

[三、Device节点](#t54)

[(1)DeviceItems节点](#%281%29DeviceItems%E8%8A%82%E7%82%B9)

[a、DeviceItem节点](#a%E3%80%81DeviceItem%E8%8A%82%E7%82%B9)

[b、HwIdentifiers节点](#b%E3%80%81HwIdentifiers%E8%8A%82%E7%82%B9)

[(2)HwIdentifiers节点](#%282%29HwIdentifiers%E8%8A%82%E7%82%B9)

[a、HwIdentifier节点](#a%E3%80%81HwIdentifier%E8%8A%82%E7%82%B9)

[四、DeviceItem节点](#t55)

* * *

一、准备工作
------

### １、 学习手册

西门子官网可下载

![](https://i-blog.csdnimg.cn/direct/1392836f2e984542b72b8996977c0fe1.png)

### ２、软件

**注意：TIA Portal版本要与OpennessExplorer版本保持一致**

#### （１）开发软件

![](https://i-blog.csdnimg.cn/direct/b103c20e06c04931b9d430ad19ab6b39.png)
![](https://i-blog.csdnimg.cn/direct/1b462028a2d044669997d3db046b40ea.png)

#### （２）辅助工具

![](https://i-blog.csdnimg.cn/direct/9b7add3b4f5a4435a62aebd64ec01444.png)

### ３、学习方法

#### （１）对Openness中的对象模型整体框架有个基本认识

**官方Openness手册**

![](https://i-blog.csdnimg.cn/direct/fb909a26a4ce4eb1848a4080d27830c2.png)

**OpennessExplorer中项目结构图**

![](https://i-blog.csdnimg.cn/direct/5bd6b548172e41838fc703d55419f9a0.png)

#### （２）先整体，后局部

在认识整体的对象模型框架后，对框架中的对象有具体的认识：属性、方法、事件等

**Visual Studio中的对象浏览器**

![](https://i-blog.csdnimg.cn/direct/b722160158fd46369f15b97504b94c57.png)

**OpennessExplore中的对象**

![](https://i-blog.csdnimg.cn/direct/3a3893ac909b48b785e9516d968cef5b.png)

#### （３）编写代码测试

```null
using (TiaPortal tiaPortal = new TiaPortal(TiaPortalMode.WithoutUserInterface))var projects = tiaPortal.Projects;string projectPath = AppDomain.CurrentDomain.BaseDirectory + "FirstDay\\FirstDay.ap19";    projects.Open(new System.IO.FileInfo(projectPath));foreach (var project in projects)        richTextBox1.Text += "项目名称：" + project.Name + "作者：" + project.Author + "\r\n";
```

二、学习TiaPortal　Openness中的对象　
---------------------------

### 一、TiaPortal 类

在TiaPortal项目中，最顶层的根节点就是TiaPortal对象

![](https://i-blog.csdnimg.cn/direct/12b4102bf6a14ad59f08e245d9e0b830.png)

#### １、属性

![](https://i-blog.csdnimg.cn/direct/7ecbcc34076b4f8da0b5bbc19907e9c8.png)

![](https://i-blog.csdnimg.cn/direct/4957eccb2ee948e88279223ae0cbf4dd.png)

##### （１）GlobalLibraries

##### （２）HardwareCatalog

##### （３）LocalSessions

##### （４）Projects

##### （５）ProjectServers

##### （６）SettingsFolders

### 二、Project类

![](https://i-blog.csdnimg.cn/direct/f51a0ca76f514d4d8990cbe7829c61e8.png)

#### 1、属性

![](https://i-blog.csdnimg.cn/direct/82b6518e9eef4c8a84bb79784f14a0e5.png)

Project类是继承自ProjectBase类，这些属性大部分也是继承自ProjectBase

#### 2、方法

##### (1)创建项目

##### (2)打开项目

```null
string projectPath = AppDomain.CurrentDomain.BaseDirectory + "FirstDay\\FirstDay.ap19";Project project = projects.Open(new System.IO.FileInfo(projectPath));
```

##### (3)修改项目属性

```null
project.IsSimulationDuringBlockCompilationEnabled = checkBox1.Checked;project.IsVirtualPlcDuringBlockCompilationEnabled = checkBox2.Checked;
```

##### (4)保存项目

```null
project.Save();
```

##### (5)另存为项目

```null
SaveFileDialog saveFileDialog = new SaveFileDialog();saveFileDialog.FileName = "NewProject.ap19"; DialogResult res = saveFileDialog.ShowDialog();if (res == DialogResult.OK)string targetFilePath = saveFileDialog.FileName;    DirectoryInfo directoryInfo = new DirectoryInfo(targetFilePath);    project.SaveAs(directoryInfo);
```

##### (6)关闭项目

```null
project.Close();
```

#### 3、示例

```null
public partial class Form1 : Form        tiaPortal = new TiaPortal(TiaPortalMode.WithoutUserInterface);private void button1_Click(object sender, EventArgs e)        richTextBox1.Text += "项目作者：" + project.Author +"\r\n"+"项目版权：" + project.Copyright + "\r\n" +"项目创建时间：" + project.CreationTime + "\r\n" +"项目系列：" + project.Family + "\r\n" +"项目名称：" + project.Name + "\r\n" +"项目路径：" + project.Path + "\r\n" +"项目大小：" + project.Size + "\r\n" +"项目版本：" + project.Version + "\r\n" +"项目最近修改时间：" + project.LastModified+ "\r\n" +"项目最近修改人：" + project.LastModifiedBy+ "\r\n" +"支持在块编译过程中进行仿真：" +project.IsSimulationDuringBlockCompilationEnabled+ "\r\n" +"启用在虚拟PLC中使用S71500块：" +project.IsVirtualPlcDuringBlockCompilationEnabled+ "\r\n" +"============" +DateTime.Now+"==============";private void button2_Click(object sender, EventArgs e)private void button5_Click(object sender, EventArgs e)var projects = tiaPortal.Projects;string projectPath = AppDomain.CurrentDomain.BaseDirectory + "FirstDay\\FirstDay.ap19";        project = projects.Open(new System.IO.FileInfo(projectPath));private void button4_Click(object sender, EventArgs e)private void button3_Click(object sender, EventArgs e)        SaveFileDialog saveFileDialog = new SaveFileDialog();        saveFileDialog.FileName = "NewProject.ap19";         DialogResult res = saveFileDialog.ShowDialog();if (res == DialogResult.OK)string targetFilePath = saveFileDialog.FileName;            DirectoryInfo directoryInfo = new DirectoryInfo(targetFilePath);            project.SaveAs(directoryInfo);private void button6_Click(object sender, EventArgs e)        project.IsSimulationDuringBlockCompilationEnabled = checkBox1.Checked;        project.IsVirtualPlcDuringBlockCompilationEnabled = checkBox2.Checked;
```

#### 4、运行效果

![](https://i-blog.csdnimg.cn/direct/4369adf1a5ec4dc68849f0885de3a893.png)

### 三、Device类

#### 1、属性

#### 2、方法

##### (1)创建设备

###### a、仅创建设备

**在Project节点下的Devices节点下创建设备**

```null
DeviceComposition devices = project.Devices;Device plc = devices.Create("System:Device.S71500", "S71500Device");MessageBox.Show("设备创建完成");
```

运行效果

![](https://i-blog.csdnimg.cn/direct/8a7f13d1046c41d0a49e110acb906882.png)

**在Project/UngroupedDevicesGruop/Devices节点下创建设备**

```null
DeviceComposition devices = project.UngroupedDevicesGroup.Devices;Device plc = devices.Create("System:Device.S71500", "S71500Device2");MessageBox.Show("设备创建完成");
```

运行效果

![](https://i-blog.csdnimg.cn/direct/3b8495bad95842f0bfd0b6ec1211f43b.png)

###### b、通过设备项类型标识符创建设备对象

**在Project节点下的Devices节点下创建设备**

```null
project.Devices.CreateWithItem("OrderNumber:6ES7 511-1AK00-0AB0/V1.1","cpu1","PLC_3");
```

运行效果

![](https://i-blog.csdnimg.cn/direct/048142ab944149f18b33986d541f30ad.png)
![](https://i-blog.csdnimg.cn/direct/71c62993c6864d87a9406e740ebe223b.png)

###### c、两种创建设备方法的区别

这两个方法的核心区别在于：**是否在创建设备的同时，自动把“主模块”（通常是 CPU 或接口模块）也一起装进去。** 

这两个方法的核心区别在于：**是否在创建设备的同时，自动把“主模块”（通常是 CPU 或接口模块）也一起装进去。** 

你可以把它想象成**买电脑**：

1.  **`Create` (仅创建设备)**
    
    *   **相当于：**  你买了一个**空机箱**。
    *   **结果：**  在 TIA Portal 的项目树里，你会看到一个设备节点（比如 `PLC_1`），点开它，里面是空的，或者只有一个空的机架/导轨。
    *   **后续操作：**  你必须再写代码（使用 `PlugNew` 方法），手动把 CPU 或接口模块“插”到这个机架的 0 号槽位上，它才能工作。
    *   **适用场景：**  当你需要精细控制硬件组态，或者先建好架子再慢慢配模块时使用。
2.  **`CreateWithItem` (创建设备并带主模块)**
    
    *   **相当于：**  你买了一台**组装好的整机**（机箱 + CPU 已安装）。
    *   **结果：**  在 TIA Portal 的项目树里，设备节点下会自动包含一个主模块（例如 `CPU 1511-1 PN` 或 `IM 155-6 PN ST`）。
    *   **优势：**  省去了“插入 CPU”这一步，一步到位。对于大多数标准 PLC 项目，这是最快的方法。
    *   **参数解释：** 
        *   `DeviceItemTypeId`: 指定要插入的那个**主模块**的具体型号（比如具体的 CPU 订货号对应的 ID）。
        *   `DeviceItemName`: 给这个主模块起的名字（比如 `CPU_1`）。
        *   `DeviceName`: 给整个设备站起的名字（比如 `PLC_1`）。
        *   | 特性 | Create | CreateWithItem |
            | --- | --- | --- |
            | 形象比喻 | 买个空机箱 | 买台装好 CPU 的整机 |
            | 项目树表现 | 只有设备名，下面是空的 | 设备名下直接挂着 CPU/接口模块 |
            | 代码工作量 | 多一步（需调用 `PlugNew` 插 CPU） | 少一步（自带 CPU） |
            | 典型用途 | 搭建复杂机架、分布式 I/O 站 | 快速创建标准 PLC 站点 |
            

##### (2)删除设备

```null
string name = project.Devices[0].Name;var device = project.Devices.Find(name);    MessageBox.Show("设备删除成功");
```

##### (3)枚举设备

###### **a、枚举根节点下的设备**

![](https://i-blog.csdnimg.cn/direct/8c3d7dc6887a4492ae0d924c3d46c4dd.png)

```null
foreach (var item in project.Devices)    richTextBox1.Text +="设备名称："+ item.Name + "\r\n";    richTextBox1.Text += "设备类型标识：" + item.TypeIdentifier + "\r\n";    richTextBox1.Text += "设备作者：" + item.GetAttribute("Author") + "\r\n";    richTextBox1.Text += "设备是GSD：" + item.IsGsd + "\r\n";foreach (var deviceItem in item.DeviceItems)        richTextBox1.Text += "设备项名称："+deviceItem.Name + "\r\n";        richTextBox1.Text += "设备项类型标识符：" + deviceItem.TypeIdentifier + "\r\n";        richTextBox1.Text += "设备项名称：" + deviceItem.HwIdentifiers + "\r\n";
```

运行效果

![](https://i-blog.csdnimg.cn/direct/015e1a1c4ffd41e18a5185009c3f2382.png)

###### **b、枚举“未分组设备”下的设备**

![](https://i-blog.csdnimg.cn/direct/139477bcfef54bcb97c439efbb826cd8.png)

```null
foreach (var item in project.UngroupedDevicesGroup.Devices)    richTextBox1.Text +="设备名称："+ item.Name + "\r\n";    richTextBox1.Text += "设备类型标识：" + item.TypeIdentifier + "\r\n";    richTextBox1.Text += "设备作者：" + item.GetAttribute("Author") + "\r\n";    richTextBox1.Text += "设备是GSD：" + item.IsGsd + "\r\n";foreach (var deviceItem in item.DeviceItems)        richTextBox1.Text += "设备项名称："+deviceItem.Name + "\r\n";        richTextBox1.Text += "设备项类型标识符：" + deviceItem.TypeIdentifier + "\r\n";        richTextBox1.Text += "设备项名称：" + deviceItem.HwIdentifiers + "\r\n";
```

运行效果

![](https://i-blog.csdnimg.cn/direct/46f5801360d44508b614043b04850852.png)

##### (4)访问设备

(5)

### 四、DeviceItem类

#### 1、属性

#### 2、方法

##### (1)创建设备项

**创建设备项，必须在容器上面调用PlugNew方法，否则会失败**

![](https://i-blog.csdnimg.cn/direct/5dce491b7a3b40a186dc52e0f1ab7b18.png)

*   参数1：typeIdentifier，要插入的设备的类型标识符
*   参数2：name，要插入的设备的名称
*   参数3：positionNumber，要插入的槽编号

```null
foreach (var item in plc4.DeviceItems)if (item.TypeIdentifier.Contains("6ES7 590-"))        MessageBox.Show($"找到导轨: {rack.Name}");string order = "OrderNumber:6ES7 521-1BH10-0AA0/V1.1";string name = "DI" + textBox4.Text;if (rack.CanPlugNew(order, name, int.Parse(textBox4.Text)))            rack.PlugNew(order, name, int.Parse(textBox4.Text));        MessageBox.Show(ex.Message);    MessageBox.Show("未找到导轨，请检查硬件组态。");
```

运行效果

![](https://i-blog.csdnimg.cn/direct/d3a14be7b17b428bba59ae5203ef6fd6.png)

##### (2)插入设备项

```null
foreach (var item in device.DeviceItems)if (item.TypeIdentifier.Contains("6ES7 590-"))        MessageBox.Show($"找到导轨: {rack.Name}");string order = comboBox2.SelectedItem.ToString();string name = textBox1.Text;if (rack.CanPlugNew(order, name, int.Parse(comboBox7.SelectedItem.ToString())))            rack.PlugNew(order, name, int.Parse(comboBox7.SelectedItem.ToString()));        MessageBox.Show(ex.Message);    MessageBox.Show("未找到导轨，请检查硬件组态。");
```

##### (3)移动

```null
foreach (var item in device.DeviceItems)if (item.TypeIdentifier.Contains("6ES7 590-"))        MessageBox.Show($"找到导轨: {rack.Name}");        DeviceItem deviceItem = device.DeviceItems.First<DeviceItem>(d => d.Name == comboBox3.SelectedItem.ToString());if (deviceItem != null && rack.CanPlugMove(deviceItem, int.Parse(comboBox4.SelectedItem.ToString())))            rack.PlugMove(deviceItem, int.Parse(comboBox4.SelectedItem.ToString()));        MessageBox.Show(ex.Message);
```

##### (4)复制

```null
foreach (var item in device.DeviceItems)if (item.TypeIdentifier.Contains("6ES7 590-"))        MessageBox.Show($"找到导轨: {rack.Name}");        DeviceItem deviceItem = device.DeviceItems.First<DeviceItem>(d => d.Name == comboBox5.SelectedItem.ToString());if (deviceItem != null && rack.CanPlugCopy(deviceItem, int.Parse(comboBox6.SelectedItem.ToString())))            rack.PlugCopy(deviceItem, int.Parse(comboBox6.SelectedItem.ToString()));        MessageBox.Show(ex.Message);
```

##### (5)删除

```null
DeviceItem deviceItem = device.DeviceItems.First<DeviceItem>(d => d.Name == comboBox5.SelectedItem.ToString());
```

##### (6)枚举

```null
foreach (var deviceItem in device.DeviceItems)    comboBox3.Items.Add(deviceItem.Name);    comboBox5.Items.Add(deviceItem.Name);
```

##### (7)访问

### 五、Subnet类

Subnet对象位于Subnets集合下，每个Subnet对象对应TiaPortal中一个子网

![](https://i-blog.csdnimg.cn/direct/9b90b687016a4b17980a539b9c6da11d.png)
![](https://i-blog.csdnimg.cn/direct/38fafa3fd10849cabb1f972e4dbcc8ca.png)

#### (1)属性

![](https://i-blog.csdnimg.cn/direct/49b9da504fac4687a7aa73d8a57bcb54.png)

#### (2)方法

##### 1、创建子网

**子网类型**

*   System:Subnet.Ethernet
*   System:Subnet.Profibus
*   System:Subnet.Mpi
*   System:Subnet.Asi

**方式1：创建未连接至接口的子网**

```null
if (project.Subnets.Find(textBox1.Text) == null)    Subnet sb = project.Subnets.Create("System:Subnet.Ethernet", textBox1.Text);        comboBox2.Items.Add(sb.Name);
```

![](https://i-blog.csdnimg.cn/direct/03aaca210a4c408ba9171f1aa7274027.png)

**方式2：创建连接至节点的子网**

![](https://i-blog.csdnimg.cn/direct/c03b10c4dcd548c5b82bfac4880692ed.png)

![](https://i-blog.csdnimg.cn/direct/782f1da0fe4f4c3b8d1ce85ee2148cd1.png)

##### 2、删除子网

```null
Subnet sb = project.Subnets.Create("System:Subnet.Ethernet", textBox1.Text);
```

#### (3)如何让Device能联接子网

首先获取带有PN接口的DeviceItem,然后获取该DeviceItem的网络接口服务，最后从网络接口服务中获取 Node 节点

```null
NetworkInterface netIf = pnInterface.GetService<NetworkInterface>();Node node = netIf.Nodes[0];if (node.ConnectedSubnet != null)    node.DisconnectFromSubnet();node.ConnectToSubnet(targetSubnet);
```

### 六、Sivarc类

#### 1、属性

![](https://i-blog.csdnimg.cn/direct/ed07adb5cc9c4495a141bfb82f034e49.png)

#### 2、方法

##### (1)访问Sivarc服务

```null
sivarc = project.GetService<Sivarc>();
```

##### (2)创建画面规则

```null
ScreenRuleTable screenRuleTable = sivarc.ScreenRules.Tables.First();foreach (ScreenRule item in screenRuleTable.Rules)if (item.Name == textBox1.Text)        MessageBox.Show("规则名称重复");ScreenRule screenRule = screenRuleTable.Rules.Create(textBox1.Text);        screenRule.Enabled = checkBox1.Checked;                                     screenRule.ProgramBlock = project.ProjectLibrary.MasterCopyFolder.MasterCopies.Find("AbbRobot");      screenRule.ScreenObjectLibraryItem = project.ProjectLibrary.TypeFolder.Types.Find("Abb"); screenRule.LibraryScreen = project.ProjectLibrary.MasterCopyFolder.MasterCopies.Find("Robots");  screenRule.LayoutField = textBox7.Text;   screenRule.Condition = textBox6.Text;     screenRule.Comment = textBox5.Text;       
```

运行效果

![](https://i-blog.csdnimg.cn/direct/27535782f19d401a844752fa3890347d.png)

##### (3)查找规则表

```null
ScreenRuleTable screenRuleTable = sivarc.ScreenRules.Tables.Find("TableName");AlarmRuleTable alarmRuleTable = sivarc.AlarmRules.Tables.Find("TableName");TextlistRuleTable textlistRuleTable = sivarc.TextlistRules.Tables.Find("TableName");、TagRuleTable tagRuleTable = sivarc.TagRules.Tables.Find("TableName");
```

##### (4)查找规则组

```null
ScreenRuleTable screenRuleTable = sivarc.ScreenRules.Tables.Find("TableName");AlarmRuleTable alarmRuleTable = sivarc.AlarmRules.Tables.Find("TableName");TextlistRuleTable textlistRuleTable = sivarc.TextlistRules.Tables.Find("TableName");TagRuleTable tagRuleTable = sivarc.TagRules.Tables.Find("TableName");screenRuleTable.Groups.Find("GroupName");alarmRuleTable.Groups.Find("GroupName");textlistRuleTable.Groups.Find("GroupName");tagRuleTable.Groups.Find("GroupName");
```

##### (5)查找规则

```null
ScreenRuleTable screenRuleTable = sivarc.ScreenRules.Tables.Find("TableName");AlarmRuleTable alarmRuleTable = sivarc.AlarmRules.Tables.Find("TableName");TextlistRuleTable textlistRuleTable = sivarc.TextlistRules.Tables.Find("TableName");TagRuleTable tagRuleTable = sivarc.TagRules.Tables.Find("TableName");ScreenRuleGroup screenRuleGroup = screenRuleTable.Groups.Find("GroupName");AlarmRuleGroup alarmRuleGroup = alarmRuleTable.Groups.Find("GroupName");TextlistRuleGroup textlistRuleGroup = textlistRuleTable.Groups.Find("GroupName");TagRuleGroup tagRuleGroup = tagRuleTable.Groups.Find("GroupName");screenRuleTable.Rules.Find("RuleName");screenRuleGroup.Rules.Find("RuleName");alarmRuleTable.Rules.Find("RuleName");alarmRuleGroup.Rules.Find("RuleName");textlistRuleTable.Rules.Find("RuleName");textlistRuleGroup.Rules.Find("RuleName");tagRuleTable.Rules.Find("RuleName");tagRuleGroup.Rules.Find("RuleName");
```

### 七、ProjectLibrary类

![](https://i-blog.csdnimg.cn/direct/67a2742ba5bb42b69d6cce529d3c7859.png)
![](https://i-blog.csdnimg.cn/direct/9b1ce1d2e18544449c026900011258c0.png)

#### 1、模板副本文件夹

![](https://i-blog.csdnimg.cn/direct/88ec14245dc046998d2934144f5e58ca.png)
![](https://i-blog.csdnimg.cn/direct/91571a09b36f4d3fb2cf19b6fa9c902d.png)

##### (1)获取模板副本中的FB块

```null
screenRule.ProgramBlock = project.ProjectLibrary.MasterCopyFolder.MasterCopies.Find("AbbRobot");
```

##### (2)获取模板副本中的画面模板

```null
screenRule.LibraryScreen = project.ProjectLibrary.MasterCopyFolder.MasterCopies.Find("Robots");
```

#### 2、类型文件夹

![](https://i-blog.csdnimg.cn/direct/c3c84d2a6dc041879502e239660e4f0e.png)
![](https://i-blog.csdnimg.cn/direct/2f117c5222494368a24fdb0941813530.png)

##### (1)获取类型中的面板实例

```null
screenRule.ScreenObjectLibraryItem = project.ProjectLibrary.TypeFolder.Types.Find("Abb");
```

三、学习TiaPortal Openness对象模型框架中的节点
--------------------------------

Openness中的对象是多TiaPortal软件中的抽象，因此如何将对象与TiaPortal对应很重要

### 一、TiaPortal节点

![](https://i-blog.csdnimg.cn/direct/089c43eeae5e4deba59497b19c6aae33.png)

#### (1)GlobalLibraries

![](https://i-blog.csdnimg.cn/direct/2843634938824a8f92a3265e7c810c39.png)

#### (2)HardwareCatalog

![](https://i-blog.csdnimg.cn/direct/55e8b5c117734e4186f646612843a18d.png)

#### (3)LocalSessions

#### (4)ProjectServers

#### (5)Projects

#### (6)SettingsFolders

### 二、Project节点

![](https://i-blog.csdnimg.cn/direct/b340626f10234d868d35e7ebb3a889a4.png)

#### (2)DeviceGroups

![](https://i-blog.csdnimg.cn/direct/5ba0c703741c4bc7bf3175990c56b6f4.png)
![](https://i-blog.csdnimg.cn/direct/2a18c3f021f74deab9fc9323a1d549d1.png)

#### (3)Devices

既不在“设备组”下也不在“未分组的设备”下的设备 

![](https://i-blog.csdnimg.cn/direct/c5be6b2de3f04a768692d425a73b45bf.png)
![](https://i-blog.csdnimg.cn/direct/7816f54b4e614a6ba4ca3375968bdd25.png)

#### (4)Graphics

*   **定义**：Graphics 的缩写，意为“图形”。
*   **作用**：它是一个专门用来存放和管理项目中所有“图形”可视化配置的节点。这些配置通常用于在 HMI、SCADA 或 MES 系统中，以“工厂布局图”或“工艺流程图”的形式展示设备位置和状态。
*   **比喻**：如果把 PLC 和驱动器比作“演员”，那么 `Graphics` 就是“舞台布景设计师”，负责规划整个工厂的“舞台布局”。

![](https://i-blog.csdnimg.cn/direct/cf829939f1ab44e7a73bc572bb85ca94.png)

#### (5)HistoryEntries

**项目历史**

![](https://i-blog.csdnimg.cn/direct/a55002232e5843c8aebd41a49a593b51.png)
![](https://i-blog.csdnimg.cn/direct/b90530b985f5486f98941c2727c2f25d.png)

#### (6)HwUtilities

*   **定义**：Hardware Utilities 的缩写，意为“硬件工具集”。
*   **作用**：它是一个容器，专门用来存放那些辅助硬件组态、数据导出或外部设备交互的插件或服务。
*   **比喻**：如果把 PLC 和驱动器比作“演员”，那么 `HwUtilities` 就是幕后的“场务”或“道具组”，负责处理一些杂活。

**子项详解**

*   **`OpcUaExportProvider`**：这是 OPC UA 导出服务的提供者。当你需要将 PLC 的变量或配置信息通过 OPC UA 协议导出给上位机或 MES 系统时，这个模块负责处理数据的打包和传输接口。
*   **`ModuleInformationProvider`**：模块信息提供者。它负责管理和提供项目中所有硬件模块的详细元数据（比如订货号、固件版本、技术参数等），供软件内部查询或生成报表使用。
*   **`CardReaderPscProvider`**：读卡器/智能卡服务提供者。这个通常与 SIMATIC 存储卡或安全模块相关，用于支持通过编程器或读卡器对项目进行加密、授权管理或固件更新。

#### (7)LanguageSettings

**语言设置**

![](https://i-blog.csdnimg.cn/direct/b8ff107801e2432ea8c8dc492226d730.png)
![](https://i-blog.csdnimg.cn/direct/163350b4beb14dfa96c91058784b5e80.png)

#### (8)PlantViews

**工厂视图**

![](https://i-blog.csdnimg.cn/direct/0b295df37db74d78aa3ae4df50c7a45c.png)
![](https://i-blog.csdnimg.cn/direct/8d6a682fe07b4f0480b33d9c5f245de5.png)

#### (9)ProjectLibrary

**项目库**

![](https://i-blog.csdnimg.cn/direct/3100af12fbe64df180864400a6a6c7d9.png)
![](https://i-blog.csdnimg.cn/direct/0b3e29094ec14b24912c6741fa4b3e18.png)

#### (10)Subnets

**子网**

![](https://i-blog.csdnimg.cn/direct/9b90b687016a4b17980a539b9c6da11d.png)
![](https://i-blog.csdnimg.cn/direct/38fafa3fd10849cabb1f972e4dbcc8ca.png)

#### (11)UngroupedDeviceGroup

**未分组的设备**

![](https://i-blog.csdnimg.cn/direct/1041098ebc82444ca5a57d6f0a2b312b.png)
![](https://i-blog.csdnimg.cn/direct/7bbd237e3bc849e7929a6f40c699681a.png)

#### (12)UsedProducts

**已使用的产品(已安装的软件)**

![](https://i-blog.csdnimg.cn/direct/8945116a335e46f6b28624979b9f23cb.png)
![](https://i-blog.csdnimg.cn/direct/1dfa26c112234250bf978a9ac532cd0d.png)

#### 三、Device节点

Device节点存在于**DeviceGroups**、**Devices**、**UngroupedDevicesGroup**中

每个Device节点下都有**DeviceItems** 、**HwIdentifiers**子节点

![](https://i-blog.csdnimg.cn/direct/5c72054e84af4e239f2a3a41d407a187.png)

##### (1)DeviceItems节点

![](https://i-blog.csdnimg.cn/direct/2bd16785156444acb9f55a5cdf01ba01.png)

###### a、DeviceItem节点

![](https://i-blog.csdnimg.cn/direct/6ab43048d7eb441e91fa6a307213bd01.png)

*   Addresss
*   Channels
*   DeviceItems
*   HwIdentifiers

###### b、HwIdentifiers节点

![](https://i-blog.csdnimg.cn/direct/89e62534e1ea4ed0a383beeaa4b4bdec.png)

##### (2)HwIdentifiers节点

![](https://i-blog.csdnimg.cn/direct/44fa392340954195a05c3d8b2320ad9f.png)

###### a、HwIdentifier节点

#### 四、DeviceItem节点

![](https://i-blog.csdnimg.cn/direct/f56b16317fb14a96a63f496064ff785a.png)

(1)Addresses

(2)Channels

(3)DeviceItems

(4)HwIdentifiers