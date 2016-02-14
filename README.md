# url_helper
Codeigniter Turkish Url Title Helper


```sh
	function url_title($str, $separator = '-', $lowercase = TRUE)
	{
		if ($separator == 'dash') 
		{
		    $separator = '-';
		}
		else if ($separator == 'underscore')
		{
		    $separator = '_';
		}
		
		$q_separator = preg_quote($separator);

		$trans = array(
                    '&.+?;' => '',
                    '[^a-z0-9 _-]' => '',
                    '\s+' => $separator,
                    '(' . $q_separator . ')+' => $separator
                );

                $search_tr = array('ı', 'İ', 'Ğ', 'ğ', 'Ü', 'ü', 'Ş', 'ş', 'Ö', 'ö', 'Ç', 'ç');
                $replace_tr = array('i', 'I', 'G', 'g', 'U', 'u', 'S', 's', 'O', 'o', 'C', 'c');
                $str = str_replace($search_tr, $replace_tr, $str);
                $str = strip_tags($str);

		foreach ($trans as $key => $val)
		{
			$str = preg_replace("#".$key."#i", $val, $str);
		}

		if ($lowercase === TRUE)
		{
			$str = strtolower($str);
		}

		return trim($str, $separator);
	}


```