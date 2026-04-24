# mobilnee


<resources>
    <string name="app_name">My Application</string>

    <string name="login_title">Login</string>
    <string name="email_hint">Email</string>
    <string name="password_hint">Lozinka</string>
    <string name="login_button">Prijavi se</string>
    <string name="register_button">Registracija</string>

    <string name="register_title">Registracija</string>
    <string name="first_name_hint">Ime</string>
    <string name="last_name_hint">Prezime</string>
    <string name="phone_hint">Broj telefona</string>
    <string name="create_account_button">Kreiraj nalog</string>

    <string name="login_success">Uspešan login</string>
    <string name="login_error">Pogrešan email ili lozinka</string>
    <string name="register_success">Korisnik registrovan</string>
    <string name="home_title">Home Screen</string>
<string name="change_wallpaper_button">Promeni wallpaper</string>
</resources>

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/loginRoot"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="24dp"
    android:gravity="center"
    android:background="#FFFFFF">

    <TextView
        android:id="@+id/loginTitle"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/login_title"
        android:textSize="30sp"
        android:textStyle="bold"
        android:layout_marginBottom="32dp"
        android:textColor="#000000" />

    <EditText
        android:id="@+id/emailInput"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="@string/email_hint"
        android:inputType="textEmailAddress"
        android:layout_marginBottom="16dp" />

    <EditText
        android:id="@+id/passwordInput"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="@string/password_hint"
        android:inputType="textPassword"
        android:layout_marginBottom="24dp" />

    <Button
        android:id="@+id/loginButton"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="@string/login_button" />

    <Button
        android:id="@+id/registerButton"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="@string/register_button"
        android:layout_marginTop="12dp" />

</LinearLayout>


package com.example.myapplication;

import android.content.Intent;
import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

public class LoginScreen extends AppCompatActivity {

    private EditText emailInput;
    private EditText passwordInput;
    private Button loginButton;
    private Button registerButton;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_login_screen);

        emailInput = findViewById(R.id.emailInput);
        passwordInput = findViewById(R.id.passwordInput);
        loginButton = findViewById(R.id.loginButton);
        registerButton = findViewById(R.id.registerButton);

        loginButton.setOnClickListener(v -> {
            String email = emailInput.getText().toString();
            String password = passwordInput.getText().toString();

            boolean success = UserRepository.login(email, password);

            if (success) {
                Toast.makeText(
                        LoginScreen.this,
                        getString(R.string.login_success),
                        Toast.LENGTH_SHORT
                ).show();

                Intent intent = new Intent(LoginScreen.this, HomeScreen.class);
                startActivity(intent);
            } else {
                Toast.makeText(
                        LoginScreen.this,
                        getString(R.string.login_error),
                        Toast.LENGTH_SHORT
                ).show();
            }
        });

        registerButton.setOnClickListener(v -> {
            Intent intent = new Intent(LoginScreen.this, RegisterScreen.class);
            startActivity(intent);
        });
    }

    @Override
    protected void onStart() {
        super.onStart();
    }

    @Override
    protected void onRestart() {
        super.onRestart();
    }

    @Override
    protected void onResume() {
        super.onResume();
    }

    @Override
    protected void onPause() {
        super.onPause();
    }

    @Override
    protected void onStop() {
        super.onStop();
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
    }
}

_________________________________

Register

<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/registerRoot"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="24dp"
    android:background="#FFFFFF">

    <TextView
        android:id="@+id/registerTitle"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/register_title"
        android:textSize="30sp"
        android:textStyle="bold"
        android:textColor="#000000"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="70dp" />

    <EditText
        android:id="@+id/firstNameInput"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="@string/first_name_hint"
        android:inputType="textPersonName"
        android:layout_below="@id/registerTitle"
        android:layout_marginTop="32dp" />

    <EditText
        android:id="@+id/lastNameInput"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="@string/last_name_hint"
        android:inputType="textPersonName"
        android:layout_below="@id/firstNameInput"
        android:layout_marginTop="16dp" />

    <EditText
        android:id="@+id/registerEmailInput"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="@string/email_hint"
        android:inputType="textEmailAddress"
        android:layout_below="@id/lastNameInput"
        android:layout_marginTop="16dp" />

    <EditText
        android:id="@+id/registerPhoneInput"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="@string/phone_hint"
        android:inputType="phone"
        android:layout_below="@id/registerEmailInput"
        android:layout_marginTop="16dp" />

    <EditText
        android:id="@+id/registerPasswordInput"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="@string/password_hint"
        android:inputType="textPassword"
        android:layout_below="@id/registerPhoneInput"
        android:layout_marginTop="16dp" />

    <Button
        android:id="@+id/createAccountButton"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="@string/create_account_button"
        android:layout_below="@id/registerPasswordInput"
        android:layout_marginTop="24dp" />

</RelativeLayout>



package com.example.myapplication;

import android.content.Intent;
import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

public class RegisterScreen extends AppCompatActivity {

    private EditText firstNameInput;
    private EditText lastNameInput;
    private EditText registerEmailInput;
    private EditText registerPhoneInput;
    private EditText registerPasswordInput;
    private Button createAccountButton;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_register_screen);

        firstNameInput = findViewById(R.id.firstNameInput);
        lastNameInput = findViewById(R.id.lastNameInput);
        registerEmailInput = findViewById(R.id.registerEmailInput);
        registerPhoneInput = findViewById(R.id.registerPhoneInput);
        registerPasswordInput = findViewById(R.id.registerPasswordInput);
        createAccountButton = findViewById(R.id.createAccountButton);

        createAccountButton.setOnClickListener(v -> {
            String firstName = firstNameInput.getText().toString();
            String lastName = lastNameInput.getText().toString();
            String email = registerEmailInput.getText().toString();
            String phone = registerPhoneInput.getText().toString();
            String password = registerPasswordInput.getText().toString();

            User user = new User(firstName, lastName, email, phone, password);
            UserRepository.addUser(user);

            Toast.makeText(
                    RegisterScreen.this,
                    getString(R.string.register_success),
                    Toast.LENGTH_SHORT
            ).show();

            Intent intent = new Intent(RegisterScreen.this, HomeScreen.class);
            startActivity(intent);
            finish();
        });
    }

    @Override
    protected void onStart() {
        super.onStart();
    }

    @Override
    protected void onRestart() {
        super.onRestart();
    }

    @Override
    protected void onResume() {
        super.onResume();
    }

    @Override
    protected void onPause() {
        super.onPause();
    }

    @Override
    protected void onStop() {
        super.onStop();
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
    }
}


_____________________________

package com.example.myapplication;

public class User {

    private String firstName;
    private String lastName;
    private String email;
    private String phone;
    private String password;

    public User(String firstName, String lastName, String email, String phone, String password) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.email = email;
        this.phone = phone;
        this.password = password;
    }

    public String getFirstName() {
        return firstName;
    }

    public String getLastName() {
        return lastName;
    }

    public String getEmail() {
        return email;
    }

    public String getPhone() {
        return phone;
    }

    public String getPassword() {
        return password;
    }
}






package com.example.myapplication;

import java.util.ArrayList;
import java.util.List;

public class UserRepository {

    private static List<User> users = new ArrayList<>();

    static {
        users.add(new User("Marko", "Markovic", "marko@gmail.com", "061111111", "123"));
        users.add(new User("Ana", "Anic", "ana@gmail.com", "062222222", "123"));
        users.add(new User("Petar", "Petrovic", "petar@gmail.com", "063333333", "123"));
    }

    public static void addUser(User user) {
        users.add(user);
    }

    public static boolean login(String email, String password) {
        for (User user : users) {
            if (user.getEmail().equals(email) && user.getPassword().equals(password)) {
                return true;
            }
        }

        return false;
    }

    public static List<User> getUsers() {
        return users;
    }
}

u manifest <activity android:name=".LoginScreen" />
<activity android:name=".RegisterScreen" />
<activity android:name=".HomeScreen" />



<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:id="@+id/homeRoot"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#FFFFFF"
    android:padding="24dp">

    <TextView
        android:id="@+id/homeTitle"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/home_title"
        android:textSize="30sp"
        android:textStyle="bold"
        android:textColor="#000000"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintBottom_toTopOf="@id/changeWallpaperButton"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintVertical_chainStyle="packed" />

    <Button
        android:id="@+id/changeWallpaperButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/change_wallpaper_button"
        android:backgroundTint="#D32F2F"
        android:textColor="#FFFFFF"
        android:layout_marginTop="24dp"
        app:layout_constraintTop_toBottomOf="@id/homeTitle"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>


package com.example.myapplication;

import android.graphics.Color;
import android.os.Bundle;
import android.widget.Button;

import androidx.appcompat.app.AppCompatActivity;
import androidx.constraintlayout.widget.ConstraintLayout;

public class HomeScreen extends AppCompatActivity {

    private ConstraintLayout homeRoot;
    private Button changeWallpaperButton;
    private boolean isWallpaperChanged = false;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_home_screen);

        homeRoot = findViewById(R.id.homeRoot);
        changeWallpaperButton = findViewById(R.id.changeWallpaperButton);

        changeWallpaperButton.setOnClickListener(v -> {
            if (!isWallpaperChanged) {
                homeRoot.setBackgroundColor(Color.parseColor("#BBDEFB"));
                isWallpaperChanged = true;
            } else {
                homeRoot.setBackgroundColor(Color.WHITE);
                isWallpaperChanged = false;
            }
        });
    }

    @Override
    protected void onStart() {
        super.onStart();
    }

    @Override
    protected void onRestart() {
        super.onRestart();
    }

    @Override
    protected void onResume() {
        super.onResume();
    }

    @Override
    protected void onPause() {
        super.onPause();
    }

    @Override
    protected void onStop() {
        super.onStop();
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
    }
}
