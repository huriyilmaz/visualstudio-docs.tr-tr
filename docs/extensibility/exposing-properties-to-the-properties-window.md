---
title: Özellikleri Özellikler Penceresine | Microsoft Docs
description: Bir nesnenin genel özellikleri hakkında bilgi edinmek. Bu özelliklerde yaptığınız değişiklikler, Özellikler penceresi.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 048a8e0316ae4c98e9e2673b017d98cfc1b15144
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057323"
---
# <a name="expose-properties-to-the-properties-window"></a>Özellikleri Özellikler penceresi

Bu kılavuz, bir nesnenin genel özelliklerini Özellikler penceresinde **gösterir.** Bu özelliklerde yaptığınız değişiklikler Özellikler penceresine **yansıtıldı.**

## <a name="prerequisites"></a>Önkoşullar

2015'Visual Studio başlayarak, Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Bu, kurulumda isteğe bağlı bir Visual Studio olarak dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="expose-properties-to-the-properties-window"></a>Özellikleri Özellikler penceresi

Bu bölümde, özel bir araç penceresi oluşturur ve Özellikler penceresinde ilişkili pencere bölmesi nesnesinin genel özelliklerini **görüntülersiniz.**

### <a name="to-expose-properties-to-the-properties-window"></a>Özellikleri Özellikler penceresi

1. Her Visual Studio uzantısı, uzantı varlıklarını içeren bir VSIX dağıtım projesiyle başlar. adlı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir VSIX projesi `MyObjectPropertiesExtension` oluşturun. VSIX proje şablonunu New **Project** "vsix" arayarak bulabilirsiniz.

2. adlı Özel Araç Penceresi öğe şablonu ekleyerek bir araç penceresi `MyToolWindow` ekleyin. Giriş **Çözüm Gezgini** proje düğümüne sağ tıklayın ve Yeni Öğe **Ekle'yi**  >  **seçin.** Yeni Öğe **Ekle iletişim kutusunda Visual** C# Öğeleri **Genişletilebilirliği'ne** gidin ve Özel  >   Araç **Penceresi'ne tıklayın.** İletişim **kutusunun** altındaki Ad alanında dosya adını *MyToolWindow.cs olarak değiştirebilirsiniz.* Özel araç penceresi oluşturma hakkında daha fazla bilgi için [bkz. Araç penceresiyle uzantı oluşturma.](../extensibility/creating-an-extension-with-a-tool-window.md)

3. *MyToolWindow.cs'yi* açın ve aşağıdaki using deyimini ekleyin:

   ```csharp
   using System.Collections;
   using System.ComponentModel;
   using Microsoft.VisualStudio.Shell.Interop;
   ```

4. Şimdi sınıfına aşağıdaki alanları `MyToolWindow` ekleyin.

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

    özelliği, `TrackSelection` arabirim sağlayan bir hizmeti almak için `GetService` `STrackSelection` <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> kullanır. Olay `OnToolWindowCreated` işleyicisi ve yöntemi birlikte, yalnızca araç penceresi bölmesi nesnesinin kendisini `SelectList` içeren seçili nesnelerin bir listesini oluşturur. yöntemi, `UpdateSelection` Özellikler **penceresine** araç penceresi bölmesinin genel özelliklerini görüntülemelerini söyler.

6. Projeyi derleme ve hata ayıklamayı başlatma. Deneysel örnek Visual Studio görün gerekir.

7. Özellikler **penceresi görünmüyorsa** F4 tuşuna basarak **açın.**

8. **MyToolWindow penceresini** açın. Bunu Diğer **Görünüm'de**  >  **bulabilirsiniz Windows.**

    Pencere açılır ve pencere bölmesinin genel özellikleri Özellikler **penceresinde** görüntülenir.

9. Özellikler **penceresindeki Caption** **özelliğini Nesne Özelliklerim** **olarak değiştirin.**

     MyToolWindow penceresinin açıklamalı alt yazısı uygun şekilde değişir.

## <a name="expose-tool-window-properties"></a>Araç penceresi özelliklerini ortaya çıkarma

Bu bölümde, bir araç penceresi ekser ve özelliklerini gösterirsiniz. Özelliklerde yaptığınız değişiklikler Özellikler penceresine **yansıtıldı.**

### <a name="to-expose-tool-window-properties"></a>Araç penceresi özelliklerini açığa çıkarmak için

1. *MyToolWindow.cs'yi* açın ve genel boole özelliğini IsChecked sınıfına `MyToolWindow` ekleyin.

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

     Bu özellik, durumunu daha sonra oluşturacağız WPF onay kutusundan alır.

2. *MyToolWindowControl.xaml.cs'yi* açın ve MyToolWindowControl oluşturucus una aşağıdaki kodu girin.

    ```vb
    private MyToolWindow pane;
    public MyToolWindowControl(MyToolWindow pane)
    {
        InitializeComponent();
        this.pane = pane;
        checkBox.IsChecked = false;
    }
    ```

     Bu, `MyToolWindowControl` bölmeye erişim `MyToolWindow` sağlar.

3. *MyToolWindow.cs içinde* `MyToolWindow` oluşturucusu aşağıdaki gibi değiştirin:

    ```csharp
    base.Content = new MyToolWindowControl(this);
    ```

4. MyToolWindowControl'un tasarım görünümüne tıklayın.

5. Düğmeyi silin ve Araç Kutusundan sol **üst köşeye** bir onay kutusu ekleyin.

6. İşaretli ve İşaretsiz olaylarını ekleyin. Tasarım görünümünde onay kutusunu seçin. Özellikler **penceresinde** olay işleyicileri düğmesine tıklayın (Özellikler penceresinin sağ üst **kısmında).** **İşaretli'checkbox_Checked** yazın, ardından İşaretsiz'i  bulun ve **checkbox_Unchecked** yazın. 

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

8. Projeyi derleme ve hata ayıklamayı başlatma.

9. Deneysel örnekte **MyToolWindow penceresini** açın.

     Özellikler penceresinde pencerenin özelliklerini **bakın.** **IsChecked** özelliği pencerenin alt kısmında, Özelliklerim kategorisi **altında** görünür.

10. **MyToolWindow penceresindeki onay kutusunu** işaretleyin. **Özellikler penceresinde IsChecked** **true** olarak **değişir.** **MyToolWindow penceresindeki onay kutusunun işaretini** kaldırın. **Özellikler penceresinde IsChecked,** False olarak **değişir.**  Özellikler penceresinde **IsChecked** **değerini** değiştirin. **MyToolWindow penceresindeki onay** kutusu yeni değerle eş değer olarak değişir.

    > [!NOTE]
    > Özellikler penceresinde görüntülenen bir nesneyi atılması gerekirse, **önce** bir seçim `OnSelectChange` `null` kapsayıcısı ile çağrısı yapın. Özelliği veya nesneyi elden verdikten sonra güncelleştirilmiş ve listeli bir seçim kapsayıcısı olarak <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> değiştirebilirsiniz.

## <a name="change-selection-lists"></a>Seçim listelerini değiştirme

 Bu bölümde, temel bir özellik sınıfı için bir seçim listesi ekecek ve araç penceresi arabirimini kullanarak hangi seçim listesinin görüntüleyeceklerini seçeceksiniz.

### <a name="to-change-selection-lists"></a>Seçim listelerini değiştirmek için

1. *MyToolWindow.cs'yi* açın ve adlı bir genel sınıf `Simple` ekleyin.

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

2. Sınıfa bir özellik ve pencere bölmesi ile nesne `SimpleObject` arasında Özellikler penceresi seçimini değiştirmek için iki yöntem `MyToolWindow`  `Simple` ekleyin.

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

3. *MyToolWindowControl.cs içinde,* onay kutusu işleyicilerini şu kod satırlarıyla değiştirin:

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

4. Projeyi derleme ve hata ayıklamayı başlatma.

5. Deneysel örnekte **MyToolWindow penceresini** açın.

6. **MyToolWindow penceresinde onay kutusunu** seçin. Özellikler **penceresinde** `Simple` **SomeText** ve **ReadOnly nesne özellikleri görüntülenir.** Onay kutusunun işaretini kaldırın. Pencerenin genel özellikleri Özellikler **penceresinde** görünür.

    > [!NOTE]
    > **SomeText'in görünen adı My** **Text 'tir.**

## <a name="best-practice"></a>En iyi yöntem

Bu kılavuzda, seçilebilir nesne koleksiyonu ve seçilen nesne koleksiyonu aynı koleksiyon <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> olacak şekilde uygulanır. Özellik Tarayıcısı listesinde yalnızca seçili nesne görünür. Daha eksiksiz bir ISelectionContainer uygulaması için bkz. Reference.ToolWindow örnekleri.

Visual Studio pencereleri, oturumlar arasında Visual Studio olur. Araç penceresi durumunu kalıcı hale hakkında daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> .

## <a name="see-also"></a>Ayrıca bkz.

- [Özellikleri ve Özellik penceresini genişletme](../extensibility/extending-properties-and-the-property-window.md)
