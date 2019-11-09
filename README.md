
 
import org.json.JSONException;
import org.json.JSONObject;
 

public class MergeJSONObjects {
 
	public static void main(String[] args) {
		JSONObject json1 = new JSONObject();
		JSONObject json2 = new JSONObject();
 
		json1.put("name","Alexis Sanchez","club","Manchester United");
		json1.put("name","Robin van Persie","club","Feyenoord");
 
		json2.put( "name","Nicolas Pepe","club","Arsenal");

                json3.put("name","Gonzalo Higuain","club","Napoli");
                json3.put("name","Sunil Chettri","club","Bengaluru FC");
 
 
		System.out.println("json1: " + json1);
		System.out.println("json2: " + json2);
                System.out.println("json3: " + json3);
 
		JSONObject mergedJSON = mergeJSONObjects(json1,json2,json3);
		System.out.println("\nmergedJSON: " + mergedJSON);
	}
 
	public static JSONObject mergeJSONObjects(JSONObject json1, JSONObject json2,JSONObject json3) {
		JSONObject mergedJSON = new JSONObject();
		try {
			mergedJSON = new JSONObject(json1, JSONObject.getNames(json1),json2, JSONObject.getNames(json2));
			for (String crunchifyKey : JSONObject.getNames(json3)) {
				mergedJSON.put(crunchifyKey, json3.get(crunchifyKey));
			}
 
		} catch (JSONException e) {
			throw new RuntimeException("JSON Exception" + e);
		}
		return mergedJSON;
	}
} 
