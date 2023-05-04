# Exercise 1

In this exercise, you will practice the creation of a new Pod in a namespace. Once created, you will inspect it, shell into it and run some operations inside of the container.


1. Create the namespace `ckad-prep`

`k create ns ckad-prep`

3. In the namespace `ckad-prep`, create a new Pod named `mypod` with the image `nginx:2.3.5`. Expose the port 80.

`k run mypod --image=nginx:2.3.5 --port=80 -ns ckad-prep`

5. Identify the issue with creating the container. Write down the root cause of issue in a file named `pod-error.txt`.
6. Change the image of the Pod to `nginx:1.15.12`.

`k set image pod mypod mypod=nginx:1.15.12`

8. List the Pod and ensure that the container is running.
10. Log into the container and run the `ls` command. Write down the output. Log out of the container.

` k exec mypod -it -n ckad-prep -- /bin/sh`

12. Retrieve the IP address of the Pod `mypod`.
` k get pod -o wide`

14. Run a temporary Pod in the namespace `ckad-prep` using the image `busybox`, shell into it and run a `wget` command against the `nginx` Pod using port 80.
` k run busybox --image=busybox --rm -it --restart=Never -n ckad-prep -- /bin/sh `

16. Render the logs of Pod `mypod`.
`k logs mypod`

18. Delete the Pod and the namespace.

