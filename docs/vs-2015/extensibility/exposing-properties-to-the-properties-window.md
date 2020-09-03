---
title: Özellikleri Özellikler penceresine gösterme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
caps.latest.revision: 37
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c28a0520680951920ee19e91f3df098066f432dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64787052"
---
# <a name="exposing-properties-to-the-properties-window"></a>Özellikleri ve Özellik Penceresini Kullanıma Sunma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, bir nesnenin ortak özelliklerini **Özellikler** penceresinde gösterir. Bu özelliklerde yaptığınız değişiklikler **Özellikler** penceresinde yansıtılır.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="exposing-properties-to-the-properties-window"></a>Özellikleri ve Özellik Penceresini Kullanıma Sunma  
 Bu bölümde, özel bir araç penceresi oluşturur ve **Özellikler** penceresinde ilişkili pencere bölmesi nesnesinin ortak özelliklerini görüntüleyebilirsiniz.  
  
#### <a name="to-expose-properties-to-the-properties-window"></a>Özellikler penceresi özellikleri göstermek için  
  
1. Her Visual Studio uzantısı, uzantı varlıklarını içeren bir VSıX dağıtım projesiyle başlar. Adlı bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] VSIX projesi oluşturun `MyObjectPropertiesExtension` . VSıX proje şablonunu, **Visual C#/genişletilebilirlik**altında **Yeni proje** iletişim kutusunda bulabilirsiniz.  
  
2. Adlı özel bir araç penceresi öğe şablonu ekleyerek bir araç penceresi ekleyin `MyToolWindow` . **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve **Ekle/yeni öğe**' yi seçin. **Yeni öğe Ekle iletişim kutusunda** **Visual C# öğeleri/genişletilebilirlik** ' e gidin ve **özel araç penceresi**' ni seçin. İletişim kutusunun alt kısmındaki **ad** alanında, dosya adını olarak değiştirin `MyToolWindow.cs` . Özel bir araç penceresi oluşturma hakkında daha fazla bilgi için bkz. [bir araç penceresi Ile uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3. MyToolWindow.cs açın ve aşağıdaki using ifadesini ekleyin:  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4. Şimdi aşağıdaki alanları `MyToolWindow` sınıfına ekleyin.  
  
    ```csharp  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5. Aşağıdaki kodu MyToolWindow sınıfına ekleyin.  
  
    ```csharp  
    private ITrackSelection TrackSelection  
    {  
        get  
        {  
            if (trackSel == null)  
                trackSel =  
                   GetService(typeof(STrackSelection)) as ITrackSelection;  
            return trackSel;  
        }  
    }  
  
    public void UpdateSelection()  
    {  
        ITrackSelection track = TrackSelection;  
        if (track != null)  
            track.OnSelectChange((ISelectionContainer)selContainer);  
    }  
  
    public void SelectList(ArrayList list)  
    {  
        selContainer = new SelectionContainer(true, false);  
        selContainer.SelectableObjects = list;  
        selContainer.SelectedObjects = list;  
        UpdateSelection();  
    }  
  
    public override void OnToolWindowCreated()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
     `TrackSelection`Özelliği `GetService` `STrackSelection` , bir arabirim sağlayan bir hizmeti elde etmek için kullanır <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> . `OnToolWindowCreated`Olay işleyicisi ve `SelectList` yöntemi birlikte yalnızca araç pencere bölmesi nesnesinin kendisini içeren seçili nesnelerin bir listesini oluşturur. `UpdateSelection`Yöntemi, **Özellikler** penceresine araç penceresi bölmesinin ortak özelliklerini göstermesini söyler.  
  
6. Projeyi derleyin ve hata ayıklamayı başlatın. Visual Studio 'nun deneysel örneği görünmelidir.  
  
7. **Özellikler** penceresi görünmüyorsa, F4 tuşuna basarak açın.  
  
8. **MyToolWindow** penceresini açın. Bunu, **Görünüm/diğer pencereler**içinde bulabilirsiniz.  
  
     Pencere açılır ve pencere bölmesinin ortak özellikleri **Özellikler** penceresinde görünür.  
  
9. **Özellikler** penceresindeki **Caption** özelliğini **nesnem özellikleri**olarak değiştirin.  
  
     MyToolWindow pencere başlığı, buna göre değişir.  
  
## <a name="exposing-tool-window-properties"></a>Araç penceresi özelliklerini gösterme  
 Bu bölümde bir araç penceresi ekler ve özelliklerini kullanıma sunun. Özelliklerde yaptığınız değişiklikler **Özellikler** penceresinde yansıtılır.  
  
#### <a name="to-expose-tool-window-properties"></a>Araç penceresi özelliklerini açığa çıkarmak için  
  
1. MyToolWindow.cs 'i açın ve MyToolWindow sınıfına IsChecked genel Boolean özelliğini ekleyin.  
  
    ```csharp  
    [Category("My Properties")]  
    [Description("MyToolWindowControl properties")]  
    public bool IsChecked  
    {  
        get {  
            if (base.Content == null)  return false;  
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;   
        }  
        set {  
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;  
        }  
    }  
    ```  
  
     Bu özellik, daha sonra oluşturacağınız WPF onay kutusunun durumunu alır.  
  
2. MyToolWindowControl.xaml.cs açın ve MyToolWindowControl oluşturucusunu aşağıdaki kodla değiştirin.  
  
    ```vb  
    private MyToolWindow pane;  
    public MyToolWindowControl(MyToolWindow pane)  
    {  
        InitializeComponent();  
        this.pane = pane;  
        checkBox.IsChecked = false;  
    }  
    ```  
  
     Bu `MyToolWindowControl` , bölmeye erişim sağlar `MyToolWindow` .  
  
3. MyToolWindow.cs içinde, `MyToolWindow` oluşturucuyu aşağıdaki gibi değiştirin:  
  
    ```csharp  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4. MyToolWindowControl Tasarım görünümüne geçin.  
  
5. Düğmeyi silin ve **araç** kutusundan sol üst köşeye bir onay kutusu ekleyin.  
  
6. Denetlenen ve Denetlenmemiş olayları ekleyin. Tasarım görünümündeki onay kutusunu seçin. **Özellikler** penceresinde olay işleyiciler düğmesine ( **Özellikler** penceresinin sağ üst kısmında) tıklayın. **Denetlenen** ve metin kutusunda **checkbox_Checked** yazın ve metin kutusuna **denetimsiz** bulun ve **checkbox_Unchecked** yazın.  
  
7. Onay kutusu olay işleyicilerini ekleyin:  
  
    ```csharp  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = true;  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.UpdateSelection();  
    }  
    ```  
  
8. Projeyi derleyin ve hata ayıklamayı başlatın.  
  
9. Deneysel örnekte **MyToolWindow** penceresini açın.  
  
     **Özellikler** penceresinde pencerenin özelliklerini bulun. **IsChecked** özelliği, pencerenin alt kısmında, **My Properties** kategorisinin altında görünür.  
  
10. **MyToolWindow** penceresindeki onay kutusunu işaretleyin. **Özellikler** penceresinde **IsChecked** **değeri true**olarak değişir. **MyToolWindow** penceresindeki onay kutusunun işaretini kaldırın. **Özellikler** penceresinde **IsChecked** **yanlış**olarak değişir. **Özellikler** penceresinde **IsChecked** değerini değiştirin. **MyToolWindow** penceresindeki onay kutusu yeni değerle eşleşecek şekilde değişir.  
  
    > [!NOTE]
    > **Özellikler** penceresinde görüntülenen bir nesneyi Dispose etmeniz gerekiyorsa, `OnSelectChange` `null` önce bir seçim kapsayıcısı ile çağırın. Özelliği veya nesneyi elden aldıktan sonra, güncelleştirilmiş ve listeleri olan bir seçim kapsayıcısına geçiş yapabilirsiniz <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> .  
  
## <a name="changing-selection-lists"></a>Seçim listelerini değiştirme  
 Bu bölümde, temel özellik sınıfı için bir seçim listesi ekler ve görüntülenecek seçim listesini seçmek için araç penceresi arabirimini kullanın.  
  
#### <a name="to-change-selection-lists"></a>Seçim listesini değiştirmek için  
  
1. MyToolWindow.cs açın ve adlı ortak bir sınıf ekleyin `Simple` .  
  
    ```csharp  
    public class Simple  
    {  
        private string someText = "";  
  
        [Category("My Properties")]  
        [Description("Simple Properties")]  
        [DisplayName("My Text")]  
        public string SomeText  
        {  
            get { return someText; }  
            set { someText = value; }  
        }  
  
        [Category("My Properties")]  
        [Description("Read-only property")]  
        public bool ReadOnly  
        {  
            get { return false; }  
        }  
    }  
    ```  
  
2. MyToolWindow sınıfına bir SimpleObject özelliği ekleyin, ayrıca pencere bölmesi ve nesnesi arasında **Özellikler** penceresi seçimini değiştirmek için iki yöntem `Simple` .  
  
    ```csharp  
    private Simple simpleObject = null;  
    public Simple SimpleObject  
    {  
        get  
        {  
            if (simpleObject == null) simpleObject = new Simple();  
            return simpleObject;  
        }  
    }  
  
    public void SelectSimpleList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(SimpleObject);  
        SelectList(listObjects);  
    }  
  
    public void SelectThisList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
3. MyToolWindowControl.cs ' de, onay kutusu işleyicilerini şu kod satırlarıyla değiştirin:  
  
    ```csharp  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
     {  
        pane.IsChecked = true;  
        pane.SelectSimpleList();  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.SelectThisList();  
        pane.UpdateSelection();  
    }  
    ```  
  
4. Projeyi derleyin ve hata ayıklamayı başlatın.  
  
5. Deneysel örnekte **MyToolWindow** penceresini açın.  
  
6. **MyToolWindow** penceresindeki onay kutusunu seçin. **Özellikler** penceresi, `Simple` **metin** ve **salt okunur**nesne özelliklerini görüntüler. Onay kutusunun işaretini kaldırın. Pencerenin ortak özellikleri **Özellikler** penceresinde görünür.  
  
    > [!NOTE]
    > **SomeText** 'in görünen adı **Metnim**.  
  
## <a name="best-practice"></a>En İyi Yöntem  
 Bu izlenecek yolda, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> seçilebilir nesne koleksiyonu ve seçilen nesne koleksiyonu aynı koleksiyon olacak şekilde uygulanır. Yalnızca seçilen nesne, özellik tarayıcısı listesinde görünür. Daha kapsamlı bir ISelectionContainer uygulaması için bkz. Reference. ToolWindow Samples.  
  
 Visual Studio aracı Windows, Visual Studio oturumları arasında kalır. Araç penceresi durumunu kalıcı hale getirme hakkında daha fazla bilgi için bkz <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> ..  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellikleri ve Özellik Penceresini Genişletme](../extensibility/extending-properties-and-the-property-window.md)
