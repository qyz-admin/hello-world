# hello-world
// ==UserScript==
// @name         admin-5.1
// @namespace    http://tampermonkey.net/
// @version      5.1
// @description  以客服查詢界面為主
// @author       You
// @match        http://13.229.176.203/admin/index/index.html
// @match        https://goms.giikin.com/admin/index/index.html
// @require      https://libs.baidu.com/jquery/1.9.0/jquery.js
// @require      file://C:\user.js
// @require      file://H:\clipboard.js
// @updateURL    https://github.com/qyz-admin/-/blob/0fb1e98ff0881a2420414bb9467a5f948121b84b/admin-2.0.user.js
// ==/UserScript==https://13.229.176.203/static/admin/js/tabs.js  // @grant        none Tampermonkey
(function() {
var targNode = document.getElementsByClassName("page-header navbar navbar-fixed-top")[0];
    var wxzSearchBarNode = document.createElement('div');
        wxzSearchBarNode.setAttribute('class','header-wxzbar header-info btn-sm');
        wxzSearchBarNode.setAttribute('id','header-nav');
        wxzSearchBarNode.style = "position: absolute;float: left;top: 10px; left: 235px;width:1400px;";//left:235
        wxzSearchBarNode.innerHTML =
      '<input placeholder=" 輸入--（編號）" class="search-button btn-sm" id="wxz_input" type="hidden">\
                   <input type="button" value="开关" class="btn default showcol btn-sm" id="close_searchButton">\
       &nbsp &nbsp\
                                 <input value="GO-客服" class="btn default showcol btn-sm" id="wxcx_searchButton" type="hidden">\
                   <input type="button" value="促单查询" class="btn default showcol btn-sm" id="w_searchButton" >\
                   <input type="button" value="金額查询" class="btn default showcol btn-sm" id="cd_searchButton" >\
                                 <input value="显示/隐藏列" class="btn purple btn-sm" id="wxcd_searchButton" type="hidden">\
                                 <input value="查詢-補發" class="btn default showcol btn-sm" id="wxz_searchButton" type="hidden">&nbsp\
                   <input type="button" value="信息表显示" class="btn green btn-sm" id="xxb_searchButton">\
                   <input type="button" value="open订单窗口" class="btn green btn-sm" id="test_searchButton">\
                                 <input value="信息55" class="btn green btn-sm" id="xxbb_searchButton" type="hidden">\
      &nbsp &nbsp\
                   <input type="button" value="导 出" class="tool-action btn yellow btn-sm" id="save_searchButton">\
                   <input type="button" value="退 货" class="btn yellow-gold btn-sm" id="th_searchButton">\
                   <input type="button" value="换 货" class="btn yellow-gold btn-sm" id="hh_searchButton">\
                   <input type="button" value="补 发" class="btn yellow-gold btn-sm" id="bf_searchButton"> \
                   <input value="点击复制" class="btn green btn-sm" id="fz_searchButton" type="hidden">\
     <input type="button" value="点击复制  退 换 补" class="tool-action btn yellow btn-sm" id="ffz_searchButton">\
     &nbsp  &nbsp  &nbsp &nbsp\
                <select name="djr" id= "djr">\
                    <option value="0">---登记人---</option>\
					<option value="齊元章">齊元章</option>\
					<option value="楊嘉儀">楊嘉儀</option>\
                    <option value="徐文建">徐文建</option>\
                    <option value="李若蘭">李若蘭</option>\
                    <option value="曹  可">曹  可</option>\
                    <option value="曲開拓">曲開拓</option>\
                    <option value="姜甜甜">姜甜甜</option>\
                    <option value="李亞芳">李亞芳</option>\
                    </select>\
                <select name="tigong" id= "tigong">\
                    <option value="運費0">-----備註-----</option>\
					<option value="運費300">運費300</option>\
					<option value="運費99">運費99</option>\
                    <option value="運費一半">退一半不取件</option>\
                    </select>\
                <select name="thvalue" id= "thvalue">\
                    <option value="">-----------退貨原因-----------</option>\
					<option value="與產品網頁不符">與產品網頁不符</option>\
					<option value="质量差">质量差</option>\
                    <option value="大小不合适">大小不合适</option>\
                    <option value="未订购">未订购</option>\
                    <option value="非正品要求退貨">非正品要求退貨</option>\
                    <option value="不适用，不喜欢，不想要">不适用，不喜欢，不想要</option>\
                    <option value="商品有瑕疵，損壞">商品有瑕疵，損壞</option>\
                    <option value="到货不能使用">到货不能使用</option>\
                    <option value="品質不符預期">品質不符預期</option>\
                    <option value="问题件">问题件</option>\
                    <option value="发错商品，少发">发错商品，少发</option>\
                    </select>\
            <select name="hhvalue" id= "hhvalue">\
                     <option value="">-------------------換貨原因------------------</option>\
					 <option value="换大，仓库发错">换大，仓库发错</option>\
					 <option value="换小，仓库发错">换小，仓库发错</option>\
                     <option value="换颜色，仓库发错">换颜色，仓库发错</option>\
                     <option value="换大，客户自己选错">换大，客户自己选错</option>\
                     <option value="换小，客户自己选错">换小，客户自己选错</option>\
                     <option value="换大，产品尺码不正常">换大，产品尺码不正常</option>\
                     <option value="换小，产品尺码不正常">换小，产品尺码不正常</option>\
                     <option value="换颜色，产品颜色与网站不符">换颜色，产品颜色与网站不符</option>\
                     <option value="发错，换新，客户自己选错">发错，换新，客户自己选错</option>\
                    <option value="发错，换新，仓库发错">发错，换新，仓库发错</option>\
                    <option value="瑕疵，换新">瑕疵，换新</option>\
                    <option value="损坏，换新">损坏，换新</option>\
                    <option value="到货不满意，与网站不符，换新">到货不满意，与网站不符，换新</option>\
                    <option value="換產品補差價，产品不满意">換產品補差價，产品不满意</option>\
                    <option value="換產品補差價，与网站不符">換產品補差價，与网站不符</option>\
                    <option value="發錯貨，二次換貨，仓库发错">發錯貨，二次換貨，仓库发错</option>\
                    <option value="發錯貨，二次換貨，客户自己提供错">發錯貨，二次換貨，客户自己提供错</option>\
                    <option value="换产品">换产品</option>\
                    <option value="無法使用，換新">無法使用，換新</option>\
                    </select>\;'
      targNode.appendChild(wxzSearchBarNode);
    //targNode.insertBefore(wxzSearchBarNode,oldNode); style = "position: relative; float: right;"
  };
  
  })();
