一个将django本地存储变更为阿里云oss存储的包，适配django4.0
-------------

使用方法
\\
1. 下载django4-aliyun-oss-storage到本地
2. 将django4-aliyun-oss-storage放置于django导包目录(可在settings.py中通过sys.path添加)或项目根目录
3. 在settings.py中加入配置

# 阿里云OSS云存储相关信息
OSS_ACCESS_KEY_ID = 'LTAI..XALxS...'  # 需要在阿里云控制台生成
OSS_ACCESS_KEY_SECRET = 'JDwn08..QW1LSV8Yy...' # 需要在阿里云控制台生成
OSS_ENDPOINT = "oss-cn-chengdu.aliyuncs.com" # 在oss控制台可以查看
OSS_BUCKET_NAME = "j.....eb" 在oss控制台可以查看
OSS_SERVER_URL = f"https://{OSS_BUCKET_NAME}.{OSS_ENDPOINT}"


# 添加下面配置后 Django admin 后台上传的 ImageField, FileField 类型的字段都会被自动上传到 oss 的服务器中, 访问路径也会自动替换
# 如果注释掉的话 oss 的配置会失效, 上传文件会存储到本地, 且访问路径也会变成本地
DEFAULT_FILE_STORAGE = 'django_oss_storage.backends.OssMediaStorage'

# 一般不用执行，如果使用，需要将simpleui等使用的静态文件先上传到oss指定目录
# STATICFILES_STORAGE = 'django_oss_storage.backends.OssStaticStorage'
-------------
