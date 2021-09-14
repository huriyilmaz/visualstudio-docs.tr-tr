---
title: Seçenekler, Metin Düzenleyici, Temel (VB), Gelişmiş
description: Analiz, İçeri Aktarma Yönergeleri ve Vurgulama özelliklerinin varsayılan ayarlarını değiştirmek için Temel bölümündeki Gelişmiş sayfasını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/12/2020
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Visual_Basic.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.Editor
- VS.ToolsOptionsPages.Visual_Basic_Editor.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage
- VS.ToolsOptionsPages.Text_Editor.Basic
- VS.ToolsOptionsPages.Text_Editor.Basic.Advanced
- VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific
helpviewer_keywords:
- Basic Text Editor Options dialog box
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
author: akhera99
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: abe1a46305ad656dca843fbb217f34eacca86410
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627188"
---
# <a name="options-text-editor-basic-visual-basic-advanced"></a>Seçenekler, Metin Düzenleyici, Temel (Visual Basic), Gelişmiş
Seçenekler **(** Araçlar menüsü) iletişim **kutusunun** **Metin** Düzenleyicisi klasörünün Temel **klasöründeki VB Özel** özellik sayfası aşağıdaki özellikleri içerir:

## <a name="analysis"></a>Analiz

- Canlı kod analizi veya Arka plan analizi kapsamı

   Yönetilen kod için arka plan analizi kapsamını yapılandırma. Daha fazla bilgi için [bkz. Nasıl yapılandırılır: Yönetilen kod için canlı kod analizi kapsamını yapılandırma.](../../code-quality/configure-live-code-analysis-scope-managed-code.md)

## <a name="using-directives"></a>Yönergeleri Kullanma

- Usings sıralamada 'System' yönergelerini ilk önce yer

   Seçildiğinde, sağ **tıklama menüsündeki** KullanarakLarı Kaldır ve Sırala komutu yönergeleri sıralar ve 'Sistem' ad alanlarını `using` listenin en üstüne yer.

- Kullanma yönerge gruplarını ayırma

   Seçildiğinde, **sağ** tıklama menüsündeki Kullanmaları Kaldır ve Sırala komutu, aynı kök ad alanına sahip yönerge grupları arasına boş bir satır ekerek yönergeleri birbirinden `using` ayırıyor.

- Başvuru derlemelerinde türler için kullanma önerin
- NuGet paketlerinde türler için kullanma önerin

   Bu seçenekler seçildiğinde, NuGet paketini [yüklemek](../quick-actions.md) ve bağlantı kurulmaz türler için bir yönerge eklemek `using` için bir Hızlı Eylem kullanılabilir.

   ![NuGet paketini Visual Studio'a yüklemek için hızlı Visual Studio](media/nuget-lightbulb.png)

## <a name="highlighting"></a>Vurgulama

 **Başvuruların ve anahtar sözcüklerin vurgularını etkinleştirme**

Metin düzenleyicisi, bir sembolün tüm örneklerini veya , veya gibi bir yan tümcede yer alan tüm `If..Then` anahtar sözcükleri `While...End While` `Try...Catch...Finally` vurgular. **Ctrl** Shift Aşağı ok veya Ctrl Shift Yukarı ok tuşlarına basarak vurgulanan başvurular veya anahtar sözcükler  +    +     +    +  **arasında gezinebilirsiniz.**

## <a name="outlining"></a>Anahat Oluşturma

**Outlining modunu etkinleştirme**

Kod düzenleyicisinde bir dosya açtıklarında, belgeyi genel açıklama modunda görüntüebilirsiniz. Daha [fazla bilgi için bkz. Outlining](../../ide/outlining.md) . Bu seçenek seçildiğinde, bir dosyayı açsanız, outlining özelliği etkinleştirilir.

**Yordam çizgisi ayırıcılarını gösterme**

Metin düzenleyicisi, yordamların görsel kapsamını gösterir. Aşağıdaki tabloda listelenen konumlarda *projenizin .vb* kaynak dosyalarında bir satır çizilir:

|.vb Kaynak DosyasındaKi Konum|Satır Konumu Örneği|
|---------------------------------|------------------------------|
|Blok bildirimi yapısı kapat sonrasında|- Bir sınıfın, yapının, modülün, arabirimin veya enum'un sonunda<br />- Bir özellik, işlev veya alt işlevden sonra<br />- Bir özellikte get ve set yan tümceleri arasında değil|
|Tek satırlı yapılardan sonra|- İçeri aktarma deyimlerini, bir sınıf dosyasındaki tür tanımından önce<br />- Herhangi bir yordamdan önce, bir sınıfta bildirilen değişkenler sonra|
|Tek satırlı bildirimlerin ardından (blok düzeyinde olmayan bildirim)|- İçeri aktarma deyimlerini takip ediyor, deyimlerini, değişken bildirimlerini, olay bildirimlerini, temsilci bildirimlerini ve DLL bildirim deyimlerini devralıyor|

## <a name="block-structure-guides"></a>Blok Yapısı Kılavuzları

Seçildiğinde düzenleyicide dikey çizgiler, tek tek kod bloklarını kolayca tanımlamanıza olanak sağlayan yapılandırılmış kod blokları ile birlikte görünür. Örneğin, bir deyiminde ile arasında `Sub` bir `EndSub` çizgi `Sub` görüyoruz.

## <a name="editor-help"></a>Düzenleyici Yardımı

::: moniker range=">=vs-2019"
**Satır Içi Parametre Adı İpuçları**    
Seçildiğinde, işlev çağrılarında her bağımsız değişkenden önce sabit değerlerin, türün atfedilen sabit değerlerin ve nesne örnek oluşturmaların parametre adı ipuçlarını ekler.  

![Visual Basic için Satır Içi Parametre Adı İpuçları](media/inline-parameter-name-hints-visualbasic.png)
::: moniker-end

**Kodun Güzel Listesi (yeniden düzenleme)** Metin düzenleyicisi kodunuzu uygun şekilde yeniden biçimlendirer. Bu seçenek seçildiğinde kod düzenleyicisi şunları sağlar:

- Kodunuzu doğru sekme konumuyla hizalama

- Anahtar sözcükleri, değişkenleri ve nesneleri doğru büyük/küçük harfe yeniden yazın

- Deyimine `Then` eksik ekleme `If...Then`

- İşlev çağrılarını parantez içinde ekleme

- Dizelere eksik bitiş tırnakları ekleme

- Üstel biçimi yeniden biçimlendirme

- Tarihleri yeniden biçimlendirme

**Son yapıların otomatik olarak yerleştirilmesi**

Bir yordam bildiriminin ilk satırı gibi bir tür yazarak Enter tuşuna basarak metin `Sub Main` düzenleyicisi eşleşen bir satır  `End Sub` ekler. Benzer şekilde, For döngüsü [eklersiniz,](/dotnet/visual-basic/language-reference/statements/for-next-statement) metin düzenleyicisi eşleşen bir deyimi `Next` ekler. Bu seçenek seçildiğinde, kod düzenleyicisi otomatik olarak son yapıyı ekler.

**Arabirim ve MustOverride üyelerini otomatik ekleme**

Bir sınıf için deyimini veya deyimini işlerken, metin düzenleyicisi sırasıyla uygulanması veya geçersiz kılınmaları gereken üyeler için `Implements` `Inherits` prototipler ekler.

**Hata düzeltme önerilerini etkinleştirme**

Metin düzenleyicisi yaygın hatalara çözüm önererek uygun düzeltmeyi seçmenize olanak sağlar. Bu düzeltme daha sonra kodunuz için geçerli olur.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
- [Seçenekler, Metin Düzenleyici, Tüm Diller, Sekmeler](../../ide/reference/options-text-editor-all-languages-tabs.md)
