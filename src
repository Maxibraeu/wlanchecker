

import java.awt.AWTException;
import java.awt.Robot;
import java.io.IOException;
import java.util.Timer;
import java.awt.Robot;
import java.io.FileWriter;
import java.io.BufferedReader;
import java.io.FileNotFoundException;
import java.io.FileReader;


public class main {
	static String outputfolder;
    public static void main(String[] args) throws AWTException {
    
    	String command = "netsh wlan show profile "+ readconfig("config.txt") ;
    	Timer t = new Timer();
        try {
            // Erstellen Sie den ProcessBuilder mit dem gewünschten Befehl
            ProcessBuilder processBuilder = new ProcessBuilder("cmd", "/c", command);

            // Starten Sie den Prozess
            Process process = processBuilder.start();
        	Robot lo = new Robot();
    		lo.delay(500);
            // Lesen Sie die Ausgabe des Befehls
            java.io.InputStream is = process.getInputStream();
            java.util.Scanner s = new java.util.Scanner(is).useDelimiter("\\A");
            String output = s.hasNext() ? s.next() : "";

            // Warten Sie, bis der Prozess beendet ist
            int exitCode = process.waitFor();

            // Zeigen Sie die Ausgabe und den Exit-Code an
          
            speichern(output + "Exitcode : "+exitCode, outputfolder+"/Passwort.pswd");
            System.out.println(outputfolder);
            System.exit(0);
        } catch (IOException | InterruptedException e) {
            e.printStackTrace();
        }
    }
    
    public static String readconfig(String dateipfad) {
        StringBuilder stringBuilder = new StringBuilder();
        
        int i =0;
        try (BufferedReader bufferedReader = new BufferedReader(new FileReader(dateipfad))) {
            String zeile;
            while ((zeile = bufferedReader.readLine()) != null ) {
            	if(i==0) {
            	stringBuilder.append(zeile+ " key=clear").append("\n");
            	}
            	if(i==1) {outputfolder= zeile; }
            	i+=1;
            }
        } catch (IOException e) {
            e.printStackTrace();
        }

        return stringBuilder.toString();
    }


   
        public static void speichern(String t,String pfad) {
            String dateipfad = pfad;
            String text = t;

            try {
                FileWriter writer = new FileWriter(dateipfad);
                writer.write(text);
                writer.close();
         
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }

