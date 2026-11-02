# Ex.No:3a Develop program to create a text field and a button “Navigate”. When you enter “www.gmail.com” and press navigate button it should open google page using Implicit Intents.
## AIM:
To create a navigate button using Implicit Intent to display the gmail page using Android Studio.

## EQUIPMENTS REQUIRED:
Latest Version Android Studio

## ALGORITHM:
Start the program.
Create a new Android project in Android Studio.
Design the layout with an EditText field to enter a website URL and a Button labeled Navigate.
Initialize the text field and button in the MainActivity.
Set an OnClickListener for the Navigate button.
Read the URL entered by the user in the text field.
If the URL does not contain https:// or http://, add https:// to it.
Create an implicit intent using Intent.ACTION_VIEW.
Convert the URL into a Uri and set it as the intent data.
Call startActivity(intent) to open the website in a suitable browser.
Run the application and enter www.gmail.com in the text field.
Click the Navigate button and verify that the website opens in the browser.
Stop the program.

## PROGRAM:

# Developed by: KARTHIK G
# Registeration Number : 212223220043
```
package com.example.implicit;

import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class MainActivity extends AppCompatActivity {

    private EditText editTextUrl;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);

        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {
            Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);
            return insets;
        });

        editTextUrl = findViewById(R.id.editTextUrl);
        Button btnClick = findViewById(R.id.btnClick);

        // Open the URL entered in EditText using Implicit Intent when clicked
        btnClick.setOnClickListener(v -> {
            String url = editTextUrl.getText().toString().trim();
            if (url.isEmpty()) {
                Toast.makeText(MainActivity.this, "Please enter a URL", Toast.LENGTH_SHORT).show();
            } else {
                openWebPage(url);
            }
        });
    }

    private void openWebPage(String rawUrl) {
        String formattedUrl = (rawUrl.startsWith("http://") || rawUrl.startsWith("https://"))
                ? rawUrl : "https://" + rawUrl;
        try {
            Intent intent = new Intent(Intent.ACTION_VIEW, Uri.parse(formattedUrl));
            startActivity(intent);
        } catch (Exception e) {
            Toast.makeText(this, "Unable to open link", Toast.LENGTH_SHORT).show();
        }
    }
}
```

## OUTPUT
<img width="1920" height="1080" alt="Screenshot 2026-11-02 132415" src="https://github.com/user-attachments/assets/c6b120c8-dff0-4a3f-abdb-bfacd0c8682d" />

<img width="1920" height="1080" alt="Screenshot 2026-11-02 132512" src="https://github.com/user-attachments/assets/6060209e-0c34-454f-be11-cafde616bab5" />



## RESULT
Thus a Simple Android Application create a navigate button using Implicit Intent to display the gmail page using Android Studio is developed and executed successfully.


