---
title: XAML Tasarımcısı’nda verilere bağlama
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.XamlDesigner.DataBinding
dev_langs:
- CSharp
- VB
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 9cc5348004f344bd62e66aa03a20b0dd61017692
ms.sourcegitcommit: d97d72308ef306e7f28c3a76913caee4ff450bbb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90713431"
---
# <a name="walkthrough-bind-to-data-in-xaml-designer"></a>İzlenecek yol: XAML Tasarımcısı’nda verilere bağlama

XAML Tasarımcısı, çalışma yüzeyini ve Özellikler penceresi kullanarak veri bağlama özelliklerini ayarlayabilirsiniz. Bu yönergedeki örnek, verileri bir denetime bağlamayı gösterir. Özellikle, izlenecek yol, adlı bir [DependencyProperty](xref:Windows.UI.Xaml.DependencyProperty) 'yi içeren basit bir alışveriş sepeti sınıfının nasıl oluşturulacağını gösterir `ItemCount` ve sonra `ItemCount` özelliği bir [TextBlock](xref:Windows.UI.Xaml.Controls.TextBlock) denetiminin **Text** özelliğine bağlar.

## <a name="to-create-a-class-to-use-as-a-data-source"></a>Veri kaynağı olarak kullanılacak bir sınıf oluşturmak için

1. **Dosya** menüsünde **Yeni**  >  **Proje**' yi seçin.

1. **Yeni proje** iletişim kutusunda, **Visual C#** veya **Visual Basic** düğümünü seçin, **Windows Masaüstü** düğümünü genişletin ve ardından **WPF uygulama** şablonunu seçin.

1. Projeyi **BindingTest**olarak adlandırın ve **Tamam** düğmesini seçin.

1. **MainWindow.xaml.cs** (veya **MainWindow. xaml. vb**) dosyasını açın ve aşağıdaki kodu ekleyin. C# dilinde, kodu `BindingTest` ad alanına ekleyin (dosyadaki son kapanış parantezinden önce). Visual Basic ' de, yeni sınıfı eklemeniz yeterlidir.

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

1. **Dosya** **menüsünde Build**  >  **Build Solution**öğesini seçin.

## <a name="to-bind-the-itemcount-property-to-a-textblock-control"></a>ItemCount özelliğini bir TextBlock denetimine bağlamak için

1. Çözüm Gezgini, **MainWindow. xaml** için kısayol menüsünü açın ve **Görünüm Tasarımcısı**' nı seçin.

1. Araç kutusunda bir [kılavuz](xref:Windows.UI.Xaml.Controls.Grid) denetimi seçin ve forma ekleyin.

1. Seçili olan `Grid` Özellikler penceresi, **DataContext** özelliğinin yanındaki **Yeni** düğmesini seçin.

1. **Nesne Seç** iletişim kutusunda, **tüm derlemeleri göster** onay kutusunun temizlenmiş olduğundan emin olun, **BindingTest** ad alanı altında **ShoppingCart** ' i seçin ve **Tamam** düğmesini seçin.

     Aşağıdaki çizimde, **ShoppingCart** seçiliyken **nesne Seç** iletişim kutusu gösterilmektedir.

     ![Nesne Seç iletişim kutusu](../designers/media/blendselectobject.png)

1. **Araç kutusunda**, `TextBlock` forma eklemek için bir denetim seçin.

1. `TextBlock`Denetim seçiliyken, Özellikler penceresi **metin** özelliğinin sağ tarafındaki özellik işaretini seçin ve sonra **veri bağlama oluştur**' u seçin. (Özellik işaretçisi küçük bir kutu gibi görünür.)

1. Veri bağlamayı oluştur iletişim kutusunda, **yol** kutusunda, **ItemCount: (Int32)** özelliğini seçin ve sonra **Tamam** düğmesini seçin.

     Aşağıdaki çizimde, **ItemCount** özelliği seçili olan **veri bağlamayı oluştur** iletişim kutusu gösterilmektedir.

     ![Veri bağlama oluştur iletişim kutusu](../designers/media/xaml_create_data_binding.png)

1. Uygulamayı çalıştırmak için **F5** tuşuna basın.

     `TextBlock`Denetim, varsayılan değer olan 0 değerini metin olarak göstermelidir.

## <a name="see-also"></a>Ayrıca bkz.

- [XAML Tasarımcısı’nı kullanarak bir kullanıcı arabirimi oluşturma](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
- [Değer Dönüştürücüsü Ekle iletişim kutusu](/previous-versions/hh965588(v=vs.140))