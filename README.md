# bupt-ncov-report-action

使用 GitHub Actions 自动填报北邮 2019-nCoV 疫情信息。

这个 Action 会自动在北京时间的每天 4:00 AM 进行填报。

## 使用方法

首先，fork。

然后，在你自己仓库的 Settings 的 Secrets 中设置以下信息：

- `BUPT_USERNAME`: 你用来登录的学号；
- `BUPT_PASSWORD`: 你用来登录的密码。

最后在仓库的 Actions 中手动启用 GitHub Actions，你需要先 Enable Actions，再开启名为 `Automatically submit the 2019-nCoV report sheet of BUPT` 的 workflow。

如果仓库没有活动，60天后 GitHub Actions 会自动停止，你需要手动再次开启它。

## 检查结果

无需任何设置。如果运行失败，GitHub 会向你的邮箱发送一封邮件。

如果你更改了设置，想手动重新运行，可以点进上方的 Actions 栏，点击 Re-run Jobs 来重新运行。

### Telegram Bot

如果你知道怎么使用 Telegram Bot，则可以额外设置如下的 Secrets 来用 Bot 给你发送结果：

- `TG_BOT_TOKEN`: 你的 Bot 的 Token；
- `TG_CHAT_ID`: 你和 Bot 的 Chat ID。

## 高级设置

你可以在 `.github/workflows/main.yml` 中来设置每天运行的时间：

```yml
on:
  schedule:
    - cron: "0 0 * * *"
```

格式是标准的 cron 格式，第一个数字代表分钟，第二个数字代表小时。例如，`0 1 * * *` 表示在每天
格林尼治时间的 1:00 AM，也就是在北京时间的 9:00 AM 自动运行。

<!-- something   />
