基于API应用程序接口 jsonp格式 实现编写HTML页面，上传到站点可访问的位置。
--
示例代码如下： 
```html
<!DOCTYPE html>
<html>
<head>
  <title>search</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <meta name="apple-mobile-web-app-capable" content="yes">
  <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
  <meta name="format-detection" content="telephone=no"/>
  <meta http-equiv="X-UA-Compatible" content="edge"/>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css">
  <style>
    html{ background:#fff; }
    body{ width:98%; max-width: 900px; min-height: 490px; background:#fff; margin:0 auto 0; }
    :-moz-any(h1, h2, h3, h4, h5, h5) i.serif{ text-transform: capitalize; }
    #wrapper{ padding:0 1%; position:relative;}
    @media only screen and (max-width: 640px) {
      table{ word-break:break-all;word-wrap:break-word;font-size:12px; }
      .typo table th, .typo table td, .typo-table th, .typo-table td .typo table caption {
        padding: 0.5em;
      }
      #fork{ display:none; }
    }
    .cname {}
    .cname h1{text-align: center;text-transform:Capitalize;}
    .s {padding: 20px 0;}
    .cti {
      color: #006d21;
      font-style: normal;
      word-wrap: break-word;
      line-height: 18px;
      border-collapse: collapse;
      border-spacing: 0
    }
    .media-body strong{font-weight: normal; color: red}
  </style>
</head>
<body>
<div class="cname">
  <h1 id="cname"></h1></div>
<div id="wrapper">
  <div class="s">
    <form role="form" method="get" action="">
      <div class="input-group">
        <input type="text" class="form-control" id="q" name="q" value="" placeholder="关键字...">
        <span class="input-group-btn">
            <button id="go" class="btn btn-primary" type="submit">搜索</button>
          </span>
      </div>
    </form>
  </div>
  <div id="qret"></div>
</div>
</body>

<script type="text/javascript">
  var cname="bookstack电子书";
  var qret = document.getElementById("qret");
  function handleResp(ret) {
    if (ret == null || ret == undefined) return;
    if (ret.result === 0 && typeof ret.data !== 'undefined' && typeof ret.data.items !== 'undefined' && ret.data.items) {
      var html = '';
      var items = ret.data.items;
      var len = items.length;
      for (var i = 0; i < len; i++) {
        if (items[i].link) {
          html += '<div class="media"><div class="media-body">\n' +
              '<h4 class="media-heading"><a href="' + items[i].link + '">' + items[i].title + '</a></h4>\n' +
              '<span class="cti">' + items[i].link + '</span>\n' +
              '<p>' + items[i].description + '</p>\n' +
              '</div></div>';
        }
      }
      qret.innerHTML = html;
    }
  }
  (function () {
    var keyword=document.getElementById('q')
    var url = location.search; //获取url中"?"符后的字串
    var urlget = new Object();
    if (url.indexOf("?") != -1) {
      var str = url.substr(1);
      console.log(str)
      var strs = str.split("&");
      for (var i = 0; i < strs.length; i++) {
        console.log(decodeURIComponent(strs[i].split("=")[1]))
        urlget[strs[i].split("=")[0]] = decodeURIComponent(strs[i].split("=")[1]);
      }
    }
    if(typeof urlget.q!=='undefined' && urlget.q) {
      keyword.value=urlget.q;
      search(urlget.q);
    }
    function search(q) {
        document.getElementById('cname').innerText=cname;  // 名称
        var script = document.createElement("script");
        script.src = "https://www.youbytes.com/api/query?c="+encodeURIComponent(cname)+"&q="+encodeURIComponent(q)+"&f=jsonp&callback=handleResp";
        document.body.insertBefore(script, document.body.firstChild);
    }
  })();
</script>
</html>
```
