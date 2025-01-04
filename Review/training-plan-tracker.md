---
id: training-plan-tracker
aliases: []
tags: []
created: 04-01-2025, 20:04:28
updated: 04-01-2025, 20:31:53
training-plans:
  - count: 12
    limit: 12
    payment-date: 2024-12-02
    started-date: 2025-01-06
    finished-date: 2025-01-31
  - count: 1
    started-date: 2025-01-04
---

# Training Plan Tracker

```js-engine
const mb = engine.getPlugin('obsidian-meta-bind-plugin').api;

const tableOptions = {
  bindTarget: mb.createBindTarget(
    'frontmatter', 
    context.file.path, 
    ['training-plans']
  ),
  tableHead: [
    "Done",
    "Limit",
    "Payment",
    "Started",
    "Finished",
  ],
  columns: [
    "INPUT[number(class(meta-bind-small-width)):scope^count]",
    "INPUT[number(placeholder(12), class(meta-bind-small-width)):scope^limit]",
    "INPUT[datePicker(defaultValue(null)):scope^payment-date]",
    "INPUT[datePicker(defaultValue(null)):scope^started-date]",
    "INPUT[datePicker(defaultValue(null)):scope^finished-date]",
  ],
};

const mountable = mb.createTableMountable(context.file.path, tableOptions);

mb.wrapInMDRC(mountable, container, component);
```
