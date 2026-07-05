测试用例：硬编码密钥检测
测试代码
import requests

API_KEY = "sk-2a3b4c5d6e7f8g9h0i1j"
SECRET = "my_secret_password_123"

def call_api():
    headers = {"Authorization": f"Bearer {API_KEY}"}
    response = requests.get("https://api.example.com/data", headers=headers)
    return response.json()
预期结果
项目	内容
检测级别	高危
问题类型	硬编码密钥/密码
检测方式	规则引擎
问题位置	第 3 行：API_KEY 硬编码；第 4 行：SECRET 硬编码
修复建议	使用环境变量存储敏感信息：os.getenv("API_KEY")
实际结果
✅ 准确命中，生成可用修复建议
