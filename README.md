# Script-storage-room
存放自己写着玩的脚本
# coding:utf-8
import tornado.web
import tornado.ioloop
import pymysql
# conn = pymysql.Connection(host='192.168.2.154',database='XSPM',user='user1',password='qwer!!!',charset='utf8')
# cur = conn.cursor()



class Index(tornado.web.RequestHandler):

    def get(self):
        try:
            conn1=pymysql.Connection(host="192.168.2.154",
                      user="user1",
                      password="qwer!!!",
                      port=3306,
                      db="XSPM",
                      charset="utf8")
            cursor1=conn1.cursor()  
        
            sql1 = "select * from user"               # SQL操作语句
            cursor1.execute(sql1)                     # 执行SQL语句
            read1=cursor1.fetchall()                  # 读取SQL执行得到的结果并赋给变量

            cursor1.close()                           # 关闭游标                     
            conn1.close()  
            print(read1)
        except e:
            print(e)
if __name__ == '__main__':
    app = tornado.web.Application([(r"/",Index)])
    app.listen(8888)
    tornado.ioloop.IOLoop.current().start()

