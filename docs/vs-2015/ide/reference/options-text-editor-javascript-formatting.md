---
title: Seçenekler, metin düzenleyici, JavaScript, biçimlendirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.New_Lines
ms.assetid: 28a0aef1-9353-4d94-95a5-54b42e15c0dc
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dcfa4a2fb15ed8f4abfff24aa8e78c2b08eb8412
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662242"
---
# <a name="options-text-editor-javascript-formatting"></a>Seçenekler, Metin Düzenleyici, JavaScript, Biçimlendirme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kod düzenleyicisinde biçimlendirme kodu seçeneklerini ayarlamak için **Seçenekler** Iletişim kutusunun **biçimlendirme** sayfasını kullanın. Bu sayfaya erişmek için, menü çubuğunda **Araçlar**, **Seçenekler**' i seçin ve ardından **metin Düzenleyicisi**, **JavaScript**ve **biçimlendirme**' yi genişletin.

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="automatic-formatting"></a>Otomatik Biçimlendirme
 Bu seçenekler, **kaynak** görünümünde biçimlendirmenin ne zaman gerçekleşeceğini belirlenir.

## <a name="uielement-list"></a>UIElement Listesi

|Seçenek|Açıklama|
|------------|-----------------|
|**Girerken Biçimlendirme tamamlandı satırı**|Bu seçenek belirlendiğinde, Enter tuşunu seçtiğinizde, kod Düzenleyicisi otomatik olarak çizgiyi biçimlendirir.|
|**; Üzerinde biçimlendirme tamamlandı ekstresi**|Bu seçenek belirlendiğinde, noktalı virgül anahtarını seçtiğinizde, kod Düzenleyicisi otomatik olarak çizgiyi biçimlendirir.|
|**} Üzerinde biçimlendirme tamamlandı bloğu**|Bu seçenek belirlendiğinde, kapanış küme ayracı tuşunu seçtiğinizde, kod Düzenleyicisi otomatik olarak çizgiyi biçimlendirir.|
|**Yapıştırırken Biçimlendir**|Bu seçenek belirlendiğinde kod Düzenleyicisi, düzenleyiciye yapıştırdığınızda kodu yeniden biçimlendirir. Düzenleyici, geçerli olarak tanımlanmış biçimlendirme kurallarını kullanır. Bu seçenek seçilmezse, düzenleyici yapıştırılan kodun özgün biçimlendirmesini kullanır.|

## <a name="new-lines"></a>Yeni satırlar
 Bu seçenekler, kod düzenleyicisinin yeni bir satırdaki işlevler ve denetim blokları için açık bir küme ayracı yerleştirip yerleştirmediğini belirtir.

## <a name="uielement-list"></a>UIElement Listesi

|Seçenek|Açıklama|
|------------|-----------------|
|**İşlevler için yeni satıra açık küme ayracı yerleştir**|Bu seçenek belirlendiğinde, kod Düzenleyicisi bir işlevle ilişkili açık küme ayracını yeni bir satıra taşıdır.|
|**Denetim blokları için yeni satıra açık küme ayracı yerleştir**|Bu seçenek belirlendiğinde, kod Düzenleyicisi bir denetim bloğu (örneğin, ve denetim blokları) ile ilişkili açık küme ayracını `if` `while` Yeni bir satıra taşıdır.|

## <a name="spacing"></a>Aralık
 Bu seçenekler, **kaynak** görünümünde boşlukların nasıl ekleneceğini tespit ediyor.

## <a name="uielement-list"></a>UIElement Listesi

|Seçenek|Açıklama|
|------------|-----------------|
|**Virgül sınırlayıcısından sonra boşluk Ekle**|Bu seçenek belirlendiğinde, kod Düzenleyicisi virgül sınırlayıcıdan sonra bir boşluk ekler.|
|**' For ' deyiminde noktalı virgülden sonra boşluk Ekle**|Bu seçenek belirlendiğinde, kod Düzenleyicisi döngünün ilk satırına her noktalı virgülden sonra bir boşluk ekler `for` .|
|**İkili işleçlerden önce ve sonra boşluk Ekle**|Bu seçenek belirlendiğinde, kod Düzenleyicisi ikili işleçlerden önce ve sonra bir boşluk ekler (örneğin, +,-,  &&,  &#124;&#124;).|
|**Denetim akışı deyimlerinde anahtar sözcüklerden sonra boşluk Ekle**|Bu seçenek belirlendiğinde, kod Düzenleyicisi denetim akış deyimlerindeki JavaScript anahtar sözcükleriyle sonra bir boşluk ekler.|
|**Anonim işlevler için Function anahtar sözcüğünden sonra boşluk Ekle.**|Bu seçenek belirlendiğinde, kod Düzenleyicisi `function` Anonim işlevler için anahtar sözcükten sonra bir boşluk ekler.|
|**Boş olmayan parantezleri kapatmadan önce ve açtıktan sonra boşluk Ekle**|Bu seçenek belirlendiğinde, kod Düzenleyicisi, parantez içinde boş olmayan karakterler varsa, açma parantezinden sonra ve kapatma parantezinden önce bir boşluk ekler.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
