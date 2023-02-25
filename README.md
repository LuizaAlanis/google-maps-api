# Google Maps Api

## Configuração

1. Adicione a dependência do Google Maps em seu arquivo build.gradle:

``` python
implementation 'com.google.android.gms:play-services-maps:17.0.0'
```

2. Adicione a permissão para acessar a localização do usuário em seu arquivo AndroidManifest.xml:

``` xml
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
```

## Implementação

1. Adicione um mapa em seu layout XML:

``` xml
<fragment
    android:id="@+id/mapFragment"
    android:name="com.google.android.gms.maps.SupportMapFragment"
    android:layout_width="match_parent"
    android:layout_height="match_parent" />
```

2. Inicialize o mapa em seu código:

``` kotlin
val mapFragment = supportFragmentManager.findFragmentById(R.id.mapFragment) as SupportMapFragment
mapFragment.getMapAsync { googleMap ->
    // configurações do mapa aqui
}
```

3. Adicione os marcadores no mapa, com suas respectivas informações:

``` kotlin
val myHome = LatLng(-23.560738, -46.674032)
val myHomeMarker = googleMap.addMarker(MarkerOptions()
    .position(myHome)
    .title("Minha Casa")
    .snippet("Informações adicionais aqui")
)
```

4. Adicione um listener para os marcadores, para que o card seja exibido quando o usuário tocar em um marcador:

``` kotlin
googleMap.setOnMarkerClickListener { marker ->
    // exibe o card com as informações adicionais do marcador
    true
}
```

5. Para exibir o card, crie um layout para o card, por exemplo:

``` kotlin
<androidx.cardview.widget.CardView
    android:id="@+id/cardView"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    app:cardCornerRadius="8dp"
    app:cardElevation="8dp"
    app:cardUseCompatPadding="true">

    <!-- Conteúdo do card aqui -->

</androidx.cardview.widget.CardView>
```

6. Para exibir o card, defina a visibilidade do CardView para View.VISIBLE quando o usuário tocar em um marcador:

``` kotlin
val cardView = findViewById<CardView>(R.id.cardView)
googleMap.setOnMarkerClickListener { marker ->
    // exibe o card com as informações adicionais do marcador
    cardView.visibility = View.VISIBLE
    true
}
```

## Observações

- A documentação oficial da Google Maps API para Android é uma ótima fonte de informações, e pode ajudar a esclarecer eventuais dúvidas que você possa ter: https://developers.google.com/maps/documentation/android-sdk/overview

- Este código é apenas um exemplo básico de como adicionar marcadores e um card com informações adicionais no Google Maps em Kotlin. Para um aplicativo completo, é necessário implementar outros recursos, como a solicitação de permissão de localização do usuário, o tratamento de exceções e erros, etc.


https://www.youtube.com/watch?v=suwq7Nta3oM
