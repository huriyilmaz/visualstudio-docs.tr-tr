---
title: Bir Windows formuna Diyagram ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa6cd040-7c88-4329-b9c3-2a80b312610f
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 487105350fe5c62a9451bccc5713c6506c76bf1f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669697"
---
# <a name="embedding-a-diagram-in-a-windows-form"></a>Windows Forms'a Diyagram Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

@No__t_0 penceresinde görünen bir Windows denetimine DSL diyagramı ekleyebilirsiniz.

## <a name="embedding-a-diagram"></a>Diyagram katıştırma

#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>Bir Windows denetimine DSL diyagramı eklemek için

1. DslPackage projesine yeni bir **Kullanıcı denetim** dosyası ekleyin.

2. Kullanıcı denetimine bir panel denetimi ekleyin. Bu panelde DSL diyagramı bulunur.

     İhtiyaç duyduğunuz diğer denetimleri ekleyin.

     Denetimlerin bağlayıcı özelliklerini ayarlayın.

3. Çözüm Gezgini, Kullanıcı denetim dosyasına sağ tıklayın ve **kodu görüntüle**' ye tıklayın. Bu oluşturucuyu ve değişkeni koda ekleyin:

    ```csharp

    internal UserControl1(MyDSLDocView docView, Control content)
      : this()
    {
      panel1.Controls.Add(content);
      this.docView = docView;
    }
    private MyDSLDSLDocView docView;

    ```

4. DslPackage projesine aşağıdaki içerikle yeni bir dosya ekleyin:

    ```
    using System.Windows.Forms;
    namespace Company.MyDSL
    {
      partial class MyDSLDocView
      {
        private UserControl1 container;
        public override IWin32Window Window
        {
          get
          {
            if (container == null)
            {
              // Put our own form inside the DSL window:
              container = new UserControl1(this,
                (Control)base.Window);
            }
            return container;
    } } } }

    ```

5. DSL 'yi test etmek için F5 tuşuna basın ve örnek bir model dosyası açın. Diyagram denetimin içinde görünür. Araç kutusu ve diğer özellikler normal şekilde çalışır.

#### <a name="updating-the-form-using-store-events"></a>Mağaza olaylarını kullanarak formu güncelleştirme

1. Form tasarımcısında `listBox1` adlı bir **ListBox** ekleyin. Bu, modeldeki öğelerin bir listesini görüntüler. *Mağaza olayları*kullanılarak modeliyle eşitlenmiş olarak tutulur. Daha fazla bilgi için bkz. [olay Işleyicileri değişiklikleri model dışında yayma](../modeling/event-handlers-propagate-changes-outside-the-model.md).

2. Özel kod dosyasında, DocView sınıfına yönelik diğer yöntemleri geçersiz kılın:

    ```

    partial class MyDSLDocView
    {
     /// <summary>
     /// Register store event listeners.
     /// This method is called when the model and diagram
     /// have completed loading.
     /// </summary>
     protected override bool LoadView()
      {
        bool result = base.LoadView();
        Store store = this.DocData.Store;
        EventManagerDirectory emd = store.EventManagerDirectory;
        DomainClassInfo componentClass = store.DomainDataDirectory.FindDomainClass(typeof(ExampleElement));
        emd.ElementAdded.Add(componentClass, new EventHandler<ElementAddedEventArgs>(AddElement));
        emd.ElementDeleted.Add(componentClass, new EventHandler<ElementDeletedEventArgs>(RemoveElement));

        // Do the initial parts list:
        container.SetUpFormFromModel();
        return result;
      }
     /// <summary>
     /// Listener method called on creation of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void AddElement(object sender, ElementAddedEventArgs e)
     {
       container.Add(e.ModelElement as ExampleElement);
     }
     /// <summary>
     /// Listener method called after deletion of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void RemoveElement(object sender, ElementDeletedEventArgs e)
     {
       container.Remove(e.ModelElement as ExampleElement);
     }

    ```

3. Kullanıcı denetiminin arkasındaki kodda eklenen ve kaldırılan öğeleri dinlemek için yöntemler ekleyin:

    ```

          public partial class UserControl1 : UserControl { ...

    private ExampleModel modelRoot;

    internal void Add(ExampleElement e) { UpdatePartsList(); }
    internal void Remove(ExampleElement e) { UpdatePartsList(); }

    internal void SetUpFormFromModel()
    {
      modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;
      UpdatePartsList();
    }

    private void UpdatePartsList()
    {
      StringBuilder builder = new StringBuilder();
      listBox1.Items.Clear();
      foreach (ExampleElement c in modelRoot.Elements)
      {
        listBox1.Items.Add(c.Name);
      }
    }

    ```

4. DSL 'yi test etmek için F5 tuşuna basın ve [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] deneysel örneğinde, örnek bir model dosyası açın.

     Liste kutusunda modeldeki öğelerin bir listesi gösterildiğine ve herhangi bir ekleme veya silme işleminden sonra, geri alma ve yineleme sonrasında doğru olduğundan emin olun.

## <a name="see-also"></a>Ayrıca Bkz.
 [Bir etki alanına özgü dili özelleştirmek Için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md) [Program kodundaki modeli gezinme ve güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)
