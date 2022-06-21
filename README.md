# Hexo博客的自动化部署

有一说一，搞得我精疲力竭。

先是看到了在Hexo群里的自动化部署的方法，于是便开始尝试，最开始是发现yml文件的格式检查非常的严格，后来改了格式，生成是没有问题了，但在部署的时候还是会有`Spawn failed`：

```shell
Warning: Permanently added the ECDSA host key for IP address '140.82.112.4' to the list of known hosts.
Load key "/home/runner/.ssh/id_rsa": invalid format
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.
Please make sure you have the correct access rights
and the repository exists.

FATAL {
  err: Error: Spawn failed
      at ChildProcess.<anonymous> (/home/runner/work/blog-deploy/blog-deploy/node_modules/hexo-util/lib/spawn.js:51:21)
      at ChildProcess.emit (events.js:314:20)
      at Process.ChildProcess._handle.onexit (internal/child_process.js:276:12) {
    code: 128
  }
} Something's wrong. Maybe you can find the solution here: %s https://hexo.io/docs/troubleshooting.html

Error: Process completed with exit code 2.
```

在把全网的方式都尝试过一遍后，我还是选择不搞了，心累:tired_face:
