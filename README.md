php-thrift-hive-client
======================
Wrap ThriftHiveClient

Usage
------

### Sample ###

    <?php
    $GLOBALS['THRIFT_ROOT'] = dirname(__FILE__) . '/lib';
    require_once $GLOBALS['THRIFT_ROOT'] . '/packages/hive_service/ThriftHive.php';
    require_once $GLOBALS['THRIFT_ROOT'] . '/transport/TSocket.php';
    require_once $GLOBALS['THRIFT_ROOT'] . '/protocol/TBinaryProtocol.php';

    require_once dirname(__FILE__) . '/ThriftHiveClientEx.php';

    $transport = new TSocket('localhost', 10000);
    $transport->setSendTimeout(600 * 1000);
    $transport->setRecvTimeout(600 * 1000);
    $client = new ThriftHiveClientEx(new TBinaryProtocol($transport));
    $client->open();
    $client->execute('SHOW DATABASES');
    var_dump($client->fetchAll());
    $client->close();
