# Script-storage-room
存放自己写着玩的脚本
# coding:utf-8
import tornado.web
import tornado.ioloop
import pymysql
conn = pymysql.Connection(host='192.168.2.154',database='XSPM',user='user1',password='qwer!!!',charset='utf8')
cur = conn.cursor()

class Index(tornado.web.RequestHandler):

    def get(self):
        cur.execute('select * from user')
        data = cur.fetchall()
        print(data)
        self.write('data')

if __name__ == '__main__':
    app = tornado.web.Application([(r"/",Index)])
    app.listen(8888)
    tornado.ioloop.IOLoop.current().start()
