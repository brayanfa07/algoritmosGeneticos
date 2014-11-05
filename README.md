### Tecnológico de Costa Rica
#####Escuela de Ingeniería en Computación
#####IC3002 Análisis de Algoritmos - Prof. Mauricio Rojas
#####201157035 Brayan Fajardo Alvarado - Fecha: 04 de noviembre de 2014
#####TAREA: Algoritmos Genéticos

__________
#####Algoritmos Genéticos
____

#####1) Problema de la mochila

```
import java.util.Random;

public class Elemento {

    public double getFitnessEntreTotal() {
        return fitnessEntreTotal;
    }

    public void setFitnessEntreTotal(double fitnessEntreTotal) {
        this.fitnessEntreTotal = fitnessEntreTotal;
    }

    public String getValorBinario() {
        return valorBinario;
    }

    public void setValorBinario(String valorBinario) {
        this.valorBinario = valorBinario;
    }

    int valor;
    int peso;
    boolean seUsa;
    double fitness;
    double fitnessEntreTotal;
    String valorBinario;

    Elemento(int valorMaximo, int pesoMaximo) {
        this.valor = generarValor(valorMaximo);
        this.peso = generarPeso(pesoMaximo);
        this.seUsa = false;
        fitness = calcularFitness(this.valor);
        fitnessEntreTotal = 0;
        valorBinario = generarBinario(this.valor);
    }
    Elemento(){
        this.valor = 0;
        this.peso = 0;
        this.seUsa = false;
        fitness = 0;
        fitnessEntreTotal = 0;
        valorBinario = String.valueOf(0);

    }

    public int generarPeso(int maximo){
        Random rnd = new Random();
        int num = (int)(rnd.nextDouble() * maximo + 1);
        return num;
    }

    public int generarValor(int maximo){
        Random  rnd = new Random();
        int num = (int)(rnd.nextDouble() * maximo + 1);
        return num;
    }

    public double calcularFitness(int valor){
        int fitness = valor * valor;
        double fitnessDouble = (double)fitness;
        return fitnessDouble;
    }

    public String generarBinario(int valor){
        String valorBinario = String.format("%8s", Integer.toBinaryString(valor)).replace(' ', '0');
        return valorBinario;
    }

    public double getValor() {
        return valor;
    }

    public void setValor(int valor) {
        this.valor = valor;
    }

    public double getPeso() {
        return peso;
    }

    public void setPeso(int peso) {
        this.peso = peso;
    }

    public boolean isSeUsa() {
        return seUsa;
    }

    public void setSeUsa(boolean seUsa) {
        this.seUsa = seUsa;
    }

    public double getFitness() {
        return fitness;
    }

    public void setFitness(double fitness) {
        this.fitness = fitness;
    }
}
//////////////////////////////////////////////////////////////////////////////////////////////////////////

import java.util.Random;

public class Poblacion {

    Elemento elemento1;
    Elemento elemento2;
    Elemento elemento3;
    Elemento elemento4;
    Elemento elemento5;
    Elemento elemento6;
    Elemento elemento7;

    public Poblacion(int pesoMaximo, int valorMaximo){
        elemento1 = new Elemento(valorMaximo, pesoMaximo);
        elemento2 = new Elemento(valorMaximo, pesoMaximo);
        elemento3 = new Elemento(valorMaximo, pesoMaximo);
        elemento4 = new Elemento(valorMaximo, pesoMaximo);
        elemento5 = new Elemento(valorMaximo, pesoMaximo);
        elemento6 = new Elemento(valorMaximo, pesoMaximo);
        elemento7 = new Elemento(valorMaximo, pesoMaximo);
    }



    public void setElemento1(Elemento elemento1) {
        this.elemento1 = elemento1;
    }

    public void setElemento2(Elemento elemento2) {
        this.elemento2 = elemento2;
    }

    public void setElemento3(Elemento elemento3) {
        this.elemento3 = elemento3;
    }

    public void setElemento4(Elemento elemento4) {
        this.elemento4 = elemento4;
    }

    public void setElemento5(Elemento elemento5) {
        this.elemento5 = elemento5;
    }

    public void setElemento6(Elemento elemento6) {
        this.elemento6 = elemento6;
    }

    public void setElemento7(Elemento elemento7) {
        this.elemento7 = elemento7;
    }

    public Elemento getElemento1() {
        return elemento1;
    }

    public Elemento getElemento2() {
        return elemento2;
    }

    public Elemento getElemento3() {
        return elemento3;
    }

    public Elemento getElemento4() {
        return elemento4;
    }

    public Elemento getElemento5() {
        return elemento5;
    }

    public Elemento getElemento6() {
        return elemento6;
    }

    public Elemento getElemento7() {
        return elemento7;
    }
}



/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
import java.util.ArrayList;

public class Algoritmo {

    Poblacion pob;
    int maximoMochila;
    double sumaMaximo;
    ArrayList<Elemento> maximos;
    Elemento maximo;

    Algoritmo(int pesoMaximo, int valorMaximo, int pMaximoMochila){
        pob = new Poblacion(pesoMaximo, valorMaximo);
        maximoMochila = pMaximoMochila;
        sumaMaximo = 0;
        maximos = new ArrayList<Elemento>();
        maximo = null;
    }

    public Poblacion getPob() {
        return pob;
    }

    public void setPob(Poblacion pob) {
        this.pob = pob;
    }

    public int getMaximoMochila() {
        return maximoMochila;
    }

    public void setMaximoMochila(int maximoMochila) {
        this.maximoMochila = maximoMochila;
    }

    public double getSumaMaximo() {
        return sumaMaximo;
    }

    public void setSumaMaximo(double sumaMaximo) {
        this.sumaMaximo = sumaMaximo;
    }

    public ArrayList<Elemento> getMaximos() {
        return maximos;
    }

    public void setMaximos(ArrayList<Elemento> maximos) {
        this.maximos = maximos;
    }

    public Elemento getMaximo() {
        return maximo;
    }

    public void setMaximo(Elemento maximo) {
        this.maximo = maximo;
    }

    public int generarFitnessEntreTotal() {
        System.out.println("Peso máximo de la mochila: " + maximoMochila);

        double sumaFitness = pob.elemento1.fitness + pob.elemento2.fitness + pob.elemento3.fitness +
                pob.elemento4.fitness + pob.elemento5.fitness + pob.elemento6.fitness +
                pob.elemento7.fitness;
        pob.elemento1.setFitnessEntreTotal(pob.elemento1.fitness / sumaFitness);
        pob.elemento2.setFitnessEntreTotal(pob.elemento2.fitness / sumaFitness);
        pob.elemento3.setFitnessEntreTotal(pob.elemento3.fitness / sumaFitness);
        pob.elemento4.setFitnessEntreTotal(pob.elemento4.fitness / sumaFitness);
        pob.elemento5.setFitnessEntreTotal(pob.elemento5.fitness / sumaFitness);
        pob.elemento6.setFitnessEntreTotal(pob.elemento6.fitness / sumaFitness);
        pob.elemento7.setFitnessEntreTotal(pob.elemento7.fitness / sumaFitness);

        return 0;
    }

    public int obtenerMaximo() {
        ArrayList <Elemento> arreglo = new ArrayList<Elemento>();
        arreglo.add(this.pob.elemento1);
        arreglo.add(this.pob.elemento2);
        arreglo.add(this.pob.elemento3);
        arreglo.add(this.pob.elemento4);
        arreglo.add(this.pob.elemento5);
        arreglo.add(this.pob.elemento6);
        arreglo.add(this.pob.elemento7);

        int posicion = 0;
        System.out.println("Fitness 1: " + arreglo.get(0).fitnessEntreTotal);
        System.out.println("Fitness 2: " + arreglo.get(1).fitnessEntreTotal);
        System.out.println("Fitness 3: " + arreglo.get(2).fitnessEntreTotal);
        System.out.println("Fitness 4: " + arreglo.get(3).fitnessEntreTotal);
        System.out.println("Fitness 5: " + arreglo.get(4).fitnessEntreTotal);
        System.out.println("Fitness 6: " + arreglo.get(5).fitnessEntreTotal);
        System.out.println("Fitness 7: " + arreglo.get(6).fitnessEntreTotal);
        System.out.println("  ");


       return almacenarMaximos(arreglo, 0);
    }


    public int almacenarMaximos (ArrayList<Elemento> arreglo, int pos){
        maximo = new Elemento();
        int posicion = pos;
        for (int i = 0; i < arreglo.size(); i++) {
            for (int j = 0; j < arreglo.size(); j++) {
                if (((arreglo.get(i).fitnessEntreTotal) >= (arreglo.get(i).fitnessEntreTotal)) && ((arreglo.get(i).peso) < maximoMochila) && (sumaMaximo <= maximoMochila)) {
                    maximo = arreglo.get(i);
                    posicion = i;
                }
            }
        }
        if (((sumaMaximo + maximo.getPeso()) < maximoMochila) && (arreglo.size() > 0)) {
            sumaMaximo = sumaMaximo + maximo.peso;
            maximos.add(maximo);
            arreglo.remove(posicion);
            almacenarMaximos(arreglo, posicion);
        }
        else if (sumaMaximo == maximoMochila) {
            return 0;
        }
        else{
            return 0;
        }
        return 0;
    }


    public int retornarElementosMochila(){
        for (int i = 0; i < maximos.size(); i++) {
            System.out.println("peso: " + maximos.get(i).getPeso() + ", valor:  " + maximos.get(i).valor );
        }
        return 0;
    }

    public static void main(String[] args) {
        Algoritmo algoritmo = new Algoritmo(100, 500, 300);
        algoritmo.generarFitnessEntreTotal();
        algoritmo.obtenerMaximo();
        algoritmo.retornarElementosMochila();
    }
}

```

#####2) Ordenamiento numérico

```
import java.util.Random;

public class Elemento {

    public double getFitnessEntreTotal() {
        return fitnessEntreTotal;
    }

    public void setFitnessEntreTotal(double fitnessEntreTotal) {
        this.fitnessEntreTotal = fitnessEntreTotal;
    }

    public String getValorBinario() {
        return valorBinario;
    }

    public void setValorBinario(String valorBinario) {
        this.valorBinario = valorBinario;
    }

    int valor;
    boolean seUsa;
    double fitness;
    double fitnessEntreTotal;
    String valorBinario;

    Elemento(int valorMaximo) {
        this.valor = generarValor(valorMaximo);
        this.seUsa = false;
        fitness = calcularFitness(this.valor);
        fitnessEntreTotal = 0;
        valorBinario = generarBinario(this.valor);
    }
    Elemento(){
        this.valor = 0;
        this.seUsa = false;
        fitness = 0;
        fitnessEntreTotal = 0;
        valorBinario = String.valueOf(0);

    }


    public int generarValor(int maximo){
        Random  rnd = new Random();
        int num = (int)(rnd.nextDouble() * maximo + 1);
        return num;
    }

    public double calcularFitness(int valor){
        int fitness = valor * valor;
        double fitnessDouble = (double)fitness;
        return fitnessDouble;
    }

    public String generarBinario(int valor){
        String valorBinario = String.format("%8s", Integer.toBinaryString(valor)).replace(' ', '0');
        return valorBinario;
    }

    public double getValor() {
        return valor;
    }

    public void setValor(int valor) {
        this.valor = valor;
    }

    public boolean isSeUsa() {
        return seUsa;
    }

    public void setSeUsa(boolean seUsa) {
        this.seUsa = seUsa;
    }

    public double getFitness() {
        return fitness;
    }

    public void setFitness(double fitness) {
        this.fitness = fitness;
    }
}
/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

import java.util.Random;

public class Conjunto {

    Elemento elemento1;
    Elemento elemento2;
    Elemento elemento3;
    Elemento elemento4;
    Elemento elemento5;
    Elemento elemento6;
    Elemento elemento7;

    public Conjunto(int valorMaximo){
        elemento1 = new Elemento(valorMaximo);
        elemento2 = new Elemento(valorMaximo);
        elemento3 = new Elemento(valorMaximo);
        elemento4 = new Elemento(valorMaximo);
        elemento5 = new Elemento(valorMaximo);
        elemento6 = new Elemento(valorMaximo);
        elemento7 = new Elemento(valorMaximo);
    }



    public void setElemento1(Elemento elemento1) {
        this.elemento1 = elemento1;
    }

    public void setElemento2(Elemento elemento2) {
        this.elemento2 = elemento2;
    }

    public void setElemento3(Elemento elemento3) {
        this.elemento3 = elemento3;
    }

    public void setElemento4(Elemento elemento4) {
        this.elemento4 = elemento4;
    }

    public void setElemento5(Elemento elemento5) {
        this.elemento5 = elemento5;
    }

    public void setElemento6(Elemento elemento6) {
        this.elemento6 = elemento6;
    }

    public void setElemento7(Elemento elemento7) {
        this.elemento7 = elemento7;
    }

    public Elemento getElemento1() {
        return elemento1;
    }

    public Elemento getElemento2() {
        return elemento2;
    }

    public Elemento getElemento3() {
        return elemento3;
    }

    public Elemento getElemento4() {
        return elemento4;
    }

    public Elemento getElemento5() {
        return elemento5;
    }

    public Elemento getElemento6() {
        return elemento6;
    }

    public Elemento getElemento7() {
        return elemento7;
    }
}


/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

import java.util.ArrayList;


public class Ordenamiento {

    Conjunto conj;
    int maximoMochila;
    double sumaMaximo;
    ArrayList<Elemento> minimos;
    Elemento minimo;

    Ordenamiento(int valorMaximo, int pMaximoMochila){
        conj = new Conjunto(valorMaximo);
        maximoMochila = pMaximoMochila;
        sumaMaximo = 0;
        minimos = new ArrayList<Elemento>();
        minimo= null;
    }




    public Conjunto getPob() {
        return conj;
    }

    public void setPob(Conjunto conj) {
        this.conj = conj;
    }

    public int getMaximoMochila() {
        return maximoMochila;
    }

    public void setMaximoMochila(int maximoMochila) {
        this.maximoMochila = maximoMochila;
    }

    public double getSumaMaximo() {
        return sumaMaximo;
    }

    public void setSumaMaximo(double sumaMaximo) {
        this.sumaMaximo = sumaMaximo;
    }

    public ArrayList<Elemento> getMaximos() {
        return minimos;
    }

    public void setMaximos(ArrayList<Elemento> maximos) {
        this.minimos = maximos;
    }

    public Elemento getMaximo() {
        return minimo;
    }

    public void setMaximo(Elemento maximo) {
        this.minimo = maximo;
    }

    public int generarFitnessEntreTotal() {
        System.out.println("Peso máximo de la mochila: " + maximoMochila);

        double sumaFitness = conj.elemento1.fitness + conj.elemento2.fitness + conj.elemento3.fitness +
                conj.elemento4.fitness + conj.elemento5.fitness + conj.elemento6.fitness +
                conj.elemento7.fitness;
        conj.elemento1.setFitnessEntreTotal(conj.elemento1.fitness / sumaFitness);
        conj.elemento2.setFitnessEntreTotal(conj.elemento2.fitness / sumaFitness);
        conj.elemento3.setFitnessEntreTotal(conj.elemento3.fitness / sumaFitness);
        conj.elemento4.setFitnessEntreTotal(conj.elemento4.fitness / sumaFitness);
        conj.elemento5.setFitnessEntreTotal(conj.elemento5.fitness / sumaFitness);
        conj.elemento6.setFitnessEntreTotal(conj.elemento6.fitness / sumaFitness);
        conj.elemento7.setFitnessEntreTotal(conj.elemento7.fitness / sumaFitness);

        return 0;
    }

    public int obtenerMaximo() {
        ArrayList <Elemento> arreglo = new ArrayList<Elemento>();
        arreglo.add(this.conj.elemento1);
        arreglo.add(this.conj.elemento2);
        arreglo.add(this.conj.elemento3);
        arreglo.add(this.conj.elemento4);
        arreglo.add(this.conj.elemento5);
        arreglo.add(this.conj.elemento6);
        arreglo.add(this.conj.elemento7);

        int posicion = 0;
        System.out.println("Fitness 1: " + arreglo.get(0).fitnessEntreTotal);
        System.out.println("Fitness 2: " + arreglo.get(1).fitnessEntreTotal);
        System.out.println("Fitness 3: " + arreglo.get(2).fitnessEntreTotal);
        System.out.println("Fitness 4: " + arreglo.get(3).fitnessEntreTotal);
        System.out.println("Fitness 5: " + arreglo.get(4).fitnessEntreTotal);
        System.out.println("Fitness 6: " + arreglo.get(5).fitnessEntreTotal);
        System.out.println("Fitness 7: " + arreglo.get(6).fitnessEntreTotal);
        System.out.println("  ");


        return almacenarMaximos(arreglo, 0);
    }


    public int almacenarMaximos (ArrayList<Elemento> arreglo, int pos){
        minimo = new Elemento();
        int posicion = pos;
        for (int i = 0; i < arreglo.size(); i++) {
            for (int j = 0; j < arreglo.size(); j++) {
                if (((arreglo.get(i).fitnessEntreTotal) <= (arreglo.get(i).fitnessEntreTotal))) {
                    minimo = arreglo.get(i);
                    posicion = i;
                }
            }
        } if(arreglo.size() > 0){
            minimos.add(minimo);
            arreglo.remove(posicion);
            almacenarMaximos(arreglo, posicion);
        }
        return 0;
    }


    public int retornarElementosMochila(){
        for (int i = 0; i < minimos.size(); i++) {
            System.out.println("valor:  " + minimos.get(i).valor );
        }
        return 0;
    }

    public static void main(String[] args) {
        Ordenamiento algoritmo = new Ordenamiento(100, 500);
        algoritmo.generarFitnessEntreTotal();
        algoritmo.obtenerMaximo();
        algoritmo.retornarElementosMochila();
    }
}


```
