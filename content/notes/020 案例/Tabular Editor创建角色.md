---
created: 2022-06-19
tags: 外部工具 tabular-editor 角色
subject:
importance: 3
skilled: 3
status:
author:
url: https://www.wolai.com/muxiaoqi/6dUqRQa3Q6VBNqXnCUg4Px
cover: 
---
## 添加角色

```C#
// Store name of role in a variable for easy reference:
var in_file = ReadFile(@"C:\Users\XXXX\Desktop\RLS.tsv");

// Split the file into rows by CR and LF characters:
var tsvRows = in_file.Split(new[] {'\r','\n'},StringSplitOptions.RemoveEmptyEntries);

foreach(var row in tsvRows) 
{
    var tsvColumns = row.Split(';'); 
    var roleName = tsvColumns[0];
    var comp_key = tsvColumns[1];

// Add the new role to the model:
Model.AddRole(roleName);

// Add a row level filter (DAX expression) on table 'Company' for the new role:
Model.Tables["Company"].RowLevelSecurity[roleName] = "[Company KEY] = \""+comp_key+"\"";

// Add permission to the role to Read, otherwise PBI_Desktop hangs trying to load
Model.Roles[roleName].ModelPermission = ModelPermission.Read;
}
```

## 修改角色

```C#
Model.Roles["ab"].Name = "abc";
```