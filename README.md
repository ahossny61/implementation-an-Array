// implementation-an-Array
#include<iostream>
#include<string>
using namespace std;
template<class t>
class Array{
private:
	int max_size = 10000, length;
	t*arr;
public:
	Array(int x = 1000)
	{
		max_size = x;
		arr = new t[x];
		length = 0;
	}
	int sort(t item){
		if (length == 0)
			return 0;
		else
		{

			for (int i = 0; i < length; i++){
				if (arr[i]>item)
					return i;
			}
			return length;
		}
	}
	void add(t item){
		int index = sort(item);
		if (index == 0 && length == 0){
			arr[index] = item;
			length++;
		}
		else
		if (max_size == length)
			cout << "full list" << endl;
		else

		if (index == length){
			arr[index] = item;
			length++;
		}
		else{
			for (int i = length; i > index; i--){
				arr[i] = arr[i - 1];
			}
			arr[index] = item;
			length++;
		}

	}
	t Max(){
		if (length == 0){
			cout << "empty list" << endl;
			return 0;
		}
		return arr[length - 1];
	}
	t Min(){
		if (length == 0){
			cout << "empty list" << endl;
			return 0;
		}
		else
		return arr[0];
	}
	void Delete(t item){
		if (length == 0)
			cout << "empty list " << endl;
		else
		if (search(item) == -1)
			cout << "Not found " << endl;
		else{
			int index = search(item);
			for (int i = index; i < length - 1; i++)
				arr[i] = arr[i + 1];
			length--;
		}

	}
	int search(t item){
		if (length == 0){
			cout << "empty list" << endl;
			return -1;
		}
		for (int i = 0; i < length; i++)
		if (arr[i] == item)
			return i;
		return -1;
	}
	bool is_empty(){
		if (length == 0)
			return true;
		else
			return false;

	}
	bool is_full(){
		if (length == max_size)
			return true;
		else
			return false;

	}
	void clear(){
		length = 0;
	}
	void swap(int index1, int index2){
		arr[index1] = arr[index2];
	}
	int Length(){
		return length;
	}
	void print(){
		if (is_empty())
			cout << "empty list" << endl;
		else
		{
			for (int i = 0; i < length; i++)
				cout << arr[i] << " ";
		}
		cout << endl;
	}
	void print_element(int index){
		cout << arr[index] << endl;
}

};
int main(){
	cout << "01010101010101010101010101010110101010101010010101010101010100101010101010101010101010101\n";
		cout<<"0101010101010101010101001    Created By Ahmed Hossny    010101011010101010101010101010101\n\n"<<endl;
	Array<int>arr(5);
	int input; int item; int index;
	do{
		cout << "1>>>to add elements" << endl;
		cout << "2>>>to delete elements" << endl;
		cout << "3>>>to get Max element" << endl;
		cout << "4>>>to get Min element" << endl;
		cout << "5>>>to get length of array" << endl;
		cout << "6 to check if array is empty????" << endl;
		cout << "7 to print an element" << endl;
		cout << "8 to print elements" << endl;
		cout << "0 to exit" << endl;
		cin >> input;
		switch (input){
		case 1:cout << "enter an item " << endl;
			cin >> item;
			arr.add(item);
			break;
		case 2:
			cout << "enter an item " << endl;
			cin >> item;
			arr.Delete(item);
			break;
		case 3:cout << arr.Max() << endl;
			break;
		case 4:cout << arr.Min() << endl;
			break;
		case 5:cout << arr.Length() << endl;
			break;
		case 6:if (arr.is_empty())
			cout << "the array is empty " << endl;
			   else
				   cout << "the array is not empty " << endl;
			break;
		case 7:
			cout << "enter the index " << endl;
			cin >> index;
			arr.print_element(index);
			break;
		case 8:
			arr.print();
			break;
		case 0:cout << "thanks goodbye" << endl;
			exit(0);
		default:
			cout << "invalid input " << endl;
		}
	} while (input != 0);
	system("pause");
	return 0;
}

