
/*Angel Aguilar Salazar y Henrik Axel de la Rosa
2023 oct 13

Ejercicio
Realicen un nuevo codigo con los siguientes requerimientos:
- Creen dos clases padres con sus respectivos metodos y atributos.
- Creen dos clases hijas de esas clases padres.
- En ambas clases padres, definan un metodo con el mismo nombre, pero distinto comportamiento
- En una de las clases hijas hagan una metodo desde el cual se pueda acceder a las funciones con el mismo nombre de las clases padres.
- En la otra clase hija hagan los cambios necesarios para que pueda acceder a ambas funciones (por separado), sin crear conflicto de ambigüedad.
- Definan los destructores para cada clase y revisen que sucede cuando el codigo termina.
*/

#include <bits/stdc++.h>
using namespace std;

class Math{
	public:
		string Found;
	Math(string found){
		Found = found;
						cout<<"Creando objeto Math"<<endl;

	}
	void solve(){
		cout<<"Time to solve math via the "<<this->Found<<endl;;
	}
	~Math(){
		cout<<"Destroying Math"<<endl;
	}
};

class Phil{
	public:
		string Moral;
	Phil(string moral){
		Moral = moral;
						cout<<"Creando objeto Phil"<<endl;

	}
	void solve(){
		cout<<"I must live a correct life via "<<this->Moral<<endl;
	}
	~Phil(){
		cout<<"Destroying Philosophy"<<endl;
	}
	
};

//hija 1
class Sci: public Math, public Phil{
		private:
			string Exper;
		public:
			Sci(string exper, string found, string moral):Math(found), Phil(moral){
			
				Exper=exper;
				cout<<"Creando objeto Sci"<<endl;
		}
	void metodo_Math(){
		cout<<"Activando metodo de clase math de clase hija 1"<<endl;
		Math::solve();
	}
	void metodo_Phil(){
		cout<<"Activando metodo de clase Phil de clase hija 1"<<endl;
		Phil::solve();
	}
	
	~Sci(){
		cout<<"Destroying Science"<<endl;
	}
};

class Comp: public Math, public Phil{
	private:
		string Code;
	public:
		Comp(string code, string found, string moral): Math(found), Phil(moral){
			Code = code;
			cout<<"Creando objeto Comp de clase hija 2"<<endl;

		}
		
	void metodo_Math_y_Phill(){
		cout<<"Activando metodo math y phil de clase hija 2"<<endl;
		cout<<" Creatin code"<<endl;
		Math::solve();
		cout<<endl;
		Phil::solve();
		cout<<" I will create a code that "<<Code<<" based on "<<this->Found<<endl;
	}
	~Comp(){
		cout<<"Destorying computer science"<<endl;
	}
};

int main(){
	Math("Counting");
	Phil("Ethics");
	
	Sci phy = Sci("SternGerlach", "Uncertainty", "NoOneHurt");
	Comp poo = Comp("AnyProgram", "Algebra+Calculus", "NoOneHurt");
	phy.metodo_Math();
	phy.metodo_Phil();
	poo.metodo_Math_y_Phill();
	
	return 0;
}
