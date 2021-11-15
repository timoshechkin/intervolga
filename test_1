<?php

function revertCharacters($str) {
	  $zn_pr_arr = array("!", ".");	//Создаем массив со знаками препинания (можно добавить и другие знаки припинания при необходимости)
	  $substr_arr=explode(" ",$str);	//Разбиваем строку на подстроки по пробелам
	  foreach ($substr_arr as &$substr)	//Перебираем подстроки
	  {
		$symb_arr=preg_split("//u", $substr, -1, PREG_SPLIT_NO_EMPTY);	//Разбиваем подстроку на отдельные символы
		$zn_pr ="";	//Задаем пустую переменную для знака препинания
		$status_upper =false;	//Задаем статус верхнего регистра по умолчанию
		$res_substr = "";	//Задаем начальное значение для посимвольной записи слова
		for($i=(count($symb_arr)-1); $i>=0; $i--) //Перебираем подстроку по символам в обратном порядке
		{
			if(in_array($symb_arr[$i],$zn_pr_arr))
			{
				$zn_pr = $symb_arr[$i];	//Если символ в подстроке является знаком препинания "!" или ".", то сохраняем его в переменную $zn_pr
			}
			else
			{
				$res_substr .= $symb_arr[$i];	//Собираем слово
				if($symb_arr[$i]===mb_strtoupper($symb_arr[$i])) $status_upper=true;	//Если текущий символ в верхнем регистре, для текущего слова присваиваем переменной $status_upper значение true 
			}
		}
		if($status_upper)	//Если слово содержит символ в верхнем регистре, то
		{
			$res_substr=mb_strtolower($res_substr);	//Переводим в нижний регистр всю подстроку
			$res_substr = mb_strtoupper(mb_substr($res_substr,0,1)).mb_substr($res_substr,1);	//Переводим первый символ в верхний регистр
		}
		echo $res_substr.$zn_pr." ";	//Собираем строку
	}
}

$result = revertCharacters("Привет! Давно не виделись.");
echo $result; // Тевирп! Онвад ен ьсиледив.

?>
