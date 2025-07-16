# Subida de archivos

Documentación oficial [aquí](https://symfony.com/doc/6.4/controller/upload_file.html) 

Para poder subir archivos desde un formulario, debemos seguir los siguientes pasos:

1  En el formulario debemos agregar el siguiente campo

```php
use Symfony\Component\Form\Extension\Core\Type\FileType;

class PostType extends AbstractType
{
    public function buildForm(FormBuilderInterface $builder, array $options): void
    {
        $builder
            //Subida de archivoas
            ->add('file', FileType::class, [
                'label' => 'photo',
                'required' => false,
            ])
            ->add('submit', SubmitType::class)
        ;
    }
    ...
}
```



2  Luego desde el controlador debemos capturarlo, cambiar el nombre del archivo por seguridad y guardarlo en la ruta especificada en services.yml

```php
use Symfony\Component\HttpFoundation\File\Exception\FileException;
use Symfony\Component\String\Slugger\SluggerInterface;
...

class PostController extends AbstractController
{
    ...
    
    #[Route('/', name: 'app_post')]
    public function index(Request $request, SluggerInterface $slugger): Response
    {
        $post = new Post();

        $posts = $this->em->getRepository(Post::class)->findAllPosts();

        $form = $this->createForm(PostType::class, $post);
        $form->handleRequest($request);
        
        if ($form->isSubmitted() && $form->isValid()) {
            $file = $form->get('file')->getData();
            $url = str_replace(" ", "-", $form->get('title')->getData());

            if ( $file ){
                //Cambiamos el nombre del archivo 
                $originalFilename = pathinfo($file->getClientOriginalName(), PATHINFO_FILENAME);
                $safeFilename = $slugger->slug($originalFilename);
                $newFilename = $safeFilename.'-'.uniqid().'.'.$file->guessExtension();
                
                //Guardamos el archivo en el servidor
                try{
                    $file->move(
                        $this->getParameter('files_directory'),
                        $newFilename
                    );
                } catch (FileException $e){
                    throw new Exception('Ups there is a problem with your file');
                }
                
                //Guardamos el nuevo nombre del archivo en BD
                $post->setFile($newFilename);
            }
            ... 
        }

        ...
    }

}
```

3  Finalmente debemos configurar en services.yaml la ruta donde se guardaran los archivos

```yaml
parameters:
    files_directory: '%kernel.project_dir%/public/uploads/files'
```
