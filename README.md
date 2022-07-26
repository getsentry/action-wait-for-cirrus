action-wait-for-cirrus
======================

waits for a cirrus task to complete and downloads its artifacts

## permissions

this action requires the following permissions:

```yaml
    permissions:
      checks: read
```

## usage

the main input to this action is the cirrus task `name`

you will want to include a `timeout-minutes` on the step using this action or
it will poll forever for missing tasks

```yaml
  - uses: getsentry/action-wait-for-cirrus@v1.0.0
    with:
      task: task name here
    timeout-minutes: 15
```

when used for both pull requests and pushes you'll need to override commit:

```yaml
  - uses: getsentry/action-wait-for-cirrus@v1.0.0
    with:
      task: task name here
      commit: ${{ github.event.pull_request.head.sha || github.sha }}
    timeout-minutes: 15
```

for the rest of the options, see `action.yml`
