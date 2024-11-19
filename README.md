## formatter

```json
{
  "[elixir]": {
    "editor.defaultFormatter": "JakeBecker.elixir-ls"
  },
}
```

해당 설정으로 elixir의 포맷터를 설정할수있다.

## 후행 문자열 자동삭제

### 어떤문제?

```elixir
test "text 일치 확인" do
  assert result == """
                  c1    | c2     | c4     
                  ------+--------+--------
                  r1 c1 | r1 c2  | r1+++c4
                  r2 c1 | r2 c2  | r2 c4  
                  r3 c1 | r3 c2  | r3 c4  
                  r4 c1 | r4++c2 | r4 c4  
                  """
end
```

<img width="460" alt="image" src="https://github.com/user-attachments/assets/613b32fd-711c-4757-ac28-3c47234286ec">

vscode의 `editor.formatOnSave = true`인 경우에 후행 공백 문자열이 자동으로 삭제된다.

테스트할때 해당 후행 공백문자열은 의도한것이지만 문제가 생긴다.

### 해결방법

`.vscode/settings.json`

```json
{
  "files.trimTrailingWhitespaceInRegexAndStrings": false
}
```

해당 설정으로 후행 공백문자를 유지할 수 있다.
