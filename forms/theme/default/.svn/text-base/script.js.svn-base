$.fn.randomize = function(selector){
    (selector ? this.find(selector) : this).parent().each(function(){
        $(this).children(selector).sort(function(){
            return Math.random() - 0.5;
        }).detach().appendTo(this);
    });
    return this;
};

function checkForm()
{
	var errorCount = 0;
	$( ".required" ).each(function( index ) {
		if ( $( this ).val() == null || $( this ).val().length == 0)
		{
			if ( $( this ).css("display") != "none" || $( this ).attr('type') == "hidden" )
			{
				$( this ).parent().css( "background-color","#FF1B00" );
				$( this ).parent().css( "color","white" );
				errorCount++;
			}
		}
		else
		{
			$( this ).parent().css( "background-color","white" );
			$( this ).parent().css( "color","black" );
		}
	});
	$( "ul.required-radio" ).each(function( index ) {
		if ($(this).val() == "checked")
		{
			$( this ).css( "background-color","white" );
			$( this ).css( "color","black" );
		}
		else
		{
			if ( $( this ).css("display") != "none" )
			{
				$( this ).css( "background-color","#FF1B00" );
				$( this ).css( "color","white" );
				errorCount++;
			}
		}
	});
	if (errorCount == 0)
	{
		return true;
	}
	$("#submitBlockId").css( "border","3px solid red" );
	return false;
}
$( document ).ready(function() {
	$( "form" ).submit(function(event) {
		return checkForm();
	});

	$( "form" ).click(function(event) {
		if ($("#submitBlockId").css( "border-color") == "rgb(255, 0, 0)")
		{
			checkForm();
		}
	});

	$('form').trigger("reset");

	$( "ul.required-radio" ).click(function(e) {
		$(this).val("checked");
	});

	$( "ul.required-radio" ).click(function(e) {
		if ( $( this ).find( "input[type=radio]:checked" ).val() == "other" || $( this ).find( "input[type=checkbox][value=other]:checked" ).val() == "other")
			$( this ).find( "textarea" ).css( "display","inline" );
		else
			$( this ).find( "textarea" ).css( "display","none" );

	});

	$( "div.rsw-picker" ).click(function(e) {
		var selectedIndex = -1;
		$( this ).find( "div.rsw-picker-stars" ).find("div").each(function(i, o){
			if (o == e.target)
			{
				selectedIndex = i;
			}
		});
		if (selectedIndex >= 0)
		{
			$( this ).find( "div.rsw-picker-stars" ).find("div").each(function(i, o){
				if (selectedIndex < i)
				{
					$(this).attr('class',"rsw-unstarred");
				}
				else
				{
					$(this).attr('class',"rsw-starred");
				}
			});
			var feedBack = "";
			switch (selectedIndex)
			{
				case 0:feedBack = "Ужасно";break;
				case 1:feedBack = "Плохо";break;
				case 2:feedBack = "Неплохо";break;
				case 3:feedBack = "Хорошо";break;
				case 4:feedBack = "Отлично";break;
			}
			$( this ).find( "input.rsw-picker-message-number" ).val(selectedIndex+1);
			$( this ).find( "input.rsw-picker-message-number" ).trigger( "change" );
			$( this ).find( "input.rsw-picker-message" ).val( feedBack);
		}
	});
});