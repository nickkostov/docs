Първо започенете с проверка на командата ```docker container run``` и нейният помощен център:

```docker container run --help```

```docker container run --help

Usage:  docker container run [OPTIONS] IMAGE [COMMAND] [ARG...]

Run a command in a new container

Options:
      --add-host list                  Add a custom host-to-IP mapping (host:ip)
  -a, --attach list                    Attach to STDIN, STDOUT or STDERR
      --blkio-weight uint16            Block IO (relative weight), between 10 and 1000, or 0 to disable (default 0)
      --blkio-weight-device list       Block IO weight (relative device weight) (default [])
      --cap-add list                   Add Linux capabilities
      --cap-drop list                  Drop Linux capabilities
      --cgroup-parent string           Optional parent cgroup for the container
      --cgroupns string                Cgroup namespace to use (host|private)
                                       'host':    Run the container in the Docker host's cgroup namespace
                                       'private': Run the container in its own private cgroup namespace
                                       '':        Use the cgroup namespace as configured by the
                                                  default-cgroupns-mode option on the daemon (default)
      --cidfile string                 Write the container ID to the file
      --cpu-period int                 Limit CPU CFS (Completely Fair Scheduler) period
      --cpu-quota int                  Limit CPU CFS (Completely Fair Scheduler) quota
      --cpu-rt-period int              Limit CPU real-time period in microseconds
      --cpu-rt-runtime int             Limit CPU real-time runtime in microseconds
  -c, --cpu-shares int                 CPU shares (relative weight)
      --cpus decimal                   Number of CPUs
      --cpuset-cpus string             CPUs in which to allow execution (0-3, 0,1)
      --cpuset-mems string             MEMs in which to allow execution (0-3, 0,1)
  -d, --detach                         Run container in background and print container ID
      --detach-keys string             Override the key sequence for detaching a container
      --device list                    Add a host device to the container
      --device-cgroup-rule list        Add a rule to the cgroup allowed devices list
      --device-read-bps list           Limit read rate (bytes per second) from a device (default [])
      --device-read-iops list          Limit read rate (IO per second) from a device (default [])
      --device-write-bps list          Limit write rate (bytes per second) to a device (default [])
      --device-write-iops list         Limit write rate (IO per second) to a device (default [])
      --disable-content-trust          Skip image verification (default true)
      --dns list                       Set custom DNS servers
      --dns-option list                Set DNS options
      --dns-search list                Set custom DNS search domains
      --domainname string              Container NIS domain name
      --entrypoint string              Overwrite the default ENTRYPOINT of the image
  -e, --env list                       Set environment variables
      --env-file list                  Read in a file of environment variables
      --expose list                    Expose a port or a range of ports
      --gpus gpu-request               GPU devices to add to the container ('all' to pass all GPUs)
      --group-add list                 Add additional groups to join
      --health-cmd string              Command to run to check health
      --health-interval duration       Time between running the check (ms|s|m|h) (default 0s)
      --health-retries int             Consecutive failures needed to report unhealthy
      --health-start-period duration   Start period for the container to initialize before starting health-retries countdown (ms|s|m|h) (default 0s)
      --health-timeout duration        Maximum time to allow one check to run (ms|s|m|h) (default 0s)
      --help                           Print usage
  -h, --hostname string                Container host name
      --init                           Run an init inside the container that forwards signals and reaps processes
  -i, --interactive                    Keep STDIN open even if not attached
      --ip string                      IPv4 address (e.g., 172.30.100.104)
      --ip6 string                     IPv6 address (e.g., 2001:db8::33)
      --ipc string                     IPC mode to use
      --isolation string               Container isolation technology
      --kernel-memory bytes            Kernel memory limit
  -l, --label list                     Set meta data on a container
      --label-file list                Read in a line delimited file of labels
      --link list                      Add link to another container
      --link-local-ip list             Container IPv4/IPv6 link-local addresses
      --log-driver string              Logging driver for the container
      --log-opt list                   Log driver options
      --mac-address string             Container MAC address (e.g., 92:d0:c6:0a:29:33)
  -m, --memory bytes                   Memory limit
      --memory-reservation bytes       Memory soft limit
      --memory-swap bytes              Swap limit equal to memory plus swap: '-1' to enable unlimited swap
      --memory-swappiness int          Tune container memory swappiness (0 to 100) (default -1)
      --mount mount                    Attach a filesystem mount to the container
      --name string                    Assign a name to the container
      --network network                Connect a container to a network
      --network-alias list             Add network-scoped alias for the container
      --no-healthcheck                 Disable any container-specified HEALTHCHECK
      --oom-kill-disable               Disable OOM Killer
      --oom-score-adj int              Tune host's OOM preferences (-1000 to 1000)
      --pid string                     PID namespace to use
      --pids-limit int                 Tune container pids limit (set -1 for unlimited)
      --platform string                Set platform if server is multi-platform capable
      --privileged                     Give extended privileges to this container
  -p, --publish list                   Publish a container's port(s) to the host
  -P, --publish-all                    Publish all exposed ports to random ports
      --pull string                    Pull image before running ("always"|"missing"|"never") (default "missing")
      --read-only                      Mount the container's root filesystem as read only
      --restart string                 Restart policy to apply when a container exits (default "no")
      --rm                             Automatically remove the container when it exits
      --runtime string                 Runtime to use for this container
      --security-opt list              Security Options
      --shm-size bytes                 Size of /dev/shm
      --sig-proxy                      Proxy received signals to the process (default true)
      --stop-signal string             Signal to stop a container (default "SIGTERM")
      --stop-timeout int               Timeout (in seconds) to stop a container
      --storage-opt list               Storage driver options for the container
      --sysctl map                     Sysctl options (default map[])
      --tmpfs list                     Mount a tmpfs directory
  -t, --tty                            Allocate a pseudo-TTY
      --ulimit ulimit                  Ulimit options (default [])
  -u, --user string                    Username or UID (format: <name|uid>[:<group|gid>])
      --userns string                  User namespace to use
      --uts string                     UTS namespace to use
  -v, --volume list                    Bind mount a volume
      --volume-driver string           Optional volume driver for the container
      --volumes-from list              Mount volumes from the specified container(s)
  -w, --workdir string                 Working directory inside the container
  ```
  
  
  Както виждате имаме доста флагове които се появяват, няма да покрием всички опции, а ще се насочим към:
  
  ```docker container run
  
  --help: Ползване с цел ориентир
  --rm: Автоматично прехване на контейнер веднага щом "излезе"
  -d; --detach: Изпълни контейнера на заден фон и извади IDто му
  -i; --interactive: Задръж стандартния вход отворен дори и да не съм закачен
  --name стринг: Посочете име на контейнера
  -p, --publish list: Публикувай портове контейнер към локална машина
  -t, --tty: Слагане на псевдо TTY (конзола)
  -v, --volume list: Закачане на обеми
  ```
  
  
  Некда да пуснем ```busybox```:
  ```docker container run busybox```
```  docker container ls 
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

Както виждате контейнера не работи защото той си изпълни командата и спря. (Виж docker команди за повече информация)


```docker container ls -a 
CONTAINER ID   IMAGE     COMMAND   CREATED         STATUS                     PORTS     NAMES
af34ebf42d30   busybox   "sh"      2 minutes ago   Exited (0) 2 minutes ago             nervous_leakey
```

Можеби забелязвате, че контейнера - поведението му е по-скоро като някаква задача.

```Контейнера е дълго изпълняващ се процес. Тоест докато ние не го спрем той няма да спре да работи или ако самата му задача бива изпълнена
```

В примера по-горе виждате, че той вече си е изпълнил длъжността (задачата), а пък от предния документ видяхте как ```nginx``` не спираше защото работата на контейнера беше да изпълни задачата си, докато не бъде спрян или премахнат.

Сега ще изпълня docker container run nginx и ще видите, че когато го изпълним той ще седи на преден фон:

```docker container run nginx
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
```

Очевидно това не е идеално и затова ще използвам -d флага който ще ме разкачи от контейнера за да може да си работи на заден план.

```docker container -d nginx```

```docker container run -d nginx
2e0805898deccc1029c9a8748b485b9a00467b67f5a9b18779e3544dd2a4c7ff
```

```
docker container ls 
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS     NAMES
2e0805898dec   nginx     "/docker-entrypoint.…"   26 seconds ago   Up 24 seconds   80/tcp    condescending_dijkstra
```

Както виждате контейнера работи.


Сега ще ви покажа как да се закачим за него със ```-i и -t ``` с цел да получим достъп до контейнер:

```docker container run -it busybox
/ # ls
bin   dev   etc   home  proc  root  sys   tmp   usr   var
/ # pwd
/
/ # ls -lah
total 44K    
drwxr-xr-x    1 root     root        4.0K Jan 29 07:26 .
drwxr-xr-x    1 root     root        4.0K Jan 29 07:26 ..
-rwxr-xr-x    1 root     root           0 Jan 29 07:26 .dockerenv
drwxr-xr-x    2 root     root       12.0K Jan 12 00:39 bin
drwxr-xr-x    5 root     root         360 Jan 29 07:26 dev
drwxr-xr-x    1 root     root        4.0K Jan 29 07:26 etc
drwxr-xr-x    2 nobody   nobody      4.0K Jan 12 00:39 home
dr-xr-xr-x  238 root     root           0 Jan 29 07:26 proc
drwx------    1 root     root        4.0K Jan 29 07:26 root
dr-xr-xr-x   13 root     root           0 Jan 29 07:26 sys
drwxrwxrwt    2 root     root        4.0K Jan 12 00:39 tmp
drwxr-xr-x    3 root     root        4.0K Jan 12 00:39 usr
drwxr-xr-x    4 root     root        4.0K Jan 12 00:39 var
```





