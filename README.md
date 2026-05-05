# 📱 Lab 2 – Application Android : Calcul des impôts locaux

## 🎯 But du lab

Créer une application Android qui calcule le **montant total des impôts locaux** en fonction de :

* 📏 La surface de la maison (en m²)
* 🏠 Le nombre de pièces
* 🏊 La présence ou non d’une piscine

---

## 🧱 Étape 1 – Création de l’interface

### 📄 Fichier : `activity_main.xml`

```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:padding="20dp"
    android:gravity="center">

    <EditText
        android:id="@+id/input_surface"
        android:hint="Surface (m²)"
        android:inputType="number" />

    <EditText
        android:id="@+id/input_pieces"
        android:hint="Nombre de pièces"
        android:inputType="number" />

    <CheckBox
        android:id="@+id/checkbox_piscine"
        android:text="Piscine" />

    <Button
        android:id="@+id/button_calcul"
        android:text="Calculer" />

    <TextView
        android:id="@+id/result"
        android:textSize="18sp"
        android:layout_marginTop="20dp" />

</LinearLayout>
```

### 💡 Explication

* **EditText** : saisir des nombres
* **CheckBox** : présence d’une piscine
* **Button** : lancer le calcul
* **TextView** : afficher le résultat

---

## ⚙️ Étape 2 – Code Java

### 📄 Fichier : `MainActivity.java`

```java
public class MainActivity extends AppCompatActivity {

    private EditText surfaceInput, piecesInput;
    private CheckBox piscineCheckbox;
    private TextView resultView;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        surfaceInput = findViewById(R.id.input_surface);
        piecesInput = findViewById(R.id.input_pieces);
        piscineCheckbox = findViewById(R.id.checkbox_piscine);
        resultView = findViewById(R.id.result);

        findViewById(R.id.button_calcul).setOnClickListener(v -> calculer());
    }

    private void calculer() {

        double surface = Double.parseDouble(surfaceInput.getText().toString());
        int pieces = Integer.parseInt(piecesInput.getText().toString());
        boolean piscine = piscineCheckbox.isChecked();

        double impotBase = surface * 2;
        double supplement = pieces * 50 + (piscine ? 100 : 0);
        double total = impotBase + supplement;

        resultView.setText("Impôt total : " + total + " DH");
    }
}
```

---

## 🧠 Fonctionnement

* Conversion des valeurs saisies en nombres
* Vérification de la piscine
* Calcul automatique des impôts
* Affichage du résultat

---

## 📊 Exemple

* Surface = 120
* Pièces = 4
* Piscine = Oui

Résultat :

* Base = 240
* Supplément = 300
* Total = 540 DH

---

## 📝 Résumé

* Interface XML
* Liaison avec Java
* Calcul logique
* Affichage dynamique
