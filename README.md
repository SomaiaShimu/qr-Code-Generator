# qr-Code-Generator

# MainActivity
## activity_main.Xml


    <FrameLayout
        android:id="@+id/frameLayout"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_above="@id/bottomNavigationView" />


    <com.google.android.material.bottomnavigation.BottomNavigationView
        android:id="@+id/bottomNavigationView"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        app:labelVisibilityMode="labeled"
        app:menu="@menu/item_menu" />


# MainActivity.Java
package com.savecode.qrcodegenerator;



import android.os.Bundle;
import android.view.MenuItem;

import androidx.annotation.NonNull;
import androidx.appcompat.app.AppCompatActivity;
import androidx.fragment.app.Fragment;
import androidx.fragment.app.FragmentManager;
import androidx.fragment.app.FragmentTransaction;

import com.google.android.material.bottomnavigation.BottomNavigationView;
import com.google.android.material.navigation.NavigationBarView;
import com.savecode.qrcodegenerator.Fragment.HomeFragment;
import com.savecode.qrcodegenerator.Fragment.ScanFragment;


public class MainActivity extends AppCompatActivity {


    BottomNavigationView bottomNavigationView;


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        bottomNavigationView=findViewById(R.id.bottomNavigationView);

        setBottomNavigationView();

        setFragment(new HomeFragment());


    }

    public void setBottomNavigationView(){
        bottomNavigationView.setOnItemSelectedListener(new NavigationBarView.OnItemSelectedListener() {
            @Override
            public boolean onNavigationItemSelected(@NonNull MenuItem item) {
                if (item.getItemId()== R.id.btn_home){
                    setFragment(new HomeFragment());
                }else if (item.getItemId()==R.id.btn_scan){
                    setFragment(new ScanFragment());

                }

                return true;
            }
        });

    }


public void setFragment(Fragment fragment){
    FragmentManager fragmentManager=getSupportFragmentManager();
    FragmentTransaction fragmentTransaction=fragmentManager.beginTransaction();
    fragmentTransaction.add(R.id.frameLayout,fragment);
    fragmentTransaction.commit();
}












}


































