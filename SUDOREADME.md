 Sudo For NPM
 ============
 我用的是Macbook Pro 笔记本，在Shell终端已经装了node和npm：
 
但是尝试使用一些npm的小工具（eg： http-server， fanyi）是输入正常的安装命令：
```
npm i -g fanyi
```
终端会提示如下错误：
```
npm WARN checkPermissions Missing write access to /usr/local/lib/node_modules
npm ERR! path /usr/local/lib/node_modules
npm ERR! code EACCES
npm ERR! errno -13
npm ERR! syscall access
npm ERR! Error: EACCES: permission denied, access '/usr/local/lib/node_modules'
npm ERR!  { [Error: EACCES: permission denied, access '/usr/local/lib/node_modules']
npm ERR!   stack:
npm ERR!    'Error: EACCES: permission denied, access \'/usr/local/lib/node_modules\'',
npm ERR!   errno: -13,
npm ERR!   code: 'EACCES',
npm ERR!   syscall: 'access',
npm ERR!   path: '/usr/local/lib/node_modules' }
npm ERR!
npm ERR! The operation was rejected by your operating system.
npm ERR! It is likely you do not have the permissions to access this file as the current user
npm ERR!
npm ERR! If you believe this might be a permissions issue, please double-check the
npm ERR! permissions of the file and its containing directories, or try running
npm ERR! the command again as root/Administrator (though this is not recommended).

npm ERR! A complete log of this run can be found in:
npm ERR!     /Users/zhaochenglong/.npm/_logs/2019-01-04T02_59_44_421Z-debug.log
bogon:desktop zhaochenglong$ which npm
/usr/local/bin/npm
bogon:desktop zhaochenglong$ npm -v
6.4.1
bogon:desktop zhaochenglong$ cd ~/user/local/bin
bash: cd: /Users/zhaochenglong/user/local/bin: No such file or directory
bogon:desktop zhaochenglong$ npm

Usage: npm <command>

where <command> is one of:
    access, adduser, audit, bin, bugs, c, cache, ci, cit,
    completion, config, create, ddp, dedupe, deprecate,
    dist-tag, docs, doctor, edit, explore, get, help,
    help-search, hook, i, init, install, install-test, it, link,
    list, ln, login, logout, ls, outdated, owner, pack, ping,
    prefix, profile, prune, publish, rb, rebuild, repo, restart,
    root, run, run-script, s, se, search, set, shrinkwrap, star,
    stars, start, stop, t, team, test, token, tst, un,
    uninstall, unpublish, unstar, up, update, v, version, view,
    whoami

npm <command> -h  quick help on <command>
npm -l            display full usage info
npm help <term>   search for help on <term>
npm help npm      involved overview

Specify configs in the ini-formatted file:
    /Users/zhaochenglong/.npmrc
or on the command line via: npm <command> --key value
Config info can be viewed via: npm help config

npm@6.4.1 /usr/local/lib/node_modules/npm
bogon:desktop zhaochenglong$ which npm
/usr/local/bin/npm
```

于是google一下这个问题怎么解决，在github上看到别人的分享，建议用sudo：
```
sudo npm i -g fanyi
```

安装成功，太帅了，于是MDN了一下sudo ：
```
bogon:desktop zhaochenglong$ sudo npm i -g fanyi
Password:
/usr/local/bin/fy -> /usr/local/lib/node_modules/fanyi/bin/fanyi
/usr/local/bin/fanyi -> /usr/local/lib/node_modules/fanyi/bin/fanyi
+ fanyi@2.0.1
added 77 packages from 134 contributors in 2.01s
bogon:desktop zhaochenglong$ fanyi lover

⠋  lover  英[ ˈlʌvə(r) ]  美[ ˈlʌvɚ ]  ~  iciba.com

 - n. 爱好者，嗜好者；情人；情妇，情夫；情侣；

 1. The grievances can be told is not real grievances; The lover can be stolen a lover.
    能够说出的委屈,便不算委屈; 能够抢走的爱人,便不算爱人.——《开到荼蘼》.
 2. NIV I am my lover's and my lover is mine; he browses among the lilies.
    3[和合]我属我的2良人;我的良人也属我. 他在百合花中牧放群羊.
 3. I. once a lover, always a lover.
    一日夫妻百日恩.
 4. Lover lover is, asas love, not to compare.
    爱人就是爱人, 只要去爱, 不要拿来比较.
 5. Ambiguous, he is not your lover, but he understand and care you than your lover.
    暧昧是, 他(她)不是你的情人, 但似乎你的情人更关心你和了解你.

```
Sudo
-----
Using sudo with a command in Linux/UNIX generally elevates your permissions to superuser levels. In Windows, the superuser account is usually called 'Administrator.' In Linux/Unix the superuser account is generally named 'root'.
The root user has permission to access, modify or delete almost any file on your computer. Normal user accounts can access, modify or delete many fewer files. The restrictions on a normal account protect your computer from unauthorized or harmful programs or users. Some processes require you to perform actions on files or folders you don't normally have permissions to access. Installing a program that everyone can access is one of these actions.

In my case, running the installation command with sudo gives you the permissions of the superuser, and allows you to modify files that your normal user doesn't have permission to modify. In the example above, the user doesn't have permission to create the fanyi in the directory /usr/local/lib/node_modules/. The root user does, and so the installation is successful.
That doesn't mean you should run everything with Sudo. You should only use sudo, or log in as the root user, when you absolutely have to.
<br>
\<br>
