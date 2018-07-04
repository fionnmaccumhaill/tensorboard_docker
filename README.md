# tensorboard_docker
A short example for starting TensorBoard in a Tensorflow Docker container

I hsve been working with TensorFlow and TensorBoard a lot lately. Since I use Docker containers as my development environment for just about everything I thought I would create this repository as a place to hold some of my files and to give a short explanation of the commands you need to use TensorBoard with Docker.

On Windows I put all of my TensorFlow projects in the C:\gitrepo directory. Obviously every project has its own directory. I start the Docker container with this command:

docker run --name tf1 -it -v c:/gitrepo:/notebooks -p 0.0.0.0:6006:6006 -p 8888:8888 tensorflow/tensorflow:latest-py3

This gives my container the name tf1 and maps port 8888 for TensorFlow so I can access Python notebooks in my browser. I also map port 6006 so I can access TensorBoard when I start that up.

The -v flag lets me map the directory containing my projects.

Once you run that command you will get a few lines at the bottom of your command Window that looks like this:

Copy/paste this URL into your browser when you connect for the first time,
    to login with a token:
        http://localhost:8888/?token=ca635d30b93547bd688b5bf6e1718c83ed81f0d98104851b
        
Copy and paste that into your browser and select the directory for the Python notebook you want to work on. Once you run your TensorFlow model you want to look at the stats in TensorBoard. This is simple to do. Just open another command window or shell and enter the following command:

docker exec -it tf1 /bin/bash

This will give you a shell into the Docker container running the TensorFlow model. You will be placed in the /notebooks directory. If you have a model in the directory /notebooks/dnneexample just cd into the dnnexample directory. I normally put my logs into the ./models directory so I can start TensorBoard by entering this command:

tensorboard --logdir ./models

This will start up TensorBoard which you can access through your browser with the URL:

http://localhost:6006

All done. 