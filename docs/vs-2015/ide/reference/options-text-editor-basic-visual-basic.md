---
title: Seçenekler, metin düzenleyici, temel (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Visual_Basic.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.Editor
- VS.ToolsOptionsPages.Visual_Basic_Editor.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage
- VS.ToolsOptionsPages.Text_Editor.Basic
- VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific
helpviewer_keywords:
- Basic Text Editor Options dialog box
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1edb7ceae1ba187b01b92d64ca33d41d83364e72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662381"
---
# <a name="options-text-editor-basic-visual-basic"></a>Seçenekler, Metin Düzenleyici, Temel (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Seçenekler** (**Araçlar** menüsü) iletişim kutusunun **metin düzenleyici** klasörünün **temel** klasöründe **vb 'ye özgü** Özellik sayfası aşağıdaki özellikleri içerir:

 **Son yapıların otomatik eklenmesi** Örneğin, bir yordam bildiriminin ilk satırını yazın `Sub Main—` ve ENTER tuşuna basarsanız, metin düzenleyici eşleşen bir `End Sub` satır ekler. Benzer şekilde, bir [for](https://msdn.microsoft.com/library/f5fc0d51-67ce-4c36-9f09-31c9a91c94e9) döngüsü eklerseniz, metin düzenleyici eşleşen bir `Next` ifade ekler. Bu seçenek belirlendiğinde, kod Düzenleyicisi bitiş yapısını otomatik olarak ekler.

 **Kodu düzgün listeleme (yeniden biçimlendirme)** Metin düzenleyici, kodunuzu uygun şekilde yeniden biçimlendirir. Bu seçenek belirlendiğinde, kod Düzenleyicisi şu şekilde olur:

- Kodunuzu doğru sekme konumuna hizalayın

- Büyük/küçük anahtar sözcükler, değişkenler ve nesneler doğru durumda

- Deyime eksik ekleme `Then` `If...Then`

- İşlev çağrılarına parantez Ekle

- Dizelere eksik bitiş tırnakları Ekle

- Üstel gösterimi yeniden Biçimlendir

- Tarihleri yeniden Biçimlendir

  **Anahat oluşturma modunu etkinleştir** Kod düzenleyicisinde bir dosya açtığınızda, belgeyi anahat modunda görüntüleyebilirsiniz. Daha fazla bilgi için bkz. [anahat oluşturma](../../ide/outlining.md) . Bu seçenek belirlendiğinde, bir dosyayı açtığınızda anahat oluşturma özelliği etkinleştirilir.

  **Arabirim ve MustOverride üyelerinin otomatik olarak eklenmesi** `Implements` Bir sınıf için bir ifadeyi veya bir `Inherits` ifadeyi kaydettiğinizde, metin düzenleyici sırasıyla uygulanması veya geçersiz kılınabilmesi gereken Üyeler için prototipler ekler.

  **Yordam satırı ayırıcılarını göster** Metin Düzenleyicisi, yordamların görsel kapsamını gösterir. Aşağıdaki tabloda listelenen konumlarda projenizin. vb kaynak dosyalarında bir çizgi çizilir:

|. Vb kaynak dosyasındaki konum|Satır konumu örneği|
|---------------------------------|------------------------------|
|Bir blok bildirimi yapısının kapandıktan sonra|-Bir sınıf, yapı, modül, arabirim veya sabit listesinin sonunda<br />-Bir özellik, işlev veya Sub öğesinden sonra<br />-Bir özellikte get ve set yan tümceleri arasında değil|
|Tek satırlık bir yapı kümesinden sonra|-İçe aktarma deyimlerinden sonra, bir sınıf dosyasındaki tür tanımından önce<br />-Öğesinden sonra, herhangi bir yordamdan önce, bir sınıfta belirtilen değişkenlerden|
|Tek satır bildirimleri sonrasında (blok düzeyi olmayan bildirimler)|-Aşağıdaki import deyimleri, Inherits deyimlerini, değişken bildirimlerini, olay bildirimlerini, temsilci bildirimlerini ve DLL bildirme deyimlerini|

 **Hata düzeltme önerilerini etkinleştir** Metin Düzenleyicisi ortak hatalara çözümler önerebilir ve daha sonra kodunuza uygulanan uygun düzeltmeyi seçmenizi sağlayabilir.

 **Başvuruların ve anahtar sözcüklerin vurgulanmasını etkinleştir** Metin Düzenleyicisi, veya gibi bir yan tümcedeki bir sembolün veya tüm anahtar sözcüklerin tüm örneklerini vurgulayabilir `If..Then` `While...End While` `Try...Catch...Finally` . CTRL + SHIFT + aşağı ok veya CTRL + SHIFT + yukarı ok tuşlarına basarak vurgulanan başvurular veya anahtar sözcükler arasında gezinebilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 [Genel, ortam, Seçenekler Iletişim kutusu](../../ide/reference/general-environment-options-dialog-box.md) [seçenekleri, metin düzenleyici, tüm diller, sekmeler](../../ide/reference/options-text-editor-all-languages-tabs.md)
