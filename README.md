# monitoring-system
 a simple monitoring-system  
 一个用于检测cpu使用情况的系统，并在cpu高负载时告警，基于Prometheus+Grafana。
# 操作系统
 wsl(ubuntu 22.04)
# 使用方法
 1、先安装docker和docker-compose  
 2、修改alertmanager/alertmanager.yml中的邮箱设置（默认使用邮箱告警，也可修改为其他告警方式）  
 3、启动服务：`docker-compose up -d`  
 4、访问各服务 Web UI：  
    ​Prometheus：http://localhost:9090  
      输入 node_cpu_seconds_total 查看指标数据。  
    ​Grafana：http://localhost:3000  
      初始账号：admin/admin，首次登录需修改密码。  
    ​Alertmanager：http://localhost:9093  
      查看告警路由和静默规则。   
 5、配置 Grafana 数据源和仪表盘：  
    ​添加 Prometheus 数据源​  
      Grafana 左侧菜单 → Connections → Data sources → Add data source → 选择 Prometheus  
      URL：http://prometheus:9090 → Save & Test  
    ​导入官方仪表盘​  
      左侧菜单 → Dashboards → New → Import  
      输入模板 ID：1860（Node Exporter 全监控）→ Load  
      选择 Prometheus 数据源 → Import  
 6、测试告警触发：  
    使用`stress`模拟高负载;  
    在Prometheus的alert页面查看告警状态;  
    检查邮箱是否收到告警通知（需要等待一段时间，默认5分钟左右）。  
# 其他
 修改：  
 在docker-compose.yml中可修改端口映射、添加新服务等;  
 在prometheus.yml中可添加监控任务、调整抓取频率等;  
 在alerts.yml中可以修改或添加告警规则;  
 在alertmanager.yml中可以修改告警方式。  
 如何获取 QQ 邮箱授权码：  
 登录 QQ 邮箱 → 设置 → 账户 → 开启 POP3/SMTP服务  
 生成授权码（16位随机字符串）
