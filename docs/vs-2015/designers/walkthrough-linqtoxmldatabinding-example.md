---
title: 'İzlenecek yol: LinqToXmlDataBinding örneği | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: aedf42e8-896c-48fa-88df-7f7c9536aa69
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e97d612e19f64110f3090029dcff82acbad8e87
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663978"
---
# <a name="walkthrough-linqtoxmldatabinding-example"></a>İzlenecek Yol: LinqToXmlDataBinding Örneği
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, LinqToXmlDataBinding örneğini açıklar ve iki birincil kaynak dosyasının (L2DBForm. xaml ve L2DBForm.xaml.cs) daha ilginç içeriğini açıklar.

## <a name="prerequisites"></a>Ön koşullar
 Bu kılavuzu kullanmadan önce, LinqToXmlDataBinding programını oluşturup çalıştırmak [için, LinqToXmlDataBinding örneğini oluşturma ve çalıştırma konusunda](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)açıklandığı gibi kesinlikle tavsiye ederiz.

## <a name="remarks"></a>Açıklamalar
 LinqToXmlDataBinding programı C# ve XAML kaynak dosyalarından oluşan bir Windows Presentation Foundation (WPF) uygulamasıdır. Kitap listesini tanımlayan ve kullanıcının bu girdileri görüntülemesini, eklemesini, silmesini ve düzenlemesini sağlayan ekli bir XML belgesi içerir. Aşağıdaki iki birincil kaynak dosyadan oluşur:

- L2DBForm. xaml, ana pencerenin kullanıcı arabirimi (UI) için XAML bildirim kodunu içerir. Ayrıca, kitap listeleri için veri sağlayıcısını ve katıştırılmış XML belgesini tanımlayan bir pencere kaynağı bölümü içerir.

- L2DBForm.xaml.cs, Kullanıcı arabirimiyle ilişkili başlatma ve olay işleme yöntemlerini içerir.

  Ana pencere aşağıdaki dört dikey UI bölümüne bölünmüştür:

- **XML** katıştırılmış kitap LISTESININ ham XML kaynağını görüntüler.

- **Kitap listesi** , kitap girişlerini standart metin olarak görüntüler ve kullanıcının tek tek girdileri seçmesini ve silmesini sağlar.

- **Seçili kitabı Düzenle** , kullanıcının şu anda seçili olan kitap girişiyle ilişkili değerleri düzenlemesini sağlar.

- **Yeni kitap ekle** , Kullanıcı tarafından girilen değerlere göre yeni bir kitap girişi oluşturulmasına izin vermez.

## <a name="in-this-section"></a>Bu Bölümde

|Konu|Açıklama|
|-----------|-----------------|
|[L2DBForm. xaml kaynak kodu](../designers/l2dbform-xaml-source-code.md)|L2DBForm. xaml dosyasındaki XAML kodunun içeriğini ve açıklamasını içerir.|
|[L2DBForm.xaml.cs kaynak kodu](../designers/l2dbform-xaml-cs-source-code.md)|L2DBForm.xaml.cs dosyasındaki C# kaynak kodunun içeriğini ve açıklamasını içerir.|

## <a name="see-also"></a>Ayrıca Bkz.
 [LINQ to XML örnek kullanarak WPF veri bağlama](../designers/wpf-data-binding-using-linq-to-xml-example.md) [nasıl yapılır: LinqToXmlDataBinding örneğini oluşturma ve çalıştırma](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)
