---
title: Seçenekler, metin düzenleyici, C#, gelişmiş | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Advanced
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- outlining options [J#]
- XML documentation, creating
ms.assetid: 947f9d9a-b0f3-408d-9866-d82895bcee31
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4f2d11e78c2402a6541bc87748ed6ba348ba80fc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662326"
---
# <a name="options-text-editor-c-advanced"></a>Seçenekler, Metin Düzenleyici, C#, Gelişmiş
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu iletişim kutusunu, Visual C#için düzenleyici biçimlendirme, kod yeniden düzenleme ve XML belge açıklamaları ayarlarını değiştirmek için kullanın. Bu iletişim kutusuna erişmek için, **Araçlar** menüsünde **Seçenekler** ' e tıklayın, **metin düzenleyici** klasörünü genişletin, öğesini genişletin **C#** ve ardından **Gelişmiş**' e tıklayın.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="outlining"></a>Anahat Oluşturma
 Dosyalar seçildiğinde, anahat oluşturma moduna girer, bu, daraltılabilir kod blokları oluşturan kod dosyasını otomatik olarak özetler. Bir dosya ilk kez açıldığında, #regions blokları ve etkin olmayan kod blokları daraltılır.

## <a name="editor-help"></a>Düzenleyici yardımı
 Düzenleyicideki hataların altını çiz koddaki derleme hatalarını tanımlar. Bu seçenek belirlendiğinde, belirli anlamlara sahip renklerde dalgalı alt çizgiler görünür:

- Ayrıştırma hataları kırmızıdır.

- Derleme hataları mavidir.

- Derleme uyarıları yeşildir.

- Geçersiz [düzenleme ve devam etme](../../debugger/edit-and-continue.md) düzenlemeleri mor.

  Hata hakkında bilgi içeren bir araç Ipucu görmek için işaretçiyi altı çizili kod segmentinin üzerine taşıyın.

  Canlı semantik hataları göster açık derleme olmadan belirli derleme hatalarını tanımlar, örneğin, bilinmeyen bir tür bildirme ve kullanma ya da bilinmeyen bir özelliğe başvurma.

  İmleç bir simgenin içine konumlandırıldığında imlecin altında sembolün başvurularını vurgula veya bir simgeye tıkladığınızda, kod dosyasındaki söz konusu sembolün tüm örnekleri vurgulanır.

## <a name="refactoring"></a>Yeniden Düzenle
 Yeniden düzenleme sonuçlarının, derleme hataları içeren kodu yeniden düzenlemeye çalıştığınızda ya da yeniden düzenleme bir kod başvurusunun özgün bağlamalarından farklı bir şeye bağlanması durumunda **doğrulama sonuçları** Iletişim kutusunu görüntüler.

 Derleyici tarafından oluşturulan başvuruların bulunduğu üyelerde uyar, bir derleyicinin oluşturduğu başvuru ile aynı ada sahip bir üyeyi yeniden düzenleme çalıştığınızda bir uyarı iletişim kutusu görüntüler.

## <a name="xml-documentation-comments"></a>XML Belgeleri Yorumları
 İçin XML belge açıklamaları oluştur///seçili olduğunda,///açıklama giriş yazdıktan sonra otomatik olarak XML belge açıklamaları için \<summary > Başlangıç ve bitiş etiketlerini ekler. XML belgeleri hakkında daha fazla bilgi için bkz. [XML belge açıklamaları](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199).

## <a name="implement-interface"></a>Arabirimi Uygulama
 #Region ile birlikte üretilen kod, arabirim uygulama veya arabirimini açık olarak Uygula ya da açıkça arabirim uygulama ' ya bir #region \<*arabirim > adı*ekler.

## <a name="organize-usings"></a>Using deyimlerini Düzenle
 ' System ' yönergelerini, seçili olduğunda using yönergelerden önce, diğer using yönergelerinden önce gösterilen `System`. Daha fazla bilgi için bkz. [using deyimlerini sıralama](../../misc/sort-usings.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [XML belge açıklamaları](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199) [dile özgü düzenleyici seçeneklerini ayarlama](../../ide/reference/setting-language-specific-editor-options.md) [Visual C# IntelliSense](../../ide/visual-csharp-intellisense.md)
