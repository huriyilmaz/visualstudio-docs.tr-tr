---
title: Özellikleri, Görev Listesi, çıktıyı ve seçenekler pencerelerini genişletme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eba2e7cbe6957ea786693f86a728ffa6b4aa2cb7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72633211"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>Özellikleri, Görev Listesi, çıktıyı ve seçenekler pencerelerini genişletme
Visual Studio 'daki herhangi bir araç penceresine erişebilirsiniz. Bu izlenecek yol, araç pencerenize ilişkin bilgilerin yeni bir **Seçenekler** sayfası ve **Özellikler** sayfasında yeni bir ayar ve ayrıca **görev listesi** ve **Çıkış** pencerelerinin nasıl yazılacağı gösterilmektedir.

## <a name="prerequisites"></a>Prerequisites
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-tool-window"></a>Araç penceresi ile uzantı oluşturma

1. VSıX şablonunu kullanarak **ToDoList** adlı bir proje oluşturun ve **todowinde**adlı özel bir araç penceresi öğesi şablonu ekleyin.

    > [!NOTE]
    > Araç penceresiyle uzantı oluşturma hakkında daha fazla bilgi için bkz. [bir araç penceresi ile uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="set-up-the-tool-window"></a>Araç penceresini ayarlama
 Yeni bir ToDo öğesi yazmak için bir TextBox, listeye yeni öğe eklemek için bir düğme ve listede öğeleri göstermek için bir liste kutusu ekleyin.

1. *Todowinet. xaml*Içinde, UserControl 'daki düğme, metin kutusu ve StackPanel denetimlerini silin.

    > [!NOTE]
    > Bu, sonraki bir adımda yeniden kullanacağınız **Button1_Click** olay işleyicisini silmez.

2. **Araç kutusunun** **tüm WPF denetimleri** bölümünden bir **tuval** denetimini kılavuza sürükleyin.

3. Bir **TextBox**, **düğme**ve bir **liste** kutusunu tuvale sürükleyin. Alt metin ve düğmenin aynı düzeyde olması için öğeleri düzenleyin ve liste kutusu aşağıdaki resimde olduğu gibi pencerenin geri kalanını doldurur.

     ![Tamamlanmış araç penceresi](../extensibility/media/t5-toolwindow.png "T5-ToolWindow")

4. XAML bölmesinde, düğmesini bulun ve Içerik özelliğini **Ekle**olarak ayarlayın. Düğme olay işleyicisini bir `Click="button1_Click"` özniteliği ekleyerek düğme denetimine yeniden bağlayın. Tuval bloğunun şuna benzer olması gerekir:

    ```xml
    <Canvas HorizontalAlignment="Left" Width="306">
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>
    </Canvas>
    ```

### <a name="customize-the-constructor"></a>Oluşturucuyu özelleştirme

1. *TodoWindowControl.xaml.cs* dosyasında, aşağıdaki using yönergesini ekleyin:

    ```csharp
    using System;
    ```

2. Turuna bir genel başvuru ekleyin ve TodoWindowControl oluşturucusunun bir todowinde parametresi alın. Kod şöyle görünmelidir:

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3. *TodoWindow.cs*' de TodoWindowControl oluşturucusunu todowıningparameter ' ı içerecek şekilde değiştirin. Kod şöyle görünmelidir:

    ```csharp
    public TodoWindow() : base(null)
    {
        this.Caption = "TodoWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;

         this.Content = new TodoWindowControl(this);
    }
    ```

## <a name="create-an-options-page"></a>Seçenekler sayfası oluşturma
 Kullanıcıların araç penceresi için ayarları değiştirebilmeleri için **Seçenekler** iletişim kutusuna bir sayfa sağlayabilirsiniz. Seçenekler sayfası oluşturmak, hem seçenekleri hem de *TodoListPackage.cs* veya *TodoListPackage. vb* dosyasındaki bir girişi açıklayan bir sınıf gerektirir.

1. @No__t_0 adlı bir sınıf ekleyin. @No__t_0 sınıfın <xref:Microsoft.VisualStudio.Shell.DialogPage> devralmasını sağlayın.

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. Aşağıdaki using yönergesini ekleyin:

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. Bu izlenecek yolda bulunan Seçenekler sayfası, yalnızca DaysAhead adlı bir seçenek sağlar. **Daysahead** adlı bir özel alan ve `ToolsOptions` sınıfına **daysahead** adlı bir özellik ekleyin:

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   Artık projeyi bu seçenekler sayfasından haberdar etmeniz gerekir.

### <a name="make-the-options-page-available-to-users"></a>Seçenekler sayfasını kullanıcılar için kullanılabilir hale getirin

1. *TodoWindowPackage.cs*' de, `TodoWindowPackage` sınıfına bir <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> ekleyin:

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2. ProvideOptionPage oluşturucusuna ilk parametresi, daha önce oluşturduğunuz `ToolsOptions` sınıf türüdür. İkinci parametre olan "ToDo", **Seçenekler** iletişim kutusundaki kategorinin adıdır. Üçüncü parametre olan "genel", Seçenekler sayfasının kullanılabildiği **Seçenekler** iletişim kutusunun alt kategori adıdır. Sonraki iki parametre dizeler için kaynak kimlikleridir; Birincisi kategorinin adı, ikincisi ise alt kategorinin adıdır. Son parametresi, bu sayfaya Otomasyon kullanılarak erişip erişemeyeceğini belirler.

     Bir Kullanıcı seçenekler sayfanızı açtığında, aşağıdaki resme benzemelidir.

     ![Seçenekler sayfası](../extensibility/media/t5optionspage.gif "T5OptionsPage")

     Kategori **Todo** ve alt kategori **genel**' i fark edin.

## <a name="make-data-available-to-the-properties-window"></a>Özellikler penceresi verileri kullanılabilir hale getirme
 Yapılacaklar listesindeki ayrı öğeler hakkında bilgi depolayan `TodoItem` adlı bir sınıf oluşturarak yapılacaklar listesi bilgilerini kullanılabilir hale getirebilirsiniz.

1. @No__t_0 adlı bir sınıf ekleyin.

     Araç penceresi kullanıcılar için kullanılabilir olduğunda, ListBox 'daki öğeler Todoıtems tarafından temsil edilir. Kullanıcı ListBox 'daki bu öğelerden birini seçtiğinde, **Özellikler** penceresi öğe hakkındaki bilgileri görüntüler.

     **Özellikleri Özellikler** penceresinde kullanılabilir hale getirmek için verileri, `Description` ve `Category` olmak üzere iki özel özniteliğe sahip ortak özelliklere dönüştürür. `Description`, **Özellikler** penceresinin alt kısmında görüntülenen metindir. `Category`, **kategorilere ayrılan** görünümde **Özellikler** penceresi görüntülendiğinde özelliğin nerede görüneceğini belirler. Aşağıdaki resimde **Özellikler** penceresi **kategorize** edilmiş görünümdeyseniz, **ToDo alanları** kategorisindeki **Name** özelliği seçilir ve **ad** özelliğinin açıklaması pencerenin alt kısmında görüntülenir.

     ![Özellik Penceresi](../extensibility/media/t5properties.png "T5Properties")

2. Aşağıdaki yönergeleri kullanarak *TodoItem.cs* dosyasını ekleyin.

    ```csharp
    using System.ComponentModel;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. @No__t_0 erişim değiştiricisini sınıf bildirimine ekleyin.

    ```csharp
    public class TodoItem
    {
    }
    ```

     @No__t_0 ve `DueDate` iki özelliği ekleyin. @No__t_0 ve `CheckForErrors()` daha sonra yapacağız.

    ```csharp
    public class TodoItem
    {
        private TodoWindowControl parent;
        private string name;
        [Description("Name of the ToDo item")]
        [Category("ToDo Fields")]
        public string Name
        {
            get { return name; }
            set
            {
                name = value;
                parent.UpdateList(this);
            }
        }

        private DateTime dueDate;
        [Description("Due date of the ToDo item")]
        [Category("ToDo Fields")]
        public DateTime DueDate
        {
            get { return dueDate; }
            set
            {
                dueDate = value;
                parent.UpdateList(this);
                parent.CheckForErrors();
            }
        }
    }
    ```

4. Kullanıcı denetimine özel bir başvuru ekleyin. Bu ToDo öğesinin kullanıcı denetimini ve adını alan bir Oluşturucu ekleyin. @No__t_0 değerini bulmak için, Seçenekler sayfası özelliğini alır.

    ```csharp
    private TodoWindowControl parent;

    public TodoItem(TodoWindowControl control, string itemName)
    {
        parent = control;
        name = itemName;
        dueDate = DateTime.Now;

        double daysAhead = 0;
        IVsPackage package = parent.parent.Package as IVsPackage;
        if (package != null)
        {
            object obj;
            package.GetAutomationObject("ToDo.General", out obj);

            ToolsOptions options = obj as ToolsOptions;
            if (options != null)
            {
                daysAhead = options.DaysAhead;
            }
        }

        dueDate = dueDate.AddDays(daysAhead);
    }
    ```

5. @No__t_0 sınıfın örnekleri liste kutusunda depolanacak ve ListBox `ToString` işlevini çağıracak, `ToString` işlevini aşırı yüklemelisiniz. Oluşturucudan sonra ve sınıfın sonundan önce, *TodoItem.cs*için aşağıdaki kodu ekleyin.

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6. *TodoWindowControl.xaml.cs*' de, `CheckForError` ve `UpdateList` yöntemleri için `TodoWindowControl` sınıfına saplama yöntemleri ekleyin. Bunları ProcessDialogChar 'dan sonra ve dosyanın sonundan önce koyun.

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     @No__t_0 yöntemi, üst nesnede aynı ada sahip bir yöntemi çağırır ve bu yöntem herhangi bir hata olup olmadığını kontrol eder ve doğru şekilde işler. @No__t_0 yöntemi üst denetimdeki ListBox 'ı güncelleştirir; yöntemi, bu sınıftaki `Name` ve `DueDate` Özellikleri değiştiğinde çağrılır. Bunlar daha sonra uygulanacaktır.

## <a name="integrate-into-the-properties-window"></a>Özellikler penceresi tümleştirme
 Şimdi **Özellikler** penceresine bağlı olan ListBox 'ı yöneten kodu yazın.

 TextBox 'ı okumak için düğme tıklayını değiştirmeniz, bir TodoItem oluşturmanız ve onu ListBox 'a eklemesi gerekir.

1. Mevcut `button1_Click` işlevini yeni bir TodoItem oluşturan kodla değiştirin ve ListBox 'a ekler. Daha sonra tanımlanacak `TrackSelection()` çağırır.

    ```csharp
    private void button1_Click(object sender, RoutedEventArgs e)
    {
        if (textBox.Text.Length > 0)
        {
            var item = new TodoItem(this, textBox.Text);
            listBox.Items.Add(item);
            TrackSelection();
            CheckForErrors();
        }
    }
    ```

2. Tasarım görünümü ListBox denetimini seçin. **Özellikler** penceresinde **olay işleyiciler** düğmesine tıklayın ve **SelectionChanged** olayını bulun. **ListBox_SelectionChanged**ile metin kutusunu girin. Bunu yapmak, SelectionChanged işleyicisi için bir saplama ekler ve bunu olaya atar.

3. @No__t_0 yöntemini uygulayın. @No__t_0 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> hizmetlerini almanız gerektiğinden, <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> TodoWindowControl tarafından erişilebilir yapmanız gerekir. @No__t_0 sınıfına aşağıdaki yöntemi ekleyin:

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4. Aşağıdaki using yönergelerini *TodoWindowControl.xaml.cs*öğesine ekleyin:

    ```csharp
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Shell.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    ```

5. SelectionChanged işleyicisini aşağıdaki gibi girin:

    ```
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        TrackSelection();
    }
    ```

6. Şimdi, **Özellikler** penceresiyle tümleştirme sağlayan TrackSelection işlevini doldurmanız gerekir. Bu işlev, Kullanıcı ListBox 'a bir öğe eklediğinde ya da ListBox içindeki bir öğeye tıkladığı zaman çağrılır. ListBox 'ın içeriğini bir SelectionContainer öğesine ekler ve SelectionContainer öğesini **Özellikler** penceresinin <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> olay işleyicisine geçirir. TrackSelection hizmeti kullanıcı arabirimindeki (UI) seçili nesneleri izler ve özelliklerini görüntüler

    ```csharp
    private SelectionContainer mySelContainer;
    private System.Collections.ArrayList mySelItems;
    private IVsWindowFrame frame = null;

    private void TrackSelection()
    {
        if (frame == null)
        {
            var shell = parent.GetVsService(typeof(SVsUIShell)) as IVsUIShell;
            if (shell != null)
            {
                var guidPropertyBrowser = new
                Guid(ToolWindowGuids.PropertyBrowser);
                shell.FindToolWindow((uint)__VSFINDTOOLWIN.FTW_fForceCreate,
                ref guidPropertyBrowser, out frame);
            }
        }
        if (frame != null)
            {
                frame.Show();
            }
        if (mySelContainer == null)
        {
            mySelContainer = new SelectionContainer();
        }

        mySelItems = new System.Collections.ArrayList();

        var selected = listBox.SelectedItem as TodoItem;
        if (selected != null)
        {
            mySelItems.Add(selected);
        }

        mySelContainer.SelectedObjects = mySelItems;

        ITrackSelection track = parent.GetVsService(typeof(STrackSelection))
                                as ITrackSelection;
        if (track != null)
        {
            track.OnSelectChange(mySelContainer);
        }
    }
    ```

     Artık **Özellikler** penceresinin kullanabileceği bir sınıfınız olduğuna göre, **Özellikler** penceresini araç penceresi ile tümleştirebilirsiniz. Kullanıcı araç penceresindeki ListBox içindeki bir öğeye tıkladığında **Özellikler** penceresi uygun şekilde güncellenmelidir. Benzer şekilde, Kullanıcı **Özellikler** penceresinde bir Todo öğesini değiştirdiğinde ilişkili öğe güncellenmelidir.

7. Şimdi, *TodoWindowControl.xaml.cs*Içindeki UpdateList işlev kodunun geri kalanını ekleyin. Değiştirilen TodoItem, ListBox ' dan bırakması ve yeniden eklemesi gerekir.

    ```csharp
    public void UpdateList(TodoItem item)
    {
        var index = listBox.SelectedIndex;
        listBox.Items.RemoveAt(index);
        listBox.Items.Insert(index, item);
        listBox.SelectedItem = index;
    }
    ```

8. Kodunuzu test edin. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örnek görünmelidir.

9. **Araçlar**  > **Seçenekler** sayfasını açın. Sol bölmede ToDo kategorisini görmeniz gerekir. Kategoriler alfabetik olarak listelendiğinde, TS 'nin altına bakın.

10. **Todo** seçenekleri sayfasında, `DaysAhead` özelliğinin **0**olarak ayarlandığını görmeniz gerekir. **2**olarak değiştirin.

11. **Görünüm/diğer pencereler** menüsünde, **todowinde**' yi açın. Metin kutusuna **EndDate** yazın ve **Ekle**' ye tıklayın.

12. Liste kutusunda bugünden sonraki iki gün sonra bir tarih görmeniz gerekir.

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Çıkış penceresine ve öğeleri Görev Listesi metin ekleme
 **Görev listesi**Için, görev türünde yeni bir nesne oluşturun ve ardından bu görev nesnesini `Add` metodunu çağırarak **görev listesi** ekleyin. **Çıkış** penceresine yazmak için, bir bölme nesnesi elde etmek üzere `GetPane` yöntemini çağırır ve ardından bölme nesnesinin `OutputString` yöntemini çağırabilirsiniz.

1. *TodoWindowControl.xaml.cs*' de, `button1_Click` yönteminde, **Çıkış** penceresinin **genel** bölmesini (varsayılan olan) almak ve ona yazmak için kod ekleyin. Yöntemi şöyle görünmelidir:

    ```csharp
    private void button1_Click(object sender, EventArgs e)
    {
        if (textBox.Text.Length > 0)
        {
            var item = new TodoItem(this, textBox.Text);
            listBox.Items.Add(item);

            var outputWindow = parent.GetVsService(
                typeof(SVsOutputWindow)) as IVsOutputWindow;
            IVsOutputWindowPane pane;
            Guid guidGeneralPane = VSConstants.GUID_OutWindowGeneralPane;
            outputWindow.GetPane(ref guidGeneralPane, out pane);
            if (pane != null)
            {
                 pane.OutputString(string.Format(
                    "To Do item created: {0}\r\n",
                 item.ToString()));
        }
            TrackSelection();
            CheckForErrors();
        }
    }
    ```

2. Görev Listesi öğe eklemek için, TodoWindowControl sınıfına iç içe bir sınıf eklemeniz gerekir. İç içe sınıfın <xref:Microsoft.VisualStudio.Shell.TaskProvider> türetilmesi gerekir. @No__t_0 sınıfının sonuna aşağıdaki kodu ekleyin.

    ```csharp
    [Guid("72de1eAD-a00c-4f57-bff7-57edb162d0be")]
    public class TodoWindowTaskProvider : TaskProvider
    {
        public TodoWindowTaskProvider(IServiceProvider sp)
            : base(sp)
        {
        }
    }
    ```

3. Ardından, `TodoWindowControl` sınıfına `TodoTaskProvider` ve `CreateProvider()` yöntemine özel bir başvuru ekleyin. Kod şöyle görünmelidir:

    ```csharp
    private TodoWindowTaskProvider taskProvider;
    private void CreateProvider()
    {
        if (taskProvider == null)
        {
            taskProvider = new TodoWindowTaskProvider(parent);
            taskProvider.ProviderName = "To Do";
        }
    }
    ```

4. @No__t_2 sınıfına Görev Listesi bir giriş ekleyen Görev Listesi ve `ReportError()` temizleyen `ClearError()` ekleyin.

    ```csharp
    private void ClearError()
    {
        CreateProvider();
        taskProvider.Tasks.Clear();
    }
    private void ReportError(string p)
    {
        CreateProvider();
        var errorTask = new Task();
        errorTask.CanDelete = false;
        errorTask.Category = TaskCategory.Comments;
        errorTask.Text = p;

        taskProvider.Tasks.Add(errorTask);

        taskProvider.Show();

        var taskList = parent.GetVsService(typeof(SVsTaskList))
            as IVsTaskList2;
        if (taskList == null)
        {
            return;
        }

        var guidProvider = typeof(TodoWindowTaskProvider).GUID;
         taskList.SetActiveProvider(ref guidProvider);
    }
    ```

5. Şimdi `CheckForErrors` yöntemini aşağıdaki şekilde uygulayın.

    ```csharp
    public void CheckForErrors()
    {
        foreach (TodoItem item in listBox.Items)
        {
            if (item.DueDate < DateTime.Now)
            {
                ReportError("To Do Item is out of date: "
                    + item.ToString());
            }
        }
    }
    ```

## <a name="try-it-out"></a>Deneyin

1. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örnek görüntülenir.

2. **Turun** ' i açın (**diğer Windows** ** >   > ** **görüntüleyin** ).

3. Metin kutusuna bir şey yazın ve ardından **Ekle**' ye tıklayın.

     Son Tarih, bugün liste kutusuna eklendikten sonra 2 gün sonra. Hiçbir hata oluşturulmaz ve **görev listesi** (**Görünüm**  > **görev listesi**) hiç giriş içermemelidir.

4. Şimdi **araçlar**  > **seçenekleri**  > **Todo** sayfasındaki ayarı **2** ' den **0**' a geri değiştirin.

5. **Turun** içine başka bir şey yazın ve sonra yeniden **Ekle** ' ye tıklayın. Bu, bir hatayı ve ayrıca **görev listesi**bir girdiyi tetikler.

     Öğe eklerken, başlangıç tarihi ve 2 gün olarak ayarlanır.

6. **Görünüm** menüsünde **Çıkış** ' a tıklayarak **Çıkış** penceresini açın.

     Her öğe eklediğinizde **görev listesi** bölmesinde bir ileti görüntülenir.

7. ListBox 'daki öğelerden birine tıklayın.

     **Özellikler** penceresi, öğe için iki özelliği görüntüler.

8. Özelliklerden birini değiştirin ve ardından **ENTER**tuşuna basın.

     Öğe ListBox 'da güncelleştirilir.
