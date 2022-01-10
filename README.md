## 主应用

```js
npx @modern-js/create main
//开启微前端
yarn new
```

配置子应用 package.json

```js
"modernConfig": {
  "runtime": {
    "router": true,
    "state": true,
    "masterApp": {
      "manifest": {
        "modules": [
          {
            "name": "Dashboard",
            "entry": "http://localhost:8081"
          }
        ]
      }
    }
  },
  "server": {
    "enableMicroFrontendDebug": true
  }
}
```

子应用

```js
import { Switch, Route, Link } from "@modern-js/runtime/router";
import { useModuleApps } from "@modern-js/runtime";
const App = () => {
  const { Dashboard, Table } = useModuleApps();
  return (
    <div>
      <div>
        <Link to="/dashboard">Dashboard</Link> &nbsp;
        <Link to="/table">Table</Link>
      </div>
      <Switch>
        <Route path="/dashboard" exact={true}>
          <Dashboard username="jessica" />
        </Route>
        <Route path="/table" exact={true}>
          <Table />
        </Route>
      </Switch>
    </div>
  );
};
```

## 子应用

```js
npx @modern-js/create dashboard
//开启微前端
yarn new
```

配置应用 package.json

```js
{
  "modernConfig": {
    "runtime": {
      "router": true,
      "state": true
    },
    "deploy": {
      "microFrontend": true
    },
    "server": {
      "port": 8081
    }
  }
}
```
