SAEDrupal Based on Drupal 7.27
=========

Drupal for SAE(http://sae.sina.com.cn)
8 points need to be changed:
    Add ./config.yaml
    Add ./sae_app_wizard.xml
    Add ./modulse/saecloud
    Add ./sites/all/modules/sae
    Add ./sites/default/files
    Add ./sites/default/settings.php
    Change ./includes/bootstrap.inc
        ini_set('magic_quotes_runtime', '0'); ===> @ini_set('magic_quotes_runtime', '0');
        ini_set('session.use_cookies', '1'); ===> @ini_set('session.use_cookies', '1');
        ini_set('session.use_only_cookies', '1'); ===> @ini_set('session.use_only_cookies', '1');
        ini_set('session.use_trans_sid', '0'); ===> @ini_set('session.use_trans_sid', '0');
        ini_set('session.cache_limiter', ''); ===> @ini_set('session.cache_limiter', '');
        ini_set('session.cookie_httponly', '1'); ===> @ini_set('session.cookie_httponly', '1');
        ini_set('session.cookie_domain', $cookie_domain); ===> @ini_set('session.cookie_domain', $cookie_domain);
        ini_set('session.cookie_secure', TRUE); ===> @ini_set('session.cookie_secure', TRUE);
        ini_set('zlib.output_compression', '0'); ===> @ini_set('zlib.output_compression', '0');
    Change ./includes/common.inc
        $socket = 'tcp://' . $uri['host'] . ':' . $port; ===> $socket = 'tcp://' . $uri['host'];
        $socket = 'ssl://' . $uri['host'] . ':' . $port; ===> $socket = 'ssl://' . $uri['host'];
        $fp = @stream_socket_client($socket, $errno, $errstr, $options['timeout']); ===> $fp = @fsockopen($socket, $port, $errno, $errstr, $options['timeout']);
        $fp = @stream_socket_client($socket, $errno, $errstr, $options['timeout'], STREAM_CLIENT_CONNECT, $options['context']); ===> $fp = @fsockopen($socket, $port, $errno, $errstr, $options['timeout'], STREAM_CLIENT_CONNECT, $options['context']);
    Change ./modules/system/system.install
        $is_writable = is_writable($directory); ===> $is_writable = TRUE;
        $is_directory = is_dir($directory); ===> $is_directory = TRUE;

Thanks a lot for yuanyeff
* ffbum - http://blog.ykfan.cn/blackhole
  yuanyeff@gmail.com
