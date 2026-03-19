# Systemd-driven battery monitor

Was hoping we could trigger the service via changes in the sysfs battery capacity level but that doesn't seem to work.

Instead, we'll just use a timer.

## Setup

```shell
mkdir -p .config/systemd/user
cp src/battery-monitor/battery-monitor.* .config/systemd/user/
```

## Test service
```shell
cp src/battery-monitor/battery-monitor.* .config/systemd/user/
systemctl --user daemon-reload
systemctl start --user battery-monitor
```

## Start monitoring
```shell
systemctl enable --now --user battery-monitor.timer
```

## Test monitoring
```shell
journalctl --user -u battery-monitor -f
```
