#  Aplicativo Camra 
Diseño
![image](https://github.com/Mhela4444/Camara/assets/133244582/83923827-eecd-4cb8-9650-4dbdff50e06c)
a realizacion de la presente aplicacion de tomar fotos con la camara se hizo el uso principalmente de un imageview e image button programando en el activitymain las distintas funciones, declaracion de variables, y creacion de los distintos metodos, tanto como el imagebutton para que pueda tomar la foto, hacer que esa foto se muestre en el imageview y dar los respectivos permisos en el androidmanifest.xml para que estas fotos puedan ser guardadas en el dispositivo
Codificacion  MainActivity
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val btnCamara = findViewById<Button>(R.id.btnCamara)

        //Evento al presionar el botón
        btnCamara.setOnClickListener {
            startForResult.launch(Intent(MediaStore.ACTION_IMAGE_CAPTURE))
        }
    }

    //Evento que procesa el resultado de la cámara y envía la vista previa de la foto al ImageView
    private val startForResult =  registerForActivityResult(ActivityResultContracts.StartActivityForResult()) { result: ActivityResult ->
            if (result.resultCode == Activity.RESULT_OK) {
                val intent = result.data
                val imageBitmap = intent?.extras?.get("data") as Bitmap
                val imageView = findViewById<ImageView>(R.id.imageView)
                imageView.setImageBitmap(imageBitmap)
            }
        }
}

Rsultado
![mm](https://github.com/Mhela4444/Camara/assets/133244582/c7e2b935-956c-4521-af8c-b92a9c2dd31c)
