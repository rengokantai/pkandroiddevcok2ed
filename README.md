#### pkandroiddevcok2ed'
#####1 Activities
######Starting a new activity with an intent
```
import android.content.Intent;
public void launch(View view){
  Intent intent = new Intent(Intent.ACTION_VIEW);  //open browser
  intent.setData(Uri.parse("www.github.com")
  startActivity(intent);
}
```
######saving an activity's state
```
@override
protected void onSaveInstanceState(Bundle outState){
  super.onSaveInstanceState(outState);
  outState.putInt(KEY_COUNTER,mCounter)
}

@override
protected void onRestoreInstanceState(Bundle savedInstanceState){
  super.onRestoreInstanceState(savedInstanceState);
  mCounter = savedInstanceState.getInt(KEY_COUNTER);
}
```
######Storing persistent data
```
@override
pretected void onPause(){
  super.onPause();
  SharedPreferences.Editor ed = getSharedPreferences(MODE_PRIVATE).edit();
  ed.putInt(KEY,mCounter);
  ed.commit();
}

@override
protected void onCreate(){
  mCounter = getPreferences(MODE_PRIVATE).getInt(KEY,def);
}
```
#####2 Layouts
######Defining and
```
setContentView(R.layout.activity_main)
```
#####2
######Using ListView
```
String[] countries = new String[]{"China", "France", "Germany", "India", "Russia", "United Kingdom", "United States"};
ListAdapter countryAdapter = new ArrayAdapter<String>(this, android.R.layout.simple_list_item_1, countries);
setListAdapter(countryAdapter);
```
setChoiceMode()
```
getListView().setChoiceMode(ListView.CHOICE_MODE_MULTIPLE);
```
###### using graphic to show button state
```
<?xml version="1.0" encoding="utf-8"?>
<selector xmlns:android="http://schemas.android.com/apk/res/android">
    <item
        android:drawable="@android:color/darker_gray"
        android:state_checked="true"/>
    <item
        android:drawable="@android:color/white"  // or change to image android:drawable="@drawable/imgname
        android:state_checked="false"/>
</selector>
```
button:
```
<ToggleButton
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="New ToggleButton"
    android:id="@+id/toggleButton"
    android:layout_centerVertical="true"
    android:layout_centerHorizontal="true"
    android:background="@drawable/state_selector" />  //can be android:button
```
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

get public dict:
```
Environment.getExternalStoragePublicDirectory(Environment.DIRECTORY_MUSIC)
```
getFreeSpace
```
Environment.getExternalStorageDirectory().getFreeSpace()
```

######including resources files in (AS = android studio)
create raw folder: res->raw  
create asset folder: AS->right click project->new->folder->asset folder  
we create a method
```
getText(InputStream is)
```
Difference:
```
TextView raw = (TextView)findViewById(R.id.textViewRaw);
raw.setText(getText(this.getResources().openRawResource(R.raw.filename)
```
read asset need try/catch
```
TextView raw = (TextView)findViewById(R.id.textViewAsset);
try{
raw.setText(getText(this.getAssets().open("filename.txt");
}catch(IOException e){
}
```
#####8 Using the touchscreen and sensors

######swipe to refresh
```
<android.support.v4.widget.SwipeRefreshLayout ..>
```
#####12Telephony Networks
######How to make a phone
```
<uses-permission android:name="android.permission.CALL_PHONE"></uses-permission>
```
```
public void dialPhone(View view,int number){
if(checkPermission("android.permission.CALL_PHONE")){
Intent intent = new Intent(Intent.ACTION_DIAL);
intent.setData(Uri.parse("tel":+number));
startActivity(intent);
}
}
```
check permission granting
```
private boolean checkPermission(String permission){
int permissionCheck = ContextCompat.checkSelfPermission(this,permission);
return (permissionCheck == PackageManager.PERMISSION_GRANTED);
}
```
###### Monitoring phone call event
```
<uses-permission android:name="android.permission.READ_PHONE_STATE"></uses-permission>
```
```

```
#####14 Getting you app ready
######The new And 6.0 run0time
```
private boolean checkPermission(String permission){
int permissionCheck = ContextCompat.checkSelfPermission(this,permission);
return (permissionCheck == PackageManager.PERMISSION_GRANTED);
}
```
permission name, permissionrequestcode
```
ActivityCompat.requestPermissions(this,new String[]{Manifest.permission.SEND_SMS, REQUSET_PERMISSION0
```
override onRequestPermissionsResult(requestCode,permissions[],grantReaults)
```
if(grantResults.length>0&&grantResults[0]==PackageManager.PERMISSION_GRANTED)
```
