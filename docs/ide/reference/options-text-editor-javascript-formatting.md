---
title: Seçenekler, Metin Düzenleyici, JavaScript, Biçimlendirme
ms.date: 10/29/2018
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.New_Lines
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Formatting.New_Lines
ms.assetid: 28a0aef1-9353-4d94-95a5-54b42e15c0dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 957dbd557a15c4c1df6028672f204a06936767c1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68605993"
---
# <a name="options-dialog-box-text-editor--javascript--formatting"></a>Seçenekler iletişim kutusu: \> Metin \> Düzenleyicisi JavaScript Biçimlendirme

Kod Düzenleyicisi'nde kod biçimlendirme seçeneklerini ayarlamak için **Seçenekler** iletişim kutusunun **Biçimlendirme** sayfasını kullanın. Bu sayfaya erişmek için menü çubuğunda **Araçlar** > **Seçenekleri'ni**seçin ve ardından **Text Editor** > **JavaScript/TypeScript** > **Biçimlendirme'yi genişletin.**

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="automatic-formatting"></a>Otomatik Biçimlendirme

Bu **seçenekler, Kaynak** görünümünde biçimlendirmenin ne zaman gerçekleşer olduğunu belirler.

### <a name="uielement-list"></a>UIElement Listesi

|Seçenek|Açıklama|
|------------|-----------------|
|**Tamamlanan satırı Gir'te biçimlendirme**|Bu seçenek seçildiğinde, Enter tuşunu seçtiğinizde Kod Düzenleyicisi satırı otomatik olarak biçimlendirin.|
|**Biçim tamamlanmış deyimi;**|Bu seçenek seçildiğinde, kod düzenleyicisi yarım nokta nokta lı anahtarı seçtiğinizde satırı otomatik olarak biçimlendirin.|
|**{'de açılan bloğu biçimlendirme**|Bu seçenek seçildiğinde, açılış ayraç anahtarını seçtiğinizde Kod Düzenleyicisi satırı otomatik olarak biçimlendirin.|
|**Tamamlanan bloğu } üzerinde biçimlendirme**|Bu seçenek seçildiğinde, Kapanış ayraç anahtarını seçtiğinizde Kod Düzenleyicisi satırı otomatik olarak biçimlendirin.|
|**Yapıştır'da biçimlendirme**|Bu seçenek seçildiğinde, kod düzenleyicisine yapıştırdığınızda Kod Düzenleyicisi kodu yeniden biçimlenir. Düzenleyici, şu anda tanımlanmış biçimlendirme kurallarını kullanır. Bu seçenek seçili değilse, düzenleyici yapıştırılan kodun özgün biçimlendirmesini kullanır.|

## <a name="new-lines"></a>Yeni Hatlar

Bu seçenekler, Kod Düzenleyicisi'nin işlevler ve denetim blokları için yeni bir satıra açık bir ayraç verip verip veremediğini belirler.

### <a name="uielement-list"></a>UIElement listesi

|Seçenek|Açıklama|
|------------|-----------------|
|**Fonksiyonlar için yeni satıra açık ayraç yerleştirin**|Bu seçenek seçildiğinde, Kod Düzenleyicisi bir işlevle ilişkili açık ayraç yeni bir satıra taşır.|
|**Denetim blokları için yeni satıra açık ayraç yerleştirin**|Bu seçenek seçildiğinde, Kod Düzenleyicisi denetim bloğuyla ilişkili açık `if` `while` ayraç (örneğin, denetim blokları) yeni bir satıra taşır.|

## <a name="spacing"></a>Aralık

Bu **seçenekler, kaynak** görünümüne boşlukların nasıl eklenmelerini belirler.

### <a name="uielement-list"></a>UIElement listesi

|Seçenek|Açıklama|
|------------|-----------------|
|**Virgül delimiter sonra boşluk ekleme**|Bu seçenek seçildiğinde, Kod Düzenleyicisi virgül delimiters sonra bir boşluk ekler.|
|**'For' ifadelerinde yarı kolondan sonra boşluk ekleme**|Bu seçenek seçildiğinde, Kod Düzenleyicisi bir döngünün ilk satırında her yarım nokta iki nokta sonra bir `for` boşluk ekler.|
|**İkili işleçler öncesi ve sonrası alan ekleme**|Bu seçenek seçildiğinde, Kod Düzenleyicisi ikili işleçlerden önce ve sonra bir alan ekler (örneğin, +, -, &&, &#124;&#124;).|
|**Denetim akış ifadelerinde anahtar kelimelerden sonra boşluk ekleme**|Bu seçenek seçildiğinde, Kod Düzenleyicisi denetim akışı ekstrelerinde JavaScript anahtar kelimesonra bir boşluk ekler.|
|**Anonim işlevler için işlev anahtar sözcüğünden sonra boşluk ekleme**|Bu seçenek seçildiğinde, Kod Düzenleyicisi `function` anonim işlevler için anahtar kelimeden sonra bir alan ekler.|
|**Açaçtıktan sonra ve boş olmayan parantezi kapatmadan önce boşluk ekleme**|Bu seçenek seçildiğinde, Kod Düzenleyicisi açılış parantezinden sonra ve parantez içinde boş olmayan karakterler varsa kapanış parantezinden önce bir boşluk ekler.|

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)