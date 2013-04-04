dcdumper
========

Adding tools to the dotcloud CLI which make it easier to do backups.

## Installation

`pip install https://github.com/metalivedev/dcdumper/archive/master.zip`

## Use

The first addition is `sshconf` which is super-useful for working directly with `ssh`, `scp` and `rsync`

```
$ dcdumper.py sshconf -A myapp --file myapp.conf
==> Wrote 1 entries to myapp.conf. You can now sync your data with:
==> "rsync -azv -e 'ssh -F myapp.conf' myapp.myservice.0:code/ code"
```

Every one of your dotCloud code services has a full copy of all the code 
for all the code services in that application. 
The code is always under the symbolic link `code/` so it is easy to find and rsync it down.

For more information about using `ssh`, `scp` and `rsync` with your dotCloud applications,
please see [the docs](http://docs.dotcloud.com/guides/copy/#generic-ssh-scp-rsync)
The magic is in using the `-F` parameter to let `ssh` know to use the file as your configuration file.
