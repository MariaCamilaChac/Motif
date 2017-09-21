# Motif
/**Param:String Aleatrorio
 * Author: Maria Camila CHacon
 * Date:12/09/2017
 */

import java.io.*;
import java.util.*;

public class Createfile {
	
	
	public Createfile() throws IOException{
	
	BufferedWriter bw = new BufferedWriter ( new FileWriter ( "Sequence.umd" ) ); //Como quiero que se ejecute el programa 
	for(int i = 0; i<1000; i++)// el numero de lineas que va a tener el programa
	{
		
		bw.write(createExperimentalRead());
		
	}
	
	bw.flush();
	
	}
	
	public String createExperimentalRead()
	{
		
		String read = " ";
		Random rd = new Random();//Se asignan la letras aleatoriamente
		int number1 = Math.abs(rd.nextInt());//se asignan numeros enteros aletoreamente
		int lenght = 5 + rd.nextInt(26);// el largo de cada linea va a ser de 5 a 30 lineas
		
		read = number1 + "," +  (number1 + lenght) + "," + createSequences(lenght) + "\n";
		
		return read;// van a retornar los dos bloques de números y el bloque de letras
		
		
	}
	

	public String createSequences(int lenght)// se van  crear los casos con las letras que se pueden asignar en el bloque de letras
	{
		
		String sequence = " ";
		Random rd = new Random();
		
		for(int i = 0 ; i<lenght; i++)
		{
			
			switch(rd.nextInt(4)){// los casos (letras) que se van a usar
			
			case 0:
			{
				sequence += "A";
			}
			break;
			
			case 1:
			{
				sequence += "C";
			}
			break;
			
			case 2:
			{
				sequence += "G";
			}
			break;
			
			case 3:
			{
				sequence += "T";
			}
			break;
			
			}
			
		}
		return sequence;
		
	}
	
	public static void main(String args[]) throws IOException
	{
		
		Createfile cf = new Createfile();
		
	}
	
}


import java.io.*;


public class reader {

	public static int numberReads(String motif) throws IOException{
		
		BufferedReader br=new BufferedReader(new FileReader("Sequence.umd"));
		int lines = 0, linesMotif=0;
		String read= br.readLine();
		
		while(read != null){
			if (read.split(",")[2].contains(motif)){
				linesMotif +=1;
			}
			lines +=1;
		    read=br.readLine();
		}
		return linesMotif;
	

	}

	public static void main(String[] args) throws IOException {
		N=reader.numberReads(“CGT”);
                      System.out.println(“N”);
		}
}
