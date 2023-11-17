/*Angel Aguilar y Axel Roa
2023 oct 4

Ejercicio:
Realizar un programa de libre eleccion relativo a POO con las siguientes caracteristicas:
- Que cuente con una clase abstracta.
- Que cuente con por lo menos un par de clases que hereden de la clase abstracta (para ello deben implementar su metodo).
- A su vez, las clases anteriores deben tener por lo menos un par de clases hijas cada una.
- Las clases padres (salvo la abstracta, que obviamente no puede instanciarse), deben contener por lo menos 5 atributos y 2 metodos respectivamente.
- Las clases hijas deben tener por lo menos 2 atributos extras a sus padres y 2 metodos unicos respectivamente.
- Generar los getters y setters de cada clase.
- Generar un metodo no miembro que pueda acceder a informacion de alguna de las clases hijas.
- Crear un objeto de cada clase y probar sus constructores. Pueden generar constructores por default con valores preestablecidos (como en el ejemplo del codigo).
- Para cada clase, prueben sus respectivos objetos.
- Con respecto a las funciones de las clases padres, apliquen un ejemplo de polimorfismo para cada una de sus clases hijas (importante usar punteros y virtual).
Notas:
- Realizarlo en una rama nueva de su repositorio.
- Como siempre, cumplir con los lineamientos de escritura de codigo.

codigo tomado de:
*/
#include <iostream>
#include <string>
using namespace std;
// Clase abstracta
class Animal {
    virtual void hacerSonido() = 0; // Método abstracto
};

// Clase derivada de Animal
class Perro : Animal {
	
public:
    //5 atributos
	string name;
	string breed;
	int age;
	string purp; //why have the animal
	bool own; //is it wild or a pet? cambia a bool
	
	
	//constructor
	Perro(string name, string breed, int age, string purp, bool own){
        this->name = name;
        this->breed=breed;
        this->age=age;
        this->purp=purp;
        this->own=own;
    } //constructor

    // Getters y Setters
    void SetName(string name){
        this->name = name;
    }
    string getName(){
        return name;
    }

    void setBreed(string breed){
        this->breed = breed;
    }
    string getBreed(){
        return breed;
    }

    void setAge(int age){
        this->age = age;
    }
    int getAge(){
        return age;
    }
    
    void setPurp(string purp){
        this->purp = purp;
    }
    string getPurp(){
        return purp;
    }
    
    void setOwn(bool own){
        this->own = own;
    }
    bool getOwn(){
        return own;
    }
	//getters y setters
	
	//implementacion de metodo abstracto
    void hacerSonido(){
        cout << "El perro " << getName() << " hace un ladrido." <<endl;
    }

    // Métodos únicos
    void perseguirCola() {
        cout << getName() << " persigue su cola." <<endl;
    }

    void ladrarAlVecino() {
        cout << getName() << " ladra al vecino." <<endl;
    }
    
    //polimorfismo
    virtual void wild(){ // Al hacerla virtual, obligamos a que las hijas hagan una implementacion del metodo wild() para aplciar polimorfismo,
                    // De lo contrario, se usa la implementacion del padre.
                    
        cout<<"por favor revisa si es un animal salvaje."<<endl;
    }
    
};

// segunda Clase derivada de Animal
class Gato : Animal {
	
public:
    //5 atributos
	string name;
	string breed;
	int age;
	string purp; //why have the animal
	bool own;
	
public:
	//constructor
	Gato(string name, string breed, int age, string purp, bool own){
        this->name = name;
        this->breed=breed;
        this->age=age;
        this->purp=purp;
        this->own=own;
    } //constructor

    // Getters y Setters
    void SetName(string name){
        this->name = name;
    }
    string getName(){
        return name;
    }

    void setBreed(string breed){
        this->breed = breed;
    }
    string getBreed(){
        return breed;
    }

    void setAge(int age){
        this->age = age;
    }
    int getAge(){
        return age;
    }
    
    void setPurp(string purp){
        this->purp = purp;
    }
    string getPurp(){
        return purp;
    }
    
    void setOwn(bool own){
        this->own=own;
    }
    bool getOwn(){
        return own;
    }
	//implementacion de metodo abstracto
    void hacerSonido(){
        cout << "El gato " << getName() << " hace un maullido." <<endl;
    }

    // Métodos únicos
    void vomita() {
        cout << getName() << " vomita despues de lamerse" <<endl;
    }

    void rasgunar() {
        cout << getName() << " rasguna los muebles." <<endl;
    }
    
    //polimorfismo
    virtual void wild(){ // Al hacerla virtual, obligamos a que las hijas hagan una implementacion del metodo wild() para aplciar polimorfismo,
                    // De lo contrario, se usa la implementacion del padre.
                    
        cout<<"por favor revisa si es un animal salvaje."<<endl;
    }
    
};

//CLASES HIJAS, deben tener por lo menos 2 atributos extras a sus padres y 2 metodos unicos respectivamente.

class Pup1: public Perro{
	//atributos extras
	private:
		string sexo;
		string add;
	
	public:	
	// Constructor de la clase hija
    Pup1(string name, string breed, int age, string purp, bool own, string sexo, string add)
        :Perro(name, breed, age, purp, own){  // Aprovecha el constructor del padre.
            this->sexo = sexo;    // Solo define el ultimo atributo que le faltaba (el propio)
            this->add = add;
        }
    
	//metodo 1    
    void comer(){
    	cout<<name<<" es de sexo "<<sexo<<" y come saludable."<<endl;
	}
	
	//metodo 2
	void sleep(){
		cout<<name<<" tiene "<<age<<" de edad y duerme mucho."<<endl;
	}
	
	//polimorfismo
	/*
	// Nueva funcion
    virtual void trabajar(){ // Al hacerla virtual, obligamos a que las hijas hagan una implementacion del metodo trabajar() para aplciar polimorfismo,
                    // De lo contrario, se usa la implementacion del padre.
        cout << "Trabajando... Atendiendo pendientes, revisando agenda..." << endl;
    }
	*/
	void wild(){
        if(own == true)
        	cout<<"Este animal es parte de una familia y vive en "<<add<<endl;
        else
        	cout<<"Es un animal salvaje."<<endl;
    }
};

class Pup2: public Perro{
	//atributos extras
	private:
		string sexo;
		string add;
	
	public:	
	// Constructor de la clase hija
    Pup2(string name, string breed, int age, string purp, bool own, string sexo, string add)
        :Perro(name, breed, age, purp, own){  // Aprovecha el constructor del padre.
            this->sexo = sexo;    // Solo define el ultimo atributo que le faltaba (el propio)
            this->add = add;
        }
    
	//metodo 1    
    void comer(){
    	cout<<name<<" es de sexo "<<sexo<<" y come saludable."<<endl;
	}
	
	//metodo 2
	void sleep(){
		cout<<name<<" tiene "<<age<<" de edad y duerme mucho."<<endl;
	}
	
	//polimorfismo
	/*
	// Nueva funcion
    virtual void trabajar(){ // Al hacerla virtual, obligamos a que las hijas hagan una implementacion del metodo trabajar() para aplciar polimorfismo,
                    // De lo contrario, se usa la implementacion del padre.
        cout << "Trabajando... Atendiendo pendientes, revisando agenda..." << endl;
    }
	*/
	void wild(){
        if(own == true)
        	cout<<"Este animal es parte de una familia y vive en "<<add<<endl;
        else
        	cout<<"Es un animal salvaje."<<endl;
    }
};

class Kit1: public Gato{
	//atributos extras
	private:
		bool cute;
		string add;
	public:
	// Constructor de la clase hija
    Kit1(string name, string breed, int age, string purp, bool own, bool cute, string add)
        :Gato(name, breed, age, purp, own){  // Aprovecha el constructor del padre.
            this->cute = cute;    // Solo define el ultimo atributo que le faltaba (el propio)
            this->add = add;
        }
        
       //metodo 1    
    void saltar(){
    	cout<<name<<" es de tipo "<<breed<<" y puede saltar muy alto."<<endl;
	}
	
	//metodo 2
	void lindo(){
		if(cute==true){
			cout<<name<<" es un gato lindo. "<<endl;
		} else{
			cout<<name<<" no es un gato lindo. "<<endl;
		}
	}
	
	//polimorfismo
	void wild(){
        if(own == true)
        	cout<<"Este animal es parte de una familia y vive en "<<add<<endl;
        else
        	cout<<"Es un animal salvaje."<<endl;
    }
};
//
class Kit2: public Gato{
	//atributos extras
	private:
		bool cute;
		string add;
	public:
	// Constructor de la clase hija
    Kit2(string name, string breed, int age, string purp, bool own, bool cute, string add)
        :Gato(name, breed, age, purp, own){  // Aprovecha el constructor del padre.
            this->cute = cute;    // Solo define el ultimo atributo que le faltaba (el propio)
            this->add = add;
        }
        
       //metodo 1    
    void saltar(){
    	cout<<name<<" es de tipo "<<breed<<" y puede saltar muy alto."<<endl;
	}
	
	//metodo 2
	void lindo(){
		if(cute==true){
			cout<<name<<" es un gato lindo. "<<endl;
		} else{
			cout<<name<<" no es un gato lindo. "<<endl;
		}
	}
	
	//polimorfismo
	void wild(){
        if(own == true)
        	cout<<"Este animal es parte de una familia y vive en "<<add<<endl;
        else
        	cout<<"Es un animal salvaje."<<endl;
    }
};

// Función no miembro que accede a información de una clase hija
//void mostrarInformacionAnimal(Perro& perro) {
//    cout << "Nombre: " << perro.getName() <<endl;
//    cout << "Edad: " << perro.getAge() << " años" << endl;
//}

void mostrarInformacionAnimal(Perro* perro) {
    cout << "Nombre: " << perro->getName() <<endl;
    cout << "Edad: " << perro->getAge() << " años" << endl;
}
//
//void mostrarInformacionAnimal2(Gato& gato) {
//    cout << "Nombre: " << gato->getName <<endl;
//    cout << "Edad: " << gato->getAge() << " años" << endl;
//}

int main() {
    // Crear objetos de cada clase
    
    //clases padre
    Perro perro1 = Perro("Fido", "husky", 3, "therapy", true);
//    Gato gato1 = Gato("Help", "meh", 3, "help", true);
    //clases hijas
    Pup1 cacho1 = Pup1("Puppy1", "goldenRetriever", 2, "Pet", false, "Macho", "Hospital1");
//    Pup2 cacho2 = Pup2("Puppy2", "cockerSpaniel", 3, "NONE", false, "Hembre", "NONE");
//    Kit1 gati1 = Ki1("Snowball", "bengall tiger", 3, "Service", false, true, "hom3");
//    Kit2 gati2 = Kit2("Zodiac", "tiger", 9, "NONE", true, flase, "NONE");

//
//    // Usar la función no miembro para mostrar información
    mostrarInformacionAnimal(&perro1);
//    mostrarInformacionAnimal2(perro2);
    perro1.wild();
    cacho1.wild();
//    mostrarInformacionAnimal2(&gato1);
//    gato1.wild();
//    gati1.wild();

    return 0;
}

//#include<bits/stdc++.h>
//using namespace std;
//
////clase abstracta
//class Hombre{
//    virtual void obtenerAumento() = 0; // Funcion virtual, debe ser implementada por quien desea utilizarla.
//    virtual void generacion()=0;
//};
////clase padre 1
//class Gen1:Hombre{
//	//5 atributos y 2 metodos respectivamente.
//	private:
//		string Nombre;
//		string Familia;
//		int Edad;
//		string Trabajo;
//		string Matrimonio;
//		
//	//metodo 1
//	public:
//		void quien(){
//		cout << "Nombre: " << Nombre << endl;
//        cout << "Es de la " << Familia <<" family "<< endl;
//        cout << "Edad: " << Edad << endl;
//		}
//		
//    //metodo 2
//    public:
//    	void status(){
//    		cout<<"Estado de matrimonio: "<<Matrimonio<<endl;
//    		cout<<"Trabajo como: "<<Trabajo<<endl;
//		}
//		
//	Gen1(string nombre, string familia, int edad, string trabajo, string matrimonio){
//        Nombre = nombre;
//        Familia = familia;
//        Edad = edad;
//        Trabajo = trabajo;
//        Matrimonio = matrimonio;
//    }
//		
//	//getters y setters
//	//edad, nombre, trabajo, matrimonio, generacion
//	//nombre
//	void setNombre(string nombre){
//        Nombre=nombre;
//    }
//
//    string getNombre(){
//        return Nombre;
//    }
//    
//    //edad
//    void setEdad(int edad){
//        Edad = edad;
//    }
//
//    int getEdad(){
//        return Edad;
//    }
//    
//    //trabajo
//    void setTrabajo(string trabajo){
//        Trabajo = trabajo;
//    }
//
//    int getTrabajo(){
//        return Trabajo;
//    }
//	
//	//matrimonio
//	void setMatrimonio(string matrimonio){
//        Matrimonio=matrimonio;
//    }
//
//    string getMatrimonio(){
//        return Matrimonio;
//    }
//    
//    //generacion
//    void setFamilia(string familia){
//    	this->Familia=familia;
//    }
//
//    string getFamilia(){
//        return Familia;
//    }
//    
//    // Implementacion del metodo de la clase abstracta
//    void generacion(){
//        if(edad>=100){
//        	cout<<"Es de la primera generacion de la familia "<<Familia;
//		}
//		else if(edad>=80&&edad<100){
//        	cout<<"Es de la SEGUNDA generacion de la familia "<<Familia;
//		}
//		else if(edad>=60&&edad<80){
//        	cout<<"Es de la TERCERA generacion de la familia "<<Familia;
//		}
//		else if(edad>=40&&edad<60){
//        	cout<<"Es de la CUARTA generacion de la familia "<<Familia;
//		}
//    }
//	
//};
//
////clase padre 2
//
////clase hija 1.1
//
////clase hija 1.2
//
////clase hija 2.1
//
////clase hija 2.2
//int main(){
//	
//}

