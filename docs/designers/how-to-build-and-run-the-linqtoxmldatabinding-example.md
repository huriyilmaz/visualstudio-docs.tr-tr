---
title: 'Nasıl yapılır: LinqToXmlDataBinding örneğini derleme ve çalıştırma'
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3b3999ae6fb602c9877bc3f997ab922bda08565b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72636871"
---
# <a name="how-to-build-and-run-the-linqtoxmldatabinding-example"></a>Nasıl yapılır: LinqToXmlDataBinding örneğini derleme ve çalıştırma

Bu konu başlığı altında, LinqToXmlDataBinding Visual Studio projesinin nasıl oluşturulduğu ve oluşturulacağı ve elde edilen LinqToXmlDataBinding Windows Presentation Foundation (WPF) örnek programının nasıl çalıştırılacağı gösterilmektedir.

Visual Studio hakkında daha fazla bilgi için bkz. [Visual STUDIO IDE 'ye genel bakış](../get-started/visual-studio-ide.md).

## <a name="create-the-project"></a>Projeyi oluşturma

1. Visual Studio 'yu açın ve **LinqToXmlDataBinding**adlı bir C# **WPF uygulaması** oluşturun.

   Projenin .NET Framework 3,5 ' i (veya üzeri) hedeflemesi gerekir.

1. Henüz yoksa, aşağıdaki .NET derlemeleri için proje başvuruları ekleyin:

    - System.Data

    - System. Data. Datase, sions

    - System.Xml

    - System. xml. Linq

1. **Ctrl** +**SHIFT** +**B**tuşlarına basarak çözümü derleyin, sonra **F5**tuşuna basarak çalıştırın. Projenin hata olmadan derlenmesi ve genel bir WPF uygulaması olarak çalışması gerekir.

## <a name="add-code-to-the-project"></a>Projeye kod ekleme

1. **Çözüm Gezgini**, **Window1. xaml** kaynak dosyasını **L2XDBForm. xaml**olarak yeniden adlandırın. Bağımlı kaynak dosyasının **Window1.xaml.cs** otomatik olarak **L2XDBForm.xaml.cs**olarak yeniden adlandırılması gerekir.

1. **L2XDBForm. xaml** dosyasında bulunan kaynak kodunu [L2DBForm. xaml kaynak kodu](../designers/l2dbform-xaml-source-code.md)konusunun Code bölümü ile değiştirin. Bu dosyayla çalışmak için XAML kaynak görünümünü kullanın.

1. Benzer şekilde, **L2XDBForm.xaml.cs** içindeki kaynağı [L2DBForm.xaml.cs kaynak kodunda](../designers/l2dbform-xaml-cs-source-code.md)bulunan kodla değiştirin.

1. **App. xaml**dosyasında `Window1.xaml` dize tüm oluşumlarını `L2XDBForm.xaml` ile değiştirin.

1. **Ctrl** +**SHIFT** +**B**'ye basarak çözümü oluşturun.

## <a name="run-the-program"></a>Programı Çalıştır

LinqToXmlDataBinding programı, kullanıcının gömülü bir XML öğesi olarak depolanan bir kitap listesini görüntülemesini ve işlemesini sağlar.

### <a name="to-run-the-program-and-view-the-book-list"></a>Programı çalıştırmak ve kitap listesini görüntülemek için

**F5** tuşuna basarak LinqToXmlDataBinding komutunu çalıştırın (hata ayıklamayı**Başlat**) veya **CTRL** +**F5** (**hata ayıklama olmadan Başlat**). **LINQ to XML kullanarak WPF veri bağlama** başlıklı bir program penceresi görüntülenir.

- UI 'nın, kitap listesini temsil eden ham **XML** 'yi görüntüleyen üst bölümüne dikkat edin. Bir WPF <xref:System.Windows.Controls.TextBlock> denetimi kullanılarak görüntülenir ve bu, fare veya klavye aracılığıyla etkileşimi etkinleştirmez.

- **Kitap listesi**etiketli ikinci dikey bölüm, kitapları düz metin sıralı bir liste olarak görüntüler. Fareyle veya klavyeden seçimi sağlayan <xref:System.Windows.Controls.ListBox> denetimini kullanır.

### <a name="to-add-and-delete-books-from-the-list"></a>Listeden kitap ekleme ve silme

- Listeye yeni bir kitap eklemek için, son bölümdeki **denetim <xref:System.Windows.Controls.TextBox>,** **Yeni kitap ekle**' **ye ve ardından** **kitap ekle** düğmesine tıklayın. Kitabın hem kitap hem de XML listelerinde listeye ekleneceğini unutmayın. Bu program giriş değerlerini doğrulamaz.

- Listeden mevcut bir kitabı silmek için **kitap listesi** bölümünde seçin ve ardından **Seçili kitabı kaldır** düğmesine tıklayın. Book girişinin hem defterden hem de ham XML kaynak listelerinden kaldırıldığını görürsünüz.

### <a name="to-edit-an-existing-book-entry"></a>Mevcut bir kitap girişini düzenlemek için

1. İkinci **kitap listesi** bölümünde kitap girişini seçin. Geçerli değerleri üçüncü bölümde görüntülenmelidir, **Seçili kitabı düzenleyin**.

1. Klavyeyi kullanarak değerleri düzenleyin. @No__t_0 denetimi odağı kaybettiğinde, değişiklikler otomatik olarak XML kaynağına ve kitap listelerine yayılır.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML örnek kullanarak WPF veri bağlama](../designers/wpf-data-binding-using-linq-to-xml-example.md)
- [İzlenecek yol: LinqToXmlDataBinding örneği](../designers/walkthrough-linqtoxmldatabinding-example.md)
- [Visual Studio IDE 'ye Genel Bakış](../get-started/visual-studio-ide.md)