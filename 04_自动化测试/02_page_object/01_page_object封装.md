

# Page Object封装

- page

    - BasePage.py

        - ```python
            from selenium.webdriver.remote.webdriver import WebDriver
            
            class BasePage(object):
                def __init__(self, driver):
                    self.driver:WebDriver = driver
            ```

        - 

    - MainPage.py

        - ```python
            from page.BasePage import BasePage
            from page.SearchPage import SearchPage
            
            class MainPage(BasePage):
                def search(self, keyword):
                    self.driver.find_element_by_name('q').send_keys(keyword)
                    self.driver.find_element_by_css_selector(".nav__search button").click()	#css选择器，找到一个类后可用空格后面加其他类型进行定位
                    return SearchPage(self.driver)
                    
            ```

        - 

    - SearchPage.py

        - ```python
            from page.BasePage import BasePage
            
            class SearchPage(BasePage):
                def follow(self, keyword):
                    self.driver.find_element_by_xpath(f'//*[contains(text(),"{keyword}")]/../../../..//*[@class="follow__control"]').click()
                    return self
            ```

        - 

    - ProfilePage.py

        - ```python
            from page.BasePage import BasePage
            from page.SelectedPage import SelectedPage
            from selenium.webdriver.support.wait import WebDriverWait
            from selenium.webdriver.support import expected_conditions as EC
            
            class ProfilePage(BasePage):
                def __init__(self, driver):
                    super().__init__(driver)
                    # super(self, driver)
                    WebDriverWait(self.driver, 30).until(EC.element_to_be_clickable((By.CSS_SELECTOR, "dingweixinxi")))		# 显示等待
                    
                def login(self):
                    print(self.driver.get_cookies())
                    self.driver.add_cookie({"name":"xxxx","value":"xxx"})
                    self.driver.add_cookie({"name":"xxxx","value":"xxx"})
                # ......
                    print(self.driver.get_cookies())
                    self.driver.refresh()
                
                def gotoSelected(self):
                    return SelectedPage(self.driver)
            ```
            
        - 

    - SelectedPage.py

        - ```python
            from page.BasePage import BasePage
            
            class SelectedPage(BasePage):
                def select(self, keyword, market):
                    self.driver.find_element_by_css_selector(".optional .search_dropdown input").send_keys(keyword)
                    self.driver.find_element_by_xpath(f"//*[@class='search_dropdown_list']//li[contains(text(), '{market}']").click()
                    # css查找元素是，父级可以不是爸爸，可以是祖父
                    
            ```

        - 

    - 

- testcase

    - BaseTestCase.py

        - ```python
            import logging
            
            class BaseTestCase(object):
                logging.basicConfig()
                _log = logging.getLogger("xueqiu")
                _log.setLevel(logging.Debug)
                
                @property
                def log(self):
                    # 将_log进行封装，防止任意篡改
                    return self._log
            ```
    
        - 
    
    - test_xueqiu.py
    
        - ```python
            from selenium import webdriver
            from selenium.webdriver import DesiredCapabilities
        from page.MainPage import MainPage
            import time
            from testcae.BaseTestCase import BaseTestCase
            from page.ProfilePage import ProfilePage
            
            class TestXueqiu(BaseTestCase):
                def setup(self):
                    # driver也应该进行封装
                    self.driver = webdriver.Remote(desired_capabilities=DesiredCapabilities.CHROME)
                    self.driver.implicitly_wait(10)
                    self.driver.get("https://xueqiu.com/")
                    self.main = MainPage(self.driver)
                
                def test_search(self):
                    self.main.search('alibaba').follow('1688')
                    # todo: add assertion
                
                def test_profile(self):
                    # cookie相关内容已封装到ProfilePage的login中
                profile = ProfilePage(self.driver)
                    profile.login()
                    selected = profile.gotoSelected()
                    selected.select("alibaba", "1688")
                    # self.driver.get("https://xueqiu.com/setting/user")
                
                def test_log(self):
                    self.log.warning("warning info")
                    self.log.debug("debug info")
                
                def teardown(self):
                    time.sleep(10)
                    self.driver.quit()
            ```
    
    - 