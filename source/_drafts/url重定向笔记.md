来源网址www.abc.com
目标网址www.baidu.com

url.redirect = ( "www\.abc\.com" => "www.baidu.com" )

$HTTP["host"] =~ "^www\.abc\.com$" {
  url.redirect = (
    ".*" => "http://www.baidu.com" 
  )
}

我的导航网址:http://360.tiandi.com/?td_2_21264