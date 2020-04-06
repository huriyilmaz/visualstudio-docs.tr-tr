---
title: Özellikler Penceresine Özellikleri Açığa Çıkarma | Microsoft Dokümanlar
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f84962628ae550676e2c2eeb10c0f3baeca1bb58
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711822"
---
# <a name="expose-properties-to-the-properties-window"></a>Özellikleri pencereye göster

Bu gözden geçirme, bir nesnenin ortak özelliklerini **Özellikler** penceresine maruz bırakır. Bu özelliklerde yaptığınız değişiklikler **Özellikler** penceresine yansıtılır.

## <a name="prerequisites"></a>Ön koşullar

Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak yer almaktadır. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="expose-properties-to-the-properties-window"></a>Özellikleri pencereye göster

Bu bölümde, özel bir araç penceresi oluşturmak ve **Özellikler** penceresinde ilişkili pencere bölmesi nesnesinin ortak özelliklerini görüntüleyin.

### <a name="to-expose-properties-to-the-properties-window"></a>Özellikleri pencereye çıkarmak için

1. Her Visual Studio uzantısı, uzantı varlıklarını içeren bir VSIX dağıtım projesiyle başlar. Adlı `MyObjectPropertiesExtension` [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir VSIX projesi oluşturun. "vsix" aramasını yaparak **VSIX** proje şablonunu Yeni Proje iletişim kutusunda bulabilirsiniz.

2. Özel Araç Penceresi öğesi şablonu ekleyerek `MyToolWindow`bir araç penceresi ekleyin. Çözüm **Gezgini'nde**proje düğümüne sağ tıklayın ve**Yeni Öğe** **Ekle'yi** > seçin. Yeni **Öğe Ekle iletişim kutusunda,** **Visual C# Items** > **Extensibility'e** gidin ve **Özel Araç Penceresi'ni**seçin. İletişim kutusunun altındaki **Ad** alanında, dosya adını *MyToolWindow.cs*olarak değiştirin. Özel bir araç penceresi oluşturma hakkında daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-a-tool-window.md)

3. *MyToolWindow.cs* açın ve aşağıdaki leri kullanarak ekleyin:

   ```csharp
   using System.Collections;
   using System.ComponentModel;
   using Microsoft.VisualStudio.Shell.Interop;
   ```

4. Şimdi `MyToolWindow` sınıfa aşağıdaki alanları ekleyin.

   ```csharp
   private ITrackSelection trackSel;
   private SelectionContainer selContainer;

   ```

5. `MyToolWindow` Sınıfa aşağıdaki kodu ekleyin.

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

    Özellik, `TrackSelection` `GetService` arabirim <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> `STrackSelection` sağlayan bir hizmet elde etmek için kullanır. Olay `OnToolWindowCreated` işleyicisi ve `SelectList` yöntemi birlikte yalnızca araç penceresi bölmesi nesnesinin kendisini içeren seçili nesnelerin bir listesini oluşturur. Yöntem, `UpdateSelection` **Özellikler** penceresine araç penceresi bölmesinin ortak özelliklerini görüntülemesini söyler.

6. Projeyi oluşturun ve hata ayıklamaya başlayın. Visual Studio'nun deneysel örneği görünmelidir.

7. **Özellikler** penceresi görünmüyorsa, **F4**tuşuna basarak açın.

8. **MyToolWindow** penceresini açın. **Diğer Windows'u** **Görüntüle'de** > bulabilirsiniz.

    Pencere açılır ve pencere bölmesinin ortak özellikleri **Özellikler** penceresinde görünür.

9. **Özellikler** penceresindeki **Resim Yazısı** özelliğini **Nesne Özelliklerim olarak**değiştirin.

     MyToolWindow pencere başlığı buna göre değişir.

## <a name="expose-tool-window-properties"></a>Araç penceresi özelliklerini ortaya çıkarma

Bu bölümde, bir araç penceresi ekleyin ve özelliklerini ortaya çıkarır. Özelliklerde yaptığınız değişiklikler **Özellikler** penceresine yansıtılır.

### <a name="to-expose-tool-window-properties"></a>Araç penceresi özelliklerini ortaya çıkarmak için

1. *MyToolWindow.cs*açın ve halka açık boolean özelliğiischecked sınıfa `MyToolWindow` ekleyin.

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

     Bu özellik, durumunu daha sonra oluşturacağınız WPF onay kutusundan alır.

2. *MyToolWindowControl.xaml.cs* açın ve MyToolWindowControl oluşturucuyu aşağıdaki kodla değiştirin.

    ```vb
    private MyToolWindow pane;
    public MyToolWindowControl(MyToolWindow pane)
    {
        InitializeComponent();
        this.pane = pane;
        checkBox.IsChecked = false;
    }
    ```

     Bu `MyToolWindowControl` `MyToolWindow` bölmeye erişim sağlar.

3. *MyToolWindow.cs*olarak, `MyToolWindow` aşağıdaki gibi yapıcı değiştirin:

    ```csharp
    base.Content = new MyToolWindowControl(this);
    ```

4. MyToolWindowControl'un tasarım görünümünü değiştirin.

5. Düğmeyi silin ve **Araç Kutusu'ndan** sol üst köşeye bir onay kutusu ekleyin.

6. İşaretli ve İşaretlenmemiş olayları ekleyin. Tasarım görünümünde onay kutusunu seçin. **Özellikler** penceresinde, olay işleyicileri düğmesini **(Özellikler** penceresinin sağ üst kısmında) tıklatın. **İşaretli'yi** bulun ve metin kutusuna **checkbox_Checked** yazın, ardından **İşaretsiz'i** bulun ve metin kutusuna **checkbox_Unchecked** yazın.

7. Onay kutusu olay işleyicileri ekleyin:

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

8. Projeyi oluşturun ve hata ayıklamaya başlayın.

9. Deneysel örnekte, **MyToolWindow** penceresini açın.

     **Özellikler** penceresinde pencerenin özelliklerini arayın. **IsChecked** özelliği pencerenin alt kısmında, **Özelliklerim** kategorisialtında görünür.

10. **MyToolWindow** penceresindeki onay kutusunu işaretleyin. **Özellikler** penceresinde **IsChecked** **True**olarak değişir. **MyToolWindow** penceresindeki onay kutusunu temizleyin. **Özellikler** penceresinde Yanlış **olarak** **değiştirildi.** **Özellikler** penceresinde **IsChecked** değerini değiştirin. **MyToolWindow** penceresindeki onay kutusu yeni değerle eşleşecek şekilde değişir.

    > [!NOTE]
    > **Özellikler** penceresinde görüntülenen bir nesneyi imha nız gerekiyorsa, `null` önce bir seçim kapsayıcısıyla arayın. `OnSelectChange` Özelliği veya nesneyi atadıktan sonra, güncelleştirilen <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> ve <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> listelenen bir seçim kapsayıcısına değiştirebilirsiniz.

## <a name="change-selection-lists"></a>Seçim listelerini değiştirme

 Bu bölümde, temel özellik sınıfı için bir seçim listesi ekleyin ve hangi seçim listesinin görüntüleyeceğini seçmek için araç penceresi arabirimini kullanın.

### <a name="to-change-selection-lists"></a>Seçim listelerini değiştirmek için

1. *MyToolWindow.cs* açın ve adlandırılmış `Simple`bir genel sınıf ekleyin.

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

2. Sınıfa `SimpleObject` bir özellik ve pencere bölmesi ve `Simple` nesne arasında Özellikler penceresi seçimini değiştirmek için iki yöntem ekleyin. **Properties** `MyToolWindow`

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

3. *MyToolWindowControl.cs,* onay kutusu işleyicilerini şu kod satırlarıyla değiştirin:

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

4. Projeyi oluşturun ve hata ayıklamaya başlayın.

5. Deneysel örnekte, **MyToolWindow** penceresini açın.

6. **MyToolWindow** penceresindeki onay kutusunu seçin. **Özellikler** penceresi `Simple` nesne özelliklerini görüntüler, **SomeText** ve **ReadOnly.** Onay kutusunu temizle. Pencerenin ortak özellikleri **Özellikler** penceresinde görünür.

    > [!NOTE]
    > **SomeText'in** görüntü adı **Benim Metnimdir.**

## <a name="best-practice"></a>En iyi yöntem

Bu izbiste, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> seçilebilir nesne koleksiyonu ve seçili nesne koleksiyonu aynı koleksiyon olacak şekilde uygulanır. Özellik Tarayıcısı listesinde yalnızca seçili nesne görünür. Daha eksiksiz bir ISelectionContainer uygulaması için Reference.ToolWindow örneklerine bakın.

Visual Studio araç pencereleri Visual Studio oturumları arasında devam etmektedir. Araç penceresi durumunu devamlandırma hakkında daha <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>fazla bilgi için bkz.

## <a name="see-also"></a>Ayrıca bkz.

- [Özellikleri ve Özellik penceresini genişletme](../extensibility/extending-properties-and-the-property-window.md)
