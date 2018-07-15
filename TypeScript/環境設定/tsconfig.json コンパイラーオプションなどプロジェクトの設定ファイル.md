# tsconfig.json コンパイラーオプションなどプロジェクトの設定ファイル

## 作り方

```batch
> tsc --init
message TS6071: Successfully created a tsconfig.json file.
```

tsc --initコマンドが生成するtsconfig.jsonは内容が複雑なので、以下の簡単な内容で自分でテキストエディタで作ってもいい。

```json
{
    "compilerOptions": {
        "target": "ES5",
        "module": "commonjs",
        "sourceMap": true
    }
}
```

## 参考

http://www.typescriptlang.org/docs/handbook/tsconfig-json.html
