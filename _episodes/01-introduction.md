---
title: "Introduction"
teaching: 10
exercises: 0
questions:
- "What are containers?"
- "What is Docker?"
- "What is it used for?"
- "What are its components?"
- "How is Docker different on OSX/Windows/Linux?"
objectives:
- "Understand what is a container and how it differs from a virtual machine."
- "Understand the purpose of Docker."
- "Understanding why docker is useful to CMS researchers."
keypoints:
- "Docker provides loosely isolated environments called containers."
- "These containers are lightweight alternatives to virtual machines."
- "You can package and run software in containers."
- "You can run many containers simultaneously on a single host machine."
---

# Containers and Images

Test test

~~~bash
docker pull sl

#if you run into a premission error, use "sudo docker run ..." as a quick fix
# to fix this for the future, see https://docs.docker.com/install/linux/linux-postinstall/
~~~
{: .source}


~~~
Using default tag: latest
latest: Pulling from library/sl
be7dd8a3f6cc: Pull complete
Digest: sha256:d20a8476d2369be2f3553382c9cce22f1aace2804cf52450b9dbacc93ae88012
Status: Downloaded newer image for sl:latest
docker.io/library/sl:latest
~~~
{: .output}

> ## Pulling Python
>
> Pull the image python:3.7-slim for Python 3.7 and then list all `python` images along with the `sl:7` image
>
> > ## Solution
> >
> > ~~~bash
> > docker pull python:3.7-slim
> > docker images --filter=reference="sl" --filter=reference="python"
> > ~~~
> > {: .source}
> >
> > ~~~
> > 3.7-slim: Pulling from library/python
42c077c10790: Pull complete
f63e77b7563a: Pull complete
dca49bd08fde: Pull complete
51a05345c44d: Pull complete
e69ebd661d90: Pull complete
Digest: sha256:f61a4c6266a902630324fc10814b1109b3f91ac86dfb25fa3fa77496e62f96f5
Status: Downloaded newer image for python:3.7-slim
docker.io/library/python:3.7-slim
> > 
> > REPOSITORY   TAG        IMAGE ID       CREATED       SIZE
> > python       3.7-slim   600bb8fe36b6   2 weeks ago   123MB
> > sl           7          33957a339e91   2 weeks ago   187MB
> > sl           latest     33957a339e91   2 weeks ago   187MB
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}


