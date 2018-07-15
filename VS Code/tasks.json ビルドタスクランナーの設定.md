# tasks.json ビルドタスクランナーの設定

## 作り方

- タスクメニューから既定のビルドタスクの構成を選ぶ。
- オプションが表示されるので、該当するものを選ぶ。
- プロジェクトフォルダ以下に.vscode/taks.jsonファイルが作成される。

### 例：TypeScript

```json
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
        {
            "type": "typescript",
            "tsconfig": "tsconfig.json",
            "problemMatcher": [
                "$tsc"
            ],
            "group": {
                "kind": "build",
                "isDefault": true
            }
        }
    ]
}
```

## 参考

https://code.visualstudio.com/docs/editor/tasks
