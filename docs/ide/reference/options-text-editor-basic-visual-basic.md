---
title: Seçenekler, metin düzenleyici, temel (VB), gelişmiş
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
ms.openlocfilehash: 11a069e17e615199e367683273adb85e771f1d9c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75584523"
---
# <a name="options-text-editor-basic-visual-basic-advanced"></a>Seçenekler, metin düzenleyici, temel (Visual Basic), gelişmiş
**Seçenekler** (**Araçlar** menüsü) iletişim kutusunun **metin düzenleyici** klasörünün **temel** klasöründe **vb 'ye özgü** Özellik sayfası aşağıdaki özellikleri içerir:

## <a name="analysis"></a>Çözümleme

- Tam çözüm analizini etkinleştirme

   Yalnızca açık kod dosyalarını değil, Çözümdeki tüm dosyalarda kod analizini mümkün bir şekilde sunar. Daha fazla bilgi için bkz. [tam çözüm Analizi](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="using-directives"></a>Using yönergeleri

- Using deyimlerini sıralarken ' System ' yönergelerini ilk olarak Yerleştir

   Seçildiğinde, sağ tıklama menüsündeki kullanımları **Kaldır ve Sırala** komutu `using` yönergelerini sıralar ve ' System ' ad alanlarını listenin en üstüne koyar.

- Yönerge gruplarını kullanarak ayır

   Seçildiğinde, sağ tıklama menüsündeki kullanımları **Kaldır ve Sırala** komutu, aynı kök ad alanına sahip yönergelerin grupları arasına boş bir satır ekleyerek `using` yönergeleri ayırır.

- Başvuru derlemelerindeki türler için kullanımlar önerin
- NuGet paketlerindeki türler için kullanımlar önerin

   Bu seçenekler belirlendiğinde, bir NuGet paketini yüklemek ve başvurulmayan türler için bir `using` yönergesi eklemek üzere [hızlı bir eylem](../quick-actions.md) kullanılabilir.

   ![Visual Studio 'da NuGet paketini yüklemeye yönelik hızlı eylem](media/nuget-lightbulb.png)

## <a name="highlighting"></a>Vurgulama

 **Başvuruların ve anahtar sözcüklerin vurgulanmasını etkinleştir**

Metin Düzenleyicisi, bir sembolün veya `If..Then`, `While...End While`veya `Try...Catch...Finally`gibi bir yan tümcedeki tüm anahtar kelimelerin tüm örneklerini vurgulayabilir. **Ctrl** + **SHIFT** + **aşağı ok** veya **CTRL** + **SHIFT** + **yukarı ok**tuşlarına basarak vurgulanan başvurular veya anahtar sözcükler arasında gezinebilirsiniz.

## <a name="outlining"></a>Anahat Oluşturma

**Anahat oluşturma modunu etkinleştir**

Kod düzenleyicisinde bir dosya açtığınızda, belgeyi anahat modunda görüntüleyebilirsiniz. Daha fazla bilgi için bkz. [anahat oluşturma](../../ide/outlining.md) . Bu seçenek belirlendiğinde, bir dosyayı açtığınızda anahat oluşturma özelliği etkinleştirilir.

**Yordam satırı ayırıcılarını göster**

Metin Düzenleyicisi, yordamların görsel kapsamını gösterir. Aşağıdaki tabloda listelenen konumlarda projenizin *. vb* kaynak dosyalarında bir çizgi çizilir:

|. Vb kaynak dosyasındaki konum|Satır konumu örneği|
|---------------------------------|------------------------------|
|Bir blok bildirimi yapısının kapandıktan sonra|-Bir sınıf, yapı, modül, arabirim veya sabit listesinin sonunda<br />-Bir özellik, işlev veya Sub öğesinden sonra<br />-Bir özellikte get ve set yan tümceleri arasında değil|
|Tek satırlık bir yapı kümesinden sonra|-İçe aktarma deyimlerinden sonra, bir sınıf dosyasındaki tür tanımından önce<br />-Öğesinden sonra, herhangi bir yordamdan önce, bir sınıfta belirtilen değişkenlerden|
|Tek satır bildirimleri sonrasında (blok düzeyi olmayan bildirimler)|-Aşağıdaki import deyimleri, Inherits deyimlerini, değişken bildirimlerini, olay bildirimlerini, temsilci bildirimlerini ve DLL bildirme deyimlerini|

## <a name="block-structure-guides"></a>Yapı kılavuzlarını engelle

Seçildiğinde, düzenleyicide tek tek kod bloklarını kolayca tanımlamanızı sağlayan, yapılandırılmış kod bloklarıyla bir dikey çizgi görüntülenir. Örneğin, bir `Sub` deyimindeki `Sub` ve `EndSub` arasında bir çizgi görürsünüz.

## <a name="editor-help"></a>Düzenleyici yardımı

**Kodu düzgün listeleme (yeniden biçimlendirme)** Metin düzenleyici, kodunuzu uygun şekilde yeniden biçimlendirir. Bu seçenek belirlendiğinde, kod Düzenleyicisi şu şekilde olur:

- Kodunuzu doğru sekme konumuna hizalayın

- Büyük/küçük anahtar sözcükler, değişkenler ve nesneler doğru durumda

- `If...Then` bildirimine eksik `Then` ekleme

- İşlev çağrılarına parantez Ekle

- Dizelere eksik bitiş tırnakları Ekle

- Üstel gösterimi yeniden Biçimlendir

- Tarihleri yeniden Biçimlendir

**Son yapıların otomatik eklenmesi**

Örneğin, bir yordam bildiriminin ilk satırı `Sub Main`, ve **ENTER**tuşuna bastığınızda, metin düzenleyici eşleşen bir `End Sub` satırı ekler. Benzer şekilde, bir [for](/dotnet/visual-basic/language-reference/statements/for-next-statement) döngüsü eklerseniz, metin düzenleyici eşleşen bir `Next` ifadesini ekler. Bu seçenek belirlendiğinde, kod Düzenleyicisi bitiş yapısını otomatik olarak ekler.

**Arabirim ve MustOverride üyelerinin otomatik olarak eklenmesi**

Bir sınıf için bir `Implements` ifadesini veya bir `Inherits` ifadesini kaydettiğinizde, metin düzenleyici sırasıyla uygulanması veya geçersiz kılınabilmesi gereken Üyeler için prototipler ekler.

**Hata düzeltme önerilerini etkinleştir**

Metin Düzenleyicisi ortak hatalara çözümler önerebilir ve daha sonra kodunuza uygulanan uygun düzeltmeyi seçmenizi sağlayabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
- [Seçenekler, Metin Düzenleyici, Tüm Diller, Sekmeler](../../ide/reference/options-text-editor-all-languages-tabs.md)
