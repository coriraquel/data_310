### My Two Images 
![image](../images/girl.jpg)
![image](../images/unnamed.jpg)

I chose the first image because it has been a pretty accurate representation of my summer and my time in Jump Start. I've spent many sleepy nights at my desk falling asleep at my computer and perking up for work the next day.
I chose the second image because Starry Night is one of my favorite paintings because I think the colors are beautiful. Even though this summer has been very stressful it has been beautiful in a lot of new ways too which has made it one of my favorites!

I had issues getting my stylized image to produce...well an image it just gave me an image line even when I put the stylzed image in print brackets. I included the result it provided for me as well as the code I ran for my image below! 

    <PIL.Image.Image image mode=RGB size=512x512 at 0x229BE1D7BB0>



    import os
    import tensorflow as tf
    # Load compressed models from tensorflow_hub
    os.environ['TFHUB_MODEL_LOAD_FORMAT'] = 'COMPRESSED'
    import IPython.display as display
    import matplotlib.pyplot as plt
    import matplotlib as mpl
    mpl.rcParams['figure.figsize'] = (12, 12)
    mpl.rcParams['axes.grid'] = False
    import numpy as np
    import PIL.Image
    import time
    import functools
    import ssl
    ssl._create_default_https_context = ssl._create_unverified_context
    def tensor_to_image(tensor):
    tensor = tensor*255
    tensor = np.array(tensor, dtype=np.uint8)
    if np.ndim(tensor)>3:
    assert tensor.shape[0] == 1
    tensor = tensor[0]
    return PIL.Image.fromarray(tensor)
    # content_path = tf.keras.utils.get_file('elie-khoury-GidYc-pS9sM-unsplash.jpg', 'https://unsplash.com/photos/GidYc-pS9sM')
    content_path = 'image/girl.jpg'
    # style_path = tf.keras.utils.get_file('europeana-pw-ap4Zp4CU-unsplash.jpg','https://unsplash.com/photos/pw-ap4Zp4CU')
    style_path = 'image/art.jpg'
    
    def load_img(path_to_img):
    max_dim = 512
    img = tf.io.read_file(path_to_img)
    img = tf.image.decode_image(img, channels=3)
    img = tf.image.convert_image_dtype(img, tf.float32)
    
    shape = tf.cast(tf.shape(img)[:-1], tf.float32)
    long_dim = max(shape)
    scale = max_dim / long_dim
    
    new_shape = tf.cast(shape * scale, tf.int32)
    
    img = tf.image.resize(img, new_shape)
    img = img[tf.newaxis, :]
    return img
    
    def imshow(image, title=None):
    if len(image.shape) > 3:
    image = tf.squeeze(image, axis=0)
    
    plt.imshow(image)
    if title:
    plt.title(title)

    content_image = load_img(content_path)
    style_image = load_img(style_path)

    plt.subplot(1, 2, 1)
    imshow(content_image, 'Content Image')

    plt.subplot(1, 2, 2)
    imshow(style_image, 'Style Image')

    import tensorflow_hub as hub
    hub_model = hub.load('https://tfhub.dev/google/magenta/arbitrary-image-stylization-v1-256/2')
    stylized_image = hub_model(tf.constant(content_image), tf.constant(style_image))[0]
    print(tensor_to_image(stylized_image))