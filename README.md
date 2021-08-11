# mywork
package abel;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.Scanner;


public class Text_hb {

	/**
	 * 递归
	 * a[5][3] :  {{q,w,e}，{x,c,v}，{1,2,3}，{4,5,6}，{7,8,9}}
	 * @param args
	 */
	public static void main(String[] args) {
		
		System.out.println("请输入数字，若多个用，隔开：");
		Scanner int_t1 = new Scanner(System.in);
		List<String> tmp_list = new ArrayList<String>();
		String str = int_t1.next().toString();
		String[] arr = str.split(",");
		
		int[] b = new int[arr.length];
		for (int i = 0; i < b.length; i++) {
			b[i] = Integer.parseInt(arr[i]);
			System.out.println(b[i] );
			if(b[i]>0 && b[i]<=9){  //个位数值
				if(1==b[i]){
					tmp_list.add("1");
				}else if(2==b[i]){
					tmp_list.add("A,B,C");
				}else if(3==b[i] ){
					tmp_list.add("D,E,F");
				}else if(4==b[i] ){
					tmp_list.add("G,H,I");
				}else if(5==b[i] ){
					tmp_list.add("J,K,L");
				}else if(6==b[i] ){
					tmp_list.add("M,N,O");
				}else if(7==b[i] ){
					tmp_list.add("P,Q,R,S");
				}else if(8==b[i] ){
					tmp_list.add("T,U,V");
				}else if(9==b[i] ){
					tmp_list.add("W,X,Y,Z");
				}
			}else if(b[i]>11 && b[i]<=99){ //十位数值
				int tt = b[i]%100/10; //十位
				int tt2 = b[i]%10;    //个位
				System.out.println(tt);
				System.out.println(tt2);
				String tt_str1 = dealStr(tt); 
				String tt_str2 = dealStr(tt2); 
				String tt_str3 = tt_str1+","+tt_str2;	
				System.out.println(tt_str3);
				tmp_list.add(tt_str3);
			}else{
				String ss = String.valueOf(b[i]); //0或1
				tmp_list.add(ss);
			}
			
		}
		
		String[] temp_ele = new String[b.length];
		for (int i = 0; i <tmp_list.size(); i++) {
			if(tmp_list.get(i) !=null){
				temp_ele[i] = tmp_list.get(i);
			}
		}
		
		//开始处理
		if(temp_ele.length==1){
			for (int i = 0; i < temp_ele.length; i++) {
				System.out.println(temp_ele[i].replace(',', ' '));
			}
			
		}else{
			BeginDeal(temp_ele);
		}
	}
	

	

	//[A,B,C,D,E,F,	// G,H,I,J,K,L]
	public static String BeginDeal(String[] ele){//[A,B,C   ,     D,E,F]     
		String res = "";
		int len = ele.length;
		String[] ts = ele[1].split(","); //[D, E, F]
		String[][] abc = new String[len][ts.length];//2行3列
		for (int f = 0; f < ele.length; f++) {
			String[] sub = ele[f].split(",");
			System.out.println(f+"--->"+Arrays.toString(sub));
			abc[f] = sub;
		}
		String[][] ret = DealArrays(abc);//处理数据
		String[] result = ret[0];
		System.out.println("共有："+result.length +"种组合");
		
		for (int i = 0; i < result.length; i++) {
			System.out.println(result[i]);
		}
		
		return res;
	}
	
	//组成数组
	public static String[][] DealArrays(String[][] doubleArrays){//[[A, B, C], [D, E, F]]
		int len = doubleArrays.length;
		if(len>=2){
			int len1 = doubleArrays[0].length;
			int len2 = doubleArrays[1].length;
			int newlen = len1*len2;
			System.out.println(len1+"---"+len2+"---"+newlen);
			
			String[] temp = new String[newlen];
			int index = 0;
			for (int i = 0; i < len1; i++) {
				for (int j = 0; j < len2; j++) {
					temp[index] = doubleArrays[0][i] + doubleArrays[1][j] ;
					index ++;
				}
			}
			String[][] newArray = new String[len-1][];
			for (int i = 2; i < len; i++) {
				newArray[i-1] = doubleArrays[i];
			}
			newArray[0] = temp;
			return DealArrays(newArray);
		}else{
			return doubleArrays;
		}
	}
	
	
	
	public static String  dealStr(int tt){
		String s1 = "";
		if(2==tt){
			s1="A,B,C";
		}else if(3==tt ){
			s1="D,E,F";
		}else if(4==tt ){
			s1="G,H,I";
		}else if(5==tt ){
			s1="J,K,L";
		}else if(6==tt ){
			s1="M,N,O";
		}else if(7==tt ){
			s1="P,Q,R,S";
		}else if(8==tt ){
			s1="T,U,V";
		}else if(9==tt ){
			s1="W,X,Y,Z";
		}
		return s1;
	} 
	
	
	
	
	
	
	

}

