---
layout: page
title: About this Demo
subtitle: Browser is what you need
---

# What is a monocular depth network?

A monocular depth network is (generally) a CNN able to infer 
the depth of the scene from a single image. We use a CNN because of the
complexity of this task.
       
# Why depth is important?
We can use depth information in many applications, such as Augmented Reality (AR),
3D Reconstruction, Collision Avoidance and many others.
We can obtain these data using *active sensors*, such as LiDAR or ToF, but also with passive ones like
stereo cameras. However, many devices do not have multiple cameras or active sensors, so monocular depth estimation
is attractive since it requires just a single camera. For many of these, (near) real time performances are necessary.

# What do I need to run a monocular depth network?
In general, you may need high performance devices, like a GPU, because many state-of-the-art networks
leverage millions of parameters (eg 50 M, or even 100M). This means that they are not able to run with high FPS
on mobile or embedded devices. On the contrary, in this project we deploy a lightweight network, called **PyDNet**
that is able to run directly on mobile devices.
We both developed a mobile application (for Android and iOS devices), but it has to be installed. Instead, in this demo, you can run the network on your device just using your
browser. Indeed, using [TensorFlow JS](https://www.tensorflow.org/js) the network runs inside the client device, and not in the remote server.

<div class="text-center">
 <figure class="figure">
   <img src="{{site.baseurl}}/assets/img/pydnet.jpg" alt="PyDNet">
   <figcaption class="figure-caption text-center">PyDNet architecture</figcaption>
 </figure>
</div>

 <div class="container">
        <div class="row">
            <div class="col-xs-12">
                <div  class="text-center">
                       <a href="https://github.com/mattpoggi/pydnet" class="btn btn-dark"> Original Code</a>
<a  href="https://github.com/FilippoAleotti/mobilePydnet" class="btn btn-success">Mobile App</a>
                 <a href="https://arxiv.org/pdf/1806.11430.pdf" class="btn btn-info">Paper</a>
                </div>
            </div>
        </div>
    </div>


If you use this code or PyDNet in your projects, please cite our paper:
```
@inproceedings{pydnet18,
  title     = {Towards real-time unsupervised monocular depth estimation on CPU},
  author    = {Poggi, Matteo and
               Aleotti, Filippo and
               Tosi, Fabio and
               Mattoccia, Stefano},
  booktitle = {IEEE/JRS Conference on Intelligent Robots and Systems (IROS)},
  year = {2018}
}
```

# Why client-side inference is great?
First, the client does not need to share user data with the server because images are processed directly by the client device. In this way the privacy of the user is enhanced.

Moreover, the server can scale better, since it has less requests to solve. In a client-server web demo the server has two types of request: page request (that is, please send me the html and scripts to render the page on the browser), and inference request (please process this image and send me back the depth).
We can expect that the second type of request requires most of the effort.
Now suppose the server has 1k requests: this means that all the clients send a page and one or many inference requests to the server, and for each inference request the server has to take the image, process it and send back the outcome to the client. 
If the users grow (for instance 10k, or even more) you may have to replicate the server because it is not able to serve all the requests in a limited amount of time. Instead, if each client is able to process the images on its own
then the server may serve more clients since it has to provide just the code for the web page!

You might argue that the server is necessary to provide the web page, and you have right. If you need to run totally server-less, you can use our native mobile application! This is also great, because we have gained in terms of dependencies: we can run the app even where, for instance, a good internet connection is not available.

<div class="container">
  <div class="row">
    <div class="col-md-6 col-sm-12">
      <figure class="figure">
        <img src="{{site.baseurl}}/assets/img/client-server.png" alt="client-server">
        <figcaption class="figure-caption text-center">Client-Side approach</figcaption>
       </figure>
    </div>
    <div class="col-md-6 col-sm-12">
      <figure class="figure">
        <img src="{{site.baseurl}}/assets/img/client.png" alt="client"> 
        <figcaption class="figure-caption text-center">Server-less approach</figcaption>
      </figure>
    </div>
  </div>
</div>

# License
The weights of this network, outside of this project, can be used only for academic research. This project has demonstration purposes only.
