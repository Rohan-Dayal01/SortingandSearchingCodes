# SortingandSearchingCodes
Java Array sort and search methods
import java.util.Scanner;
public class sortingandsearchingpractice {
public static void main(String[]args){
	Scanner rod = new Scanner(System.in);
	int[] x = new int[100];
	for(int a=0;a<x.length;a++){
		x[a] = (int)(Math.random()*100);
	}
	for(int e:x){
		System.out.print(e + " ");
	}
	System.out.println();
	//selectionsort(x);
	insertion(x);
	for(int a:x){
		System.out.print(a + " ");
	}
	System.out.println();
	System.out.println("What number would you like to search for?");
	int key = rod.nextInt();
	int index = binSearch(x,key);
	if(index==-1){
		System.out.println(key + " does not occur in the array.");
	}
	else
		System.out.println(key + " occurs in position " + index + " in the array.");
}
static void selectionsort(int[]array){		// iterations = n*(n-1)/2
	int min = array[0];
	for(int x=0;x<array.length;x++){
		int position = x;
		min = array[x];
		for(int a = x+1;a<array.length;a++){
			if(array[a]<min){
				position = a;
				min = array[a];
			}
		}
		int temp = array[x];
		array[x] = array[position];
		array[position] = temp;
	}
}
static int binSearch(int[]array, int key){		
	insertion(array);			
	int start = 0;
	int end = array.length-1;
	while(start<=end){
		int middle = (start+end)/2;
		if(key==array[middle])
			return middle;
		else if(key<array[middle]){
			end = middle-1;
		}
		else if(key>array[middle]){
			start = middle+1;
		}
	}
	return -1;
}
static void insertion(int[]array){			//best case n-1 iterations
	for(int x=1;x<array.length;x++){		//worst case n(n+1)/2 iterations
		for(int z=x;z>0;z--){
			if(array[z]<array[z-1]){
				int temp = array[z-1];
				array[z-1] = array[z];
				array[z] = temp;
			}
		}
	}
}
}


