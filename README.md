# DataTables

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

### ISSUE

When a table is displayed in a v-dialog component, the left-most column is misaligned.

```
Fix
```

Module datatables.net redraws a table using the columns.adjust().draw() method.