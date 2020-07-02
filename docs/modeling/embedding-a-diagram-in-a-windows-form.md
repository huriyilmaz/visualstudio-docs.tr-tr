---
title: Windows Forms'a Diyagram Ekleme
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e81a5ff10cd6e309ffbf17e40ffbaa9ec88f185
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547634"
---
# <a name="embed-a-diagram-in-a-windows-form"></a>Windows Formunda bir Diyagram ekleme

Bir DSL diyagramını, Visual Studio penceresinde görünen bir Windows denetimine ekleyebilirsiniz.

## <a name="embed-a-dsl-diagram-in-a-windows-control"></a>Windows denetimine DSL diyagramı ekleme

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
    private MyDSLDocView docView;
    ```

4. DslPackage projesine aşağıdaki içerikle yeni bir dosya ekleyin:

    ```csharp
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

5. DSL 'yi test etmek için **F5** tuşuna basın ve örnek bir model dosyası açın. Diyagram denetimin içinde görünür. Araç kutusu ve diğer özellikler normal şekilde çalışır.

## <a name="update-the-form-using-store-events"></a>Mağaza olaylarını kullanarak formu güncelleştirme

1. Form tasarımcısında adlı bir **ListBox** ekleyin `listBox1` . Bu, modeldeki öğelerin bir listesini görüntüler. *Mağaza olayları*kullanılarak modeliyle eşitlenir. Daha fazla bilgi için bkz. [olay Işleyicileri değişiklikleri model dışında yayma](../modeling/event-handlers-propagate-changes-outside-the-model.md).

2. Özel kod dosyasında, DocView sınıfına yönelik diğer yöntemleri geçersiz kılın:

    ```csharp
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

    ```csharp
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

4. DSL 'yi test etmek için **F5** tuşuna basın ve Visual Studio 'nun deneysel örneğinde örnek bir model dosyası açın.

     Liste kutusunda modeldeki öğelerin bir listesi gösterildiğine ve herhangi bir ekleme veya silme işleminden sonra, geri alma ve yineleme sonrasında doğru olduğundan emin olun.

## <a name="see-also"></a>Ayrıca bkz.

- [Program Kodunda Modeli Gezinme ve Güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Etki Alanına Özgü Dili Özelleştirmek için Kod Yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)
