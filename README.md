
		<input type="tel" id="valueOfSolarPanelSystem" name="valueOfSolarPanelSystem" pattern="\d*" maxlength="8" value="$!{quoteDataVO.dwellingVO.valueOfSolarPanelSystem}" class="form-control inputTypeTel validate[requiredbr]"/>
		  
		  $(document).on('keypress, paste, input','#valueOfSolarPanelSystem',function(event){
            debugger;
            if($(this).val() != ''){
                debugger;
                parseInt($(this).val())
                console.log("aaaa", this.val())
                if(event.which >= 37 && event.which <= 40) return;
                $(this).val().replace('$','');
                // format number
                $(this).val(function(index, value) {
                    return '$'+ value.replace(/\D/g, "").replace(/\B(?=(\d{3})+(?!\d))/g, ",");
                });
            }
        });
