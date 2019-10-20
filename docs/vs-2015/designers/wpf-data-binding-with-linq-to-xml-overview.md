---
title: LINQ to XML genel bakış ile WPF veri bağlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3bf80845-891b-41de-a71b-4080b5bd3ea6
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 09c0c26a75d6881f06e67fa84f30ac7279bddf33
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663900"
---
# <a name="wpf-data-binding-with-linq-to-xml-overview"></a>LINQ to XML ile WPF Verilerini Bağlamaya Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, <xref:System.Xml.Linq> ad alanındaki dinamik veri bağlama özelliklerini tanıtır. Bu özellikler, Windows Presentation Foundation (WPF) içindeki kullanıcı arabirimi (UI) öğeleri için bir veri kaynağı olarak kullanılabilir.

## <a name="xaml-and-linq-to-xml"></a>XAML ve LINQ to XML
 Extensible Application Markup Language (XAML), Microsoft tarafından .NET Framework 3,0 teknolojilerini desteklemek için oluşturulan bir XML diyalekti. Kullanıcı arabirimi öğelerini ve olaylar ve veri bağlama gibi ilgili özellikleri temsil etmek için WPF 'de kullanılır. Windows Workflow Foundation, XAML program denetimi (*iş akışları*) gibi program yapısını temsil etmek için kullanılır. XAML, bir teknolojinin bildirim temelli yönlerinin bir programın daha kişiselleştirilmiş davranışını tanımlayan ilgili yordamsal koddan ayrılmasını sağlar.

 XAML ve LINQ to XML etkileşime girebileceği iki geniş yol vardır:

- XAML dosyaları iyi biçimlendirilmiş XML olduğundan, LINQ to XML gibi XML teknolojileri aracılığıyla sorgulanabilir ve işlenebilir.

- LINQ to XML sorguları bir veri kaynağını temsil ettiğinden, bu sorgular WPF Kullanıcı arabirimi öğeleri için veri bağlama için bir veri kaynağı olarak kullanılabilir.

  Bu belgede İkinci senaryo açıklanmaktadır.

## <a name="data-binding-in-the-windows-presentation-foundation"></a>Windows Presentation Foundation veri bağlama
 WPF veri bağlama, bir kullanıcı arabirimi öğesinin özelliklerinden birini bir veri kaynağıyla ilişkilendirebilmesine olanak sağlar. Bunun basit bir örneği, metni Kullanıcı tanımlı bir nesne içinde ortak özelliğin değerini temsil eden bir <xref:System.Windows.Controls.Label>. WPF veri bağlama, aşağıdaki bileşenlere bağımlıdır:

|Bileşen|Açıklama|
|---------------|-----------------|
|Bağlama hedefi|Veri kaynağıyla ilişkilendirilecek Kullanıcı arabirimi öğesi. WPF 'deki görsel öğeler <xref:System.Windows.UIElement> sınıfından türetilir.|
|Target özelliği|Veri bağlama kaynağının değerini yansıtan bağlama hedefinin *bağımlılık özelliği* . Bağımlılık özellikleri, <xref:System.Windows.UIElement> türetilen <xref:System.Windows.DependencyObject> sınıfı tarafından doğrudan desteklenir.|
|Bağlama kaynağı|Sunum için Kullanıcı arabirimi öğesine sağlanan bir veya daha fazla değer için kaynak nesne. WPF, bağlama kaynakları olarak şu türleri otomatik olarak destekler: CLR nesneleri, ADO.NET veri nesneleri, XML verileri (XPath veya LINQ to XML sorgularından) veya başka bir <xref:System.Windows.DependencyObject>.|
|Kaynak yolu|Bağlanacak olan bağlama kaynağının özelliği veya bağlanacak değer kümesi.|

 Bağımlılık özelliği, bir UI öğesinin dinamik olarak hesaplanan özelliğini temsil eden WPF 'e özgü bir kavramdır. Örneğin, bağımlılık özellikleri genellikle bir üst öğe tarafından belirtilen varsayılan değerlere veya değerlere sahiptir. Bu özel özellikler, <xref:System.Windows.DependencyProperty> sınıfının örnekleri tarafından desteklenir (standart özelliklerle birlikte alanlar değildir). Daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](https://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5).

### <a name="dynamic-data-binding-in-wpf"></a>WPF 'de dinamik veri bağlama
 Varsayılan olarak, veri bağlama yalnızca hedef UI öğesi başlatıldığında gerçekleşir. Bu, *tek seferlik* bağlama olarak adlandırılır. Çoğu amaçla bu yeterli değildir; Genellikle, bir veri bağlama çözümü, aşağıdakilerden biri kullanılarak değişikliklerin çalışma zamanında dinamik olarak yayılmasını gerektirir:

- *Tek yönlü* bağlama, değişikliklerin bir yandan otomatik olarak yayılmasına neden olur. En yaygın olarak, kaynakta yapılan değişiklikler hedefte yansıtılır, ancak ters işlem bazen yararlı olabilir.

- *İki yönlü* bağlamada, kaynakta yapılan değişiklikler otomatik olarak hedefe yayılır ve hedefteki değişiklikler otomatik olarak kaynağa dağıtılır.

  Tek yönlü veya iki yönlü bağlamanın gerçekleşmesi için, kaynağın <xref:System.ComponentModel.INotifyPropertyChanged> arabirimini uygulayarak veya desteklenen her özellik için bir *PropertyNameChanged* modelini kullanarak bir değişiklik bildirim mekanizması uygulaması gerekir.

  WPF 'de veri bağlama hakkında daha fazla bilgi için bkz. [veri bağlama (WPF)](https://msdn.microsoft.com/library/90f79b97-17e7-40d1-abf0-3ba600ad1d7e).

## <a name="dynamic-properties-in-linq-to-xml-classes"></a>LINQ to XML sınıflarında dinamik özellikler
 Çoğu LINQ to XML sınıf uygun WPF dinamik veri kaynakları olarak nitelendirmez: en yararlı bilgilerden bazıları yalnızca yöntemler aracılığıyla (ve özellikleri değil) kullanılabilir ve bu sınıflardaki Özellikler değişiklik bildirimlerini uygulamaz. WPF veri bağlamayı desteklemek için LINQ to XML, bir dizi *dinamik özellik*kullanıma sunar.

 Bu dinamik özellikler, <xref:System.Xml.Linq.XAttribute> ve <xref:System.Xml.Linq.XElement> sınıflarında mevcut yöntemlerin ve özelliklerin işlevselliğini yineleyen özel çalışma zamanı özellikleridir. Bunlar bu sınıflara yalnızca WPF için dinamik veri kaynakları görevi görmesini sağlamak için eklenmiştir. Bu gereksinimi karşılamak için, tüm bu dinamik özellikler değişiklik bildirimlerini uygular. Bu dinamik özelliklere yönelik ayrıntılı bir başvuru, bir sonraki bölümde verilmiştir [LINQ to XML dinamik özellikler](../designers/linq-to-xml-dynamic-properties.md).

> [!NOTE]
> @No__t_0 ad alanındaki çeşitli sınıflarda bulunan standart ortak özelliklerin birçoğu, tek seferlik veri bağlama için kullanılabilir. Ancak, ne kaynak ne de hedefin bu şema altında dinamik olarak güncelleştirileceğini unutmayın.

### <a name="accessing-dynamic-properties"></a>Dinamik özelliklere erişme
 @No__t_0 ve <xref:System.Xml.Linq.XElement> sınıflarında dinamik özelliklere standart özellikler gibi erişilemez. Örneğin, gibi CLR uyumlu dillerde C#şu olamaz:

- Doğrudan derleme zamanında erişilir. Dinamik özellikler derleyiciye ve Visual Studio IntelliSense 'e görünmez.

- .NET Reflection kullanılarak çalışma zamanında keşfedildi veya erişilir. Çalışma zamanında bile, temel CLR Sense içinde Özellikler değildir.

  ' C#De, dinamik özelliklere yalnızca <xref:System.ComponentModel> ad alanı tarafından sunulan tesislerde çalışma zamanında erişilebilir.

  Buna karşılık, bir XML kaynak dinamik özelliklerine aşağıdaki biçimde doğrudan bir gösterim aracılığıyla erişilebilir:

```
<object>.<dynamic-property>
```

 Bu iki sınıf için dinamik özellikler, doğrudan kullanılabilecek bir değere çözümlenmez ya da sonuç değerini ya da değerleri toplamayı elde etmek için bir dizinle birlikte sağlanması gereken bir dizin oluşturucudur. İkinci sözdizimi şu biçimdedir:

```
<object>.<dynamic-property>[<index-value>]
```

 Daha fazla bilgi için bkz. [dinamik özellikler LINQ to XML](../designers/linq-to-xml-dynamic-properties.md).

 WPF dinamik bağlamayı uygulamak için dinamik özellikler, <xref:System.Windows.Data> ad alanı tarafından sunulan tesislerle birlikte kullanılır, bu da özellikle <xref:System.Windows.Data.Binding> sınıfıdır.

## <a name="see-also"></a>Ayrıca Bkz.
 [Iş akışı işaretlemesini kullanarak](http://go.microsoft.com/fwlink/?LinkId=98685) WPF veri [bağlama (wpf)](https://msdn.microsoft.com/library/90f79b97-17e7-40d1-abf0-3ba600ad1d7e) LINQ to XML [LINQ to XML dinamik özellikler](../designers/linq-to-xml-dynamic-properties.md) [xaml](https://msdn.microsoft.com/library/5d858575-a83b-42df-ad3f-047ed2d6e3c8) [ile WPF veri bağlama](../designers/wpf-data-binding-with-linq-to-xml.md)
