package com.example.test;

import java.io.BufferedWriter;
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileWriter;
import java.io.IOException;
import java.text.ParseException;
import java.util.HashMap;
import java.util.Iterator;
import java.util.Map;
import java.util.Set;
import java.util.Stack;

import org.apache.commons.io.FileUtils;
import org.apache.commons.io.IOUtils;
import org.json.CDL;
import org.json.JSONArray;
import org.json.JSONException;
import org.json.JSONObject;


public class test1 {
	
	
	static File file = new File("E:\\Output.csv");
	static FileWriter writer;
	static {
		try{
			writer = new FileWriter(file);
		}
		catch (IOException e){
			e.printStackTrace();
		}
	}
	

	public static void main(String[] args) throws IOException {
		String everything = null;
		FileInputStream inputStream = null;
		try {
			inputStream = new FileInputStream("E:\\json.txt");
		} catch (FileNotFoundException e1) {
			e1.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		}
		try {
			everything = IOUtils.toString(inputStream);
		} catch (IOException e) {
			e.printStackTrace();
		}
		System.out.println(everything);
		
		try {
			JSONObject output = new JSONObject(everything);
			loadJson(output);

			
			
		} catch (JSONException e) {
			e.printStackTrace();
		}
		
		writer.flush();
	    writer.close();
	}
	
	public static void loadJson(JSONObject json) throws IOException{
		
		Iterator<?> json_keys = json.keys();
	    while( json_keys.hasNext() ){
	        Object obj = json_keys.next();
	        try {
				if (json.get((String) obj) instanceof JSONArray) {
				    System.out.println(obj.toString());
				    writer.append(obj.toString() + "\n");
				    getArray(json.get((String) obj));
				} else {
				    if (json.get((String) obj) instanceof JSONObject) {
				        loadJson((JSONObject) json.get((String) obj));
				    } else {
				        System.out.println(obj.toString() + "\t"
				                + json.get((String) obj));
				        writer.append(obj.toString() + ","
				                + json.get((String) obj));
				        writer.append("\n");
				    }
				}	

			} catch (JSONException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			} catch (ParseException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
	    }
	    
	    }
	
	public static void getArray(Object object2) throws ParseException, IOException {

	    JSONArray jsonArr = (JSONArray) object2;

	    for (int k = 0; k < jsonArr.length(); k++)  {

	        try {
				if (jsonArr.get(k) instanceof JSONObject) {
				    loadJson((JSONObject) jsonArr.get(k));
				} else {
				    System.out.println(jsonArr.get(k));
				    writer.append(jsonArr.getString(k) 	);
				}
			} catch (JSONException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
	        
	    }
	    //writer.append("\n");
	}

	
}
