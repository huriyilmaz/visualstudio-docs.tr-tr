---
title: Windows Forms'a Diyagram Ekleme
description: Visual Studio penceresinde görünen bir Windows DSL diyagramını nasıl Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 63a58dba9c6698b46786c665df0262c580b9048c3675a3715787459005405999
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121271387"
---
# <a name="embed-a-diagram-in-a-windows-form"></a>Windows Formunda bir Diyagram ekleme

DSL diyagramını, Windows penceresinde görünen bir Visual Studio ebilirsiniz.

## <a name="embed-a-dsl-diagram-in-a-windows-control"></a>Dsl diyagramını bir Windows ekleme

1. DslPackage **projesine** yeni bir Kullanıcı Denetimi dosyası ekleyin.

2. Kullanıcı Denetimi'ne bir Panel denetimi ekleyin. Bu panel DSL Diyagramını içerir.

     Gereken diğer denetimleri ekleyin.

     Denetimlerin Yer noktası özelliklerini ayarlayın.

3. Bu Çözüm Gezgini, kullanıcı denetim dosyasına sağ tıklayın ve Kodu **Görüntüle'ye tıklayın.** Koda şu oluşturucu ve değişkeni ekleyin:

    ```csharp
    internal UserControl1(MyDSLDocView docView, Control content)
      : this()
    {
      panel1.Controls.Add(content);
      this.docView = docView;
    }
    private MyDSLDocView docView;
    ```

4. DslPackage projesine aşağıdaki içeriğe sahip yeni bir dosya ekleyin:

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

5. DSL'yi test etmek için **F5 tuşuna** basın ve bir örnek model dosyası açın. Diyagram denetimin içinde görünür. Araç kutusu ve diğer özellikler normal şekilde çalışır.

## <a name="update-the-form-using-store-events"></a>Mağaza olaylarını kullanarak formu güncelleştirme

1. Form tasarımcısında adlı bir **ListBox** `listBox1` ekleyin. Bu, modelde öğelerin listesini görüntüler. Mağaza olayları kullanılarak modelle *eşitlenir.* Daha fazla bilgi için [bkz. Olay İşleyicileri Değişiklikleri Modelin Dışına Yayma.](../modeling/event-handlers-propagate-changes-outside-the-model.md)

2. Özel kod dosyasında DocView sınıfına diğer yöntemleri geçersiz kılın:

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

3. Kullanıcı denetimi arkasındaki kodda, eklenen ve kaldırılan öğeleri dinlemek için yöntemler girin:

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

4. DSL'yi test etmek için **F5 tuşuna** basın ve Visual Studio örnek model dosyasını açın.

     Liste kutusunda modelde yer alan öğelerin listesinin yanı sıra ekleme veya silme işlemlerinin yanı sıra Geri Al ve Yinele'den sonra bunun doğru olduğunu fark edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Program Kodunda Modeli Gezinme ve Güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Etki Alanına Özgü Dili Özelleştirmek için Kod Yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)
