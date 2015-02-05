zabbix-etcd
-----------

Zabbix monitoring template for [ETCD](https://github.com/coreos/etcd)

**How to install**

- put the `etcd-stats.py` in you zabbix `libexec` dir (I use `/usr/local/libexec/zabbix`)
- put the `etcd-params.conf` file in your zabbix `conf.d` path
- change the path of the `etcd-stats.py` in the params file to where you put it
- import the template (`etcd-template.xml`)
- apply to desired hosts

**Monitored items**

`etcd` process status (up/down):

    proc.num[etcd]

`/v2/stats/self`:

    etcd.self[recvAppendRequestCnt]
    etcd.self[sendAppendRequestCnt]
    etcd.self[state]

`/v2/stats/store`:

    # local stats that are uniqie to the node
    etcd.store[expireCount]
    etcd.store[getsFail]
    etcd.store[getsSuccess]
    etcd.store[watchers]

    # global stats that are shared across the cluster
    etcd.store[compareAndDeleteFail]
    etcd.store[compareAndDeleteSuccess]
    etcd.store[compareAndSwapFail]
    etcd.store[compareAndSwapSuccess]
    etcd.store[createFail]
    etcd.store[createSuccess]
    etcd.store[deleteFail]
    etcd.store[deleteSuccess]
    etcd.store[setsFail]
    etcd.store[setsSuccess]
    etcd.store[updateFail]
    etcd.store[updateSuccess]

`/v2/stats/leader`:

    etcd.follower[counts,fail]
    etcd.follower[counts,success]
    etcd.follower[latency,average]
    etcd.follower[latency,current]
    etcd.follower[latency,standardDeviation]

**License**

    Copyright 2015 Alex Simenduev <shamil.si@gmail.com>

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
