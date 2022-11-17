#include<stdio.h>
#include<stdlib.h>
#include<conio.h>

typedef struct {
	char nombre[20];
	char apellido[20];
	char sexo[10];
	int cedula;
}elemento;

typedef struct nodo{
	elemento dato;
	nodo *sgt;
}nodo;

void agregar(nodo *&,elemento);
void sacar(nodo *&);
void mostrar(nodo *);
void registro(nodo *&);

main (){
	nodo *raiz=NULL;
	elemento dato;
	int opc;
	bool sw=true;
	while(sw==true){
		printf("\n\tMENU\n");
		printf("\nIngrese la opcion que desea.\n");
		printf("\n1-Agregar Persona.\n");
		printf("\n2-Sacar Persona.\n");
		printf("\n3-Mostrar Persona.\n");
		printf("\n4-Crear Registro.\n");
		printf("\n5-Salir.\n");
		printf("\nMARQUE UNA OPCION:   ");
		scanf("%d",&opc);
		switch(opc){
			case 1:
				system("cls");
				printf("\nNombre:  ");
				scanf("%s",&(dato.nombre));
				printf("\nApellido:  ");
				scanf("%s",&(dato.apellido));
				printf("\nSexo:  ");
				scanf("%s",&(dato.sexo));
				printf("\nNro de Cedula:  ");
				scanf("%s",&(dato.cedula));
				agregar(raiz,dato);
				break;
			case 2:
				system("cls");
				sacar(raiz);
				break;
			case 3:
				mostrar(raiz);
				break;
			case 4:
				registro(raiz);
				break;
			case 5:
				system("cls");
				printf("\n\t\tPrograma Cerrado...");
				sw=false;
				break;
		}
	}
}

void agregar(nodo *&raiz,elemento dato){
	nodo *newnodo=(nodo*)malloc(sizeof(nodo));
	newnodo->dato=dato;
	newnodo->sgt=raiz;
	raiz=newnodo;
	printf("\n\t\tPersona Agregada.\n");
	printf("\n\n");
	system("pause");
	system("cls");
}

void sacar(nodo *&raiz){
	nodo *aux=raiz;
	raiz=raiz->sgt;
	free(aux);
	printf("\n\t\tEliminado Correctamente.\n");
	printf("\n\n");
	system("pause");
	system("cls");
}

void mostrar(nodo *raiz){
	system("cls");
	nodo *aux=raiz;
	while(aux!=NULL){
		printf("\n\t%s\t%s\t%s\t%d\n",aux->dato.nombre,aux->dato.apellido,aux->dato.sexo,aux->dato.cedula);
		aux=aux->sgt;
	}
	system("pause");
	system("cls");
}

void registro(nodo *raiz){
	FILE *Ar;
	if((Ar=fopen("copia.txt","w"))==NULL){
		printf("\t\tERROR\n");
	}
	nodo *aux=raiz;
	while(aux!=NULL){
		fprintf(Ar,"\n\t%s\t%s\t%s\t%d\n",aux->dato.nombre,aux->dato.apellido,aux->dato.sexo,aux->dato.cedula);
		aux=aux->sgt;
	}
	fclose(Ar);
}
