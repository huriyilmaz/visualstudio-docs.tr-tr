---
title: 'Nasıl yapılır: LinqToXmlDataBinding örneği oluşturma ve çalıştırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3943deaf-80e2-4968-ac04-d3ef56cfad6c
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5584494f65eaef72c2aa350af4e5af36155e0501
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664623"
---
# <a name="how-to-build-and-run-the-linqtoxmldatabinding-example"></a>Nasıl yapılır: LinqToXmlDataBinding örneğini derleme ve çalıştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu başlığı altında, LinqToXmlDataBinding Visual Studio projesinin nasıl oluşturulduğu ve oluşturulacağı ve elde edilen LinqToXmlDataBinding Windows Presentation Foundation (WPF) örnek programının nasıl çalıştırılacağı gösterilmektedir.

 Projeler oluşturmak için Visual Studio 'yu kullanma hakkında daha fazla bilgi için bkz. [Visual Studio 'Da uygulama geliştirme](https://msdn.microsoft.com/97490c1b-a247-41fb-8f2c-bc4c201eff68).

## <a name="creating-and-populating-the-project"></a>Projeyi oluşturma ve doldurma

#### <a name="to-create-the-starting-project"></a>Başlangıç projesini oluşturmak için

1. Visual Studio 'Yu başlatın ve LinqToXmlDataBinding adlı bir C# WPF uygulaması oluşturun. Projenin .NET Framework 3,5 (veya üzeri) kullanması gerekir.

2. Henüz yoksa, aşağıdaki .NET derlemeleri için proje başvuruları ekleyin:

    - System.Data

    - System. Data. Datase, sions

    - System.Xml

    - System.Xml. Sorgusunda

3. **Ctnrl + SHIFT + B**tuşlarına basarak çözümü oluşturun ve **F5**'e basarak çalıştırın. Projenin hata olmadan derlenmesi ve genel bir WPF uygulaması olarak çalışması gerekir.

#### <a name="to-add-custom-code-to-the-project"></a>Projeye özel kod eklemek için

1. Çözüm Gezgini, Window1. xaml kaynak dosyasını L2XDBForm. xaml olarak yeniden adlandırın. Bağımlı kaynak dosyasının Window1.xaml.cs otomatik olarak L2XDBForm.xaml.cs olarak yeniden adlandırılması gerekir.

2. L2XDBForm. xaml dosyasında bulunan kaynak kodunu [L2DBForm. xaml kaynak kodu](../designers/l2dbform-xaml-source-code.md)konusunun Code bölümü ile değiştirin. (Bu dosyayla çalışmak için XAML kaynak görünümünü kullanın.)

3. Benzer şekilde, L2XDBForm.xaml.cs içindeki kaynağı [L2DBForm.xaml.cs kaynak kodunda](../designers/l2dbform-xaml-cs-source-code.md)bulunan kodla değiştirin.

4. App. xaml dosyasında, "Window1. xaml" dizesinin tüm oluşumlarını "L2XDBForm. xaml" ile değiştirin.

5. **CTRL + SHIFT + B**tuşlarına basarak çözümü oluşturun.

## <a name="running-the-program"></a>Programı çalıştırma
 LinqToXmlDataBinding programı, kullanıcının gömülü bir XML öğesi olarak depolanan bir kitap listesini görüntülemesini ve işlemesini sağlar.

#### <a name="to-run-the-program-and-view-the-book-list"></a>Programı çalıştırmak ve kitap listesini görüntülemek için

1. **F5** tuşuna basarak LinqToXmlDataBinding komutunu çalıştırın (hata ayıklamayı**Başlat**) veya **CTRL + F5** (**hata ayıklama olmadan Başlat**). **LINQ to XML kullanarak WPF veri bağlama** başlıklı bir program penceresi görüntülenmelidir.

2. UI 'nın, kitap listesini temsil eden ham **XML** 'yi görüntüleyen üst bölümüne dikkat edin. Bir WPF denetimi kullanılarak görüntülenir <xref:System.Windows.Controls.TextBlock> ve bu, fare veya klavye aracılığıyla etkileşimi etkinleştirmez.

3. **Kitap listesi**etiketli ikinci dikey bölüm, kitapları düz metin sıralı bir liste olarak görüntüler. <xref:System.Windows.Controls.ListBox>Fare veya klavye olmasına rağmen seçimi sağlayan bir denetim kullanır.

#### <a name="to-add-and-delete-books-from-the-list"></a>Listeden kitap ekleme ve silme

1. Listeden mevcut bir kitabı silmek için **kitap listesi** bölümünde seçin ve ardından **Seçili kitabı kaldır** düğmesine tıklayın. Book girişinin hem defterden hem de ham XML kaynak listelerinden kaldırıldığını görürsünüz.

2. Listeye yeni bir kitap eklemek için son bölümdeki **kimlik** ve **değer** <xref:System.Windows.Controls.TextBox> denetimlerine değerler girin, **Yeni kitap ekleyin**ve ardından **kitap ekle** düğmesine tıklayın. Kitabın hem kitap hem de XML listelerinde listeye ekleneceğini unutmayın. Bu program giriş değerlerini doğrulamaz.

#### <a name="to-edit-an-existing-book-entry"></a>Mevcut bir kitap girişini düzenlemek için

1. İkinci **kitap listesi** bölümünde kitap girişini seçin. Geçerli değerleri üçüncü bölümde görüntülenmelidir, **Seçili kitabı düzenleyin**.

2. Klavyeyi kullanarak değerleri düzenleyin. Her iki denetim de <xref:System.Windows.Controls.TextBox> odağı kaybettiğinde, değişiklikler otomatik olarak XML kaynağına ve kitap listelerine yayılır.

## <a name="see-also"></a>Ayrıca Bkz.
 [LINQ to XML örnek kullanarak WPF veri bağlama](../designers/wpf-data-binding-using-linq-to-xml-example.md) [Izlenecek yol: LinqToXmlDataBinding örneği](../designers/walkthrough-linqtoxmldatabinding-example.md) [Visual Studio 'da uygulama geliştirme](https://msdn.microsoft.com/97490c1b-a247-41fb-8f2c-bc4c201eff68)
