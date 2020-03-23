---
title: Seçenekler, Metin Düzenleyicisi, Temel (VB), Gelişmiş
ms.date: 01/16/2019
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 562358ca90e223a07926aaa383ded41a5f7557cc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79431481"
---
# <a name="options-text-editor-basic-visual-basic-advanced"></a>Seçenekler, Metin Düzenleyicisi, Temel (Visual Basic), Gelişmiş
**VB Özel** özellik sayfası, **Seçenekler** **(Araçlar** menüsü) iletişim kutusunun **Metin Düzenleyicisi** klasörünün **Temel** klasöründe aşağıdaki özellikleri içerir:

## <a name="analysis"></a>Analiz

- Canlı kod analizi veya Arka Plan analizi kapsamı

   Yönetilen kod için arka plan çözümleme kapsamını yapılandırın. Daha fazla bilgi için [bkz: Yönetilen kod için canlı kod çözümlemesi kapsamını yapılandırma.](../../code-quality/configure-live-code-analysis-scope-managed-code.md)

## <a name="using-directives"></a>Direktifleri Kullanma

- Kullanır sıralama yaparken önce 'Sistem' yönergelerini yerleştirin

   Seçildiğinde, Sağ tıklatma menüsündeki **Kullanımları Kaldır ve Sırala** komutu `using` yönergeleri sıralar ve 'Sistem' ad alanlarını listenin en üstüne yerleştirir.

- Yönerge gruplarını ayrı kullanma

   Seçildiğinde, sağ tıklatma menüsündeki **Kullan-Kaldır komutu,** aynı kök ad alanına sahip yönerge grupları arasına boş bir satır ekleyerek `using` yönergeleri ayırır.

- Referans derlemelerinde türleri için kullanır önerin
- NuGet paketlerindeki türler için kullanma önerin

   Bu seçenekler seçildiğinde, [Quick Action](../quick-actions.md) Bir NuGet paketi yüklemek ve başvurulmamış türler için bir `using` yönerge eklemek için hızlı eylem kullanılabilir.

   ![Visual Studio'da NuGet paketini yüklemek için hızlı aksiyon](media/nuget-lightbulb.png)

## <a name="highlighting"></a>Vurgulama

 **Referansların ve anahtar kelimelerin vurgulanmasını etkinleştirme**

Metin düzenleyicisi, bir sembolün tüm örneklerini veya `If..Then`tüm `While...End While`anahtar `Try...Catch...Finally`kelimeleri , , veya . Ctrl Shift**Down ok** veya **Ctrl** + **Shift** +  **Ctrl** + **Shift** + **Up ok**tuşuna basarak vurgulanan başvurular veya anahtar kelimeler arasında gezinebilirsiniz.

## <a name="outlining"></a>Anahat Oluşturma

**Anahat modunu etkinleştirme**

Kod düzenleyicisinde bir dosya yı açtığınızda, belgeyi anahat modunda görüntüleyebilirsiniz. Daha fazla bilgi için [Anahat'a](../../ide/outlining.md) bakın. Bu seçenek seçildiğinde, bir dosyayı açtığınızda anahat özelliği etkinleştirilir.

**Yordam çizgisi ayırıcılarını göster**

Metin düzenleyicisi yordamların görsel kapsamını gösterir. Aşağıdaki tabloda listelenen konumlarda projenizin *.vb* kaynak dosyalarında bir çizgi çizilir:

|.vb Kaynak Dosyasındaki Konum|Hat Konumu Örneği|
|---------------------------------|------------------------------|
|Bir blok bildirimi oluşturma kapatıldıktan sonra|- Bir sınıfın sonunda, yapı, modül, arayüz veya enum<br />- Bir özellik, işlev veya alt<br />- Bir özellikteki al ve ayar yan tümceleri arasında değil|
|Tek satır yapılarından sonra|- Alma ekstresinden sonra, sınıf dosyasındaki tür tanımından önce<br />- Bir sınıfta bildirilen değişkenlerden sonra, herhangi bir yordamdan önce|
|Tek satır lı bildirimlerden sonra (blok düzeyinde olmayan düzey bildirimleri)|- İthalat beyannamelerini takiben, beyannameleri, değişken beyannameleri, olay beyanları, temsilci beyanları ve DLL beyan beyan beyanları|

## <a name="block-structure-guides"></a>Blok Yapı Kılavuzları

Seçildiğinde, yapılandırılmış kod bloklarıyla hizalanan düzenleyicide dikey çizgiler görünür ve bu da kod bloklarını tek tek belirlemenize olanak tanır. Örneğin, bir deyim arasında `Sub` ve `EndSub` içinde `Sub` bir satır görürsünüz.

## <a name="editor-help"></a>Editör Yardımı

**Pretty Listing (yeniden biçimlendirme) kodu** Metin düzenleyicisi, kodunuzu uygun şekilde yeniden biçimze verir. Bu seçenek seçildiğinde, kod düzenleyicisi şunları yapacaktır:

- Kodunuzu doğru sekme konumuna hizalama

- Anahtar kelimeleri, değişkenleri ve nesneleri doğru servis talebine yeniden kullanma

- `If...Then` Bir bildirime eksik `Then` ekleme

- İşlev çağrılarına parantez ekleme

- Dizeleri eksik uç tırnak ekleme

- Reformat üstel gösterim

- Reformat tarihleri

**Uç yapılarının otomatik olarak eklenmesi**

Örneğin, bir yordam bildiriminin `Sub Main`ilk satırı yazdığınızda ve **Enter**tuşuna bastığında, metin düzenleyicisi eşleşen `End Sub` bir satır ekler. Benzer şekilde, Bir [For](/dotnet/visual-basic/language-reference/statements/for-next-statement) döngüsü eklerseniz, metin `Next` düzenleyicisi eşleşen bir deyim ekler. Bu seçenek seçildiğinde, kod düzenleyicisi otomatik olarak son yapıyı ekler.

**Arabirim ve MustOverride üyelerinin otomatik olarak eklenmesi**

Bir sınıf `Implements` için bir `Inherits` deyim veya deyim işlediğinde, metin düzenleyicisi sırasıyla uygulanması veya geçersiz kılınması gereken üyeler için prototipler ekler.

**Hata düzeltme önerilerini etkinleştirme**

Metin düzenleyicisi sık karşılaşılan hatalara çözümler önerebilir ve daha sonra kodunuza uygulanan uygun düzeltmeyi seçmenize izin verebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
- [Seçenekler, Metin Düzenleyici, Tüm Diller, Sekmeler](../../ide/reference/options-text-editor-all-languages-tabs.md)
