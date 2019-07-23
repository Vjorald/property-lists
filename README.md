# property-lists

import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;
import java.util.Enumeration;
import java.util.Properties;


public class PropertiesTest1 {

	public static void main(String[] args) throws IOException  {
		
		Properties p = new Properties();
		
		FileInputStream in = new FileInputStream("properties.txt");
		p.load(in);
		in.close();
		

		Enumeration keys = p.propertyNames();
		while  (keys.hasMoreElements()){
			String key = (String) keys.nextElement();
			String value = p.getProperty(key);
			System.out.println(key + " = " + value);
		}
		
		
		//Change
		
		p.put("Weight", "6.5");
		p.put("Colour", "blue");
		
		FileOutputStream out = new FileOutputStream("properties2.txt");
		p.store(out, "Example Version 2");
		out.close();
	}

}
