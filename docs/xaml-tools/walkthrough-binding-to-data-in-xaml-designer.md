---
title: XAML Tasarımcısı’nda verilere bağlama
description: Çalışma panosu ve veri bağlama özelliklerini kullanarak XAMl Tasarımcısı'nda bir denetime veri bağlamayı Özellikler penceresi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.XamlDesigner.DataBinding
dev_langs:
- CSharp
- VB
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.openlocfilehash: 084f91e368c4addaebe53d768966459080f9d7a1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122037791"
---
# <a name="walkthrough-bind-to-data-in-xaml-designer"></a>İzlenecek yol: XAML Tasarımcısı’nda verilere bağlama

Bu XAML Tasarımcısı, çalışma panosu ve veri bağlama özelliklerini ayarlamak için çalışma Özellikler penceresi. Bu kılavuzda yer alan örnek, bir denetime veri bağlamayı gösterir. Özellikle izlenecek yol, [adlı DependencyProperty](xref:Windows.UI.Xaml.DependencyProperty) değerine sahip basit bir alışveriş sepeti sınıfı oluşturma ve ardından özelliğini TextBlock denetiminde `ItemCount` `ItemCount` **Text** özelliğine bağlama [adımlarını](xref:Windows.UI.Xaml.Controls.TextBlock) gösterir.

## <a name="to-create-a-class-to-use-as-a-data-source"></a>Veri kaynağı olarak kullanmak üzere bir sınıf oluşturmak için

1. Dosya menüsünde **Yeni** **dosya'Project.**  >  

1. Yeni **Project** iletişim kutusunda **Visual C#** **veya Visual Basic** düğümünü seçin, **Windows Masaüstü** düğümünü genişletin ve **ardından WPF Uygulaması şablonunu** seçin.

1. Projeye **BindingTest adını ve** ardından Tamam **düğmesini** seçin.

1. **MainWindow.xaml.cs** (veya **MainWindow.xaml.vb**) dosyasını açın ve aşağıdaki kodu ekleyin. C# içinde kodu ad alanına `BindingTest` ekleyin (dosyada son kapatma parantezi öncesinde). Bu Visual Basic yeni sınıfı eklemeniz gerekir.

   ```csharp
   public class ShoppingCart : DependencyObject
   {
       public int ItemCount
       {
           get { return (int)GetValue(ItemCountProperty); }
           set { SetValue(ItemCountProperty, value); }
       }

       public static readonly DependencyProperty ItemCountProperty =
            DependencyProperty.Register("ItemCount", typeof(int),
            typeof(ShoppingCart), new PropertyMetadata(0));
   }
   ```

   ```vb
   Public Class ShoppingCart
       Inherits DependencyObject

       Public Shared ReadOnly ItemCountProperty As DependencyProperty = DependencyProperty.Register(
            "ItemCount", GetType(Integer), GetType(ShoppingCart), New PropertyMetadata(0))
       Public Property ItemCount As Integer
           Get
               ItemCount = CType(GetValue(ItemCountProperty), Integer)
           End Get
           Set(value As Integer)
               SetValue(ItemCountProperty, value)
           End Set
       End Property
   End Class
   ```

   Bu kod, [PropertyMetadata](xref:Windows.UI.Xaml.PropertyMetadata) nesnesini kullanarak varsayılan öğe sayısı olarak 0 değerini ayarlar.

1. Dosya menüsünde **Derleme**   >  **Çözümü'ne tıklayın.**

## <a name="to-bind-the-itemcount-property-to-a-textblock-control"></a>ItemCount özelliğini textBlock denetimine bağlamak için

1. Bu Çözüm Gezgini **MainWindow.xaml** kısayol menüsünü açın ve öğesini **Görünüm Tasarımcısı.**

1. Araç Kutusunda bir Kılavuz [denetimi seçin](xref:Windows.UI.Xaml.Controls.Grid) ve forma ekleyin.

1. `Grid`seçiliyken, Özellikler penceresi **DataContext** **özelliğinin** yanındaki Yeni düğmesini seçin.

1. Nesne **Seç iletişim kutusunda Tüm**  derlemeleri göster onay kutusunun temiz olduğundan emin olun, BindingTest ad alanının altında **ShoppingCart'ı** seçin ve ardından **Tamam düğmesini** seçin. 

     Aşağıdaki çizimde **ShoppingCart** **öğesinin** seçili olduğu Nesne Seç iletişim kutusu gösterilmiştir.

     ![Nesne Seç iletişim kutusu](../designers/media/blendselectobject.png)

1. Araç **Kutusunda,** forma `TextBlock` eklemek için bir denetim seçin.

1. Denetim seçiliyken, Özellikler penceresi Text özelliğinin sağ tarafından özellik işaretçisini seçin ve ardından Veri `TextBlock` **BağlamaSı Oluştur'a seçin.**  (Özellik işaretçisi küçük bir kutuya benzer.)

1. Veri Bağlama Oluştur iletişim kutusundaki  Yol kutusunda **ItemCount : (int32)** özelliğini ve ardından Tamam **düğmesini** seçin.

     Aşağıdaki çizimde **ItemCount** **özelliğinin seçili** olduğu Veri BağlamaSı Oluştur iletişim kutusu gösterilmiştir.

     ![Veri Bağlama Oluştur iletişim kutusu](../designers/media/xaml_create_data_binding.png)

1. Uygulamayı **çalıştırmak için F5** tuşuna basın.

     Denetimde `TextBlock` varsayılan 0 değeri metin olarak göster gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [XAML Tasarımcısı’nı kullanarak bir kullanıcı arabirimi oluşturma](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
- [Değer Dönüştürücü ekle iletişim kutusu](/previous-versions/hh965588(v=vs.140))