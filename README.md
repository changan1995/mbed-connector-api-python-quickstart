# update_addon_acc&mag
##prevision

![out come](http://wx3.sinaimg.cn/mw690/4b7a5121gy1fet44rh5cuj21h60n8te5.jpg)

![simple illustration](http://wx2.sinaimg.cn/mw690/4b7a5121gy1fet450joj9j219e0p3tgc.jpg)

#introduction
This project is used to practice the usage of mbed OS, python, js and promote understanding of Flask-sokcet framework.
And probably will be used as one of the mbed IOT course.
So if you are interested in ARM University Course, do check the program.
#realization
##1.how to use
code listed here serves as the framework for localhost server through ARM Connector Service.So you should probably check the 
client (mbed OS client):
https://github.com/changan1995/mbed-os-example-client/tree/update_addon_acc%26mag
##2.how to wcode
this code is mainly made up of two part.
###app.py
serve as the back end of the project.
if you wish to add one resource,just create one more @socketio.on(‘post_from_front_end’)
and followed the template listed there
###index.hbs
serve as the front end of the project.
by adding code below respectively to html part and js part.
#### control button
`
              <button class="get-accel">GET ACCEL</button>
`
#### display
`
             <h4>accelerometer:<span class="acc-value">unknown</span></h4>
`
#### respond to the click of button
` _this.find('.get-accel').on('click', function() {
            socket.emit('get_accel',{
              endpointName: _this.attr('id')
            });
          });
`
#### change the display part
` socket.on('accel', function (data) {
          console.log('accel', data);
          $('#' + data.endpointName + ' .acc-value').html(data.value);
        });
`
then you can 
``
