package q1;

import java.io.*;
import java.util.*;
 
public class MySpecificWords {
 
    public List<String> getSpecificWordList(String fileName){
 
        FileInputStream file = null;
        DataInputStream data = null;
        BufferedReader br = null;
        List<String> wordList = new ArrayList<String>();
        try {
            file = new FileInputStream(fileName);
            data = new DataInputStream(file);
            br = new BufferedReader(new InputStreamReader(data));
            String line = null;
            while((line = br.readLine()) != null){
                StringTokenizer st = new StringTokenizer(line, " ,.;:\"");
                while(st.hasMoreTokens()){
                    String tmp = st.nextToken().toLowerCase();
                    if(!wordList.contains(tmp)){
                        wordList.add(tmp);
                    }
                }
            }
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        } finally{
            try{if(br != null) br.close();}catch(Exception ex){}
        }
        return wordList;
    }
     
    public static void main(String a[]){
         
        MySpecificWords distFw = new MySpecificWords();
        List<String> wordList = distFw.getSpecificWordList("C:/sample.txt");
        System.out.println("The number of distinct word in text file : " +wordList.size());
    }
}