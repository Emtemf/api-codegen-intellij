# API Codegen IntelliJ Plugin

IntelliJ IDEA 插件，用于从 YAML 定义自动生成 Java API 代码。

## 环境要求

- **JDK 17** (IntelliJ Platform SDK 要求)
- **IntelliJ IDEA** 2023.2 或更高版本

## 快速开始

### 1. 安装依赖

插件依赖 `api-codegen-core:1.0.0`，需要先在主项目中安装：

```bash
cd D:\idea\workSpace\api-codegen
mvn install -DskipTests -pl api-codegen-core
```

### 2. 打开插件项目

```
File > Open > 选择 D:\idea\workSpace\api-codegen-intellij-standalone\
```

### 3. 配置 SDK

```
File > Project Structure > Project Settings > Project
SDK: IntelliJ IDEA Community Edition IC-241.0 或更高版本
Language level: 17
```

### 4. 运行插件

找到 `ApiCodegenPlugin.java`，右键选择 `Run Plugin`

## 插件功能

- **侧边栏工具窗口**：图形化界面管理 YAML 文件
- **一键分析**：检测缺少的校验规则
- **自动修复**：一键添加校验规则
- **代码生成**：生成 Controller、Request、Response

## 项目结构

```
api-codegen-intellij-standalone/
├── api-codegen-intellij/
│   ├── src/main/
│   │   ├── java/com/apicgen/intellij/
│   │   │   ├── ApiCodegenPlugin.java          # 插件入口
│   │   │   ├── AnalyzeAction.java             # 分析动作
│   │   │   ├── AutoFixAction.java             # 自动修复动作
│   │   │   ├── GenerateCodeAction.java        # 代码生成动作
│   │   │   ├── RefreshAction.java             # 刷新动作
│   │   │   ├── ShowToolWindowAction.java      # 显示工具窗口动作
│   │   │   ├── ui/
│   │   │   │   └── ApiCodegenToolWindowPanel.java  # 主界面
│   │   │   ├── toolwindow/
│   │   │   │   └── ApiCodegenToolWindowFactory.java # 工具窗口工厂
│   │   │   └── service/
│   │   │       ├── ApiCodegenProjectService.java      # 服务接口
│   │   │       └── ApiCodegenProjectServiceImpl.java  # 服务实现
│   │   └── resources/
│   │       └── META-INF/plugin.xml           # 插件配置
│   ├── build.gradle                           # Gradle 构建
│   └── settings.gradle
└── README.md
```

## 构建命令

```bash
# 使用 Gradle Wrapper
./gradlew build

# 运行插件
./gradlew runIde

# 打包插件
./gradlew buildPlugin
```

## 依赖说明

插件依赖 `api-codegen-core:1.0.0` JAR（从 Maven 中央仓库或本地安装）：

```groovy
// build.gradle
dependencies {
    implementation 'com.apicgen:api-codegen-core:1.0.0'
}
```

## License

Apache-2.0
