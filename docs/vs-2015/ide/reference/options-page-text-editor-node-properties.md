---
title: Seçenekler sayfası, metin düzenleyici düğümü özellikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Text Editor node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 19438302-0677-4f4d-9720-5667e6a22ab2
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 62dddacaea1846c8e5d5da404ad7a16fde90f209
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662414"
---
# <a name="options-page-text-editor-node-properties"></a>Seçenekler Sayfası, Metin Düzenleyici Düğümü Özellikleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu belgede, **Seçenekler** iletişim kutusunun `DTE.Properties("TextEditor", <Property Page>)` **metin düzenleyici** kategorisiyle ilişkili bazı sayfalar (veya özellikler koleksiyonlar) açıklanmaktadır. Her alt bölümünün başlığı, `Properties` koleksiyonuna erişmek için kullanılan çağrıdır ve her alt tablodaki tablo koleksiyondaki özellikleri listeler.

 [Seçenek ayarları denetim](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) içindeki Visual Basic makroları, **Seçenekler** iletişim kutusunun her bir sayfası için geçerli seçeneklerin ve değerlerinin nasıl görüntüleneceğini gösterir.

## <a name="general"></a>Genel
 `DTE.Properties("TextEditor", "General")`

|Özellik Öğesi Adı|Değer|Açıklama|
|------------------------|-----------|-----------------|
|GoToAnchorAfterEscape|Get/Set (Boole)|@No__t_0, bir seçim olduğunda Escape tuşuna basmak, ekleme noktasının seçimi oluşturan eylemin başlatıldığı yere taşınmasına neden olur. `False` ekleme noktasını seçimin diğer sonuna taşımıyor.|
|DragNDropTextEditing|Get/Set (Boole)|Seçilen bir metin bölümünü, kopyala veya kes/yapıştır işlemleri için belge içinde bir yerden başka bir yere sürükleyip sürükleyemeyeceğinizi belirler.|
|HorizontalScrollBar|Get/Set (Boole)|Düzenleyici pencerelerinde yatay kaydırma çubuğu olup olmadığını belirler.|
|VerticalScrollBar|Get/Set (Boole)|Düzenleyici pencerelerinde dikey kaydırma çubuğu olup olmadığını belirler.|
|SelectionMargin|Get/Set (Boole)|Metin bölmesinin solunda özel seçim işlemleri, kesme noktası çizimleri vs. için boşluk olup olmadığını belirler.|
|MarginIndicatorBar|Get/Set (Boole)|Metin bölmesinin sol kenar boşluğunu metin bölmesinin ana gövdesinden ayıran bir dikey çizgi olup olmadığını belirler.|
|UndoCaretActions|Get/Set (Boole)|@No__t_0. arabelleği değiştiren eylemleri düzenlemenin yanı sıra ekleme noktası hareketini, seçim komutlarını ve benzeri işlemleri geri alın.|
|AutoDelimiterHighlighting|Get/Set (Boole)|Kapanış sınırlayıcısı girmenin, düzenleyicinin açılış sınırlayıcısını vurgulamasına neden olup olmayacağını belirler. Bu özelliğin değerinden bağımsız olarak, düzenleyici açık sınırlayıcıyı her zaman kalın yapar.|
|EditorEmulation|Get/Set (Enum)||
|DetectUTF8WithoutSignature|Get/Set (Boole)|Bir dosyanın kodlama imzası olmadığında, UTF-8 kodlaması kullanıp kullanmadığını belirler.|
|TrackChanges|Get/Set (Boole)||

## <a name="plain-text"></a>Düz Metin
 `DTE.Properties("TextEditor", "PlainText")`

 @No__t_0 Düzenleyicisi seçenekleri metin dosyaları düzenlendiğinde düzenleyici ayarlarını etkiler. Her programlama dili ve [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] paketinin kendine özgü **metin Düzenleyicisi** ayarları vardır. Örneğin, [!INCLUDE[csprcs](../../includes/csprcs-md.md)] Düzenleyicisi ayarlarını görüntülemek veya değiştirmek için `DTE.Properties("TextEditor", "CSharp") or DTE.Properties("TextEditor", "CSharp-Specific")` kullanın. **SQL betik** Düzenleyicisi ayarları için `DTE.Properties("TextEditor", "SQL ")` kullanın.

|Özellik Öğesi Adı|Değer|Açıklama|
|------------------------|-----------|-----------------|
|AutoListMembers|Get/Set (Boole)|Kullanıcı, bir değişken başvurusunun ardından nokta girdiğinde, kullanılabilir üye listesinin otomatik olarak görünüp görünmeyeceğini belirler.|
|AutoListParams|Get/Set (Boole)|Kullanıcılar bir işlev adının ardından "(" girdiğinde, bağımsız değişken listesi açıklamasının otomatik olarak görüntülenip görüntülenmeyeceğini belirler.|
|HideAdvancedMembers|Get/Set (Boole)|Deyim tamamlama özelliğinin tüm üyeleri mi, yoksa sadece sık kullanılanları mı listeleyeceğini belirler.|
|VirtualSpace|Get/Set (Boole)|Boşluk karakterlerinin grafik olarak görüntülenip görüntülenmeyeceğini belirler. Bunun `true` olarak ayarlanması `WordWrap` özellik öğesinin (Bu listede) `false` olarak ayarlanmasına neden olur.|
|WordWrap|Get/Set (Boole)|Görünümün, uzun satırları sözcük sınırlarından kaydırıp kaydırmayacağını belirler. Bunun `true` olarak ayarlanması `VirtualSpace` özellik öğesinin (Bu listede) `false` olarak ayarlanmasına neden olur.|
|WordWrapGlyphs|Get/Set (Boole)|Satırın sonunda bir karakter (glif) görüntüler; bu da satırın bir sonraki satıra kaydırılacağını gösterir.|
|EnableLeftClickForURLs|Get/Set (Boole)|Düzenleyicinin URL'lerin altını çizip çizmeyeceğini ve tek sol tıklamanın ilgili URL'yi sistemde kayıtlı Web tarayıcısında açmayı sağlayıp sağlamayacağını belirler.|
|IndentStyle|Al/ayarla (<xref:EnvDTE.vsIndentStyle>)|Girintilendirme stilini belirler: Varsayılan, Akıllı veya Yok.|
|TabSize|Get/Set (Long)|Bir sekmeye eşit olan boşluk sayısını temsil eder. 1 ile 60 (dahil) aralığının dışında bir tamsayı ayarı başarısız olur.|
|InsertTabs|Get/Set (Boole)|@No__t_0, girintileme sırasında sekme karakterleri kullanılır.|
|IndentSize|Get/Set (Long)|Tek bir girinti düzeyine eşit boşluk sayısını temsil eder. 1 ila 60 aralığı (sınırlar dahil) dışında bir tamsayı değeri ayarlanması hata verir.|
|ShowLineNumbers|Get/Set (Boole)|Çekirdek düzenleyici belge görünümünün, sol kenar boşluğu boyunca satır numaraları görüntüleyip görüntülemeyeceğini belirler.|
|ShowNavigationBar|Get/Set (Boole)|Düzenleyici pencerelerinin en üstünde açılan listeler ve düğmeler görünüp görünmeyeceğini belirler.|
|CutCopyBlankLines|Get/Set (Boole)|Seçildiklerinde, boş satırları keser veya kopyalar:|

## <a name="see-also"></a>Ayrıca Bkz.
 Seçenekler sayfa seçenekleri sayfasında [özellik öğelerinin adlarını belirleyen](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa) [seçenek ayarlarını denetleme](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) [sayfası, ortam düğümü özellikleri](../../ide/reference/options-page-environment-node-properties.md) [Seçenekler sayfası, yazı tipleri ve renkler düğüm özellikleri](../../ide/reference/options-page-fonts-and-colors-node-properties.md)
