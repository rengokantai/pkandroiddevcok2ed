#### pkandroiddevcok2ed'
#####6 Working with Data
######Storing simple data
```
SharedPreference sharedPreference = getPreference(MODE_PRIVATE);
String name = sharedPreference.getString(KEY,null);  //(key,defvalue)
SharedPreference.Editor editor = getPreferences(MODE_PRIVATE).edit();
editor.putString(KEY,editText.getText().toString());
editor.commit();
```
######Read and write a text
readFile
```
publid void readFile(View view){
  StringBuilder stringBuilder = new StringBuilder();
  try{
  InputStream inputStream = openfileInput(FILENAME);
  if(inputStream!=null){
    InputStreamReader i = new InputStreamReader(inputStream);
    BufferedReader br = new BufferedReader(i);
    String newLine = null;
    while(newLine = bufferedReader.readLine())!=null){
      stringBuilder.append(new+"\n");
    }
    inputStream.close();
    }
  }catch(IOException){
    e.printStackTrace();
  }
  editText().setText(stringBuilder);
}
```

#####8 Using the touchscreen and sensors

######swipe to refresh
```
<android.support.v4.widget.SwipeRefreshLayout ..>
```
