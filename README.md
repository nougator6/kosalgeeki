# Generic Asynctask 1.2

This is an update version of Generic AsyncTask library.

### Now you can watch my video tutorials at https://www.youtube.com/watch?v=5v_1cqkFSuQ for the Part 1 and at https://www.youtube.com/watch?v=YdmJaSQWP9c for the Part 2 which show you how to use this library step by step. You can watch other videos in my YouTube Channel https://www.youtube.com/user/oumsaokosal

This is a custom class that performs a POST call from Android App to Web Server and get the response's result back.

For the Introduction and the motivation of this library, please read https://github.com/kosalgeek/generic_asynctask. In this page, only the usage and setup will be provided.


# Usage

## Class: PostResponseAsyncTask

### 1. Constuctor: PostResponseAsyncTask(Context context, AsyncResponse delegate)
```java
public PostResponseAsyncTask(Context context, AsyncResponse delegate)
```
In the previous version where this constructor has only one argument, this version of constructor needs 2 inputs. The first one is the context which is your Activity class. And the second one is the AsyncResponse interface. The big difference of this version is the second input. This input will let you make a different call to get a different response result. Even better, you can use anonymous class call here. As you can see an example below, two different tasks can have a complete different thread call to get a different result at a different time (First in, First Out):
```java
//10.0.3.2 is the alias IP for GenyMotion
//10.0.2.2 is the alias IP for Android native Emulator
String url1 = "http://10.0.3.2/client/post.php?format=json"; 
PostResponseAsyncTask task1 = new PostResponseAsyncTask(MainActivity.this, new AsyncResponse() {
    @Override
    public void processFinish(String s) {
        Toast.makeText(MainActivity.this, s, Toast.LENGTH_LONG).show();
    }
});
task1.execute(url1);

String url2 = "http://someurl.com/read.php";
PostResponseAsyncTask task2 = new PostResponseAsyncTask(MainActivity.this, new AsyncResponse() {
    @Override
    public void processFinish(String s) {
        Toast.makeText(MainActivity.this, s, Toast.LENGTH_LONG).show();
    }
});
task.execute(url2);
```

### 2. Constructor: PostResponseAsyncTask(Context context, boolean showLoadingMessage, AsyncResponse delegate)
```java
public PostResponseAsyncTask(Context context, boolean showLoadingMessage, AsyncResponse delegate);
```
This constructor is not so different to the previous one except it has *boolean showLoadingMessage* where you can set *false* to disable the loading message. By default, it shows a loading message everytime you retrieve data. Sometimes the data is too small to retriev so you can disable the loading message to make it look better for user experience. However, I would prefer not to set it to false while even the small data can take a very long time due to a slow internet speed. So, be causious when setting it to false. Below is sample code:
```java
String url1 = "http://someurl.com/read.php";
PostResponseAsyncTask task1 = new PostResponseAsyncTask(MainActivity.this, false, new AsyncResponse() {
    @Override
    public void processFinish(String s) {
        Toast.makeText(MainActivity.this, s, Toast.LENGTH_LONG).show();
    }
});
task1.execute(url1);
```
       
### 3. Constructor: PostResponseAsyncTask(Context context, HashMap&lt;String, String&gt; postData, AsyncResponse delegate);
This is another important constructor. This constructor has three inputs instead of two. The first one is your Activity class; the second one is the postData where you post data as HashMap into the server; and the last one is the usual AsyncResponse. See the example below:
```java
String url = "http://10.0.3.2/client/post.php";
HashMap postData = new HashMap();
postData.put("id", "1");
postData.put("name", "John");
PostResponseAsyncTask readTask = new PostResponseAsyncTask(MainActivity.this, postData, new AsyncResponse() {
  @Override
  public void processFinish(String s) {
    Toast.makeText(MainActivity.this, s, Toast.LENGTH_LONG).show();
  }
});
readTask.execute(url);
```

### 4. Constructor: PostResponseAsyncTask(Context context, HashMap&lt;String, String&gt; postData, boolean showLoadingMessage, AsyncResponse delegate);
This is like the previous one except the third argument is where you can set false to disable loading message. 
```java
String url = "http://10.0.3.2/client/post.php";
HashMap postData = new HashMap();
postData.put("id", "1");
postData.put("name", "John");
PostResponseAsyncTask readTask = new PostResponseAsyncTask(MainActivity.this, postData, false, new AsyncResponse() {
  @Override
  public void processFinish(String s) {
    Toast.makeText(MainActivity.this, s, Toast.LENGTH_LONG).show();
  }
});
readTask.execute(url);
```

### Other Constructor:
```java
public PostResponseAsyncTask(Context context,
                                 String loadingMessage,
                                 AsyncResponse delegate);
```
The above constructor can let you customize your loadin message text while posting data.

```java
public PostResponseAsyncTask(Context context,
                                 HashMap<String, String> postData,
                                 String loadingMessage,
                                 AsyncResponse delegate);
```
The above constructor can let you customize your loadin message text while posting data and retreiving data.


# Set Up

1. Download **GenAsync.1.2.jar** from this github to your local machine. 
2. Go to your project in Android Studio, on a Project panel (on the left), go to *app > libs*. You copy the *GenAsync.jar* and paste it in the *libs* folder > Press OK if a asked message appeared.
3. Right click on the jar file > Choose *Add As Library*. And if you are still not sure how to do that, please check out this link http://code2care.org/pages/import-external-jars-to-android-studio-project/.
4. Try this code below:
```java
PostResponseAsyncTask task;
```
5. If it shows no errors and you see  **import com.kosalgeek.genasync12.PostResponseAsyncTask;** correctly, then you are good to go.

## Follow Me
 * Get more free source codes at https://github.com/kosalgeek
 * Watch video tutorials at my YouTube channel https://youtube.com/user/oumsaokosal
 * Like my Facebook Page at https://facebook.com/kosalgeek
 * Follow me on Twitter https://twitter.com/kosalgeek and https://twitter.com/okosal
 * Get more tutorials at http://www.kosalgeek.com and http://www.top12review.com
 
# LICENSE

(The MIT License)
Copyright (c) 2015 KosalGeek. (kosalgeek at gmail dot com)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the 'Software'), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
