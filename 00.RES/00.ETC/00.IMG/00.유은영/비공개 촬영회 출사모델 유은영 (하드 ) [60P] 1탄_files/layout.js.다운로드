
// Layout
function miso_content_height() {

	var hmain = $('#at-main').height();
	var hleft = 0;
	var hright = 0;
	if ($("#at-left").length > 0 ) {
		hleft = $('#at-left').height();
	}
	if ($("#at-right").length > 0 ) {
		hright = $('#at-right').height();
	}

	if(hleft > hmain) {
		hmain = hleft;
	}

	if(hright > hmain) {
		hmain = hright;
	}

	$("#at-wrap").css('min-height', hmain);
}

$(document).ready(function() {

	miso_content_height();

	$(window).resize(function(){
		miso_content_height();
	});

	$(".sidebar-toggle").on('click', function(){
		setTimeout(function(){ miso_content_height(); }, 500);
	});

	$(".main-sidebar").on('hover', function(){
		setTimeout(function(){ 
			$(".sidebar-expanded-on-hover .main-sidebar").mouseover(function() { 
				miso_content_height();
			}).mouseout(function() { 
				setTimeout(function(){ miso_content_height(); }, 500);
			});
		}, 500);
	});
});