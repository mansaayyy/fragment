# fragment

#<fragment
#android:id="@+id/fragments"
#android:layout_width="match_parent"
#android:layout_height="match_parent" />


import android.os.Bundle;
import android.support.v4.app.Fragment;
import android.view.LayoutInflater;
import android.view.ViewGroup;

public class FirstFragment extends Fragment {
@Override
public View onCreateView(LayoutInflater inflater, ViewGroup container,
Bundle savedInstanceState) {
// Inflate the layout for this fragment
return inflater.inflate(R.layout.fragment_first, container, false);
}
}



<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:tools="http://schemas.android.com/tools"
android:layout_width="match_parent"
android:layout_height="match_parent"
android:orientation="vertical"
android:paddingBottom="@dimen/activity_vertical_margin"
android:paddingLeft="@dimen/activity_horizontal_margin"
android:paddingRight="@dimen/activity_horizontal_margin"
android:paddingTop="@dimen/activity_vertical_margin"
tools:context=".MainActivity">
<!-- display two Button's and a FrameLayout to replace the Fragment's  -->
<Button
android:id="@+id/firstFragment"
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:background="@color/button_background_color"
android:text="First Fragment"
android:textColor="@color/white"
android:textSize="20sp" />

<Button
android:id="@+id/secondFragment"
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:layout_marginTop="10dp"
android:background="@color/button_background_color"
android:text="Second Fragment"
android:textColor="@color/white"
android:textSize="20sp" />

<FrameLayout
android:id="@+id/frameLayout"
android:layout_width="match_parent"
android:layout_height="match_parent"
android:layout_marginTop="10dp" />
</LinearLayout>





package com.abhiandroid.fragmentexample;

import android.app.Fragment;
import android.app.FragmentManager;
import android.app.FragmentTransaction;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;

public class MainActivity extends AppCompatActivity {

Button firstFragment, secondFragment;

@Override
protected void onCreate(Bundle savedInstanceState) {
super.onCreate(savedInstanceState);
setContentView(R.layout.activity_main);
// get the reference of Button's
firstFragment = (Button) findViewById(R.id.firstFragment);
secondFragment = (Button) findViewById(R.id.secondFragment);

// perform setOnClickListener event on First Button
firstFragment.setOnClickListener(new View.OnClickListener() {
@Override
public void onClick(View v) {
// load First Fragment
loadFragment(new FirstFragment());
}
});
// perform setOnClickListener event on Second Button
secondFragment.setOnClickListener(new View.OnClickListener() {
@Override
public void onClick(View v) {
// load Second Fragment
loadFragment(new SecondFragment());
}
});

}

private void loadFragment(Fragment fragment) {
// create a FragmentManager
FragmentManager fm = getFragmentManager();
// create a FragmentTransaction to begin the transaction and replace the Fragment
FragmentTransaction fragmentTransaction = fm.beginTransaction();
// replace the FrameLayout with new Fragment
fragmentTransaction.replace(R.id.frameLayout, fragment);
fragmentTransaction.commit(); // save the changes
}
}





package com.abhiandroid.fragmentexample;

import android.app.Fragment;
import android.os.Bundle;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.Button;
import android.widget.Toast;

public class FirstFragment extends Fragment {


View view;
Button firstButton;

@Override
public View onCreateView(LayoutInflater inflater, ViewGroup container,
Bundle savedInstanceState) {
// Inflate the layout for this fragment
view = inflater.inflate(R.layout.fragment_first, container, false);
// get the reference of Button
firstButton = (Button) view.findViewById(R.id.firstButton);
// perform setOnClickListener on first Button
firstButton.setOnClickListener(new View.OnClickListener() {
@Override
public void onClick(View v) {
// display a message by using a Toast
Toast.makeText(getActivity(), "First Fragment", Toast.LENGTH_LONG).show();
}
});
return view;
}
}


<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:tools="http://schemas.android.com/tools"
android:layout_width="match_parent"
android:layout_height="match_parent"
tools:context="com.abhiandroid.fragmentexample.FirstFragment">

<!--TextView and Button displayed in First Fragment -->
<TextView
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:layout_centerHorizontal="true"
android:layout_marginTop="100dp"
android:text="This is First Fragment"
android:textColor="@color/black"
android:textSize="25sp" />

<Button
android:id="@+id/firstButton"
android:layout_width="fill_parent"
android:layout_height="wrap_content"
android:layout_centerInParent="true"
android:layout_marginLeft="20dp"
android:layout_marginRight="20dp"
android:background="@color/green"
android:text="First Fragment"
android:textColor="@color/white"
android:textSize="20sp"
android:textStyle="bold" />
</RelativeLayout>
