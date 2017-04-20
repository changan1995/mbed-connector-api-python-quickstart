# update_addon_acc&mag
## Prevision

![out come](http://wx3.sinaimg.cn/mw690/4b7a5121gy1fet44rh5cuj21h60n8te5.jpg)

![simple illustration](http://wx2.sinaimg.cn/mw690/4b7a5121gy1fet450joj9j219e0p3tgc.jpg)

# introduction
This project is used to practice the usage of mbed OS, python, js and promote understanding of Flask-sokcet framework.
And probably will be used as one of the mbed IOT course.
So if you are interested in ARM University Course, do check the program.
# realization
## How to use
code listed here serves as the framework for localhost server through ARM Connector Service.So you should probably check the 
client (mbed OS client):
https://github.com/changan1995/mbed-os-example-client/tree/update_addon_acc%26mag
## How to wcode
this code is mainly made up of two part.
### App.py
serve as the back end of the project.
if you wish to add one resource,just create one more @socketio.on(‘post_from_front_end’)
and followed the template listed there
### Index.hbs
serve as the front end of the project.
by adding code below respectively to html part and js part.
#### Control button
`
              <button class="get-accel">GET ACCEL</button>
`
#### Display
`
             <h4>accelerometer:<span class="acc-value">unknown</span></h4>
`
#### Respond to the click of button
` _this.find('.get-accel').on('click', function() {
            socket.emit('get_accel',{
              endpointName: _this.attr('id')
            });
          });
`
#### Change the display part
` socket.on('accel', function (data) {
          console.log('accel', data);
          $('#' + data.endpointName + ' .acc-value').html(data.value);
        });
`
# Run

then you can run the cmd by
`
python path\app.py
`
and open the browser check the 
`
localhost:8080
`
