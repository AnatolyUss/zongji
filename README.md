# ZongJi
A MySQL binlog listener running on Node.js.

ZongJi (踪迹) is pronounced as `zōng jì` in Chinese.

## Prerequisite

* Node.js v0.10+
* libmysqlclient-dev
* enable MySQL binlog in `my.cnf`, here is a sample config, remember to restart MySQL server after making the changes.
  > Notice that binlog checksum is disabled, ZongJi doesn't support it right now. It's a new feature from [MySQL 5.6](https://dev.mysql.com/doc/refman/5.6/en/replication-options-binary-log.html).

  ```
  # binlog config
  server-id = 1
  log_bin = /usr/local/var/log/mysql/mysql-bin.log
  binlog_do_db = employees
  expire_logs_days = 10
  max_binlog_size  = 100M

  #Very important if you want to receive write, update and delete row events
  binlog_format    = row

  # only do it in mysql 5.6
  binlog_checksum  = none
  ```

## Reference

I learnt many things from following resources while making ZongJi.

* http://intuitive-search.blogspot.co.uk/2011/07/binary-log-api-and-replication-listener.html
* https://github.com/Sannis/node-mysql-libmysqlclient
* https://kkaefer.com/node-cpp-modules/
* http://dev.mysql.com/doc/internals/en/replication-protocol.html
* http://www.cs.wichita.edu/~chang/lecture/cs742/program/how-mysql-c-api.html

### License
MIT
