
// Message Count
function miso_response_check() {

	var $labels = $('.msgLabel');
	var $counts = $('.msgCount');
	var url = g5_url + '/thema/' + is_miso_thema + '/widget/response.php?count=1';

	$.get(url, function(data) {
		if (data.count > 0) {
			$counts.text(number_format(data.count));
			$labels.show();
		} else {
			$labels.hide();
		}
	}, "json");
}

// Time = 1000ms ex) 10sec = 10 * 1000
if(g5_is_member && is_response_time > 0) {
	var is_response_check = is_response_time * 1000;
	var misoResponse = setInterval(function() {
		miso_response_check();
	}, is_response_check);
}

// Today View
function miso_shop(opt) {
	var url;
	
	url = g5_url + '/thema/' + is_miso_thema + '/widget/';

	if(opt == 'cart') {
		url = url + 'cart.php';
		$('#cartViewList').load(url);
	} else if(opt == 'today') {
		url = url + 'today.php';
		$('#todayViewList').load(url);
	} else if(opt == 'tdel') {
		url = url + 'today.php?del=1';
		$('#todayViewList').load(url);
		$('.todayLabel').hide();
	}
}

// Message List
function miso_msg() {

	var sidebar = $('.control-sidebar');

	if(!sidebar.hasClass('control-sidebar-open')) {
		var url = g5_url + '/thema/' + is_miso_thema + '/widget/response.php';
		$('#sidebarList').load(url);
	}
}

// More
function miso_more(id){
	var more = $('#' + id + ' .nav .active a');
	var href = more.attr("ref");
	if(href) {
		document.location.href = href;
	}
	return false;
}

function miso_sidelogin_form(f) {
	if (f.mb_id.value == '') {
		alert('아이디를 입력해 주세요.');
		f.mb_id.focus();
		return false;
	}
	if (f.mb_password.value == '') {
		alert('비밀번호를 입력해 주세요.');
		f.mb_password.focus();
		return false;
	}
	return true;
}

function tsearch_submit(f) {

	if (f.stx.value.length < 2) {
		alert("검색어는 두글자 이상 입력하십시오.");
		f.stx.select();
		f.stx.focus();
		return false;
	}

	f.action = f.url.value;

	return true;
}

$(document).ready(function() {

	$(window).scroll(function(){
		if ($(this).scrollTop() > 250) {
			$('#go-btn').fadeIn();
		} else {
			$('#go-btn').fadeOut();
		}
	});

	$('.go-top').on('click', function () {
		$('html, body').animate({ scrollTop: '0px' }, 500);
		return false;
	});

	$('.go-bottom').on('click', function () {
		$('html, body').animate({ scrollTop: $(document).height() }, 500);
		return false;
	});

	$('.navbar-custom-menu .dropdown-menu').on({
		"click":function(e){
		  e.stopPropagation();
		}
	});

	$('.cart-view').on('click', function(e) {
	    e.stopPropagation();
		var _this = $('#cart-view');
		if(_this.hasClass('open')) {
			_this.removeClass('open');
		} else {
			$('.navbar-custom-menu .dropdown').removeClass('open');
			miso_shop('cart');
			_this.addClass('open');
		}
	});

	$('.today-view').on('click', function(e) {
	    e.stopPropagation();
		var _this = $('#today-view');
		if(_this.hasClass('open')) {
			_this.removeClass('open');
		} else {
			$('.navbar-custom-menu .dropdown').removeClass('open');
			miso_shop('today');
			_this.addClass('open');
		}
	});

	// Tab Swipe
	$(".swipe-tab").swiperight(function(e) {
		e.preventDefault();
		var tab_id = $(this).attr("id");
		var $tab = $('#' + tab_id + ' .nav .active').prev();
		if ($tab.length > 0) {
			e.preventDefault()
			$tab.find('a').tab('show');
		}
		return false;
	});

	$(".swipe-tab").swipeleft(function(e) {
		e.preventDefault();
		var tab_id = $(this).attr("id");
		var $tab = $('#' + tab_id + ' .nav .active').next();
		if ($tab.length > 0) {
			$tab.find('a').tab('show');
		}
		return false;
	});

	// SubMenu Toggles
	$('.submenu-toggle').on('click', function () {
		var _this = $(this).parents('.dropdown-submenu').find('.dropdown-menu-sub');

		$('.dropdown-submenu').removeClass('sub-on').addClass('sub-off');

		if(_this.is(":visible")){
			_this.hide();
		} else {
			$('.dropdown-menu-sub').hide();
			$(this).parents('.dropdown-submenu').removeClass('sub-off').addClass('sub-on');
			_this.show();
		}

		return false;
	});

});