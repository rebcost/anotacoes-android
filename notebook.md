# Recuperar valor de String do tipo TextView

```java
private TextView textView;
String string = textView.getText().toString();
```

# Passar valor de string o TextView

```java
private TextView textView;
textView.setText("Escreva sua mensagem");
```

# Passar um número aleatório para o TextView

```java
TextView texto = findViewById(R.id.textoNumero);
int gerador = new Random().nextInt(11);
texto.setText(String.format(" %d", gerador));
```

# Criar um vetor com string 

```java
public void gerarNovaFrase(View view){

        String[] frases = {
                "Nem todas as tempestades vêm para atrapalhar a sua vida. Algumas vêm para limpar seu caminho.",
                "A persistência realiza o impossível.",
                "Não se desespere quando a caminhada estiver difícil, é sinal de que você está no caminho certo.",
                "Seus sonhos não precisam de plateia, eles só precisam de você.",
                "A persistência é o caminho do êxito.",
                "As pessoas costumam dizer que a motivação não dura sempre. Bem, nem o efeito do banho, por isso recomenda-se diariamente.",
                "No meio da dificuldade encontra-se a oportunidade.",
                "Lute. Acredite. Conquiste. Perca. Deseje. Espere. Alcance. Invada. Caia. Seja tudo o quiser ser, mas, acima de tudo, seja você sempre.",
                "Eu faço da dificuldade a minha motivação. A volta por cima vem na continuação."

        };

        TextView texto = findViewById(R.id.textoResultado);
        texto.setText(frases[new Random().nextInt(frases.length)]);

    }
```

# Recuperar uma imagem 

```java
ImageView imageResultado = findViewById(R.id.imageResultado);
imageResultado.setImageResource(R.drawable.nomeDaImagem);
```

# Escolher uma Cor para o texto

```java
textViewExemplo.setTextColor(escolheCor());

public int escolheCor(){
        int[] cores = {Color.RED, Color.BLACK, Color.BLUE, Color.GREEN, Color.YELLOW};
        return cores[new Random().nextInt(cores.length)];
    }
```



# Radio Button 

```java
opcaoSexo.setOnCheckedChangeListener(new RadioGroup.OnCheckedChangeListener() {
            @Override
            public void onCheckedChanged(RadioGroup radioGroup, int checkedId) {
                if (checkedId == R.id.radioButtonMasculino){
                    resultado.setText("Masculino");
                }else if(checkedId == R.id.radioButtonFeminino){
                    resultado.setText("Feminino");
                }
            }
        });
```

# Toast

```java
Toast toast = Toast.makeText(getApplicationContext(), "Simple Toast In Android", Toast.LENGTH_LONG); // initiate the Toast with context, message and duration for the Toast
toast.setGravity(Gravity.TOP | Gravity.LEFT, 0, 0);     // set gravity for the Toast.
toast.setDuration(Toast.LENGTH_SHORT); // set the duration for the Toast.
toast.show(); // display the Toast
```

```java
// Retrieve the Layout Inflater and inflate the layout from xml
LayoutInflater inflater = getLayoutInflater();
View layout = inflater.inflate(R.layout.custom_toast_layout,
(ViewGroup) findViewById(R.id.toast_layout_root));

// create a new Toast using context
Toast toast = new Toast(getApplicationContext());
toast.setDuration(Toast.LENGTH_LONG); // set the duration for the Toast
toast.setView(layout); // set the inflated layout
toast.show(); // display the custom Toast
```

# Alert Dialog

```java
AlertDialog.Builder alertDialogBuilder = new AlertDialog.Builder(this);

// Setting Alert Dialog Title
alertDialogBuilder.setTitle("Confirm Exit..!!!");

// Icon Of Alert Dialog
alertDialogBuilder.setIcon(R.drawable.question);

// Setting Alert Dialog Message
alertDialogBuilder.setMessage("Are you sure,You want to exit");

alertDialogBuilder.setCancelable(false);
```

```java
alertDialogBuilder.setPositiveButton("yes", new DialogInterface.OnClickListener() {

     @Override
     public void onClick(DialogInterface arg0, int arg1) {
         finish();
     }
 });
```

```java
alertDialogBuilder.setNegativeButton("No", new DialogInterface.OnClickListener() {
    @Override
    public void onClick(DialogInterface dialog, int which) {
    Toast.makeText(MainActivity.this,"You clicked over No",Toast.LENGTH_SHORT).show();
    	}
    });
```

```java
 alertDialogBuilder.setNeutralButton("Cancel", new DialogInterface.OnClickListener() {
     @Override
     public void onClick(DialogInterface dialog, int which) {
     Toast.makeText(getApplicationContext(),"You clicked on Cancel",Toast.LENGTH_SHORT).show();
     	}
     });
```

**Colocar no final do codigo essa parte**

```java
AlertDialog alertDialog = alertDialogBuilder.create();
alertDialog.show();
```

# ToggleButton

Código XML 

```xml
<ToggleButton
    android:id="@+id/simpleToggleButton"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:checked="true" /><!-- set the current state of the toggle button-->
```

```java
ToggleButton simpleToggleButton = findViewById(R.id.simpleToggleButton); // initiate a toggle button
simpleToggleButton.setChecked(true); // set the current state of a toggle button

// displayed text of the toggle button whenever it is in checked or on state
simpleToggleButton.setTextOn("TextOn Attribute Of Toggle b3`utton");
// displayed text of the toggle button whenever it is in unchecked or off state
simpleToggleButton.setTextOff("TextOff Attribute Of Toggle b3`utton");
```

# Switch

```java
// initiate a Switch
Switch simpleSwitch = (Switch) findViewById(R.id.simpleSwitch);

// check current state of a Switch (true or false).
Boolean switchState = simpleSwitch.isChecked();

//displayed text of the Switch
simpleSwitch.setText("switch");

simpleSwitch.setTextOn("On"); // displayed text of the Switch whenever it is in checked or on state
simpleSwitch.setTextOff("Off"); // displayed text of the Switch whenever it is in unchecked i.e. off state
```

# Progress Bar

**Progress bar code xml**

```xml
<ProgressBar
android:id="@+id/simpleProgressBar"
android:layout_width="wrap_content"
android:layout_height="wrap_content" />
```

**Progress bar horizontal code xml**

```xml
<ProgressBar
android:id="@+id/simpleProgressBar"
android:layout_width="fill_parent"
android:layout_height="wrap_content"
style="@style/Widget.AppCompat.ProgressBar.Horizontal"/>
```

```java
ProgressBar simpleProgressBar=(ProgressBar) findViewById(R.id.simpleProgressBar); // initiate the progress bar 
int maxValue=simpleProgressBar.getMax(); // get maximum value of the progress bar

int progressValue=simpleProgressBar.getProgress(); // get progress value from the progress bar

simpleProgressBar.setMax(100); // 100 maximum value for the progress value
simpleProgressBar.setProgress(50); // 50 default progress value for the progress bar
```

# List View

1. Drag list view in Main Activity
2. Another Activity for list View and add UI elements
3. Create custom adapter
4. Set adapter Data to List View
5. Customization
6. On click event

**List view code xml**

```xml
<!-- List Selector Code in ListView -->
<ListView
android:id="@+id/simpleListView"
android:layout_width="fill_parent"
android:layout_height="wrap_content"
android:divider="#f00"
android:dividerHeight="1dp" 
android:listSelector="#0f0"/> <!--list selector in green color-->
```

**Adapter code java**

```java
ArrayAdapter adapter = new ArrayAdapter<String>(this,R.layout.ListView,R.id.textView,StringArray);

```

**Exemplo de Implementação**

```java
public class MainActivity extends Activity
{
    // Array of strings...
    ListView simpleList;
    String countryList[] = {"India", "China", "australia", "Portugle", "America", "NewZealand"};

    @Override   protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);      
        setContentView(R.layout.activity_main);
        simpleList = (ListView)findViewById(R.id.simpleListView);
        ArrayAdapter<String> arrayAdapter = new ArrayAdapter<String>(this, R.layout.activity_listview, R.id.textView, countryList);
        simpleList.setAdapter(arrayAdapter);
    }
}
```

![listview](/home/filipe/Pictures/Screenshots/listview.png)

# List View Customizada

**Step 1:** [Create a new project](https://abhiandroid.com/androidstudio/start-create-project) Listebasexample and activity Main Activity. Here we will create a ListView in LinearLayout. **Below is the code of activity_main.xml or content_main.xml:**

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
android:layout_width="match_parent"
android:layout_height="match_parent"
android:orientation="vertical">

<ListView
android:id="@+id/simpleListView"
android:layout_width="fill_parent"
android:layout_height="wrap_content"
android:divider="@color/material_blue_grey_800"
android:dividerHeight="1dp"
android:footerDividersEnabled="false" />
</LinearLayout>	
```

**Step 2:** Create a new activity name Listview and below is the code of activity_listview.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
android:layout_width="match_parent"
android:layout_height="match_parent"
android:orientation="horizontal">

<ImageView
android:id="@+id/icon"
android:layout_width="50dp"
android:layout_height="50dp"
android:src="@drawable/ic_launcher" />

<TextView
android:id="@+id/textView"
android:layout_width="fill_parent"
android:layout_height="wrap_content"
android:layout_gravity="center"
android:padding="@dimen/activity_horizontal_margin"
android:textColor="@color/black" />
</LinearLayout>
```

**Step 3:** In third step we will use custom adapter to display the country names in UI by coding MainActivity.[java](https://abhiandroid.com/java/).

```java
public class MainActivity extends Activity {

    ListView simpleList;
    String countryList[] = {"India", "China", "australia", "Portugle", "America", "NewZealand"};
    int flags[] = {R.drawable.india, R.drawable.china, R.drawable.australia, R.drawable.portugle, R.drawable.america, R.drawable.new_zealand};

    @Override
    protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);
    simpleList = findViewById(R.id.simpleListView);
    CustomAdapter customAdapter = new CustomAdapter(getApplicationContext(), countryList, flags);
    simpleList.setAdapter(customAdapter);
    }
}
```

**Step 4:** Now create another class Custom Adapter which will extend BaseAdapter. Below is the code of CustomAdapter.[java](https://abhiandroid.com/java/)

```java
public class CustomAdapter extends BaseAdapter {
    Context context;
    String countryList[];
    int flags[];
    LayoutInflater inflter;

    public CustomAdapter(Context applicationContext, String[] countryList, int[] flags) {
    this.context = context;
    this.countryList = countryList;
    this.flags = flags;
    inflter = (LayoutInflater.from(applicationContext));
    }

    @Override
    public int getCount() {
    return countryList.length;
    }

    @Override
    public Object getItem(int i) {
    return null;
    }

    @Override
    public long getItemId(int i) {
    return 0;
    }

    @Override
    public View getView(int i, View view, ViewGroup viewGroup) {
        view = inflter.inflate(R.layout.activity_listview, null);
        TextView country = (TextView) view.findViewById(R.id.textView);
        ImageView icon = (ImageView) view.findViewById(R.id.icon);
        country.setText(countryList[i]);
        icon.setImageResource(flags[i]);
    return view;
}
```

# Recycler View 

[Tutorial FreshByte](https://www.freshbytelabs.com/2018/12/android-recyclerview-with-cardview.html)

[Tutorial Android Development](https://developer.android.com/guide/topics/ui/layout/recyclerview?hl=pt-br)

1. No activity_main.xml arrastar para dentro o recycler view
1. Criar um layout_recyclerView.xml e montar a seu estilo de visualização
1. Criar três packages(activity, adapter, model)
1. Criar uma classe adapter.java dentro do package adapter e fazer sua configuração
1. Configurar o recycler View no mainActivity
1. Criar uma classe model dentro do package model e fazer sua configuração



**Configuração do RecyclerView no ActivityMain**

```java
RecyclerView recyclerView = findViewById(R.id.recyclerView);

//Configurar Recyclerview
RecyclerView.LayoutManager layoutManager = new LinearLayoutManager(getApplicationContext());
recyclerView.setLayoutManager(layoutManager);
recyclerView.setHasFixedSize(true);
recyclerView.addItemDecoration(new DividerItemDecoration(this, LinearLayout.VERTICAL));
recyclerView.setAdapter(adicionar o adapter);

```

**Clean code adapter**

```java
public class Adapter extends RecyclerView.Adapter<Adapter.MyViewHolder> {

    @NonNull
    @Override
    public MyViewHolder onCreateViewHolder(@NonNull ViewGroup parent, int viewType) {
        return null;
    }

    @Override
    public void onBindViewHolder(@NonNull MyViewHolder holder, int position) {

    }

    @Override
    public int getItemCount() {
        return 0;
    }

    public class MyViewHolder extends RecyclerView.ViewHolder{
        public MyViewHolder(@NonNull View itemView) {
            super(itemView);
        }
    }
}
```

Dentro da classe MyViewHolder definir os atributos do que vai conter essa RecyclerView por exemplo: 

```java
public class MyViewHolder extends RecyclerView.ViewHolder{

        TextView titulo;
        TextView genero;
        TextView ano;

        public MyViewHolder(@NonNull View itemView) {
            super(itemView);
            
           titulo 	= itemView.findViewById(R.id.textTitulo);
           ano 		= itemView.findViewById(R.id.textAno);
           genero 	= itemView.findViewById(R.id.textGenero);

        }
    }
```

**Configuração do método onCreateViewHolder**

É o método responsável por criar a visualização

- Criar um elemento do tipo View
- Retorna um objeto ViewHolder que recebe como parâmetro um tipo View.

```java
public MyViewHolder onCreateViewHolder(@NonNull ViewGroup parent, int viewType) {
        View itemLista = LayoutInflater.from(parent.getContext())
                .inflate(R.layout.recycler_frutas, parent, false);
        return new MyViewHolder(itemLista);
    }
```

**Configuração do método onBindViewHolder**

É o método responsável por mostrar os itens na tela.

*obs: Esse método exibe os itens de maneira estática.*

```java
@Override
    public void onBindViewHolder(@NonNull MyViewHolder holder, int position) {
        holder.titulo.setText ("Titulo de teste");
        holder.genero.setText( "Comédia");
        holder.ano.setText( "2017") ;

    }
```

**Configuração do método onBindViewHolder (Forma dinâmica)**

*obs: Somente será possível implementar essa funcionalidade quando a classe model estiver configurada com seus getters e setters.*

```java
@Override
public void onBindViewHolder(MyViewHolder holder, int position) {

    Filme filme = listaFilmes.get( position );
    holder. titulo.setText( filme.getTituloFilme() );
    holder.genero.setText( filme.getGenero() );
    holder.ano.setText( filme.getAno() );

```

Voltamos ao activityMain para instanciar o adapter e para configurar um tipo list.

```java
//Configurar adapter
Adapter adapter = new Adapter();
```

```java
//No mainActivity
private List<Filme> listaFilme = new ArrayList<>();
```

Voltamos a classe adapter e vamos configurar um construtor para receber uma lista. Vamos configurar o método getItemCount()

```java
public class Adapter extends RecyclerView.Adapter<Adapter.MyViewHolder> {

private List<Filme> ListaFilmes;

public Adapter(List<Filme> lista) {
	this.ListaFilmes = Lista;
}
```

**Configuração do método getItemCount**

```java
@Override
public int getItemCount() {
	return ListaFilmes.size();
}
```

Voltamos ao activityMain para passar como parâmetro o tipo lista para o adapter

```java
Adapter adapter = new Adapter(listaFilme);
```

**Configuração da classe model**

Adicionar os mesmos atributos da classe MyViewHolder *(titulo, genero, ano)*. Implementar os construtores, getters e setters.

```java
public class Filme
    
    private String tituloFilme;
	private String genero;
    private String ano;

    public Filme (){ }
	public Filme (String tituloFilme, String genero, String ano) {
        this. tituloFilme = tituloFilme;
        this. genero = genero;
        this. ano = ano;

```

Vamos criar um método na MainActivity que será reponsável por configurar os filmes

```java
recyclerView = findViewById(R. id.recyclerView) ;
//Listagem de filmes
this.criarFilmes();

public void criarFilmes(){ 
	Filme filme = new Filme(tituloFilme: "titulo", genero: "genero", ano: 2017");
	listaFilme.add(filme)
}
```

**Configuração de eventos de click no RecyclerView**

No MainActivity criar a configuração do evento

[Baixar o código para evento de click (RecyclerItemClickListener)](https://github.com/jamiltondamasceno/RecyclerItemClickListener/blob/master/RecyclerItemClickListener.java) e colar dentro do ambiente de desenvolvimento.

```java
//Configurar Evento de Click
        recyclerView.addOnItemTouchListener(
            new RecyclerItemClickListener(
                    getApplicationContext(),
                    recyclerView,
                    new RecyclerItemClickListener.OnItemClickListener() {
                        @Override
                        public void onItemClick(View view, int position) {
                            Filme filme = listaFilmes.get(position);
                            Toast.makeText(
                                    getApplicationContext(),
                                    "Item Pressionado " + filme.getTituloFilme(),
                                    Toast.LENGTH_SHORT
                            ).show();
                        }

                        @Override
                        public void onLongItemClick(View view, int position) {
                            Filme filme = listaFilmes.get(position);
                            Toast.makeText(
                                    getApplicationContext(),
                                    "Clique Longo " + filme.getAno(),
                                    Toast.LENGTH_SHORT
                            ).show();

                        }

                        @Override
                        public void onItemClick(AdapterView<?> adapterView, View view, int i, long l) {

                        }
                    }
            )
        );
```

# Passando Dados entre Activities

- Na activity 1 foi criado uma tela com um botão para chamar a activity 2
- Na activity 2 temos um editText com nome e idade
- Na activity 3 é exibido o resultado 

**Code Activity 1**

```java
public class MainActivity extends AppCompatActivity {

    private Button buttonEnviar;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        buttonEnviar = findViewById(R.id.buttonEntrar);
        buttonEnviar.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent intent = new Intent(getApplicationContext(), SecondActivity.class);
                startActivity(intent);
            }
        });

    }
}
```

**Code Activity 2**

```java
ublic class SecondActivity extends AppCompatActivity {

    private EditText editTextNome, editTextIdade;
    private Button buttonEnviar;

    @SuppressLint("MissingInflatedId")
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_second);

        editTextNome =  findViewById(R.id.editTextNome);
        editTextIdade = findViewById(R.id.editTextIdade);
        buttonEnviar = findViewById(R.id.buttonEnviar);

        buttonEnviar.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent intent = new Intent(getApplicationContext(), ThirdActivity.class);
                //Passando os dados
                intent.putExtra("nome", ""+editTextNome.getText());
                intent.putExtra("idade", ""+editTextIdade.getText());

                startActivity(intent);

            }
        });

```

**Code Activity 3**

```java
public class ThirdActivity extends AppCompatActivity {

    private TextView textViewNome, textViewIdade;

    @SuppressLint("MissingInflatedId")
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_third);

        textViewNome =  findViewById(R.id.textViewNome);
        textViewIdade = findViewById(R.id.textViewIdade);

        // Recuperar dados
        Bundle dados = getIntent().getExtras();
        String nome = dados.getString("nome");
        String idade = dados.getString("idade");

        //Configurar valores recuperados
        textViewNome.setText(nome);
        textViewIdade.setText(idade);

    }
}
```

# Fragments

- Adicionar dois botões (fragment1 e fragment2)
- Criar uma estrutura frameLayout clicar e arrastar para dentro do activity
- Criar dois packages (activity, fragment)
- Clicar com botão direito no package fragment >  novo  > fragment(blank)
  - Criar fragment PrimeiroFragment e SegundoFragment
- No Main Activity criar uma instância do Primeiro e Segundo Fragment



**Code Main Activity**

*obs: Ao usar o objeto **FragmentTransaction** utilizar do package **androidx.fragment.app***

```java
public class MainActivity extends AppCompatActivity {

    private Button buttonFragment1, buttonFragment2;
    private PrimeiroFragment primeiroFragment;
    private SegundoFragment segundoFragment;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        buttonFragment1 = findViewById(R.id.buttonFragment1);
        buttonFragment2 = findViewById(R.id.buttonFragment2);

        primeiroFragment = new PrimeiroFragment();

        // Configura objeto para fragmento
        FragmentTransaction transaction = getSupportFragmentManager().beginTransaction();
        transaction.replace(R.id.frameConteudo, primeiroFragment);
        transaction.commit();

        buttonFragment1.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                primeiroFragment = new PrimeiroFragment();

                FragmentTransaction transaction = getSupportFragmentManager().beginTransaction();
                transaction.replace(R.id.frameConteudo, primeiroFragment);
                transaction.commit();
            }
        });

        buttonFragment2.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                segundoFragment = new SegundoFragment();
                
                FragmentTransaction transaction = getSupportFragmentManager().beginTransaction();
                transaction.replace(R.id.frameConteudo, segundoFragment);
                transaction.commit();
            }
        });


    }
}
```



**Code Primeiro Fragment**

```java
public class PrimeiroFragment extends Fragment {

    private TextView textViewFragment1;

    public PrimeiroFragment (){

    }

    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {

        View view = inflater.inflate(R.layout.fragment_primeiro, container, false);
        textViewFragment1 = view.findViewById(R.id.textViewFragment1);
        textViewFragment1.setText("Fragment 1");
        return view;
    }
}
```

**Code Segundo Fragment**

```java
public class SegundoFragment extends Fragment {

    private TextView textViewFragment2;

    public SegundoFragment() {
        // Required empty public constructor
    }

    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        // Inflate the layout for this fragment
        View view = inflater.inflate(R.layout.fragment_segundo, container, false);
        textViewFragment2 = view.findViewById(R.id.textViewFragment2);
        textViewFragment2.setText("Fragment 2");

        return view;
    }
}
```

# Snackbar

```java
buttonAbrir = findViewById(R.id.buttonAbrir);
        buttonAbrir.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Snackbar.make(view, "Botão Precionado", Snackbar.LENGTH_LONG).setAction( // configura snakbar
                        "Confirmar", new View.OnClickListener() {
                            @Override
                            public void onClick(View view) {
                                buttonAbrir.setText("Botão abrir alterado");
                            }
                        }
                ).setActionTextColor(getResources().getColor(R.color.teal_200)) // atribui uma cor ao botao
                        .show();

            }
        });
```

 

# Navegation Drawer

O *Navigation Drawer* é usado para facilitar a navegação no aplicativo e evitar que o usuário fique perdido na troca entre uma tela e outra.

<div> 
    <center>
       <img src="https://luizmarcus.com/wp-content/uploads/2016/07/drawer-300x533.png" height="300px" wight="100px"> 
    </center> 
</div>





### Links Úteis

- [Intents e filtros de intents](https://developer.android.com/guide/components/intents-filters?hl=pt-)
- [Mine Types ](https://www.sitepoint.com/mime-types-complete-list/)
-  [Criar About me](https://github.com/medyo/android-about-page)

 

# Executando sons

1. Clicar com o botão direito do mouse sobre res new > Android Resouces > escolher a opção Raw
2. Adicionar as músicas para dentro dessa pasta
3. Na classe MainActivity criar um atributo do tipo Media player 

```java
private MediaPlayer mediaPlayer;
```

4. Configurar o objeto MediaPlayer

```java
mediaPlayer = MediaPlayer.create(getApplicationContext(), R.raw.bach);
```

5. Configurar os botões *play, pause, stop* e adicionar suas funcionalidades

```java
Button buttonPlay = findViewById(R.id.ButtonPlay);
Button buttonPause = findViewById(R.id.ButtonPause);
Button buttonStop = findViewById(R.id.ButtonStop);

buttonPlay.setOnClickListener(new View.OnClickListener() {// inicia a execução da música
            @Override
            public void onClick(View v) {
                if(mediaPlayer != null){
                    mediaPlayer.start();
                }
            }
        });
        
 buttonPause.setOnClickListener(new View.OnClickListener() { // pausa a musica
            @Override
            public void onClick(View v) {
                if (mediaPlayer.isPlaying()){
                    mediaPlayer.pause();
                }
            }
        });  
        
buttonStop.setOnClickListener(new View.OnClickListener() { // stop a musica
            @Override
            public void onClick(View v) {
                if(mediaPlayer.isPlaying()){
                    mediaPlayer.stop();
                    mediaPlayer = MediaPlayer.create(getApplicationContext(), R.raw.bach);
                }
            }
        });
```

6. Definir como escopo global SeekBar e AudioManager.

```JAVA
private SeekBar seekBarVolume;
private AudioManager audioManager;
```

7. Criar um método para configuração da seekbar

```java
mediaPlayer = MediaPlayer.create(getApplicationContext(), R.raw.bach);

incializarSeekBar();
```

```java
private void incializarSeekBar() {
        seekBarVolume = findViewById(R.id.seekVolume);

        // Configura audio manager
        audioManager = (AudioManager) getSystemService(Context.AUDIO_SERVICE);

        // recupera os valores do volume máximo e o volume atual
        int volMaximo = audioManager.getStreamMaxVolume(AudioManager.STREAM_MUSIC);
        int volAtual = audioManager.getStreamVolume(AudioManager.STREAM_MUSIC);

        // Configura os valores máximos para o seekbar
        seekBarVolume.setMax(volMaximo);

        // Configura o progresso atual do seekbar
        seekBarVolume.setProgress(volAtual);

        // Permitir que o usuário configure a seekbar
        seekBarVolume.setOnSeekBarChangeListener(new SeekBar.OnSeekBarChangeListener() {
            @Override
            public void onProgressChanged(SeekBar seekBar, int progress, boolean fromUser) {
                audioManager.setStreamVolume(AudioManager.STREAM_MUSIC, progress, 0);
            }

            @Override
            public void onStartTrackingTouch(SeekBar seekBar) {

            }

            @Override
            public void onStopTrackingTouch(SeekBar seekBar) {

            }
        });

    }
```

8. Configurar o ciclo de vida do app *(onStart, onStop, onDestroy)*

   ```java
   @Override
       protected void onStart() {
           super.onStart();
           if(mediaPlayer != null){
               mediaPlayer.start();
           }
       }
   
       @Override
       protected void onStop() {
           super.onStop();
           if (mediaPlayer.isPlaying()){
               mediaPlayer.pause();
           }
   
       }
   
       @Override
       protected void onDestroy() {
           super.onDestroy();
           if (mediaPlayer != null && mediaPlayer.isPlaying()){
               mediaPlayer.stop();
               mediaPlayer.release(); // liberar a musica da memoria
               mediaPlayer = null;
           }
       }
   ```

   

# Executando Vídeos

1.  Ao criar o projeto criar uma pasta do tipo *Android Resourses Diretory* do tipo *Raw* e adicionar o vídeo
2. Criar uma nova *Activity* para adicionar os recursos do player de vídeo 
3. Criar um atributo do tipo *VideoView* e atribuir o *id*

```java
private VideoView videoView;
videoView = findViewById(R.id.videoView);
```

4. Configurar para ocutar o *actionBar , statusBar e barra de navegacão*

```java
//Ocutar actionbar
getSupportActionBar().hide();

//Esconde statusbar e barra de navegação
View decorView =  getWindow().getDecorView();
int uiOpcoes = View.SYSTEM_UI_FLAG_FULLSCREEN | View.SYSTEM_UI_FLAG_HIDE_NAVIGATION;
decorView.setSystemUiVisibility(uiOpcoes);
```

5. Código para executar vídeo

```java
// Executar video
videoView.setMediaController(new MediaController(this));
// Acessar local que está armazendo o video
videoView.setVideoPath("android.resource://" + getPackageName() + "/" + R.raw.video);
videoView.start();
```

6. Na *MainActivity* criar o método **abrirVideo** e passar como *onClick* para o botão play.

```java
    public void abrirVideo(View view){
        startActivity(new Intent(this, PlayerActivity.class));
    }
```

# Abas

1. Adicionar a dependência [SmartTabLayout](https://github.com/ogaclejapan/SmartTabLayout/) ao projeto 

```java
    implementation'com.ogaclejapan.smarttablayout:library:2.0.0@aar'

    //Optional: see how to use the utility.
    implementation 'com.ogaclejapan.smarttablayout:utils-v4:2.0.0@aar'
```

2. Adicionar o trecho de código abaixo dentro do *activity_main.xml* 

​	***obs: Mudar de constrain para linearLayout - Vertical***

```xml
<com.ogaclejapan.smarttablayout.SmartTabLayout
    android:id="@+id/viewpagertab"
    android:layout_width="match_parent"
    android:layout_height="48dp"
    app:stl_indicatorAlwaysInCenter="false"
    app:stl_indicatorWithoutPadding="false"
    app:stl_indicatorInFront="false"
    app:stl_indicatorInterpolation="smart"
    app:stl_indicatorGravity="bottom"
    app:stl_indicatorColor="#40C4FF"
    app:stl_indicatorThickness="4dp"
    app:stl_indicatorWidth="auto"
    app:stl_indicatorCornerRadius="2dp"
    app:stl_overlineColor="#4D000000"
    app:stl_overlineThickness="0dp"
    app:stl_underlineColor="#4D000000"
    app:stl_underlineThickness="1dp"
    app:stl_dividerColor="#4D000000"
    app:stl_dividerThickness="1dp"
    app:stl_defaultTabBackground="?attr/selectableItemBackground"
    app:stl_defaultTabTextAllCaps="true"
    app:stl_defaultTabTextColor="#FC000000"
    app:stl_defaultTabTextSize="12sp"
    app:stl_defaultTabTextHorizontalPadding="16dp"
    app:stl_defaultTabTextMinWidth="0dp"
    app:stl_distributeEvenly="false"
    app:stl_clickable="true"
    app:stl_titleOffset="24dp"
    app:stl_drawDecorationAfterTab="false"
    />

<androidx.viewpager.widget.ViewPager
    android:id="@+id/viewpager"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:layout_below="@id/viewpagertab"
    />
```

3. No *MainActitvity.java* criar uma referência para a *SmartTabLayout* epara o *ViewPager*

```java
private SmartTabLayout smartTabLayout;
private ViewPager viewPager;
```

4. Configurar o adapter para as tabs

   ```java
   FragmentPagerItemAdapter adapter = new FragmentPagerItemAdapter(
           getSupportFragmentManager(), FragmentPagerItems.with(this)
           .add(R.string.titleA, PageFragment.class)
           .add(R.string.titleB, PageFragment.class)
           .create());
   ```

5.  Criar um *package **fragment*** e adicionar um novo fragmento. 

   ***obs: Criar um fragment por aba***

6. Mostrar as tabs 

   ```java
   viewPager.setAdapter(adapter);
   smartTabLayout.setViewPager(viewPager);
   ```

### Personalizando Abas

1. Configuracão da elevacão da SmartTabBar

   ```java
   // Configura a elevação da smartab
   Objects.requireNonNull(getSupportActionBar()).setElevation(0);
   ```

2. Configuracao dos atributos no arquivo xml. Para mais detalhes acessar o [link](https://github.com/ogaclejapan/SmartTabLayout/#attributes)

```xml
<com.ogaclejapan.smarttablayout.SmartTabLayout
        android:id="@+id/viewPagerTab"
        android:layout_width="match_parent"
        android:layout_height="48dp"
        android:background="@color/primary"
        app:stl_clickable="true"

        app:stl_defaultTabBackground="?attr/selectableItemBackground"
        app:stl_defaultTabTextAllCaps="true"
        app:stl_defaultTabTextColor="@color/white"
        app:stl_defaultTabTextHorizontalPadding="16dp"
        app:stl_defaultTabTextMinWidth="0dp"
        app:stl_defaultTabTextSize="14sp"
        app:stl_distributeEvenly="false"
        app:stl_dividerColor="#4D000000"
        app:stl_dividerThickness="1dp"
        app:stl_drawDecorationAfterTab="false"

        app:stl_indicatorAlwaysInCenter="false"
        app:stl_indicatorColor="@color/white"
        app:stl_indicatorCornerRadius="2dp"
        app:stl_indicatorGravity="bottom"
        app:stl_indicatorInFront="false"
        app:stl_indicatorInterpolation="smart"
        app:stl_indicatorThickness="4dp"
        app:stl_indicatorWidth="auto"
        app:stl_indicatorWithoutPadding="false"

        app:stl_overlineColor="#4D000000"
        app:stl_overlineThickness="0dp"
        app:stl_titleOffset="24dp"
        app:stl_underlineColor="#4D000000"
        app:stl_underlineThickness="1dp"
        tools:ignore="SpeakableTextPresentCheck" />
```

### Configurando Fragment para eventos de click

1. Na classe *fragment* implementar a funcão para click. Adicionar o código abaixo após a palavra *Fragment*. Em seguida, adicionar o método onClick.

```java
implements View.OnClickListener
```

2. Declarar minhas variáveis que serão os botões

```java
private ImageView buttonCao, buttonGato, buttonLeao, buttonMacaco, buttonOvelha, buttonVaca;
```

3. Declarar o MediaPlayer

```java
private MediaPlayer mediaPlayer;
```

4. Dentro do método *OnCreateView* declarar os *ids* e aplicar os eventos de click para cada botão.

```java
public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        // Inflate the layout for this fragment
        View view = inflater.inflate(R.layout.fragment_animais, container, false);

        // Define Ids
        buttonCao = view.findViewById(R.id.buttonCao);
        buttonGato = view.findViewById(R.id.buttonGato);
        buttonLeao = view.findViewById(R.id.buttonLeao);
        buttonMacaco = view.findViewById(R.id.buttonMacaco);
        buttonOvelha = view.findViewById(R.id.buttonOvelha);
        buttonVaca = view.findViewById(R.id.buttonVaca);

        //Aplica os eventos de click
        buttonCao.setOnClickListener(this);
        buttonGato.setOnClickListener(this);
        buttonLeao.setOnClickListener(this);
        buttonMacaco.setOnClickListener(this);
        buttonOvelha.setOnClickListener(this);
        buttonVaca.setOnClickListener(this);

        return view;
    }
```

5. No método *onClick* adicionar um *switch - case* para cada botão.

```java
public void onClick(View view) {
        switch (view.getId()){
            case R.id.buttonCao:
                reproduzirSom(R.raw.dog);
                break;
            case R.id.buttonGato:
                reproduzirSom(R.raw.cat);
                break;
            case R.id.buttonLeao:
                reproduzirSom(R.raw.lion);
                break;
            case R.id.buttonMacaco:
                reproduzirSom(R.raw.monkey);
                break;
            case R.id.buttonOvelha:
                reproduzirSom(R.raw.sheep);
                break;
            case R.id.buttonVaca:
                reproduzirSom(R.raw.cow);
                break;
        }
    }
```

7. Criar um método que será responsável por reproduzuir o som.

```java
public void reproduzirSom(int nomeAudio){
        mediaPlayer = MediaPlayer.create(getActivity(), nomeAudio);
        if (mediaPlayer != null){
            mediaPlayer.start();

            mediaPlayer.setOnCompletionListener(new MediaPlayer.OnCompletionListener() {
                @Override
                public void onCompletion(MediaPlayer mediaPlayer) {
                    mediaPlayer.release();
                }
            });
        }
    }
```

8. Adicionar o método *OnDestroy*

```java
 @Override
    public void onDestroy() {
        super.onDestroy();
        if(mediaPlayer != null){
            mediaPlayer.release();
            mediaPlayer = null;
        }
    }
```

# Salvando Dados no dispositivo

1. Criar uma constante para receber o nome do arquivo

```java
private static final String ARQUIVO_PREFERENCIA = "ArquivoPreferencia";
```

2. Criar um objeto do tipo *SharedPreferences* e em seguida um editor.

```java
SharedPreferences preferences = getSharedPreferences(ARQUIVO_PREFERENCIA, 0 );
                SharedPreferences.Editor editor =  preferences.edit();
```

3. Armazenar os dados dentro do arquivo

```java
String nome = Objects.requireNonNull(editNome.getText()).toString();

//armazena os dados
editor.putString("Nome", nome);
editor.commit();

textViewResultado.setText("Olá "+nome);
```

4. Recupera os dados salvos

```java
SharedPreferences preferences = getSharedPreferences(ARQUIVO_PREFERENCIA, 0 );
```

5.  Validacão dos dados em *preferences*

```java
//Valida se temos o nome em preferencia
if (preferences.contains("nome")){
    String nome =  preferences.getString("nome", "usuário não definido");
    textViewResultado.setText("Olá "+nome);
}else{
    textViewResultado.setText("Olá, usuário não definido");
}
```

### Código completo

```java
public class MainActivity extends AppCompatActivity {

    private Button buttonSalvar;
    private TextView textViewResultado;
    private TextInputEditText editNome;
    private static final String ARQUIVO_PREFERENCIA = "ArquivoPreferencia";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        buttonSalvar = findViewById(R.id.buttonSalavar);
        textViewResultado = findViewById(R.id.textResultado);
        editNome = findViewById(R.id.editNome);

        buttonSalvar.setOnClickListener(new View.OnClickListener() {
            @SuppressLint("SetTextI18n")
            @Override
            public void onClick(View v) {
                SharedPreferences preferences = getSharedPreferences(ARQUIVO_PREFERENCIA, 0 );
                SharedPreferences.Editor editor =  preferences.edit();

                // validacao
                if (editNome.getText().equals(" ")){
                    Toast.makeText(getApplicationContext(),
                            "Preencha o texto",
                            Toast.LENGTH_LONG).show();
                }else{
                    String nome = Objects.requireNonNull(editNome.getText()).toString();
                    editor.putString("Nome", nome);
                    editor.commit();
                    textViewResultado.setText("Olá "+nome);
                }

            }
        });

        //Recupera os dados salvos
        SharedPreferences preferences = getSharedPreferences(ARQUIVO_PREFERENCIA, 0 );

        //Valida se temos o nome em preferencia
        if (preferences.contains("nome")){
            String nome =  preferences.getString("nome", "usuário não definido");
            textViewResultado.setText("Olá "+nome);
        }else{
            textViewResultado.setText("Olá, usuário não definido");
        }

    }
}
```

### Criando uma classe a parte para salvar as preferências

1. Criar uma nova classe preferencias.java
2. Adicionar um atributo do tipo *Context* e outro do tipo *SharedPreferences*

```java
private Context context;
private SharedPreferences preferences;
```

3. Adicionar um construtor a classe e passar o *context* como parâmetro

```java
    public AnotacoesPreferencias(Context c) {
        this.context = c;     
    }
```

4. No *MainActivity* declarar o objeto do tipo Preferencia e passando como parâmetro o contexto.

```java
private AnotacoesPreferencias preferencias;

preferencias = new AnotacoesPreferencias(getApplicationContext());
```

5. Criar um atributo para o nome do aquivo.

```java
private final String NOME_ARQUIVO = "anotacao.preferencias";
```

6. Dentro do construtor **AnotacoesPreferencias ** adicionar o preferences

```java
public AnotacoesPreferencias(Context c) {
        this.context = c;
        preferences = context.getSharedPreferences(NOME_ARQUIVO, 0);
    	editor = preferences.edit();
    }
```

7. Criar um atributo **editor**

```
private SharedPreferences.Editor editor;
```

8. Adicionar ao construtor

```java
public AnotacoesPreferencias(Context c) {
        this.context = c;
        preferences = context.getSharedPreferences(NOME_ARQUIVO, 0);
    	editor = preferences.edit();
    }
```

9. Criar dois métodos **salvar e recuperar**. O método recuperar vai depender do tipo de dado que deseja retornar, nesse caso é do tipo String.

```java
public void salvar(){

    }

public String recuperar(){

	return "";
}
```

10. Criar um atributo que serve como chave para ser recuperado seu valor dentros dos métodos

```java
private final String CHAVE_NOME = "nome";
```

11. Dentro do método salvar adicionar os seguintes códigos

```java
public void salvar(String anotacao){
        editor.putString(CHAVE_NOME, anotacao);
        editor.commit();
    }
```

12. Dentro do método recuperar adicionar os seguites códigos

```java
public String recuperar(){
        return preferences.getString(CHAVE_NOME,"");
    }
```

13. Retornar a *ActivityMain* e criar o objeto Anotacoes preferencias

```java
 // Fora do OnCreate
 private AnotacoesPreferencias preferencias;
 // Dentro do OnCreate
 preferencias = new AnotacoesPreferencias(getApplicationContext());
```

14. Adicionar a validacão para recuperacão do texto digitado pelo usuário

```java
binding.fab.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                // validar se foi digitado algo
                String textoRecuperado = editAnotacao.getText().toString();
                if (textoRecuperado.equals("")){
                    Snackbar.make(view, "Preencha a anotação", Snackbar.LENGTH_LONG).show();
                }else{
                    preferencias.salvar(textoRecuperado);
                    Snackbar.make(view, "Anotação Salva com sucesso!", Snackbar.LENGTH_LONG).show();
                }
            }
        });
```

15. Recuperando os valores salvos

```java
// Recuperar anotacao
    String anotacao = preferencias.recuperar();
    if (!anotacao.equals("")){
        editAnotacao.setText(anotacao);
    }
```

# Bancos de Dados - SQLite

1. Criar o banco de dados

```java
SQLiteDatabase bancoDados = openOrCreateDatabase("app", MODE_PRIVATE, null);
```

2. Criar uma tabela 

```sql
bancoDados.execSQL("CREATE TABLE IF NOT EXISTS pessoas (nome VARCHAR, idade INT(3))");

```

```sqlite
// Tabela com chave primária
bancoDados.execSQL("CREATE TABLE IF NOT EXISTS pessoas (id INTEGER PRIMARY KEY AUTOINCREMENT, nome VARCHAR, idade INT(3))");
```

3. Inserir dados

```sql
bancoDados.execSQL("INSERT INTO pessoas(nome, idade) VALUES('Filipe', 25) ");
```

4.  Recuperando os dados

```java
Cursor cursor = bancoDados.rawQuery("SELECT nome, idade FROM pessoas", null);

// Indices da tabela
int indiceNome = cursor.getColumnIndex("nome");
int indiceIdade = cursor.getColumnIndex("idade");

//Iniciar o cursor
cursor.moveToFirst();

//Exibir todos os itens
while (cursor != null){
    Log.i("RESULTADO - nome: ", cursor.getString(indiceNome));
    Log.i("RESULTADO - Idade: ", cursor.getString(indiceIdade));
    cursor.moveToNext(); // move o cursor para o proximo item da lista
}
```

5. Fazer consultas

```java
String consulta = "SELECT nome, idade " +
                                "FROM pessoas WHERE nome = 'Filipe'";
Cursor cursor = bancoDados.rawQuery(consulta, null);

```

```
String consulta = "SELECT nome, idade FROM pessoas WHERE idade > 25";
Cursor cursor = bancoDados.rawQuery(consulta, null);
```

```
String consulta = "SELECT nome, idade FROM pessoas WHERE idade < 25 OR idade = 16";
Cursor cursor = bancoDados.rawQuery(consulta, null);
```

```
String consulta = "SELECT nome, idade FROM pessoas WHERE idade IN (18, 25)";
Cursor cursor = bancoDados.rawQuery(consulta, null);
```

```
String consulta =
         "SELECT nome, idade FROM pessoas " +
                " WHERE idade BETWEEN 35 AND 50 ";

```

```java
/* O % é um caractere coringa que pode ser adicionado nas palavras.
por exemplo temos os nomes Maria, Mário, Nilmar, Cristian
Retorna todos os nomes que tem 'mar´: MARia, MARio, NilMAR.*/

String filtro = "mar";
String consulta =
“SELECT nome, idade FROM pessoas “ +
"WHERE nome LIKE ‘%"+filtro+"%' "

```

6. Ordenacões

```java
// Ordem crescente
String consulta = "SELECT nome, idade FROM pessoas WHERE 1=1 ORDER BY nome ASC ";

// Ordes decrescente
String consulta = "SELECT nome, idade FROM pessoas WHERE 1=1 ORDER BY nome DESC ";

```

```sql
// Ordem crescente retorna cinco valores
String consulta = "SELECT nome, idade FROM pessoas WHERE 1=1 ORDER BY nome ASC LIMIT 5";
```

7. Atualizar dados

```sql
bancoDados.execSQL("UPDATE pessoas SET idade = 19 WHERE nome = 'Mariana'");

bancoDados.execSQL("UPDATE pessoas SET nome = 'Mariana Silva' WHERE nome = 'Mariana'");
```

8.  Deletando uma tabela do banco de dados

```sql
bancoDados.execSQL("DROP TABLE pessoas")
```

9. Deletando um registro da taexbela 

```sql
bancoDados.execSQL("DELETE FROM pessoas WHERE id = 1")
```

# Criando itens de menu

1. Criar um novo *Android Resource Diretory* em *resource type* escolher o tipo menu

2. Clicar com botão direito sobre a *diretory* **menu** e escolher a opcão *menu resource file* e atribuir um nome

3. No arquivo xml adicionar os items para o menu

   1. ```xml
      <?xml version="1.0" encoding="utf-8"?>
      <menu xmlns:android="http://schemas.android.com/apk/res/android"
          xmlns:app="http://schemas.android.com/apk/res-auto">
          <item
              android:id="@+id/itemSalvar"
              android:title="Salvar"
              android:orderInCategory="100"
              app:showAsAction="always"
              android:icon="@drawable/ic_save"
              />
          <item
              android:id="@+id/itemEditar"
              android:title="Editar"
              android:orderInCategory="200"
              app:showAsAction="never"
              />
          <item
              android:id="@+id/itemConfiguracoes"
              android:title="Configurações"
              android:orderInCategory="300"
              app:showAsAction="never"
              />
      </menu>
      ```

      

4. No *MainActivity* adicionar o método *onCreateOptionsMenu* para criar o menu

```java
@Override
    public boolean onCreateOptionsMenu(Menu menu) {
        getMenuInflater().inflate(R.menu.menu_principal, menu);
        return super.onCreateOptionsMenu(menu);
    }
```

5. Adicionar um método *onOptionsItemSelected* para tratar dos itens selecionados

```java
public boolean onOptionsItemSelected(@NonNull MenuItem item) {

        switch (item.getItemId()){
            case R.id.itemSalvar:
                Toast.makeText(MainActivity.this, "Item Salvar", Toast.LENGTH_SHORT).show();
                break;
            case R.id.itemEditar:
                Toast.makeText(MainActivity.this, "Item Editar", Toast.LENGTH_SHORT).show();
                break;
            case R.id.itemConfiguracoes:
                Toast.makeText(MainActivity.this, "Item Configurações", Toast.LENGTH_SHORT).show();
                break;
        }

        return super.onOptionsItemSelected(item);
    }
```

