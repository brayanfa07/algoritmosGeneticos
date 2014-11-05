### Tecnológico de Costa Rica
#####Escuela de Ingeniería en Computación
#####IC3002 Análisis de Algoritmos - Prof. Mauricio Rojas
#####201157035 Brayan Fajardo Alvarado - Fecha: 04 de noviembre de 2014
#####TAREA: Algoritmos Genéticos
___________
______________
__________
#####Algoritmos Genéticos
____
____

#####1) Problema de la mochila

```

import java.util.Random;

/**
 * Created by Brayan on 02/11/2014.
 */
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

    public int generarPeso(int maximo){
        Random rnd = new Random();
        int num = (int)(rnd.nextDouble() * maximo);
        return num;
    }

    public int generarValor(int maximo){
        Random  rnd = new Random();
        int num = (int)(rnd.nextDouble() * maximo);
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

/**
 * Created by Brayan on 02/11/2014.
 */
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

    public int generarPeso(int maximo){
        Random rnd = new Random();
        int num = (int)(rnd.nextDouble() * maximo);
        return num;
    }

    public int generarValor(int maximo){
        Random  rnd = new Random();
        int num = (int)(rnd.nextDouble() * maximo);
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
/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

import javax.lang.model.element.Element;

public class Algoritmo {

    Poblacion pob;
    int maximoMochila;
    double sumaMaximo;
    Elemento [] maximos;

    Algoritmo(int pesoMaximo, int valorMaximo, int pMaximoMochila){
        pob = new Poblacion(pesoMaximo, valorMaximo);
        maximoMochila = pMaximoMochila;
        sumaMaximo = 0;
        maximos = new Elemento[7];
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

    public Elemento[] getMaximos() {
        return maximos;
    }

    public void setMaximos(Elemento[] maximos) {
        this.maximos = maximos;
    }

    public int generarFitnessEntreTotal() {
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

    public int obtenerMaximo(){
        Elemento[] arreglo = new Elemento[7];
        arreglo[0] = pob.elemento1;
        arreglo[1] = pob.elemento2;
        arreglo[2] = pob.elemento3;
        arreglo[3] = pob.elemento4;
        arreglo[4] = pob.elemento5;
        arreglo[5] = pob.elemento6;
        arreglo[6] = pob.elemento7;
        Elemento maximo = null;
        int posicion = 0;

        for (int k = 0; k < 6; k++) {
            for (int i = 0; i < arreglo.length - 1; i++) {
                for (int j = 0; j < arreglo.length - 1; j++) {
                    if ((arreglo[i].fitnessEntreTotal >= arreglo[j + 1].fitnessEntreTotal) &&
                            (arreglo[i].peso <= maximoMochila) && sumaMaximo <= maximoMochila) {
                        maximo = arreglo[i];
                        posicion = i;

                    }
                }
            }
            if ((sumaMaximo + maximo.peso) <= maximoMochila){
                sumaMaximo = sumaMaximo + maximo.peso;
                maximos[k] = maximo;
                arreglo[posicion] = null;
            }
        }
        return 0;
    }


    public int retornarElementosMochila(){
        for (int i = 0; i < maximos.length; i++) {
            System.out.println("peso: " + maximos[i].peso + ", valor:  " + maximos[i].valor );
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
