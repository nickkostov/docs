Командите в докер:

Винаги в началото е хубаво да погледнете след като инсталирате какъвто и да е софтуеър на вашата машина, нейният ``` help ```:

``` docker -h | more ``` 

След като си създадете контейнер и той е стартирал и работи може да пробвате две команди с цел да видите статута на вашият контейнер:

``` docker ps ``` и ``` docker container ls ```


Пример:
``` docker container ls
CONTAINER ID   IMAGE          COMMAND       CREATED      STATUS      PORTS     NAMES
eea7b5d418be   ansible        "/bin/bash"   4 days ago   Up 4 days             ans
d207354362e1   9eeef9904181   "/bin/bash"   4 days ago   Up 4 days             ansible_kofa
b46001e17517   9eeef9904181   "/bin/bash"   4 days ago   Up 4 days             youthful_leakey 
```

Пример:

``` docker ps
CONTAINER ID   IMAGE          COMMAND       CREATED      STATUS      PORTS     NAMES
eea7b5d418be   ansible        "/bin/bash"   4 days ago   Up 4 days             ans
d207354362e1   9eeef9904181   "/bin/bash"   4 days ago   Up 4 days             ansible_kofa
b46001e17517   9eeef9904181   "/bin/bash"   4 days ago   Up 4 days             youthful_leakey
```

Команди с цел мениджмънт на контейнерите:

```
docker image
```

Когато използвате, обаче:

``` docker image -h | more ``` 

Ше може да видите командите които са пряко свързани с ``` docker image ```

Например 
```docker image ls
REPOSITORY                                 TAG               IMAGE ID       CREATED         SIZE
ansible                                    latest            5759301c99d1   4 days ago      559MB
registry.gitlab.com/nickkostov/docker-ci   latest            5759301c99d1   4 days ago      559MB
php                                        7                 f45b6ac10d34   5 days ago      420MB
<none>                                     <none>            9eeef9904181   5 days ago      559MB
gitlab/gitlab-runner-helper                x86_64-775dd39d   8a1cb3c72281   5 days ago      67.3MB
ubuntu                                     20.04             f63181f19b2f   5 days ago      72.9MB
node                                       latest            1db64f55f800   6 days ago      936MB
docker                                     stable            b0757c55a1fd   7 weeks ago     220MB
alpine                                     3.7               6d1ef012b567   23 months ago   4.21MB
golang                                     1.10              6fd1f7edb6ab   24 months ago   760MB
```
В примера горе виджате, че имам доста имиджи свалени на локалната ми машина.

Ако нямате никакви имиджи и искате да си свалите даден имидж може да направите следното:

```docker image pull nginx```

Ще получите следният изход на вашият екран:

```docker image pull nginx
Using default tag: latest
latest: Pulling from library/nginx
a076a628af6f: Already exists
0732ab25fa22: Extracting [>                                                  ]  294.9kB/26.5MB
d7f36f6fe38f: Download complete
f72584a26f32: Download complete
7125e4df9063: Download complete
```

И сега ще се сдобиете с ваш имидж на софтуеъра ```nginx``` и ще може да създадете контейнер който да има ```nginx``` и да го използвате с цел да побликувате например вашият уеб сайт.

Когато го свалите ще може да видите, че вече притежавате изображението с мениджмънт командата ```docker image ls``` или ```docker images```:

```docker image ls
REPOSITORY                                 TAG               IMAGE ID       CREATED         SIZE
ansible                                    latest            5759301c99d1   4 days ago      559MB
registry.gitlab.com/nickkostov/docker-ci   latest            5759301c99d1   4 days ago      559MB
php                                        7                 f45b6ac10d34   5 days ago      420MB
<none>                                     <none>            9eeef9904181   5 days ago      559MB
gitlab/gitlab-runner-helper                x86_64-775dd39d   8a1cb3c72281   5 days ago      67.3MB
ubuntu                                     20.04             f63181f19b2f   5 days ago      72.9MB
node                                       latest            1db64f55f800   6 days ago      936MB
nginx                                      latest            f6d0b4767a6c   2 weeks ago     133MB
docker                                     stable            b0757c55a1fd   7 weeks ago     220MB
alpine                                     3.7               6d1ef012b567   23 months ago   4.21MB
golang                                     1.10              6fd1f7edb6ab   24 months ago   760MB
```
```docker images
REPOSITORY                                 TAG               IMAGE ID       CREATED         SIZE
registry.gitlab.com/nickkostov/docker-ci   latest            5759301c99d1   4 days ago      559MB
ansible                                    latest            5759301c99d1   4 days ago      559MB
php                                        7                 f45b6ac10d34   5 days ago      420MB
<none>                                     <none>            9eeef9904181   5 days ago      559MB
gitlab/gitlab-runner-helper                x86_64-775dd39d   8a1cb3c72281   5 days ago      67.3MB
ubuntu                                     20.04             f63181f19b2f   5 days ago      72.9MB
node                                       latest            1db64f55f800   6 days ago      936MB
nginx                                      latest            f6d0b4767a6c   2 weeks ago     133MB
docker                                     stable            b0757c55a1fd   7 weeks ago     220MB
alpine                                     3.7               6d1ef012b567   23 months ago   4.21MB
golang                                     1.10              6fd1f7edb6ab   24 months ago   760MB
```
Или за по кратко след като сте видяли този изход може спокойно да използвате:

```docker image ls nginx
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
nginx        latest    f6d0b4767a6c   2 weeks ago   133MB
```

След като свалите имиджа може да направите инспекция на имиджа:
Накратко това е един гигантски изход във JSON формат с цел да ви покаже основите на даденото изображение и как работи:

```docker inspect nginx:latest
[
    {
        "Id": "sha256:f6d0b4767a6c466c178bf718f99bea0d3742b26679081e52dbf8e0c7c4c42d74",
        "RepoTags": [
            "nginx:latest"
        ],
        "RepoDigests": [
            "nginx@sha256:10b8cc432d56da8b61b070f4c7d2543a9ed17c2b23010b43af434fd40e2ca4aa"
        ],
        "Parent": "",
        "Comment": "",
        "Created": "2021-01-12T10:17:41.649267496Z",
        "Container": "faa742a137cfbf261402d359c09203c3fd894fa49689e4f4952a657ea80d9107",
        "ContainerConfig": {
            "Hostname": "faa742a137cf",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "ExposedPorts": {
                "80/tcp": {}
            },
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "NGINX_VERSION=1.19.6",
                "NJS_VERSION=0.5.0",
                "PKG_RELEASE=1~buster"
            ],
            "Cmd": [
                "/bin/sh",
                "-c",
                "#(nop) ",
                "CMD [\"nginx\" \"-g\" \"daemon off;\"]"
            ],
            "Image": "sha256:a5531bdc09faaa444e565e6f9ec98ed4474970ed6fdd5db6b8b255534b220689",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": [
                "/docker-entrypoint.sh"
            ],
            "OnBuild": null,
            "Labels": {
                "maintainer": "NGINX Docker Maintainers <docker-maint@nginx.com>"
            },
            "StopSignal": "SIGQUIT"
        },
        "DockerVersion": "19.03.12",
        "Author": "",
        "Config": {
            "Hostname": "",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "ExposedPorts": {
                "80/tcp": {}
            },
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "NGINX_VERSION=1.19.6",
                "NJS_VERSION=0.5.0",
                "PKG_RELEASE=1~buster"
            ],
            "Cmd": [
                "nginx",
                "-g",
                "daemon off;"
            ],
            "Image": "sha256:a5531bdc09faaa444e565e6f9ec98ed4474970ed6fdd5db6b8b255534b220689",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": [
                "/docker-entrypoint.sh"
            ],
            "OnBuild": null,
            "Labels": {
                "maintainer": "NGINX Docker Maintainers <docker-maint@nginx.com>"
            },
            "StopSignal": "SIGQUIT"
        },
        "Architecture": "amd64",
        "Os": "linux",
        "Size": 132951424,
        "VirtualSize": 132951424,
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/9f504eecf7634a887a428ddac3bf690d3417261841f7fff2c6de3afc2023452b/diff:/var/lib/docker/overlay2/00dc731f8e51545b82cbb33ed442780cab53198a2e25f5c154130e9ae9194e77/diff:/var/lib/docker/overlay2/b97d980644c87bbca2067d1e91fbd6c8385656147c07853492f22b486e6b3621/diff:/var/lib/docker/overlay2/3261059e64529493ad49f93cf24a94a97ae977726e9d258a28fb2251f7abd467/diff",
                "MergedDir": "/var/lib/docker/overlay2/52aa955f92ae8e9913a69f8628c2395ba3825f8c60b9225d489dab1745660644/merged",
                "UpperDir": "/var/lib/docker/overlay2/52aa955f92ae8e9913a69f8628c2395ba3825f8c60b9225d489dab1745660644/diff",
                "WorkDir": "/var/lib/docker/overlay2/52aa955f92ae8e9913a69f8628c2395ba3825f8c60b9225d489dab1745660644/work"
            },
            "Name": "overlay2"
        },
        "RootFS": {
            "Type": "layers",
            "Layers": [
                "sha256:cb42413394c4059335228c137fe884ff3ab8946a014014309676c25e3ac86864",
                "sha256:1c91bf69a08b515a1f9c36893d01bd3123d896b38b082e7c21b4b7cc7023525a",
                "sha256:56bc37de0858bc2a5c94db9d69b85b4ded4e0d03684bb44da77e0fe93a829292",
                "sha256:3e5288f7a70f526d6bceb54b3568d13c72952936cebfe28ddcb3386fe3a236ba",
                "sha256:85fcec7ef3efbf3b4e76a0f5fb8ea14eca6a6c7cbc0c52a1d401ad5548a29ba5"
            ]
        },
        "Metadata": {
            "LastTagTime": "0001-01-01T00:00:00Z"
        }
    }
]
```

Това което виждате са основните неща които прави и съдържа имиджа: команда която изпълнява, променливи на средата и други.

За да видим всички команди които ```docker container``` има просто можем да изпълним ```docker container -h```.



```docker container -h
Flag shorthand -h has been deprecated, please use --help

Usage:  docker container COMMAND

Manage containers

Commands:
  attach      Attach local standard input, output, and error streams to a running container
  commit      Create a new image from a container's changes
  cp          Copy files/folders between a container and the local filesystem
  create      Create a new container
  diff        Inspect changes to files or directories on a container's filesystem
  exec        Run a command in a running container
  export      Export a container's filesystem as a tar archive
  inspect     Display detailed information on one or more containers
  kill        Kill one or more running containers
  logs        Fetch the logs of a container
  ls          List containers
  pause       Pause all processes within one or more containers
  port        List port mappings or a specific mapping for the container
  prune       Remove all stopped containers
  rename      Rename a container
  restart     Restart one or more containers
  rm          Remove one or more containers
  run         Run a command in a new container
  start       Start one or more stopped containers
  stats       Display a live stream of container(s) resource usage statistics
  stop        Stop one or more running containers
  top         Display the running processes of a container
  unpause     Unpause all processes within one or more containers
  update      Update configuration of one or more containers
  wait        Block until one or more containers stop, then print their exit codes

Run 'docker container COMMAND --help' for more information on a command.
```

След като видяхте всички команди към ```docker container``` можем да видим ```docker container ls```. Това е мениджмънт команда която ни показва актуалните ни контейнери.

```docker container ls
CONTAINER ID   IMAGE          COMMAND       CREATED      STATUS      PORTS     NAMES
eea7b5d418be   ansible        "/bin/bash"   4 days ago   Up 4 days             ans
d207354362e1   9eeef9904181   "/bin/bash"   4 days ago   Up 4 days             ansible_kofa
b46001e17517   9eeef9904181   "/bin/bash"   4 days ago   Up 4 days             youthful_leakey
```

При мен изхода е доста по изпълнен защото имам 3 контейнера, но при вас това местенце може да е празно може да пробвате следното:

```docker container run busybox```

Обаче когато изпълните ```docker container ls``` не се чудете, защото контейнера не работи. Просто ```busybox``` изпълнява ```sh```.
Когато дадете ```dokcer container ls -a``` (Ползвайки флага -a е с цел да може да видите всички контейнери: дори и спрелите) или ```docker container ps -a ``` ще видите, че работата на контейнера е свършила:

```docker container ps -a
CONTAINER ID   IMAGE          COMMAND        CREATED         STATUS                     PORTS     NAMES
50ee82aba11a   busybox        "sh"           2 minutes ago   Exited (0) 2 minutes ago             epic_brown
```

Сега обаче нека да използваме друго изображение:
Например можем да използваме ```nginx``` изображението което туко що свалихме:


```docker container run -P -d nginx``` ---> Нека разбием командата след ```run``` това което става е следното ```-P``` ще определи случаен порт на контейнера, а ```-d``` защото 
контейнера ще се изпълни на преден план и просто няма да можем да изпълним никакви команди.


След като командата се изпълни ще получите подобен на този странен изход:

```dc72604062ae04ceb5f4a4ddef8da19e38e2f19dbba6de3b7d75c13ea0627e10```
Това означава, че туко що генерирахме един контейнер, ако искате да му видите статута може да изпълните ```docker container ls/docker ps``` и ще видите, че е там.

```docker container ls
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS                   NAMES
dc72604062ae   nginx:latest   "/docker-entrypoint.…"   14 seconds ago   Up 13 seconds   0.0.0.0:49153->80/tcp   eloquent_euler
```
Сега нека видим малко повече за нашият контейнер:   ```!!! В голяма, част от командите ще използвам Container ID което в тази ситуация е dc72604062ae !!!```

```docker inspect dc72604062ae
[
    {
        "Id": "075d6a17a16e42cc8508ee2009fc19e6188b95f0f1f388fd311f43e6d52086af",
        "Created": "2021-01-27T00:01:54.490318671Z",
        "Path": "/docker-entrypoint.sh",
        "Args": [
            "nginx",
            "-g",
            "daemon off;"
        ],
        "State": {
            "Status": "running",
            "Running": true,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 95377,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2021-01-27T00:01:54.845386353Z",
            "FinishedAt": "0001-01-01T00:00:00Z"
        },
        "Image": "sha256:f6d0b4767a6c466c178bf718f99bea0d3742b26679081e52dbf8e0c7c4c42d74",
        "ResolvConfPath": "/var/lib/docker/containers/075d6a17a16e42cc8508ee2009fc19e6188b95f0f1f388fd311f43e6d52086af/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/075d6a17a16e42cc8508ee2009fc19e6188b95f0f1f388fd311f43e6d52086af/hostname",
        "HostsPath": "/var/lib/docker/containers/075d6a17a16e42cc8508ee2009fc19e6188b95f0f1f388fd311f43e6d52086af/hosts",
        "LogPath": "/var/lib/docker/containers/075d6a17a16e42cc8508ee2009fc19e6188b95f0f1f388fd311f43e6d52086af/075d6a17a16e42cc8508ee2009fc19e6188b95f0f1f388fd311f43e6d52086af-json.log",
        "Name": "/elated_meitner",
        "RestartCount": 0,
        "Driver": "overlay2",
        "Platform": "linux",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "docker-default",
        "ExecIDs": null,
        "HostConfig": {
            "Binds": null,
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "json-file",
                "Config": {}
            },
            "NetworkMode": "default",
            "PortBindings": {},
            "RestartPolicy": {
                "Name": "no",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "CapAdd": null,
            "CapDrop": null,
            "CgroupnsMode": "host",
            "Dns": [],
            "DnsOptions": [],
            "DnsSearch": [],
            "ExtraHosts": null,
            "GroupAdd": null,
            "IpcMode": "private",
            "Cgroup": "",
            "Links": null,
            "OomScoreAdj": 0,
            "PidMode": "",
            "Privileged": false,
            "PublishAllPorts": true,
            "ReadonlyRootfs": false,
            "SecurityOpt": null,
            "UTSMode": "",
            "UsernsMode": "",
            "ShmSize": 67108864,
            "Runtime": "runc",
            "ConsoleSize": [
                0,
                0
            ],
            "Isolation": "",
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": null,
            "BlkioDeviceWriteBps": null,
            "BlkioDeviceReadIOps": null,
            "BlkioDeviceWriteIOps": null,
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DeviceRequests": null,
            "KernelMemory": 0,
            "KernelMemoryTCP": 0,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": false,
            "PidsLimit": null,
            "Ulimits": null,
            "CpuCount": 0,
            "CpuPercent": 0,
            "IOMaximumIOps": 0,
            "IOMaximumBandwidth": 0,
            "MaskedPaths": [
                "/proc/asound",
                "/proc/acpi",
                "/proc/kcore",
                "/proc/keys",
                "/proc/latency_stats",
                "/proc/timer_list",
                "/proc/timer_stats",
                "/proc/sched_debug",
                "/proc/scsi",
                "/sys/firmware"
            ],
            "ReadonlyPaths": [
                "/proc/bus",
                "/proc/fs",
                "/proc/irq",
                "/proc/sys",
                "/proc/sysrq-trigger"
            ]
        },
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/638d394c96a91ae5875949f113dd757e79619ff41d74017642652bff6dbb24e8-init/diff:/var/lib/docker/overlay2/52aa955f92ae8e9913a69f8628c2395ba3825f8c60b9225d489dab1745660644/diff:/var/lib/docker/overlay2/9f504eecf7634a887a428ddac3bf690d3417261841f7fff2c6de3afc2023452b/diff:/var/lib/docker/overlay2/00dc731f8e51545b82cbb33ed442780cab53198a2e25f5c154130e9ae9194e77/diff:/var/lib/docker/overlay2/b97d980644c87bbca2067d1e91fbd6c8385656147c07853492f22b486e6b3621/diff:/var/lib/docker/overlay2/3261059e64529493ad49f93cf24a94a97ae977726e9d258a28fb2251f7abd467/diff",
                "MergedDir": "/var/lib/docker/overlay2/638d394c96a91ae5875949f113dd757e79619ff41d74017642652bff6dbb24e8/merged",
                "UpperDir": "/var/lib/docker/overlay2/638d394c96a91ae5875949f113dd757e79619ff41d74017642652bff6dbb24e8/diff",
                "WorkDir": "/var/lib/docker/overlay2/638d394c96a91ae5875949f113dd757e79619ff41d74017642652bff6dbb24e8/work"
            },
            "Name": "overlay2"
        },
        "Mounts": [],
        "Config": {
            "Hostname": "075d6a17a16e",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "ExposedPorts": {
                "80/tcp": {}
            },
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "NGINX_VERSION=1.19.6",
                "NJS_VERSION=0.5.0",
                "PKG_RELEASE=1~buster"
            ],
            "Cmd": [
                "nginx",
                "-g",
                "daemon off;"
            ],
            "Image": "nginx:latest",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": [
                "/docker-entrypoint.sh"
            ],
            "OnBuild": null,
            "Labels": {
                "maintainer": "NGINX Docker Maintainers <docker-maint@nginx.com>"
            },
            "StopSignal": "SIGQUIT"
        },
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "59ea1fe6c43608c7ea11e66f47d1d4c965a8a6edba2f54b8056d0fa185f54b10",
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "Ports": {
                "80/tcp": [
                    {
                        "HostIp": "0.0.0.0",
                        "HostPort": "49153"
                    }
                ]
            },
            "SandboxKey": "/var/run/docker/netns/59ea1fe6c436",
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "096e2850a89a9079952a1309b9dda102757f3e0d5fcf02cb120289af3994cf79",
            "Gateway": "172.17.0.1",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "IPAddress": "172.17.0.5",
            "IPPrefixLen": 16,
            "IPv6Gateway": "",
            "MacAddress": "02:42:ac:11:00:05",
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "f42cb02c0334b845b721ebe77d7e1f013ccf882b2ef956ef6d12ad9eb6845c08",
                    "EndpointID": "096e2850a89a9079952a1309b9dda102757f3e0d5fcf02cb120289af3994cf79",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.5",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:11:00:05",
                    "DriverOpts": null
                }
            }
        }
    }
]
```
Ще може да видите статута на контейнера какъв и обикновенните мрежови настройки.

Сега ще изпълним следното:

```docker container top dc72604062ae
UID                 PID                 PPID                C                   STIME               TTY
       TIME                CMD
root                95377               95353               0                   00:01               ?
       00:00:00            nginx: master process nginx -g daemon off;
systemd+            95440               95377               0                   00:01               ?
       00:00:00            nginx: worker process
```
Както виждате са показани двата основни процеса на които изпълнява контейнера.

```nginx: мастър процеса и worker процеса```

Нека се прикрепим към контейнера със ```docker container attach dc72604062ae```

Това което се случва в момента е ние се прикрепяме към стандартният вход и изход на контейнера. Не можем да направим нищо, защото контейнера нон-стоп ни изпраща изходящи сигнали към логовете за достъп. Заради това ние нямаме достъп до черупката му, поне по този начин. За да се откачим ще трябва да изпълните ```Ctrl+C``` това ще спре контейнера ни.

За да го стартираме ще трябва да изпълним ```docker container start dc72604062ae```

След като го стартираме може да отворите web-browser и да наберете IP адреса на вашата локална машина или да изпълните ```curl localhost:49153``` след като го направите ще генерирате трафик върху вашият web сървър. Тоест ще можем да видим в употреба командата ```docker container logs dc72604062ae```

Примерен изход на ```curl``` командата.

```curl localhost:49153
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```
Изход от ```docker container logs```

```docker container logs dc72604062ae
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
192.168.100.118 - - [27/Jan/2021:00:27:24 +0000] "GET / HTTP/1.1" 200 612 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/88.0.4324.104 Safari/537.36" "-"
2021/01/27 00:27:24 [error] 28#28: *1 open() "/usr/share/nginx/html/favicon.ico" failed (2: No such file or directory), client: 192.168.100.118, server: localhost, request: "GET /favicon.ico HTTP/1.1", host: "192.168.100.127:49153", referrer: "http://192.168.100.127:49153/"
192.168.100.118 - - [27/Jan/2021:00:27:24 +0000] "GET /favicon.ico HTTP/1.1" 404 555 "http://192.168.100.127:49153/" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/88.0.4324.104 Safari/537.36" "-"
172.17.0.1 - - [27/Jan/2021:00:30:53 +0000] "GET / HTTP/1.1" 200 612 "-" "curl/7.68.0" "-"
```

Сега ще погледнем статистиките на контейнера със ```docker container stats```:

Ако искате да погледнете статистиките просто изпълнете ```docker container stats dc72604062ae```
```
CONTAINER ID   NAME             CPU %     MEM USAGE / LIMIT     MEM %     NET I/O           BLOCK I/O         PIDS
dc72604062ae   recursing_pare   0.00%     3.363MiB / 1.913GiB   0.17%     3.72kB / 3.86kB   8.19kB / 16.4kB   2
```

