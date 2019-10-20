---
title: 'İzlenecek yol: XAML Tasarımcısı veriye bağlama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner.DataBinding
ms.assetid: 1a99aeae-c3ef-407d-ba79-b8055489a43d
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 38434d89544ed290f9adfd077593d7de9bdc1231
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664011"
---
# <a name="walkthrough-binding-to-data-in-xaml-designer"></a>İzlenecek yol: XAML Tasarımcısı veriye bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XAML Tasarımcısı, çalışma yüzeyini ve Özellikler penceresi kullanarak veri bağlama özelliklerini ayarlayabilirsiniz. Bu yönergedeki örnek, verileri bir denetime bağlamayı gösterir. Özellikle, izlenecek yol, `ItemCount` adlı bir [DependencyProperty](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.dependencyproperty.aspx) 'ye sahip basit bir alışveriş sepeti sınıfının nasıl oluşturulacağını gösterir ve ardından `ItemCount` özelliğini bir [TextBlock](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) denetiminin **Text** özelliğine bağlar.

### <a name="to-create-a-class-to-use-as-a-data-source"></a>Veri kaynağı olarak kullanılacak bir sınıf oluşturmak için

1. **Dosya** menüsünde, **Yeni**, **Proje**' yi seçin.

2. **Yeni proje** iletişim kutusunda, **Visual C#**  veya **Visual Basic** düğümünü seçin, **Windows Masaüstü** düğümünü genişletin ve ardından **WPF uygulama** şablonunu seçin.

3. Projeyi **BindingTest**olarak adlandırın ve **Tamam** düğmesini seçin.

4. MainWindow.xaml.cs (veya MainWindow. xaml. vb) dosyasını açın ve aşağıdaki kodu ekleyin. İçinde C#, kodu `BindingTest` ad alanına ekleyin (dosyadaki son kapanış parantezinden önce). Visual Basic ' de, yeni sınıfı eklemeniz yeterlidir.

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

     Bu kod, [PropertyMetadata](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.propertymetadata.aspx) nesnesini kullanarak varsayılan öğe sayısı olarak 0 değerini ayarlar.

5. **Dosya** menüsünde **Oluştur**, **çözüm oluştur**' u seçin.

### <a name="to-bind-the-itemcount-property-to-a-textblock-control"></a>ItemCount özelliğini bir TextBlock denetimine bağlamak için

1. Çözüm Gezgini, MainWindow. xaml için kısayol menüsünü açın ve **Görünüm Tasarımcısı**' nı seçin.

2. Araç kutusunda bir [kılavuz](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) denetimi seçin ve forma ekleyin.

3. @No__t_0 seçili olan Özellikler penceresi, **DataContext** özelliğinin yanındaki **Yeni** düğmesini seçin.

4. **Nesne Seç** iletişim kutusunda, **tüm derlemeleri göster** onay kutusunun temizlenmiş olduğundan emin olun, **BindingTest** ad alanı altında **ShoppingCart** ' i seçin ve **Tamam** düğmesini seçin.

     Aşağıdaki çizimde, **ShoppingCart** seçiliyken **nesne Seç** iletişim kutusu gösterilmektedir.

     ![Nesne Seç iletişim kutusu](../designers/media/blendselectobject.PNG "BlendSelectObject")

5. **Araç kutusunda**, forma eklemek için bir `TextBlock` denetimi seçin.

6. @No__t_0 denetimi seçiliyken, Özellikler penceresi **metin** özelliğinin sağ tarafındaki özellik işaretçisini seçin ve sonra **veri bağlama oluştur**' u seçin. (Özellik işaretçisi küçük bir kutu gibi görünür.)

7. Veri bağlamayı oluştur iletişim kutusunda, **yol** kutusunda, **ItemCount: (Int32)** özelliğini seçin ve sonra **Tamam** düğmesini seçin.

     Aşağıdaki çizimde, **ItemCount** özelliği seçili olan **veri bağlamayı oluştur** iletişim kutusu gösterilmektedir.

     ![Veri bağlama oluştur iletişim kutusu](../designers/media/xaml-create-data-binding.png "xaml_create_data_binding")

8. Uygulamayı çalıştırmak için F5 tuşuna basın.

     @No__t_0 denetim, varsayılan değer olan 0 değerini metin olarak göstermelidir.

## <a name="see-also"></a>Ayrıca Bkz.
 XAML Tasarımcısı [nib: değer Dönüştürücüsü Ekle iletişim kutusunu](https://msdn.microsoft.com/c5f3d110-a541-4b55-8bca-928f77778af8) [kullanarak bir kullanıcı arabirimi oluşturma](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
