import unittest
from time import sleep
from shareclass import Share
#只打开一次浏览器要把setUp(self)和tearDown(self)改为setUpClass(self)和tearDownClass(self)
#在def setUpClass(self):和def setUpClass(self):前面加上@classmethod
class RUN(unittest.TestCase):
    @classmethod
    def setUpClass(self):
        Share.wbdriver(self)
        Share(self.driver).login("test002", "test0948")
        sleep(2)
    def test(self):
        Share.affirm(self)#断言单独一个test
        print("1")
        sleep(2)
    def test_2(self):
        """运价代码新增、修改、删除"""
        Share.YJGL_yjdm(self)
    def test_3(self):
        self.driver.find_element_by_xpath("//h2[contains(text(),'运单管理')]").click()
        self.driver.implicitly_wait(10)
        self.driver.find_element_by_xpath("//a[contains(text(),'运单统计')]").click()
        self.driver.implicitly_wait(10)
        print("3")
        sleep(2)
    @classmethod
    def tearDownClass(self):
        sleep(1)
        self.driver.quit()
if __name__ == '__main__':
    unittest.main()
