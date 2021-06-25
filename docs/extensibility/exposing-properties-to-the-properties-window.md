---
title: Özellikleri Özellikler penceresine gösterme | Microsoft Docs
description: Bir nesnenin ortak özellikleri hakkında bilgi edinin. Bu özelliklerde yaptığınız değişiklikler Özellikler penceresi yansıtılır.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5f932772b031332d7df2a2487c70576f49407ba1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898743"
---
# <a name="expose-properties-to-the-properties-window"></a>Özellikler penceresi özellikleri kullanıma sunun

Bu izlenecek yol, bir nesnenin ortak özelliklerini **Özellikler** penceresinde gösterir. Bu özelliklerde yaptığınız değişiklikler **Özellikler** penceresinde yansıtılır.

## <a name="prerequisites"></a>Önkoşullar

Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="expose-properties-to-the-properties-window"></a>Özellikler penceresi özellikleri kullanıma sunun

Bu bölümde, özel bir araç penceresi oluşturur ve **Özellikler** penceresinde ilişkili pencere bölmesi nesnesinin ortak özelliklerini görüntüleyebilirsiniz.

### <a name="to-expose-properties-to-the-properties-window"></a>Özellikler penceresi özellikleri göstermek için

1. Her Visual Studio uzantısı, uzantı varlıklarını içeren bir VSıX dağıtım projesiyle başlar. Adlı bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX projesi oluşturun `MyObjectPropertiesExtension` . "VSIX" araması yaparak VSıX proje şablonunu **Yeni proje** iletişim kutusunda bulabilirsiniz.

2. Adlı özel bir araç penceresi öğe şablonu ekleyerek bir araç penceresi ekleyin `MyToolWindow` . **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve   >  **Yeni öğe** Ekle ' yi seçin. **Yeni öğe Ekle iletişim kutusunda**, **Visual C# öğeleri**  >  **genişletilebilirliği** ' ne gidin ve **özel araç penceresi**' ni seçin. İletişim kutusunun alt kısmındaki **ad** alanında, dosya adını *MyToolWindow. cs* olarak değiştirin. Özel bir araç penceresi oluşturma hakkında daha fazla bilgi için bkz. [bir araç penceresi ile uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md).

3. *MyToolWindow. cs* ' i açın ve aşağıdaki using ifadesini ekleyin:

   ```csharp
   using System.Collections;
   using System.ComponentModel;
   using Microsoft.VisualStudio.Shell.Interop;
   ```

4. Şimdi aşağıdaki alanları `MyToolWindow` sınıfına ekleyin.

   ```csharp
   private ITrackSelection trackSel;
   private SelectionContainer selContainer;

   ```

5. Aşağıdaki kodu `MyToolWindow` sınıfına ekleyin.

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

   public void UpdateSelection()
   {
       ITrackSelection track = TrackSelection;
       if (track != null)
           track.OnSelectChange((ISelectionContainer)selContainer);
   }

   public void SelectList(ArrayList list)
   {
       selContainer = new SelectionContainer(true, false);
       selContainer.SelectableObjects = list;
       selContainer.SelectedObjects = list;
       UpdateSelection();
   }

   public override void OnToolWindowCreated()
   {
       ArrayList listObjects = new ArrayList();
       listObjects.Add(this);
       SelectList(listObjects);
   }
   ```

    `TrackSelection`Özelliği `GetService` `STrackSelection` , bir arabirim sağlayan bir hizmeti elde etmek için kullanır <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> . `OnToolWindowCreated`Olay işleyicisi ve `SelectList` yöntemi birlikte yalnızca araç pencere bölmesi nesnesinin kendisini içeren seçili nesnelerin bir listesini oluşturur. `UpdateSelection`Yöntemi, **Özellikler** penceresine araç penceresi bölmesinin ortak özelliklerini göstermesini söyler.

6. Projeyi derleyin ve hata ayıklamayı başlatın. Visual Studio 'nun deneysel örneği görünmelidir.

7. **Özellikler** penceresi görünmüyorsa, **F4** tuşuna basarak açın.

8. **MyToolWindow** penceresini açın.   >  **Diğer pencereleri** görüntülemek için bunu bulabilirsiniz.

    Pencere açılır ve pencere bölmesinin ortak özellikleri **Özellikler** penceresinde görünür.

9. **Özellikler** penceresindeki **Caption** özelliğini **nesnem özellikleri** olarak değiştirin.

     MyToolWindow pencere başlığı, buna göre değişir.

## <a name="expose-tool-window-properties"></a>Araç penceresi özelliklerini kullanıma sunma

Bu bölümde bir araç penceresi ekler ve özelliklerini kullanıma sunun. Özelliklerde yaptığınız değişiklikler **Özellikler** penceresinde yansıtılır.

### <a name="to-expose-tool-window-properties"></a>Araç penceresi özelliklerini açığa çıkarmak için

1. *MyToolWindow. cs*' yi açın ve sınıfa IsChecked genel Boolean özelliğini ekleyin `MyToolWindow` .

    ```csharp
    [Category("My Properties")]
    [Description("MyToolWindowControl properties")]
    public bool IsChecked
    {
        get {
            if (base.Content == null)  return false;
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;
        }
        set {
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;
        }
    }
    ```

     Bu özellik, daha sonra oluşturacağınız WPF onay kutusunun durumunu alır.

2. *MyToolWindowControl. xaml. cs* ' i açın ve MyToolWindowControl oluşturucusunu aşağıdaki kodla değiştirin.

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

3. *MyToolWindow. cs* dosyasında, `MyToolWindow` oluşturucuyu aşağıdaki gibi değiştirin:

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

10. **MyToolWindow** penceresindeki onay kutusunu işaretleyin. **Özellikler** penceresinde **IsChecked** **değeri true** olarak değişir. **MyToolWindow** penceresindeki onay kutusunun işaretini kaldırın. **Özellikler** penceresinde **IsChecked** **yanlış** olarak değişir. **Özellikler** penceresinde **IsChecked** değerini değiştirin. **MyToolWindow** penceresindeki onay kutusu yeni değerle eşleşecek şekilde değişir.

    > [!NOTE]
    > **Özellikler** penceresinde görüntülenen bir nesneyi Dispose etmeniz gerekiyorsa, `OnSelectChange` `null` önce bir seçim kapsayıcısı ile çağırın. Özelliği veya nesneyi elden aldıktan sonra, güncelleştirilmiş ve listeleri olan bir seçim kapsayıcısına geçiş yapabilirsiniz <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> .

## <a name="change-selection-lists"></a>Seçim listelerini Değiştir

 Bu bölümde, temel özellik sınıfı için bir seçim listesi ekler ve görüntülenecek seçim listesini seçmek için araç penceresi arabirimini kullanın.

### <a name="to-change-selection-lists"></a>Seçim listesini değiştirmek için

1. *MyToolWindow. cs* ' i açın ve adlı ortak bir sınıf ekleyin `Simple` .

    ```csharp
    public class Simple
    {
        private string someText = "";

        [Category("My Properties")]
        [Description("Simple Properties")]
        [DisplayName("My Text")]
        public string SomeText
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

2. `SimpleObject` `MyToolWindow` Pencere bölmesi ve nesnesi arasında **Özellikler** penceresi seçimini değiştirmek için sınıfa bir özellik ve iki yöntem ekleyin `Simple` .

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

3. *MyToolWindowControl. cs* dosyasında, onay kutusu işleyicilerini şu kod satırlarıyla değiştirin:

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

6. **MyToolWindow** penceresindeki onay kutusunu seçin. **Özellikler** penceresi, `Simple` **metin** ve **salt okunur** nesne özelliklerini görüntüler. Onay kutusunun işaretini kaldırın. Pencerenin ortak özellikleri **Özellikler** penceresinde görünür.

    > [!NOTE]
    > **SomeText** 'in görünen adı **Metnim**.

## <a name="best-practice"></a>En iyi yöntem

Bu izlenecek yolda, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> seçilebilir nesne koleksiyonu ve seçilen nesne koleksiyonu aynı koleksiyon olacak şekilde uygulanır. Yalnızca seçilen nesne, özellik tarayıcısı listesinde görünür. Daha kapsamlı bir ISelectionContainer uygulaması için bkz. Reference. ToolWindow Samples.

Visual Studio aracı Windows, Visual Studio oturumları arasında kalır. Araç penceresi durumunu kalıcı hale getirme hakkında daha fazla bilgi için bkz <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> ..

## <a name="see-also"></a>Ayrıca bkz.

- [Özellikleri ve özellik penceresini genişletme](../extensibility/extending-properties-and-the-property-window.md)
