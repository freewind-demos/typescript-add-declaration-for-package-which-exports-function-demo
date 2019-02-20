TypeScript Add Declaration for Package Which Exports "function" Demo
====================================================================

注意有三种做法：

1. 随便定义一个`.ts`文件（不是`.d.ts`），比如`strip.declaration.ts`，然后在需要用到的文件中，`import `./strip.declaration.ts`
  - 优点：不需要任何配置，兼容性好
  - 缺点：每个用到的文件都需要import一下，繁琐

2. 随便定义一个`.d.ts`文件，比如`strip.d.ts`，然后在`tsconfig.json`->`files`中把它加进去即可，直接使用无需import
  - 优点：配置简单，无需import
  - 缺点：有的工具（比如`ts-node`）似乎不支持这种做法

3. 在`tsconfig.json` -> `typeRoots`中加上某个目录，在该目录下，有子目录对应于相应的package（如`strip`），内有`index.d.ts`
  - 优点：无需import，在多种工具下（`tsc`，`ts-node`）下都工作良好
  - 缺点：配置略麻烦
  - 注意：如果在`tsconfig.json`中还使用了`types`来指明想要默认导入的package，那么需要把`strip`也加进去。因为在这种情况下，它没有被显示import，不会被import。

本demo使用的是第3种方式，最通用的方式。

```
npm install
npm run demo
```


