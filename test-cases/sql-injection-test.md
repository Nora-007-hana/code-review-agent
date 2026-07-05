# 测试用例：SQL 注入检测

## 测试代码

```python
import sqlite3

def get_user(user_id):
    conn = sqlite3.connect('users.db')
    cursor = conn.cursor()
    # 高危：使用字符串拼接构造 SQL
    query = "SELECT * FROM users WHERE id = " + user_id
    cursor.execute(query)
    return cursor.fetchall()

预期结果
项目	内容
检测级别	高危
问题类型	SQL 注入
检测方式	规则引擎 + LLM
问题位置	第 7 行：字符串拼接构造 SQL 查询
修复建议	使用参数化查询：cursor.execute("SELECT * FROM users WHERE id = ?", (user_id,))

实际结果
✅ 准确命中，生成可用修复建议
