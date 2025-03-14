**DBeaver Proxy Driver** is a JDBC driver that lets third-party tools connect to databases configured in [CloudBeaver Enterprise](https://dbeaver.com/cloudbeaver-enterprise/) or [Team Edition](https://dbeaver.com/dbeaver-team-edition/).  

### Set up the driver

1. [Download](https://github.com/dbeaver/jdbc-driver-upd/releases) the driver.
2. Add all downloaded `.jar` files to your tool’s JDBC driver configuration. Check your tool’s documentation for details.
3. In CloudBeaver or Team Edition (web interface), go to **Settings -> Administration -> Server configuration**, then enable the **DBeaver Proxy Driver** checkbox.
4. Generate an API token. For details, see [Generate API access token guide](https://github.com/dbeaver/cloudbeaver/wiki/Generate-API-access-token).

### Connect to a database

To establish a connection, specify the following parameters:

#### JDBC URL

```
jdbc:dbeaver:upd:<server-host>:<server-port>:<project-name>:<connection>
```

| Placeholder       | Description                                                                              |
|-------------------|------------------------------------------------------------------------------------------|
| `<server-host>`   | The server hostname or IP address.                                                       |
| `<server-port>`   | The server port.                                                                         |
| `<project-name>`  | The project name. In CloudBeaver, the only available project is `Shared`.                |
| `<connection>`    | The connection ID or the name of the database connection in CloudBeaver or Team Edition. |

> To find the connection ID or name, connect to CloudBeaver or Team Edition (web interface), right-click the database in **Database
> Navigator**, select **Open**, and copy **ID** or **Name**. Using the **ID** is more reliable than the connection name.

#### Driver class name

```
com.dbeaver.jdbc.upd.driver.UPDDriver
```

#### Authentication properties

| Property           | Description                           |
|--------------------|---------------------------------------|
| `dbeaver.token`    | API token (recommended).              |
| `dbeaver.user`     | Username (only if not using a token). |
| `dbeaver.password` | Password (only if not using a token). |

### Limitations

Currently, the driver supports only basic queries and database operations. It does not yet support:

- Editing **date/time values**.
- Performing **dump/restore operations**.
- Switching **schemas**.
- Handling **special data types** (e.g., `timestamp`, `arrays`).
- Executing **complex queries** (e.g., `JOIN` operations).
- Opening more than five connections.
