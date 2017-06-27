#!/bin/sh
set +x
sw="swconfig dev switch0"

wait="";
event="";

while [ true ]; do

p4_st="$($sw port 4 get link | cut -d " " -f 2 | cut -d ":" -f 2)";
p4_dis=$($sw port 4 get disable);
p3_st="$($sw port 3 get link | cut -d " " -f 2 | cut -d ":" -f 2)";
p3_dis=$($sw port 3 get disable);
	ev="$p4_st-$p4_dis;$p3_st-$p3_dis";
	[ "$event" != "$ev" ] && {	
		event=$ev;
		echo $ev;
		[ "$wait" != "" ] && {
			[ "$wait" == "$ev" ] && wait="";
			continue;
		}
		if [ "$p4_st" == "down" ] && [ $p4_dis -eq 0 ] && [ $p3_dis -eq 0 ]; then
			wait="down-0;down-1";
			$sw port 3 set disable 1;
			$sw set apply;
			continue;
		fi
		if [ "$p4_st" == "up" ] && [ $p3_dis -eq 1 ]; then
			wait="up-0;up-0";
			$sw port 3 set disable 0;
			$sw set apply;
			continue;
		fi
		
		if [ "$p3_st" == "down" ] && [ $p3_dis -eq 0 ] && [ $p4_dis -eq 0 ]; then
			wait="down-1;down-0";
			$sw port 4 set disable 1;
			$sw set apply;
			continue;
		fi
		if [ "$p3_st" == "up" ] && [ $p4_dis -eq 1 ]; then
			wait="up-0;up-0";
			$sw port 4 set disable 0;
			$sw set apply;
			continue;
		fi
	}	
done
