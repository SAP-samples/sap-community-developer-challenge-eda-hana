## Create `DevChallenger` user in your SAP HANA db instance

### ... using `dhbsql`

1. Connect as an administrator, here `DBAdmin` user
    ```Shell
    hdbsql -u DBAdmin -n <yourinstanceid>.hana.trial-us10.hanacloud.ondemand.com:443
    ```

2. Switch the input to multiline SQL statements separated with `;` by default.
    ```SQL
    \multiline ON
    ```

3. Execute SQL statement to create a user.
    ```SQL
    CREATE USER DevChallenger 
    PASSWORD "Up2TheChallenge!Iam" --replace this with your password of choice!
    NO FORCE_FIRST_PASSWORD_CHANGE;
    ```

4. Execute SQL statement to grant a role `AFL__SYS_AFL_AFLPAL_EXECUTE` to the user. 
    ```SQL
    GRANT AFL__SYS_AFL_AFLPAL_EXECUTE TO DevChallenger;
    ```

5. Optionally, check that the user record has been added to the `USERS` system table.
    ```SQL
    SELECT COUNT(*) FROM USERS WHERE USER_NAME='DEVCHALLENGER';
    ```

6. Quit `hdbsql` utility.
    ```SQL
    \quit
    ```

![Create a DB user called DEVCHALLENGER](CreateDevChallenger.png)