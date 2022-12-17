# Lista de Tarefas

1.  Criar um projeto do tipo *Activity (basic)*
2.  Adicionar os seguintes valores de cores em *colors.xml*

```xml
    <color name="primary">#9c27b0</color>
    <color name="primaryDark">#6c1492</color>
    <color name="accent">#ae6cba</color>
```

3. Adicionar as cores acima no arquivo *themes.xml*

4. No arquivo *content_main.xml* adicionar um *recyclerView*

```xml
<androidx.recyclerview.widget.RecyclerView
android:id="@+id/recyclerView"
android:layout_width="0dp"
android:layout_height="729dp"
app:layout_constraintEnd_toEndOf="parent"
app:layout_constraintStart_toStartOf="parent"
app:layout_constraintTop_toTopOf="parent" />
```

5. Criar um layout para o adapter chamado *lista_tarefa_adapter*

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:layout_margin="16dp"
    >

    <TextView
        android:id="@+id/textTarefa"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Texto da lista de tarefas"
        android:textSize="16sp"
        android:padding="10dp"
        />

</LinearLayout>
```



5. Criar três packages *activity, adapter, model*
6. Arrastar o MainActivity para dentro do package activity e criar uma nova activity chamada **AdicionarTarefaActivity**.
7. Chamar a classe **AdicionarTarefaActivity** dentro do *fab no MainActivity*

```java
binding.fab.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent intent = new Intent(getApplicationContext(), AdicionarTarefaActivity.class);
                startActivity(intent);
            }
        });
```

8. Dentro do package adapter criar um chamado **TarefaAdapter**

```java
public class TarefaAdapter extends RecyclerView.Adapter<TarefaAdapter.MyViewHolder> {

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

Adapter depois de finalizado

```java
public class TarefaAdapter extends RecyclerView.Adapter<TarefaAdapter.MyViewHolder> {

    private List<Tarefa> listaTarefas;

    public TarefaAdapter(List<Tarefa> lista){
        this.listaTarefas = lista;
    }

    @NonNull
    @Override
    public MyViewHolder onCreateViewHolder(@NonNull ViewGroup parent, int viewType) {

        View itemLista = LayoutInflater.from(parent.getContext())
                .inflate(R.layout.lista_tarefa_adapter, parent, false);

        return new MyViewHolder(itemLista);
    }

    @Override
    public void onBindViewHolder(@NonNull MyViewHolder holder, int position) {
        Tarefa tarefa = listaTarefas.get(position);
        holder.tarefa.setText(tarefa.getNomeTarefa());
    }

    @Override
    public int getItemCount() {
        return this.listaTarefas.size();
    }

    public class MyViewHolder extends RecyclerView.ViewHolder{

        TextView tarefa;

        public MyViewHolder(@NonNull View itemView) {
            super(itemView);

            tarefa = itemView.findViewById(R.id.textTarefa);
        }
    }
```



9. Criar uma classe java em model chamada **Tarefa**

```java
public class Tarefa implements Serializable {
    
    private Long id;
    private String nomeTarefa;

    public Long getId() {
        return id;
    }

    public void setId(Long id) {
        this.id = id;
    }

    public String getNomeTarefa() {
        return nomeTarefa;
    }

    public void setNomeTarefa(String nomeTarefa) {
        this.nomeTarefa = nomeTarefa;
    }
}
```



10. No Main Activity criar um método chamado **carregarListaTarefas** que será responsável por carregar o recyclerView.



```java
// Declaracao dos atributos
private RecyclerView recyclerView;
private TarefaAdapter tarefaAdapter;
private List<Tarefa> listaTarefas = new ArrayList<>();
```

```java
// Lista
Tarefa tarefa1 = new Tarefa();
tarefa1.setNomeTarefa("Ir ao mercado");
listaTarefas.add(tarefa1);
```

```java
// Configuracao adapter
tarefaAdapter = new TarefaAdapter(listaTarefas); 

//obs Voltar ao adapter e criar um construtor para receber a lista de tarefas

private List<Tarefa> listaTarefas;
    
public TarefaAdapter(List<Tarefa> lista){
    this.listaTarefas = lista;
}
```

```java
//Configuracao do RecyclerView
recyclerView = findViewById(R.id.recyclerView);
RecyclerView.LayoutManager layoutManager = new LinearLayoutManager(getApplicationContext());
recyclerView.setLayoutManager(layoutManager);
recyclerView.setHasFixedSize(true);
recyclerView.addItemDecoration(new DividerItemDecoration(getApplicationContext(), LinearLayout.VERTICAL));
recyclerView.setAdapter(tarefaAdapter);
```

```java
@Override
protected void onStart() {
    carregarListaTarefas();
    super.onStart();
}
```

11. Adicionar evento de click

- Criar um *package helper* e uma classe chamada *RecyclerItemClickListener* 
- Copiar o código do [repositório](https://github.com/jamiltondamasceno/RecyclerItemClickListener/blob/master/RecyclerItemClickListener.java)
- Colar dentro da classe criada
- Adicionar o código abaixo dentro do *MainActivity no onCreate*

```java
//add Evento de Click
        recyclerView.addOnItemTouchListener(
                new RecyclerItemClickListener(
                        getApplicationContext(),
                        recyclerView,
                        new RecyclerItemClickListener.OnItemClickListener() {
                            @Override
                            public void onItemClick(View view, int position) {

                            }

                            @Override
                            public void onLongItemClick(View view, int position) {

                            }

                            @Override
                            public void onItemClick(AdapterView<?> adapterView, View view, int i, long l) {

                            }
                        }
                )
        );
```

12. Adicionar o menu de opcões

- Os métodos *onCreateOptionsMenu* e *onOptionsItemSelected* foram criados dentro do Adicionar_Tarefa

```xml
<menu xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    tools:context="br.com.listadetarefas.activity.MainActivity">
    <item
        android:id="@+id/itemSalvar"
        android:orderInCategory="100"
        android:title="@string/salvar"
        app:showAsAction="always"
        android:icon="@drawable/ic_check"/>
</menu>

```

```java
@Override
    public boolean onCreateOptionsMenu(Menu menu) {
        getMenuInflater().inflate(R.menu.menu_adicionar_tarefa, menu);
        return super.onCreateOptionsMenu(menu);
    }
```

```java
@Override
    public boolean onOptionsItemSelected(@NonNull MenuItem item) {
        switch (item.getItemId()){
            case R.id.itemSalvar:
                break;
        }
        return super.onOptionsItemSelected(item);
    }
```

13. Configurar banco de dados

- No package helper criar uma classe chamada **DbHelper**
- Na classe **DbHelper** extender para o *SQLiteOpenHelper* e implementar os seus métodos e seu construtor

```java
public class DbHelper extends SQLiteOpenHelper {
    
    public DbHelper(@Nullable Context context, @Nullable String name, @Nullable SQLiteDatabase.CursorFactory factory, int version) {
        super(context, name, factory, version);
    }
    
    @Override
    public void onCreate(SQLiteDatabase db) {
        
    }

    @Override
    public void onUpgrade(SQLiteDatabase db, int oldVersion, int newVersion) {

    }
}
```

- Será feitos algumas modificacões na classe construtor 
  - A classe receberá apenas como paramêtro o *Context*
  - Os outros paramêtros excluidos serão declarados como constantes

```java
private static int VERSION = 1;
private static String NOME_DB = "DB_TAREFAS";

public DbHelper(@Nullable Context context) {
    super(context, NOME_DB, null, VERSION);
}
```

- No método *onCreate* será criado a nossa tabela.

```java
@Override
    public void onCreate(SQLiteDatabase db) {
        String sql = "CREATE TABLE IF NOT EXISTS " + TABELA_TAREFAS
                + " (id INTEGER PRIMARY KEY AUTOINCREMENT, " + 
                " nome TEXT NOT NULL ); ";
        try{
            db.execSQL(sql);
            Log.i("INFO DB", "Sucesso ao criar a tabela");
        }catch (Exception e){
            Log.i("INFO DB", "Erro ao criar tabela"+ e.getMessage());
        }
    }
```

-  Método *onUpgrade*

```JAVA
public void onUpgrade(SQLiteDatabase db, int oldVersion, int newVersion) {
//        String sql = "ALTER TABLE "+ TABELA_TAREFAS + " ADD COLUMN status VARCHAR(2)";
        String sql = "DROP TABLE IF EXISTS "+ TABELA_TAREFAS + " ;";
        try{
            db.execSQL(sql);
            onCreate(db)
            Log.i("INFO DB", "Sucesso ao atualizar app");
        }catch (Exception e){
            Log.i("INFO DB", "Erro ao atualizar app"+ e.getMessage());
        }
    }
```

14. Salvar os dados no banco de dados

- Dentro do package *helper* criar uma inteface **ITarefaDAO**

```java
public interface ITarefaDAO {

    public boolean salvar(Tarefa tarefa);
    public boolean atualizar(Tarefa tarefa);
    public boolean deletar(Tarefa tarefa);
    public List<Tarefa> listar();
}
```

- Dentro do package *helper* criar uma classe **TarefaDAO** e implementar o **ITarefaDAO** e um construtor para a classe 

```java
public class TarefaDAO implements ITarefaDAO{

    public TarefaDAO() {
    }

    @Override
    public boolean salvar(Tarefa tarefa) {
        return false;
    }

    @Override
    public boolean atualizar(Tarefa tarefa) {
        return false;
    }

    @Override
    public boolean deletar(Tarefa tarefa) {
        return false;
    }

    @Override
    public List<Tarefa> listar() {
        return null;
    }
}
```

- No construtor da classe adicionar o méotodo do tipo *Context*, pois usaremos essa classe para o **DbHelper** que tem como parâmetro um tipo *Conxtext* também;

```java
private SQLiteDatabase escreve;
private SQLiteDatabase le;

public TarefaDAO(Context context) {
    DbHelper db = new DbHelper(context);
    escreve = db.getWritableDatabase();
    le = db.getReadableDatabase();
}
```

- Adicionar os códigos para o método salvar

```java
public boolean salvar(Tarefa tarefa) {
        ContentValues cv = new ContentValues();
        cv.put("nome", tarefa.getNomeTarefa());

        try {
            escreve.insert(DbHelper.TABELA_TAREFAS, null, cv );
            Log.i("INFO", "Tarefa salva com sucesso");
        }catch (Exception e){
            Log.i("INFO", "Erro ao salvar tarefa "+ e.getMessage());
            return false;
        }
        return true;
    }
```

- Recuperar o valor do id do *TextInputEditText* localizado no *activity_adicionar_tarefa.xml*

```java
public class AdicionarTarefaActivity extends AppCompatActivity {
    
    private TextInputEditText editTarefa;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_adicionar_tarefa);
        
        editTarefa = findViewById(R.id.textTarefa);
    }
```

- Instaciar o objeto dentro do *AdicionarTarefa*

```java
    public boolean onOptionsItemSelected(@NonNull MenuItem item) {
        switch (item.getItemId()){
            case R.id.itemSalvar:
                //Executa ação para o item salvar
                TarefaDAO tarefaDAO = new TarefaDAO(getApplicationContext());

                // Recupera o que o usuario escreveu
                Tarefa tarefa = new Tarefa();
                tarefa.setNomeTarefa("Ir a feira");

                tarefaDAO.salvar(tarefa);
                finish();
                break;
        }
        return super.onOptionsItemSelected(item);
    }
```

15. Recuperando Tarefas de maneira dinâmica

- Na classe *MainActivity* no método **carregarListaTarefas** adicionamos o seguite código.

```java
// Listar tarefas
TarefaDAO tarefaDAO = new TarefaDAO(getApplicationContext());
listaTarefas = tarefaDAO.listar();
```

- Na classe *TarefaDAO* no método listar vai recuperar as tarefas e retornar como uma lista.

```java
@Override
    public List<Tarefa> listar() {
        List<Tarefa> tarefas = new ArrayList<>();
        //Recuperar as tarefas do banco de dados
        String sql = "SELECT * FROM "+ DbHelper.TABELA_TAREFAS + " ;";
        Cursor cursor = le.rawQuery(sql, null);
        
        while(cursor.moveToNext()){
            Tarefa tarefa = new Tarefa();
            
            @SuppressLint("Range") Long id = cursor.getLong(cursor.getColumnIndex("id"));
            @SuppressLint("Range") String nomeTarefa = cursor.getString(cursor.getColumnIndex("nome"));
            
            tarefa.setId(id);
            tarefa.setNomeTarefa(nomeTarefa);
            
            //List Tarefas
            tarefas.add(tarefa);
            
        }
        return tarefas;
    }
```

16. Atualizar uma tarefa

- Editar o método **atualizar** na classe *TarefaDAO*

```java
public boolean atualizar(Tarefa tarefa) {
        
        ContentValues cv = new ContentValues();
        cv.put("nome", tarefa.getNomeTarefa());
        
        try {
            String[] args = {tarefa.getId().toString()};
            escreve.update(DbHelper.TABELA_TAREFAS, cv, "id=?",args);
            Log.i("INFO", "Tarefa atualizada com sucesso");
        }catch (Exception e){
            Log.i("INFO", "Erro ao atualizar tarefa "+ e.getMessage());
            return false;
        }
        return true;
    }
```

-  para esse recurso será utilizado os eventos de click do recyclerView
- onItemClick que será utlizado para editar as tarefas

```java
@Override
public void onItemClick(View view, int position) {
    // Recuperar tarefa para edição
    Tarefa tarefaSelecionada = listaTarefas.get(position);

    //Envia a tarefa selecionada para a proxima activity
    Intent intent = new Intent(MainActivity.this, AdicionarTarefaActivity.class);
    intent.putExtra("tarefaSelecionda", tarefaSelecionada);
    startActivity(intent);

}
```

-  Na classe *AdicionarTarefa* no método onCreate vamos recuperar essa tarefa selecionada

```java
private Tarefa tarefaAtual;

//Recuperando a tarefa selecionada, caso seja edição
tarefaAtual = (Tarefa) getIntent().getSerializableExtra("tarefaSelecionada");

//Exibir o texto da tarefa recuperada na caixa de texto
if (tarefaAtual != null){
	editTarefa.setText(tarefaAtual.getNomeTarefa());
}
```

- Implementar uma verificacão para salvar a tarefa recuperada. Vamos editar o trecho de código do método *onOptionsItemSelected* na própria classe *AdicionarTarefa*.

```java
public boolean onOptionsItemSelected(@NonNull MenuItem item) {
        switch (item.getItemId()){
            case R.id.itemSalvar:
                
                //Executa ação para o item salvar
                TarefaDAO tarefaDAO = new TarefaDAO(getApplicationContext());

                if (tarefaAtual != null){//edicao
                    String nomeTarefa = Objects.requireNonNull(editTarefa.getText()).toString();
                    if (!nomeTarefa.isEmpty()){
                        Tarefa tarefa = new Tarefa();
                        tarefa.setNomeTarefa(nomeTarefa);
                        tarefa.setId(tarefaAtual.getId());
                        
                        //atualizar no banco de dados
                        if (tarefaDAO.atualizar(tarefa)){
                            finish();
                            Toast.makeText(getApplicationContext(),
                                    "Sucesso ao atualizar tarefa",
                                    Toast.LENGTH_LONG).show();
                        }else{
                            Toast.makeText(getApplicationContext(),
                                    "Erro ao atualizar tarefa",
                                    Toast.LENGTH_LONG).show();
                        }
                        
                    }
                    
                }else{// Salvar
                    
                    // Recupera o que o usuario escreveu
                    String nomeTarefa = Objects.requireNonNull(editTarefa.getText()).toString();
                    if (!nomeTarefa.isEmpty()){
                        Tarefa tarefa = new Tarefa();
                        tarefa.setNomeTarefa(nomeTarefa);
                        
                        if (tarefaDAO.salvar(tarefa)){
                            finish();
                            Toast.makeText(getApplicationContext(),
                                    "Sucesso ao salvar tarefa",
                                    Toast.LENGTH_LONG).show();
                        }else{
                            Toast.makeText(getApplicationContext(),
                                    "Erro ao salvar tarefa",
                                    Toast.LENGTH_LONG).show();
                        }                       
                        
                    }
                }
                break;
        }
        return super.onOptionsItemSelected(item);
    }
```

17. Remover as tarefas

- onLongItemClick que será utilizado para remover as tarefas

```

```

