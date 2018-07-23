# Gitコミットメッセージ編集の場合にスペルチェックを有効にする

### .vimrc

```clike
autocmd FileType gitcommit setlocal spell
```

## 参考

- https://vi.stackexchange.com/questions/6950/how-to-enable-spell-check-for-certain-file-types
- http://vim.wikia.com/wiki/Always_start_on_first_line_of_git_commit_message
