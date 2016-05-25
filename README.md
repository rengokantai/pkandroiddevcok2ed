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
writeFile
```
public void writeFile(View view){
  try{
    FileOutputStream fos = openFileOutput(FN, Context.MODE_PRIVATE);
    FileOutputStream.write(editText.getText().toString().getBytes());
    fileOutputStream.close();
  }catch(IOException e){
  }
}
```
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

######Read and write text file to external
is readable?
```
Environment.MEDIA_MOUNTED.equals(Environment.getExternalStorageState()) || Environment.MEDIA_MOUNTED_READ_ONLY.equals(Environment.getExternalStorageState())
```
write a text file?
```
File f = new File(Environment.getExternalStorageDirectory(),filename);
FileOutputStream fos = new FileOutputStream(f);
fileoutputStream.write(editText.getText().toString().getBytes());
f.close()
```
read a text file?
```
File f = new File(Environment.getExternalStorageDirectory(),filename);
FileInputStream fis = new FileInputStream(f);
if(fos!=null){
  InputStreamReader isr = new InputStramReader(fis);
  BufferedReader br = new BufferedReader(isr);
  String newline = null;
  while ((newline = br.readLine())!=null){
  sb.append(newline);
  }
  fis.close();
  }
  editText.setText(sb);
```

#####8 Using the touchscreen and sensors

######swipe to refresh
```
<android.support.v4.widget.SwipeRefreshLayout ..>
```
