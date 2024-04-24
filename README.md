# IDEA-plugin-quickstart

开发 IntelliJ IDEA 插件可以是一个很有趣的项目，因为它允许你扩展 IDE 的功能以适应你的开发需要。以下是创建一个简单的 IntelliJ IDEA 插件的步骤，以及一个具体的示例，即创建一个简单的“Hello World”插件。

### 开发环境设置

1. **安装 IntelliJ IDEA**：首先，你需要有 IntelliJ IDEA。可以选择 Community 版本，因为它是免费的。

2. **安装 JDK**：你需要安装 JDK（Java 开发工具包）。推荐使用和 IDEA 相同版本的 JDK。

3. **配置开发环境**：在 IDEA 中，你可以通过安装“IntelliJ Platform Plugin SDK”来配置插件开发环境。可以通过 **File > Project Structure > SDKs** 来添加。

### 创建插件项目

1. **新建项目**：在 IDEA 中，选择 **File > New > Project**，然后选择 **IntelliJ Platform Plugin**。

2. **设置项目**：填写项目名称和基本配置。选择之前配置的 Plugin SDK。

3. **项目结构**：项目创建后，你会得到一些默认的文件和目录结构，包括 `src` 目录来放置源代码。

### 编写插件代码

1. **创建一个动作**：插件通常通过动作来触发。可以在 `src` 目录中创建一个新的 Java 类，继承自 `AnAction` 类。

   ```java
   import com.intellij.openapi.actionSystem.AnAction;
   import com.intellij.openapi.actionSystem.AnActionEvent;
   import com.intellij.openapi.ui.Messages;

   public class HelloWorldAction extends AnAction {
       public void actionPerformed(AnActionEvent e) {
           // 显示一个消息对话框
           Messages.showMessageDialog(e.getProject(), "Hello, World!", "Greeting", Messages.getInformationIcon());
       }
   }
   ```

2. **注册动作**：在 `resources/META-INF/plugin.xml` 文件中注册你的动作。

   ```xml
   <idea-plugin>
       <id>com.yourcompany.unique.plugin.id</id>
       <name>Sample Plugin</name>
       <vendor email="support@yourcompany.com" url="http://www.yourcompany.com">Your Company</vendor>
       <description>Simple plugin to say hello.</description>
       <actions>
           <action id="HelloWorldAction" class="com.example.HelloWorldAction" text="Say Hello" description="Says Hello.">
               <add-to-group group-id="EditorPopupMenu" anchor="last" />
           </action>
       </actions>
   </idea-plugin>
   ```

### 运行和测试插件

1. **运行插件**：通过在 IDEA 中配置一个运行/调试配置来运行你的插件。选择 **Run > Edit Configurations > Add New Configuration > Plugin**。

2. **测试功能**：启动插件后，IDEA 会启动一个新的实例。在这个实例中，你可以测试你的插件是否按预期工作。

### 打包和发布

1. **打包插件**：在 IDEA 中，使用 **Build > Prepare Plugin Module For Deployment** 来生成插件的 zip 文件。

2. **发布插件**：你可以选择将插件提交到 JetBrains Plugin Repository，让其他用户也能下载和使用。

以上就是开发一个简单的 IntelliJ IDEA 插件的步骤。你可以通过这个基本框架来创建更复杂的功能和扩展。

