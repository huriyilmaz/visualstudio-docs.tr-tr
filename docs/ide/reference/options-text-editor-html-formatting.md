---
title: Seçenekler, metin düzenleyici, HTML (Web Forms), biçimlendirme
description: HTML bölümündeki biçimlendirme sayfasını kullanarak kod düzenleyicisinde biçimlendirme kodu için HTML projesi seçeneklerini ayarlama hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Format
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3c8fe85b7bce856867802d43411816ae2df5d2c
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040985"
---
# <a name="options-text-editor-html-web-forms-formatting"></a>Seçenekler, metin düzenleyici, HTML (Web Forms), biçimlendirme

Kod düzenleyicisinde biçimlendirme kodu için HTML projesi seçeneklerini ayarlamak için **biçimlendirme** seçenekleri sayfasını kullanın. Bu sayfaya erişmek için, menü çubuğunda **Araçlar**  >  **Seçenekler**' i seçin ve ardından **metin düzenleyici**  >  **HTML (Web Forms)**  >  **biçimlendirmesini** genişletin.

## <a name="capitalization"></a>Büyük harfe çevirme

Bu seçenekler belirlendiğinde, kaynak görünümü ve XML düzenleyicileri öğeler ilk oluşturulduğunda ve otomatik biçimlendirme sırasında öğe ve özniteliklerin adlarına varsayılan bir durum biçimi uygular. **Otomatik biçimlendirme ayarlarını uygula** ayarı otomatik yeniden biçimlendirme işleminin gerçekleştiği saati belirlenir.

> [!WARNING]
> XML büyük/küçük harfe duyarlıdır. Varsayılan bir durum ayarlama, XML ayrıştırıcılarını etkileyebilir.

### <a name="uielement-list"></a>UIElement listesi

**Sunucu etiketi, sunucu öznitelikleri**

Bu seçenekler, Web sunucusu denetimleri için biçimlendirmenin nasıl büyük harfli olduğunu belirtir.

|Seçenek|Sonuç|
|---------------------------------|------------------------------|
|**Girildiği gibi**|Öğe durumu tam olarak girdiğiniz gibidir.|
|**Büyük harfe**|Öğe adları büyük harfle yeniden biçimlendirilir.|
|**Küçük harf**|Öğe adları küçük harfe biçimlendirilir.|
|**Derleme tanımı**|Öğe durumu, öğenin karşılık gelen tür sınıfında nasıl tanımlandığınıza göre belirlenir.|

**İstemci etiketi, Istemci öznitelikleri**

Bu seçenekler, otomatik biçimlendirmenin HTML özniteliklerinin ve özelliklerinin adlarını büyük veya küçük harfe ve bu adların girildiği gibi tutup değiştirmediğini belirtir.

|Seçenek|Sonuç|
|---------------------------------|------------------------------|
|**Girildiği gibi**|Öznitelik durumu tam olarak girdiğiniz gibidir.|
|**Büyük harfe**|Öznitelik adları büyük harfle yeniden biçimlendirilir.|
|**Küçük harf**|Öznitelik adları küçük harfe biçimlendirilir.|

## <a name="automatic-formatting-options"></a>Otomatik biçimlendirme seçenekleri

Bu seçenekler, otomatik biçimlendirme sırasında kaynak görünümü düzenleyicisinin fiziksel satır sonlarını eklemesine veya kaldırmasına neden olur. Ayrıca, düzenleyicinin özniteliklerin etrafına tırnak ekleyip eklememeyeceğini de belirtebilirsiniz.

> [!NOTE]
> Bu ayarlar, XML biçimlendirmesi içinde boşluk değiştirmez.

### <a name="uielement-list"></a>UIElement listesi

- **Yazarken öznitelik değer tırnakları Ekle**

   Bu seçenek belirlendiğinde, düzenleyici, yazarken otomatik olarak özniteliklerin etrafında tırnak işaretleri koyar (örneğin: ID = "Select1"). İşaretinizdeki tırnak işaretlerini el ile eklemeyi tercih ediyorsanız bu seçeneği temizleyin.

   > [!NOTE]
   > Bu seçeneğin seçili olup olmadığı, işaretinizdeki tüm mevcut tırnak işaretleri korunur; tırnak işaretleri hiçbir şekilde kaldırılmaz.

- **Biçimlendirme sırasında öznitelik değer tırnakları Ekle**

   Bu seçenek belirlendiğinde, otomatik biçimlendirme öznitelik değerlerinin etrafında tırnak işaretleri ekler (örneğin: ID = "Select1").

   > [!NOTE]
   > Bu seçeneğin seçili olup olmadığı, işaretinizdeki tüm mevcut tırnak işaretleri korunur.

- **Kapanış etiketini otomatik ekle**

   Bu seçenek belirlendiğinde, açma etiketini kapattığınızda düzenleyici otomatik olarak bir kapatma etiketi (örneğin, **\</b>** ) oluşturur.

## <a name="tag-wrapping"></a>Etiket sarmalama

Bu seçenekler, belirli bir uzunluktan daha fazla gittiklerinde düzenleyicinin etiketleri çizgilere böler.

### <a name="uielement-list"></a>UIElement listesi

- **Belirtilen uzunluk aşıldığında etiketleri sarın**

   Seçildiğinde, etiket, **uzunluk** metin kutusunda belirttiğiniz uzunlukla daha fazla olursa düzenleyici çizgiler arasındaki etiketleri keser. Bu eylem, yeni bir etiket yazarken değil, yalnızca etiketi biçimlendirirken oluşur.

   > [!NOTE]
   > Belirttiğiniz değer en düşük değer olarak kullanılır. Düzenleyici bağımsız öznitelikleri parçalara ayırmaz.

- **Uzunluk**

   Sarmalamadan önce bir satırda görüntülenecek karakter sayısını belirtir. Bu giriş kutusu, **belirtilen uzunluk aşıldığında etiketleri Sarla** onay kutusu işaretli değilse devre dışıdır.

- **Etikete özgü seçenekler**

   Tek tek Etiketler veya etiket grupları için biçimlendirme seçeneklerini ayarlamanıza olanak sağlayan **etikete özgü seçenekler** iletişim kutusunu görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
