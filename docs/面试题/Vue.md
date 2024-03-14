## package.json文件中的dependencies和devDependencies 的区别
1、在 npm 的 package.json 文件中，dependencies 和 devDependencies 是两个不同的字段，用于定义项目的依赖项。  
2、dependencies：这个字段用于列出项目在运行时所依赖的包。这些包通常是项目的核心依赖，是项目正常运行所必需的。当你通过 npm install 安装项目时，dependencies 中列出的包将被自动安装。  
3、devDependencies：这个字段用于列出项目开发过程中所需要的开发工具和测试库等依赖项。这些包通常不会在项目的生产环境中被使用，只在开发、构建或测试过程中需要。当你通过 npm install 安装项目时，devDependencies 中列出的包默认情况下不会被安装，除非你使用了 --dev 或 -D 标志。  
4、当你在生产环境中使用 npm install --production 命令安装项目时，devDependencies 中的包将不会被安装。  

