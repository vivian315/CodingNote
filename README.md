记录编程过程中遇到的问题以及解决办法

## Python
1. Mac上pygame图片不显示问题的解决:[点这里](https://github.com/vivian315/CodingNote/blob/gh-pages/pygameForMac)

## Selenium
1. 关闭Chrome浏览器开发模式
        options = webdriver.ChromeOptions()
        # 在用Selenium做自动化测试的时候，默认ChromeDriver是会提示“Chrom正受到自动测试软件控制”的，关闭此提示
        options.add_experimental_option('excludeSwitches', ['enable-automation'])
        browser = webdriver.Chrome(options=options)
        
        # 用Selenium打开Chrome时window.navigator.webdriver 属性为true，而正常打开的浏览器该属性为 undefined
        # 在执行get方法前前将 webdriver 设置成 undefined"""
        browser.execute_cdp_cmd("Page.addScriptToEvaluateOnNewDocument", {
            "source": """Object.defineProperty(navigator, 'webdriver', {get: () => undefined})""",
        })
        
2、关闭Chrome的保存密码提示
        prefs = {}
        prefs["credentials_enable_service"] = False
        prefs["profile.password_manager_enabled"] = False
        options.add_experimental_option("prefs", prefs)

