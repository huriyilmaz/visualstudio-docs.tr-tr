---
title: Özellikleri Genişletme, Görev Listesi, Çıkış, Seçenekler pencereleri
description: Yeni seçenekler sayfasındaki araç pencereniz hakkında Visual Studio yeni seçenekler sayfasına ve Özellikler sayfasındaki yeni bir ayara nasıl tümleştirebilirsiniz?
ms.date: 11/04/2016
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3334ba3694ee3c1354c152b013c38472e4b90b72
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903287"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>Özellikler, Görev Listesi, Çıkış ve Seçenekler pencerelerini genişletme
Araç penceresinden herhangi bir araç penceresine Visual Studio. Bu kılavuzda, araç pencereniz hakkında bilgileri yeni bir **Seçenekler** sayfasıyla  ve Özellikler sayfasındaki yeni  bir ayarla tümleştirin, ayrıca Görev Listesi ve Çıkış pencerelerine yazma **gösterilir.**

## <a name="prerequisites"></a>Önkoşullar
 2015'Visual Studio başlayarak, Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Bu, kurulumda isteğe bağlı bir Visual Studio olarak dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-an-extension-with-a-tool-window"></a>Araç penceresiyle uzantı oluşturma

1. VSIX şablonunu kullanarak **TodoList** adlı bir proje oluşturun ve **TodoWindow** adlı özel bir araç penceresi öğesi şablonu ekleyin.

    > [!NOTE]
    > Araç penceresiyle uzantı oluşturma hakkında daha fazla bilgi için [bkz. Araç penceresiyle uzantı oluşturma.](../extensibility/creating-an-extension-with-a-tool-window.md)

## <a name="set-up-the-tool-window"></a>Araç penceresini ayarlama
 Yeni bir ToDo öğesi, listeye yeni öğe eklemek için bir Düğme ve listedeki öğeleri görüntülemek için listBox yazarak bir TextBox ekleyin.

1. *TodoWindow.xaml'de* UserControl'den Button, TextBox ve StackPanel denetimlerini silin.

    > [!NOTE]
    > Bu işlem, **button1_Click** sonraki bir adımda yeniden kullanacağız olay işleyicisini silemez.

2. Araç **Kutusunun Tüm WPF** Denetimleri bölümünde **bir** Tuval **denetimi sürükleyerek** kılavuza sürükleyin.

3. **TextBox,** **Düğme** ve **ListBox'ı Tuvale** sürükleyin. Öğeleri, TextBox ve Düğmenin aynı düzeyde olması ve ListBox'ın aşağıdaki resimde olduğu gibi pencerenin geri kalanını altlarında dolduracak şekilde düzenleme.

     ![Bitmiş Araç Penceresi](../extensibility/media/t5-toolwindow.png "T5-ToolWindow")

4. XAML bölmesinde Düğme'yi bulun ve İçerik özelliğini Ekle olarak **ayarlayın.** Öznitelik ekleyerek düğme olay işleyicisini Düğme denetimine yeniden `Click="button1_Click"` bağlayın. Tuval bloğu aşağıdaki gibi görünüyor olmalı:

    ```xml
    <Canvas HorizontalAlignment="Left" Width="306">
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>
    </Canvas>
    ```

### <a name="customize-the-constructor"></a>Oluşturucu özelleştirme

1. *TodoWindowControl.xaml.cs* dosyasında aşağıdaki using yönergesine ekleyin:

    ```csharp
    using System;
    ```

2. TodoWindow'a genel bir başvuru ekleyin ve TodoWindowControl oluşturucus un bir TodoWindow parametresini almalıdır. Kod aşağıdaki gibi görünüyor olmalı:

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3. *TodoWindow.cs içinde* TodoWindowControl oluşturucusu'nun todoWindow parametresini içerecek şekilde değiştirme. Kod aşağıdaki gibi görünüyor olmalı:

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
 Kullanıcıların araç penceresi için ayarları **değiştiresin** diye Seçenekler iletişim kutusunda bir sayfa sabilirsiniz. Seçenekler sayfası oluşturmak için hem seçenekleri açıklayan bir sınıf hem de *TodoListPackage.cs* veya *TodoListPackage.vb* dosyasındaki bir giriş gerekir.

1. adlı bir sınıf `ToolsOptions.cs` ekleyin. sınıfını `ToolsOptions` 'den <xref:Microsoft.VisualStudio.Shell.DialogPage> devralın.

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. Aşağıdaki using yönergesi ekleyin:

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. Bu kılavuzda yer alan Seçenekler sayfası DaysAhead adlı tek bir seçenek sağlar. sınıfına **daysAhead adlı özel** bir alan ve **DaysAhead adlı** bir özellik `ToolsOptions` ekleyin:

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   Şimdi projeyi bu Seçenekler sayfasından haberdar edin.

### <a name="make-the-options-page-available-to-users"></a>Seçenekler sayfasını kullanıcılar için kullanılabilir yapma

1. *TodoWindowPackage.cs* içinde <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> sınıfına bir `TodoWindowPackage` ekleyin:

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2. ProvideOptionPage oluşturucus un ilk parametresi, daha önce oluşturduğunuz `ToolsOptions` sınıfının t değeridir. İkinci parametre olan "ToDo", Seçenekler iletişim kutusundaki **kategorinin** adıdır. Üçüncü parametre olan "Genel", Seçenekler iletişim kutusunun Seçenekler  sayfasının kullanılabilir olduğu alt kategorinin adıdır. Sonraki iki parametre dizeler için kaynak kimlikleridir; birincisi kategorinin adı, ikincisi ise alt kategorinin adıdır. Son parametre, bu sayfaya otomasyon kullanılarak erişilip erişilileileyil olmadığını belirler.

     Bir kullanıcı Seçenekler sayfanızı açtığında aşağıdaki resme benzer.

     ![Seçenekler Sayfası](../extensibility/media/t5optionspage.gif "T5OptionsPage")

     **ToDo kategorisine ve Genel** alt kategorisine **dikkatin.**

## <a name="make-data-available-to-the-properties-window"></a>Verileri veri kaynağına Özellikler penceresi
 ToDo listesinde tek tek öğelerle ilgili bilgileri depolar adlı bir sınıf oluşturarak ToDo `TodoItem` listesi bilgilerini kullanılabilir hale ekleyebilirsiniz.

1. adlı bir sınıf `TodoItem.cs` ekleyin.

     Araç penceresi kullanıcılar tarafından kullanılabilir olduğunda ListBox'daki öğeler TodoItems ile temsil edilen öğeler olur. Kullanıcı ListBox'ta bu öğelerden birini seçerken Özellikler **penceresi** öğeyle ilgili bilgileri görüntüler.

     Özellikler penceresinde verileri kullanılabilir **hale yapmak** için, verileri iki özel özniteliği olan genel özelliklere ve olarak `Description` `Category` açarsınız. `Description`, Özellikler penceresinin en altında görünen **metindir.** `Category` Özellikler penceresi Kategorilere Ayrılmış görünümde **görüntülendiğinde** özelliğin nerede **görünmesi gerektiğini** belirler. Aşağıdaki resimde Özellikler  penceresi Kategorilere  ayrılmış görünümdedir, **ToDo Fields** kategorisindeki **Name** özelliği seçilidir ve pencerenin alt kısmında Name özelliğinin açıklaması görüntülenir. 

     ![Özellikler Penceresi](../extensibility/media/t5properties.png "T5Properties")

2. *TodoItem.cs dosyasına aşağıdaki* using yönergelerini ekleyin.

    ```csharp
    using System.ComponentModel;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Sınıf `public` bildirimine erişim değiştiricisini ekleyin.

    ```csharp
    public class TodoItem
    {
    }
    ```

     ve olmak için iki özellik `Name` `DueDate` ekleyin. ve daha sonra `UpdateList()` `CheckForErrors()` yapacağız.

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

4. Kullanıcı denetimine özel bir başvuru ekleyin. Kullanıcı denetimi alan bir oluşturucu ve bu ToDo öğesinin adını ekleyin. değerini bulmak için `daysAhead` Seçenekler sayfası özelliğini alır.

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

5. Sınıf örnekleri ListBox'ta depolandığı ve ListBox'ın işlevi çağıracak olması `TodoItem` `ToString` nedeniyle, işlevi aşırı `ToString` yüklemelisiniz. Aşağıdaki kodu *TodoItem.cs'ye,* oluşturucudan sonra ve sınıfının sonundan önce ekleyin.

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6. *TodoWindowControl.xaml.cs* içinde, ve yöntemleri `TodoWindowControl` için sınıfına `CheckForError` saplama `UpdateList` yöntemleri ekleyin. Bunları ProcessDialogChar'ın sonuna ve dosyanın sonuna koyabilirsiniz.

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     yöntemi, üst nesnede aynı adı olan bir yöntemi çağıracak ve bu yöntem herhangi bir hatanın olup olmadığını kontrol eder ve bunları `CheckForError` doğru şekilde işler. yöntemi, `UpdateList` üst denetimde ListBox'ı güncelleştirecek; bu sınıftaki ve özellikleri `Name` değiştir olduğunda yöntemi `DueDate` çağrılır. Bunlar daha sonra uygulanacak.

## <a name="integrate-into-the-properties-window"></a>Uygulamayla Özellikler penceresi
 Şimdi Özellikler penceresine bağlanacak ListBox'ını yöneten kodu **yazın.**

 TextBox'ı okumak, todoItem oluşturmak ve ListBox'a ekleyen düğme tıklama işleyicisini değiştirebilirsiniz.

1. Mevcut işlevi `button1_Click` yeni bir TodoItem oluşturan ve ListBox'a ekleyen kodla değiştirin. Daha sonra `TrackSelection()` tanımlanacak olan çağrısı.

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

2. Bu Tasarım görünümü ListBox denetimi seçin. Özellikler penceresinde **Olay** **işleyicileri düğmesine tıklayın** ve **SelectionChanged olayını** bulun. Metin kutusunu **listBox_SelectionChanged.** Bunu yapmak SelectionChanged işleyicisi için bir saplama ekler ve olayına atar.

3. yöntemini `TrackSelection()` uygulama. Hizmetleri ala ihtiyacınız <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> olacak, çünkü <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> TodoWindowControl tarafından erişilebilir hale gelecektir. `TodoWindow` sınıfına aşağıdaki yöntemi ekleyin:

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4. *TodoWindowControl.xaml.cs'ye aşağıdaki using yönergelerini ekleyin:*

    ```csharp
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Shell.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    ```

5. SelectionChanged işleyicisini aşağıdaki gibi doldurun:

    ```
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        TrackSelection();
    }
    ```

6. Şimdi, Özellikler penceresiyle tümleştirme sağlayacak TrackSelection işlevini **doldurun.** Kullanıcı ListBox'a bir öğe ekledığında veya ListBox'ta bir öğeye tıkladığında bu işlev çağrılır. ListBox içeriğini bir SelectionContainer'a ekler ve SelectionContainer'i **Özellikler** penceresinin olay işleyiciye <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> iletir. TrackSelection hizmeti, kullanıcı arabiriminde (UI) seçili nesneleri izler ve özelliklerini görüntüler

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

     Özellikler penceresinin kullanabileceği bir **sınıfına sahip** olduğunuza göre, Özellikler penceresini araç **penceresiyle** tümleştirebilirsiniz. Kullanıcı araç penceresinde ListBox'ta bir öğeye tıkladığında Özellikler **penceresinin** uygun şekilde güncelleştirilmiş olması gerekir. Benzer şekilde, kullanıcı Özellikler penceresinde bir ToDo **öğesini** değiştirirse, ilişkili öğenin güncelleştirilmiş olması gerekir.

7. Şimdi UpdateList işlev kodunun geri kalanını *TodoWindowControl.xaml.cs'ye ekleyin.* Değiştirilen TodoItem'i ListBox'tan bırakması ve yeniden eklemesi gerekir.

    ```csharp
    public void UpdateList(TodoItem item)
    {
        var index = listBox.SelectedIndex;
        listBox.Items.RemoveAt(index);
        listBox.Items.Insert(index, item);
        listBox.SelectedItem = index;
    }
    ```

8. Kodunuzu test etmek. Projeyi derleme ve hata ayıklamayı başlatma. Deneysel örneğin görünmesi gerekir.

9. Araçlar **Seçenekler**  >  **sayfasını** açın. Sol bölmede ToDo kategorisini görüyor gerekir. Kategoriler alfabetik olarak listelenir, bu nedenle Ts'nin altına bakın.

10. Todo **seçenekleri** sayfasında özelliğinin `DaysAhead` 0 olarak ayarlanmış olduğunu **görüyoruz.** 2 **olarak değiştirebilirsiniz.**

11. Görünüm **/ Diğer Windows menüsünde** **TodoWindow'u açın.** Metin **kutusuna EndDate** yazın ve Ekle'ye **tıklayın.**

12. Liste kutusunda, bugünden iki gün sonra bir tarih görüyor olun.

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Çıkış penceresine metin ve öğeler ekleme Görev Listesi
 bu **Görev Listesi,** Görev türünde yeni bir nesne oluşturur ve ardından yöntemini çağırarak **bu Görev nesnesini Görev Listesi** nesnesine `Add` eklersiniz. Çıkış penceresine **yazmak** için yöntemini çağırarak bir bölme nesnesi elde edersiniz ve `GetPane` ardından bölme `OutputString` nesnesinin yöntemini çağırabilirsiniz.

1. *TodoWindowControl.xaml.cs* içinde yönteminde, Çıkış penceresinin Genel bölmesini (varsayılandır) almak için kod ekleyin `button1_Click` ve bu bölmeye yazın.   Yöntem şöyle görünmelidir:

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

2. Veri sınıfına öğe eklemek Görev Listesi TodoWindowControl sınıfına iç içe geçmiş bir sınıf eklemeniz gerekir. İç içe geçmiş sınıfın 'den türetmiş olması <xref:Microsoft.VisualStudio.Shell.TaskProvider> gerekir. Aşağıdaki kodu sınıfının sonuna `TodoWindowControl` ekleyin.

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

3. Ardından sınıfına özel bir `TodoTaskProvider` başvuru ve `CreateProvider()` yöntemi `TodoWindowControl` ekleyin. Kod aşağıdaki gibi görünüyor olmalı:

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

4. sınıfına bir giriş Görev Listesi ve sınıfını `ClearError()` `ReportError()` temizleyen Görev Listesi `TodoWindowControl` ekleyin.

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

5. Şimdi yöntemini `CheckForErrors` aşağıdaki gibi gerçekleştirin.

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

1. Projeyi derleme ve hata ayıklamayı başlatma. Deneysel örnek görünür.

2. **TodoWindow ' u açın** (**Diğer**  >  **Windows**  >  **TodoWindow'u Görüntüle**).

3. Metin kutusuna bir şey yazın ve Ekle'ye **tıklayın.**

     Liste kutusuna bugünden 2 gün sonra bir son tarih eklenir. Hiçbir hata oluşturulmaz ve Görev Listesi **(** **Görünüm**  >  **Görev Listesi**) hiçbir girişe sahip değildir.

4. Şimdi Araçlar Seçenekler   >  ToDo **sayfasındaki ayarı**  >   **2'den** **0'a ayarlayın.**

5. **TodoWindow'a başka bir şey yazın ve** yeniden Ekle'ye tıklayın.  Bu, bir hata ve aynı zamanda içinde bir girişi **Görev Listesi.**

     Öğe eklerken başlangıç tarihi şimdi artı 2 gün olarak ayarlanır.

6. Görünüm menüsünde **Çıkış'a** **tıklayın** ve Çıkış **penceresini** açın.

     Bir öğe ekley her ekleyebilirsiniz, bu bölmede bir ileti **Görev Listesi.**

7. ListBox'ta öğelerden birini tıklatın.

     Özellikler **penceresinde** öğenin iki özelliği görüntülenir.

8. Özelliklerden birini değiştirin ve Enter tuşuna **basın.**

     Öğe ListBox'ta güncelleştirilir.
