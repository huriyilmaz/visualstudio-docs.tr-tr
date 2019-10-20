---
title: Seçenekler, metin düzenleyici, tüm diller, sekmeler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.ResJSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs
helpviewer_keywords:
- indents, Code Editor
- Code Editor, default behavior
- tabs, setting in Code Editor
- All Languages Text Editor Options dialog box
- editors, Code Editor
- Code Editor, indenting
- Code Editor, tabs
ms.assetid: 7e208e1d-5e3a-4bf7-a27b-4417e3e049c7
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4cb670ab52e321f15c5b009c66ca40623409f10a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662391"
---
# <a name="options-text-editor-all-languages-tabs"></a>Seçenekler, Metin Düzenleyici, Tüm Diller, Sekmeler
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu iletişim kutusu, kod düzenleyicisinin varsayılan davranışını değiştirmenize izin verir. Bu ayarlar ayrıca, HTML tasarımcısının kaynak görünümü gibi kod düzenleyicisine dayalı diğer düzenleyiciler için de geçerlidir. Bu seçenekleri göstermek için, **Araçlar** menüsünden **Seçenekler** ' i seçin. **Metin Düzenleyicisi** klasörü Içinde **tüm diller** alt klasörünü genişletin ve ardından **Sekmeler**' i seçin.

> [!CAUTION]
> Bu sayfa tüm geliştirme dillerinin varsayılan seçeneklerini ayarlar. Bu iletişim kutusunda bir seçeneğin sıfırlanması, burada seçili olan seçimler için tüm dillerdeki sekmeler seçeneklerini sıfırlayacaktır. Yalnızca bir dile ait metin düzenleyici seçeneklerini değiştirmek için, bu dilin alt klasörünü genişletin ve seçenek sayfalarını seçin.

 Belirli programlama dilleri için sekmeler seçenekler sayfalarında farklı ayarlar seçilirse, "tekil metin biçimleri için girinti ayarları birbirleriyle çakışıyor" iletisi, farklı **girintileme** seçenekleri için görüntülenir; ve "tekil metin biçimleri için sekme ayarları birbirleriyle çakışıyor" iletisi, farklı **sekme** seçenekleri için görüntülenir. Örneğin, **akıllı girintileme** seçeneği Visual Basic için seçilmişse bu anımsatıcı görüntülenir, ancak görsel C++için **blok girintileme** seçilidir.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="indenting"></a>Girintileme
 Seçildiğinde, yeni satırlar girintilenmez. Ekleme noktası yeni bir satırın ilk sütununa yerleştirilir.

 Seçili olduğunda engelle, yeni satırlar otomatik olarak girintilenir. Ekleme noktası, önceki satır ile aynı başlangıç noktasına yerleştirilir.

 Akıllı seçildiğinde, yeni satırlar, geliştirme diliniz için diğer kod biçimlendirme ayarları ve IntelliSense kuralları için kod bağlamına sığacak şekilde konumlandırılır. Bu seçenek tüm geliştirme dilleri için kullanılamaz.

 Örneğin, bir açma küme ayracı ({) ve bir kapanış ayracı (}) arasına alınmış satırlar otomatik olarak hizalı küme ayraçlarının konumundan fazladan bir sekme durağı girintili olabilir.

## <a name="tabs"></a>Sekmeler
 Sekme boyutu, sekme duraklarının boşluk cinsinden uzaklığını ayarlar. Varsayılan değer dört boşluklardan oluşamaz.

 Girinti boyutu, bir otomatik girintileme için boşluk cinsinden boyutu ayarlar. Varsayılan değer dört boşluklardan oluşamaz. Belirtilen boyutu dolduracak şekilde sekme karakterleri, boşluk karakterleri veya her ikisi de eklenir.

 Seçili olduğunda boşluk Ekle, girinti işlemleri sekme karakterleri değil yalnızca boşluk karakterleri ekler. Örneğin, **girinti boyutu** 5 olarak AYARLANDıYSA, sekme tuşuna veya **biçimlendirme** araç çubuğundaki **Girintiyi Artır** düğmesine her bastığınızda beş boşluk karakteri eklenir.

 Sekmeleri seçili olduğunda tut, Girintile işlemleri mümkün olduğunca çok sekme karakteri ekler. Her sekme karakteri, **sekme boyutunda**belirtilen boşluk sayısını doldurur. **Girinti boyutu** **sekme boyutunun**Çift katı değilse, farkı dolduracak şekilde boşluk karakterleri eklenir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Seçenekler, metin düzenleyici, tüm diller](../../ide/reference/options-text-editor-all-languages.md) [Genel, ortam, Seçenekler iletişim kutusu](../../ide/reference/general-environment-options-dialog-box.md)
