---
title: Özellikleri, Görev Listesini, Çıktıyı, Seçenekleri pencerelerini genişletme
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db14068c97ff6868f5fb73c9ddd790020e99e7c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711629"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>Özellikleri, Görev Listesini, Çıktıyı ve Seçenekleri genişletme
Visual Studio'daki herhangi bir araç penceresine erişebilirsiniz. Bu izim, araç pencereniz hakkındaki bilgileri yeni bir **Seçenekler** sayfasına ve **Özellikler** sayfasındaki yeni bir ayara nasıl entegre edilebildiğini ve **görev listesi** ve **çıktı** pencerelerine nasıl yazılanın caiz olduğunu gösterir.

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak yer almaktadır. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-an-extension-with-a-tool-window"></a>Araç penceresi ile uzantı oluşturma

1. VSIX şablonu kullanarak **TodoList** adında bir proje oluşturun ve **TodoWindow**adlı özel bir araç penceresi öğesi şablonu ekleyin.

    > [!NOTE]
    > Araç penceresi yle uzantı oluşturma hakkında daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-a-tool-window.md)

## <a name="set-up-the-tool-window"></a>Araç penceresini ayarlama
 Yeni bir ToDo öğesi yazacak bir TextBox, listeye yeni öğeyi eklemek için bir Düğme ve listedeki öğeleri görüntülemek için bir ListBox ekleyin.

1. *TodoWindow.xaml'da,* Button, TextBox ve StackPanel denetimlerini UserControl'den silin.

    > [!NOTE]
    > Bu, daha sonraki bir adımda yeniden kullanacağınız **button1_Click** olay işleyicisini silmez.

2. **Araç Kutusu'nun** **Tüm WPF Denetimleri** bölümünden, **Bir Tuval** denetimini ızgaraya sürükleyin.

3. **TextBox,** **Düğme**ve **ListBox'ı** Tuvale sürükleyin. Öğeleri TextBox ve Düğme aynı düzeyde olacak şekilde düzenleyin ve ListBox aşağıdaki resimde olduğu gibi altlarındaki pencerenin geri kalanını doldurur.

     ![Bitmiş Takım Penceresi](../extensibility/media/t5-toolwindow.png "T5-Araç Penceresi")

4. XAML bölmesinde Düğme'yi bulun ve İçerik özelliğini **Ekle**olarak ayarlayın. Bir `Click="button1_Click"` öznitelik ekleyerek düğme olay işleyicisini Düğme denetimine yeniden bağlayın. Tuval bloğu aşağıdaki gibi görünmelidir:

    ```xml
    <Canvas HorizontalAlignment="Left" Width="306">
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>
    </Canvas>
    ```

### <a name="customize-the-constructor"></a>Oluşturucuyu özelleştirin

1. *TodoWindowControl.xaml.cs* dosyasına aşağıdaki yönergeleri ekleyin:

    ```csharp
    using System;
    ```

2. TodoWindow'a genel bir başvuru ekleyin ve TodoWindowControl oluşturucusu todoWindow parametresi almak zorunda. Kod şu na benzemelidir:

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3. *TodoWindow.cs,* TodoWindowControl oluşturucuyu TodoWindow parametresini içerecek şekilde değiştirin. Kod şu na benzemelidir:

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
 Kullanıcıların araç penceresinin ayarlarını değiştirebilmesi için **Seçenekler** iletişim kutusunda bir sayfa sağlayabilirsiniz. Seçenekler sayfası oluşturmak, hem seçenekleri açıklayan bir sınıf hem de *TodoListPackage.cs* veya *TodoListPackage.vb* dosyasındaki bir girişi gerektirir.

1. Adlı sınıf `ToolsOptions.cs`ekle. Sınıfın `ToolsOptions` devralını <xref:Microsoft.VisualStudio.Shell.DialogPage>yaratın.

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. Yönergeyi kullanarak aşağıdakileri ekleyin:

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. Bu gözden geçirme deki Seçenekler sayfası DaysAhead adında yalnızca bir seçenek sağlar. `ToolsOptions` **daysAhead** adlı özel bir alan ve sınıfa **DaysAhead** adlı bir özellik ekleyin:

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   Şimdi projeyi bu Seçenekler sayfasından haberdar etmek zorundasınız.

### <a name="make-the-options-page-available-to-users"></a>Seçenekler sayfasını kullanıcıların kullanımına sun

1. *TodoWindowPackage.cs,* `TodoWindowPackage` sınıfa <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> bir ekleyin:

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2. ProvideOptionPage oluşturucuya ilk parametre, daha önce `ToolsOptions`oluşturduğunuz sınıfın türüdür. İkinci parametre, "ToDo", **Seçenekler** iletişim kutusundaki kategorinin adıdır. Üçüncü parametre olan "Genel", **Seçenekler** iletişim kutusunun Seçenekler sayfasının bulunacağı alt kategorisinin adıdır. Sonraki iki parametre dizeleri için kaynak disleri; birincisi kategorinin adı, ikincisi ise alt kategorinin adıdır. Son parametre, bu sayfaya otomasyon kullanılarak erişilip erişilemeyeceğini belirler.

     Bir kullanıcı Seçenekler sayfanızı açtığında, aşağıdaki resme benzemesi gerekir.

     ![Seçenekler Sayfası](../extensibility/media/t5optionspage.gif "T5OptionsPage")

     **ToDo** kategorisine ve **Genel**alt kategoriye dikkat edin.

## <a name="make-data-available-to-the-properties-window"></a>Verileri Özellikler penceresinde kullanılabilir hale getirme
 ToDo listesi bilgilerini, Yapılacaklar listesindeki `TodoItem` tek tek öğeler le ilgili bilgileri depolayan adlandırılmış bir sınıf oluşturarak kullanılabilir hale getirebilirsiniz.

1. Adlı sınıf `TodoItem.cs`ekle.

     Araç penceresi kullanıcılar tarafından kullanılabilir olduğunda, ListBox'taki öğeler TodoItems tarafından temsil edilir. Kullanıcı ListBox'ta bu öğelerden birini seçtiğinde, **Özellikler** penceresi öğe yle ilgili bilgileri görüntüler.

     **Özellikleri** penceresinde veri kullanılabilir hale getirmek için, iki özel öznitelikleri `Description` olan `Category`ortak özellikleri içine veri açın ve . `Description`**Özellikler** penceresinin alt kısmında görünen metindir. `Category`**Özellikler** penceresi **Kategorilere Ayrılgı** görünümünde görüntülendiğinde özelliğin nerede görünacağını belirler. Aşağıdaki resimde, **Özellikler** penceresi **Kategorilere** Ayrılgörünümünde, **ToDo Alanları** kategorisindeki **Ad** özelliği seçilir ve **Ad** özelliğinin açıklaması pencerenin alt kısmında görüntülenir.

     ![Özellikler Penceresi](../extensibility/media/t5properties.png "T5Özellikleri")

2. *Yönergeleri kullanarak TodoItem.cs* dosyasını kullanarak aşağıdakileri ekleyin.

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

     İki özelliği ekleyin `Name` `DueDate`ve . Yaparız `UpdateList()` ve `CheckForErrors()` sonra.

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

4. Kullanıcı denetimine özel bir başvuru ekleyin. Bu Yapılacak Lar öğesinin kullanıcı denetimini ve adını alan bir oluşturucu ekleyin. Değerini bulmak için, `daysAhead`Seçenekler sayfa özelliği alır.

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

5. `TodoItem` Sınıfın örnekleri ListBox'ta depolanacağı ve ListBox `ToString` işlevi çağıracağı `ToString` için, işlevi aşırı yüklemeniz gerekir. Aşağıdaki kodu *TodoItem.cs,* oluşturucusonra ve sınıfın sonundan önce ekleyin.

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6. *TodoWindowControl.xaml.cs,* `TodoWindowControl` sınıfa saplama yöntemleri ni `CheckForError` `UpdateList` ve yöntemleri ekleyin. ProcessDialogChar'dan sonra ve dosyanın bitiminden önce koyun.

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     Yöntem, `CheckForError` üst nesnede aynı ada sahip bir yöntem çağırır ve bu yöntem herhangi bir hata oluştu olup olmadığını denetler ve bunları doğru şekilde işler. Yöntem, `UpdateList` listenin üst denetiminde güncellenir; yöntem, bu `Name` sınıftaki `DueDate` özellikler değiştiğinde çağrılır. Bunlar daha sonra uygulanacak.

## <a name="integrate-into-the-properties-window"></a>Özellikler penceresine tümleştirme
 Şimdi **Özellikler** penceresine bağlı olacak ListBox, yöneten kodu yazın.

 TextBox'ı okumak, Bir TodoItem oluşturmak ve ListBox'a ekler için düğme tıklama işleyicisini değiştirmeniz gerekir.

1. Varolan `button1_Click` işlevi yeni bir TodoItem oluşturan ve ListBox'a ekleyen kodla değiştirin. Daha `TrackSelection()`sonra tanımlanacak olan çağrıyı çağırır.

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

2. Tasarım görünümünde ListBox denetimini seçin. **Özellikler** penceresinde Olay **işleyicileri** düğmesini tıklatın ve **Seçim Değiştirildi** olayını bulun. Metin kutusunu **listBox_SelectionChanged**ile doldurun. Bunu yapmak, SelectionChanged işleyicisi için bir saplama ekler ve onu olaya atar.

3. Yöntemi `TrackSelection()` uygulayın. Hizmetleri almanız <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> gerektiğinden, TodoWindowControl <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> tarafından erişilebilir hale getirmeniz gerekir. <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> `TodoWindow` sınıfına aşağıdaki yöntemi ekleyin:

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4. *TodoWindowControl.xaml.cs*için yönergeleri kullanarak aşağıdakileri ekleyin:

    ```csharp
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Shell.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    ```

5. Seçilen işleyiciyi aşağıdaki gibi doldurun:

    ```
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        TrackSelection();
    }
    ```

6. Şimdi, **Özellikler** penceresi ile tümleştirme sağlayacak TrackSelection işlevini doldurun. Bu işlev, kullanıcı ListBox'a bir öğe eklediğinde veya ListBox'taki bir öğeyi tıklattığında çağrılır. ListBox'ın içeriğini Bir SelectionContainer'a ekler ve SelectionContainer'ı <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> **Özellikler** penceresinin olay işleyicisine geçirir. TrackSelection hizmeti, kullanıcı arabiriminde (UI) seçili nesneleri izler ve özelliklerini görüntüler

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

     **Artık Özellikler** penceresinin kullanabileceği bir sınıfa sahip olduğunuza göre, **Özellikler** penceresini araç penceresiyle tümleştirebilirsiniz. Kullanıcı araç penceresindeki ListBox'taki bir öğeyi tıklattığında, **Özellikler** penceresi buna göre güncelleştirilmelidir. Benzer şekilde, kullanıcı **Özellikler** penceresinde bir ToDo öğesini değiştirdiğinde, ilişkili öğenin güncelleştirilmelidir.

7. Şimdi, TodoWindowControl.xaml.cs UpdateList işlev kodunun geri kalanını *ekleyin.* ListBox'tan değiştirilmiş TodoItem'i düşürmeli ve yeniden eklemelidir.

    ```csharp
    public void UpdateList(TodoItem item)
    {
        var index = listBox.SelectedIndex;
        listBox.Items.RemoveAt(index);
        listBox.Items.Insert(index, item);
        listBox.SelectedItem = index;
    }
    ```

8. Kodunuzu test edin. Projeyi oluşturun ve hata ayıklamaya başlayın. Deneysel örnek görünmelidir.

9. **Araç** > **Seçenekleri** sayfasını açın. Sol bölmede ToDo kategorisini görmelisiniz. Kategoriler alfabetik olarak listelenir, bu nedenle Ts altına bakın.

10. **Todo** seçenekleri sayfasında, **0**olarak `DaysAhead` ayarlanmış özelliği görmeniz gerekir. **2**olarak değiştirin.

11. Görünüm **/ Diğer Windows** menüsünde, **TodoWindow'u**açın. Metin kutusuna **Bitiş Tarihi** yazın ve **Ekle'yi**tıklatın.

12. Liste kutusunda, bugünden iki gün sonra bir tarih görmeniz gerekir.

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Çıktı penceresine metin ve Görev Listesine öğeler ekleme
 Görev **Listesi**için, Görev türünde yeni bir nesne oluşturursunuz ve ardından bu `Add` Görev nesnesini yöntemini çağırarak **Görev Listesi'ne** eklersiniz. **Çıktı** penceresine yazmak için, `GetPane` bir bölme nesnesi elde etmek için `OutputString` yöntemini çağırırsınız ve sonra bölme nesnesinin yöntemini çağırırsınız.

1. *TodoWindowControl.xaml.cs,* `button1_Click` yöntemde, **Çıkış** penceresinin **Genel** bölmesini almak için kod ekleyin (varsayılan dır) ve ona yazın. Yöntem şöyle görünmelidir:

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

2. Görev Listesi'ne öğe eklemek için, TodoWindowControl sınıfına iç içe bir sınıf eklemek için a'nın olması gerekir. İç içe geçen <xref:Microsoft.VisualStudio.Shell.TaskProvider>sınıfın. `TodoWindowControl` Sınıfın sonuna aşağıdaki kodu ekleyin.

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

3. Sonraki `TodoTaskProvider` `TodoWindowControl` sınıfa özel bir `CreateProvider()` başvuru ve bir yöntem ekleyin. Kod şu na benzemelidir:

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

4. Görev `ClearError()`Listesini temizleyen ve `ReportError()`Görev Listesi'ne bir giriş ekleyen `TodoWindowControl` sınıfa ekle.

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

5. Şimdi aşağıdaki `CheckForErrors` gibi yöntemi uygulayın.

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

1. Projeyi oluşturun ve hata ayıklamaya başlayın. Deneysel örnek görüntülenir.

2. **TodoWindow'u** açın (**Diğer Windows** > **TodoWindow'u****Görüntüle** > ).

3. Metin kutusuna bir şey yazın ve sonra **Ekle'yi**tıklatın.

     Bugünden 2 gün sonra vade tarihi liste kutusuna eklenir. Hiçbir hata oluşturulmaz ve **Görev Listesi** **(Görev Listesini****Görüntüle)** > girişi olmamalıdır.

4. Şimdi **Araçlar** > **Seçenekleri** > **Yapılacaklar** sayfasındaki ayarı **2'den** **0'a**değiştirin.

5. **TodoWindow'a** başka bir şey yazın ve sonra yeniden **Ekle'yi** tıklatın. Bu, bir hatayı ve görev **listesindeki**bir girişi tetikler.

     Öğeleri eklediğinizde, başlangıç tarihi şimdi artı 2 gün olarak ayarlanır.

6. **Görünüm** menüsünde Çıktı penceresini açmak için **Çıktı'yı** tıklatın. **Output**

     Her öğe eklediğinizde, **Görev Listesi** bölmesinde bir iletinin görüntülendiğine dikkat edin.

7. ListBox'taki öğelerden birini tıklatın.

     **Özellikler** penceresi maddenin iki özelliğini görüntüler.

8. Özelliklerden birini değiştirin ve **Enter**tuşuna basın.

     Öğe ListBox'ta güncelleştirilir.
