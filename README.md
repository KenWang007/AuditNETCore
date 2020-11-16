# AuditNETCore
Demo for audit solution in .net core project with custom serialize rules

近期想为项目上添加audit log，经过调研之后发现在.NET平台下比较好用的框架Audit.NET(https://github.com/thepirat000/Audit.NET), 我们的需求是：对于一些用户敏感数据是不能计入审计日志的，那就想在序列化的过程中通过忽略特定的属性，Newtonsoft提供的默认属性JsonIgnore可以对特定属性忽略序列化，但是如果加上这个属性就会影响程序的正常运行（如：在api返回给前端的过程中加上JsonIgnore属性的这些数据就丢失了），想要实现我们的需求就需要我们在包含用户敏感数据的字段上添加自定义的Attribute,然后在Audit的序列化过程中对带有特定属性的字段忽略，这样既保证程序正常的序列化不受影响，又能达到我们的目的，所以就用到了当前repo里面的方法。

Audit.NET : https://github.com/KenWang007/Audit.NET
