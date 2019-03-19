# -STL-stl-
Итератора STL. Обучение С++
#include<iostream>
#include<vector>
using namespace std;
int main()
{
	setlocale(LC_ALL, "ru");

	vector<int> myVector = { 0,22,78,99,101,55,17 }; 
	cout << myVector[1] << endl;
	vector<int>::iterator it;//it-это итератор, а vector<int>::iterator - это тип данных итератора
	//сейчас этот ит. ничего нет, чтб ыего использовать, н. его свзязать с вектором
	it = myVector.begin();//присваиваем рез-т работы нашего вестора с помощью begin
	//и нашему ит. предоставлен доступ к 1му эл-ту вектора(как указателю)
	//т е мы получили доступ к 1му элемент уколлекции

	cout << *it << endl;//получаем данные рез-т 0
	//если ит. неконстантный, и мы можем получить через него доступ к данным,
	//значит мы можем их изменить
	*it = 1000;
	cout << *it << endl;//по тому адресу памяти. где хранился 0, будет помещено число 1000


	it++;//это означает перейти на следующий эл-т коллекции
	cout << *it << endl;//22
	it += 2;//сдвинули на 2 элемента
	cout << *it << endl;//99
	it --;//на минус один элемент
	cout << *it << endl;//78


	//чтобы создать условие прекращения цикла, воспольз-ся методом end(),
	//который возвращает ит., указывающий на следующий элемент, который идет
	//после последнего эл-та контейнера, т е указыв-й вникуда, т к такого эл-та не существует 

	
	for (vector<int>::iterator i= myVector.begin(); i !=myVector.end(); i++)
		//мы создае ит., присваиваем ему адрес 1го эл-та в коллекции
		//т е i= myVector.begin(). Условие: пока ит. не равен результату работы метода end()
		//т е пока ит. не попадет в точку, где последний эл-т после последнего эл-та контейнера
		//цикл б. работать
	{
		cout << *i << endl; 
	}



	//чтобы нельзя б. изменять данные, надо использовать константный ит.
	//синтаксис vector<int>::const_iterator i . Данные уже не поменяешь!!
	for (vector<int>::const_iterator i = myVector.cbegin(); i != myVector.cend(); i++)
	{
		/**i = 55;так нельзя сделать*/
		cout << *i << endl;
	}
	//myVector.begin() метод этот возвращает обычный ит., но здесь работает даже
	//с константным, работает благодаря наследованию и полиморфизму, т е м. use begin()
	//здесь мы применили спец-е методы для работы с константными ит - cbegin() cend()






	//////////////////////////////мы можем итерироваться не только с начала коллекци,
	//но и с конца!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
	//для это используем не обычный ит. а reverse_iterator, и метод rbegin()  rend()

	for (vector<int>::reverse_iterator i = myVector.rbegin(); i != myVector.rend(); i++)
	//при методе rbegin() доступ б. не к 1му эл-ту, а к последнему у вектора,
		//rend()б. указывать перед самым первым элементом
	{
		cout << *i << endl;
	}


	return 0;
}

#include<vector>
int main()
{
	setlocale(LC_ALL, "ru");

	vector<int> myVector = { 0,22,78,99,101,55,17 };
	/*vector<int>::iterator it = myVector.begin();*/


	for (vector<int>::iterator i = myVector.begin(); i != myVector.end(); i++)
			{
				cout << *i << endl; 
			}
	cout << "insert()"<<endl << endl;//добавляет эл-т в начало
	vector<int>::iterator it = myVector.begin();
	//мы взяли значение myVector.begin(); т е первый элемент и 
	myVector.insert(it, 999);//добавили в него 999, потому число встало в начало


	for (vector<int>::iterator i = myVector.begin(); i != myVector.end(); i++)
	{
		cout << *i << endl;
	}


	cout << "/////////////////////////////////////////////////////////////////////" << endl;
	//мы можем указать, куда поставить нужное число
	//vector<int>::iterator it = myVector.begin();
	//it++;//во второй эл-т поставить 999
	//advance(it, 5);//т е в пятый эл-т поставить 999
	//myVector.insert(it, 999);//добавили в него 999


	//for (vector<int>::iterator i = myVector.begin(); i != myVector.end(); i++)
	//{
	//	cout << *i << endl;
	//}

	cout << "/////////////////////////////////////////////////////////////////////" << endl;
	cout << "erase()" << endl << endl;//тот эл-т, на который указывает ит. будет удален из коллекции
	vector<int>::iterator itErase = myVector.begin();
	myVector.erase(itErase);

	//удалился первый элемент

	for (vector<int>::iterator i = myVector.begin(); i != myVector.end(); i++)
	{
		cout << *i << endl;
	}

	cout << "/////////////////////////////////////////////////////////////////////" << endl;
	//если erase куда-ниб сдвинуть, то удалится нужный эл-т
	/*vector<int>::iterator itErase = myVector.begin();*/
	/*it++;*/
	 
	myVector.erase(itErase);
	myVector.erase(itErase,itErase+3);//можно удалить диапозон элементов с нулевого по третий
	for (vector<int>::iterator i = myVector.begin(); i != myVector.end(); i++)
	{
		cout << *i << endl;
	}



	cout << "/////////////////////////////////////////////////////////////////////" << endl;
	//cout << *(it+3) << endl;//не всегда м. сдвинут ьна несколько эл-в с помощью ит., 
	////эту проблему решает advance
	//advance(it,3);//1й парам. это ит., второй - кол-во шагов, на которое сдвигаем
	//cout << *it << endl;

	return 0;
}
