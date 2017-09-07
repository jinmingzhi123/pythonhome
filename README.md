# pythonhome
python
#!/usr/bin/python
#coding:utf-8

import os
import glob
import unittest
from time import sleep
import HTMLTestRunner
from appium import webdriver
import time
from appium.common.exceptions import NoSuchContextException
from selenium.webdriver.common.keys import Keys
from appium.webdriver.webdriver import WebDriverWait
from appium.webdriver.common.mobileby import MobileBy
from appium.webdriver.switch_to import MobileSwitchTo
from appium.webdriver.common.touch_action import TouchAction
from selenium.webdriver.support import expected_conditions as EC



# Returns abs path relative to this file and not cwd
PATH = lambda p: os.path.abspath(
    os.path.join(os.path.dirname(__file__), p)
)
ISOTIMEFORMAT='%Y-%m-%d %X'



class AndroidWebViewTests(unittest.TestCase):

    def setUp(self):
        desired_caps = {}
        '''desired_caps['app'] = os.PATH(
                   '../../../sample-code/apps/ContactManager/ContactManager.apk'
               )'''
        desired_caps['platformName'] = 'Android'
        desired_caps['platformVersion'] = '5.1'
        desired_caps['deviceName'] = 'QLXBBBA611532268'
        desired_caps['appPackage'] = 'com.sina.book'
        desired_caps['appActivity'] = '.ui.activity.splash.SplashActivity'
        desired_caps['noSign'] = 'true'
        desired_caps['unicodeKeyboard'] = 'true'
        desired_caps['resetKeyboard'] = 'true'
        desired_caps['noReset'] = 'false'
        desired_caps['newCommandTimeout'] = '10'
        self.driver = webdriver.Remote('http://10.205.13.142:4723/wd/hub', desired_caps)
        

    def tearDown(self):
        self.driver.quit()


    def test_webview(self):
        j = 0
        for i in range(1, 101):
            sleep(3)
            print"open"
            sleep(2)
            if i < 100:
               print time.strftime(ISOTIMEFORMAT, time.localtime(time.time()))                             #起始时间
               WebDriverWait(self.driver, 10).until(EC.presence_of_element_located((MobileBy.ID, 'com.sina.book:id/rb_handpick')))
               print time.strftime(ISOTIMEFORMAT, time.localtime(time.time()))                             #结束时间
               self.driver.find_element_by_id('com.sina.book:id/rb_handpick').click()
               sleep(2)
               self.driver.find_element_by_name('玄武大帝').click()
               sleep(5)
               name = '免费试读'
               if name == '免费试读':
                   print 'user'
                   self.driver.find_element_by_name('免费试读').click()
                   sleep(2)
                   self.driver.switch_to.context('NATIVE_APP')
                   sleep(2)
                   self.driver.swipe(700, 500, 100, 500, duration=1000)
                   sleep(3)
                   self.driver.find_element_by_id('com.sina.book:id/layout_read_toolbar').click()
                   sleep(3)
                   self.driver.tap([(54, 106), ])
                   sleep(3)
                   self.driver.find_element_by_id('com.sina.book:id/textview_dialog_cancal').click()
                   sleep(3)
                   self.driver.tap([(54, 106), ])
                   sleep(3)
                   self.driver.find_element_by_name('女生').click()
                   sleep(3)
                   self.driver.swipe(700, 1000, 700, 100, duration=1000)
                   sleep(3)
                   self.driver.tap([(54, 104), ])
                   sleep(3)
                   self.driver.find_element_by_name('排行').click()
                   sleep(3)
                   self.driver.swipe(700, 1000, 700, 100, duration=1000)
                   sleep(3)
                   self.driver.tap([(54, 104), ])
                   sleep(3)
                   self.driver.find_element_by_name('书单').click()
                   sleep(3)
                   self.driver.swipe(700, 1000, 700, 100, duration=1000)
                   sleep(3)
                   self.driver.tap([(54, 104), ])
                   sleep(3)
                   self.driver.find_element_by_name('出版').click()
                   sleep(3)
                   self.driver.swipe(700, 1000, 700, 100, duration=1000)
                   sleep(3)
                   self.driver.tap([(54, 104), ])
                   sleep(3)
                   self.driver.swipe(700, 1000, 700, 100, duration=1000)
                   sleep(3)
                   self.driver.find_element_by_name('绝品武神').click()
                   sleep(3)
                   self.driver.find_element_by_name('下载').click()
                   sleep(4)
                   self.driver.swipe(700, 1000, 700, 100, duration=1000)
                   sleep(3)
                   self.driver.tap([(54, 104), ])
                   sleep(3)
                   self.driver.swipe(700, 200, 700, 1000, duration=1000)
                   sleep(3)
                   self.driver.swipe(700, 200, 700, 1000, duration=1000)
                   sleep(3)
                   self.driver.press_keycode('4')
                   sleep(2)
               else:
                   print 'close'
               i += 1
            else :
                sleep(3)
                print"close"



if __name__ == '__main__':
    suite = unittest.TestLoader().loadTestsFromTestCase(AndroidWebViewTests)
    unittest.TextTestRunner(verbosity=2).run(suite)
