
# C#编码风格插件配置

为了更好地执行部门的C#编程规范，建议在使用Visual Studio Code编写C#代码时，配置Roslynator代码分析插件。


1. 在Visual Studio Code中安装Roslynator插件；
2. 有两种方式将规则应用到C#代码检查中：  
    - 在工程中配置
        1. 将csharp_style_dc.ruleset文件拷贝到工作区中；
        2. 打开需要执行代码分析工程的.csproj工程文件，在\<PropertyGroup>中增加\<CodeAnalysisRuleSet>项;
 
        示例：
        ```
        <Project Sdk="Microsoft.NET.Sdk">
          <PropertyGroup>
            <OutputType>Exe</OutputType>
            <TargetFramework>netcoreapp3.1</TargetFramework>
            <CodeAnalysisRuleSet>$(MSBuildThisFileDirectory)..\csharp_style_dc.ruleset</CodeAnalysisRuleSet>
          </PropertyGroup>
        </Project>
        ```
    - 全局配置
        1. 打开Roslynator插件的默认规则目录（默认路径为C:\Users\Administrator\AppData\Local\JosefPihrt\Roslynator\VisualStudioCode\）；
        2. 将csharp_style_dc.ruleset文件改名为roslynator.ruleset，覆盖原有默认规则文件；
3. 重启Visual Studio Code;
4. 检查生效后，在不符合检查规则处，将会提示不满足RCS规则；
>例如：[CSProjectName]csharp(RCS0001)
5. 在Visual Studio Code编写C#代码时，应按照部门约定的代码规范要求，结合C#编码规范文档及Roslynator代码检查严格执行。必须全部解决错误（红色波浪线）提示，尽量全部解决警告（黄色波浪线）提示，尽量解决信息（蓝色波浪线）提示。