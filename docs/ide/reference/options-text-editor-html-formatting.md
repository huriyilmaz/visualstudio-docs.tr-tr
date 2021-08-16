---
title: Seçenekler, Metin Düzenleyici, HTML (Web Forms), Biçimlendirme
description: Kod Düzenleyicisi'nde kodu biçimlendirmek üzere HTML projesi seçeneklerini ayarlamak için HTML bölümündeki Biçimlendirme sayfasını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Format
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 22e4d986204645e136709efad87e27b5b97289ec0d6042d8bc03cbfbcd9fb9ee
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121271920"
---
# <a name="options-text-editor-html-web-forms-formatting"></a>Seçenekler, Metin Düzenleyici, HTML (Web Forms), Biçimlendirme

Kod **Düzenleyicisi'nde** kodu biçimlendirmek üzere HTML projesi seçeneklerini ayarlamak için Biçimlendirme seçenekleri sayfasını kullanın. Bu sayfaya erişmek için menü çubuğunda Araçlar Seçenekleri'ni seçin ve ardından Metin  >  Düzenleyicisi   >  **HTML (Web Forms) Biçimlendirme'yi**  >  **genişletin.**

## <a name="capitalization"></a>Büyük harf

Bu seçenekler seçildiğinde, Kaynak görünümü ve XML düzenleyicileri, öğeler ilk oluşturulduğunda ve otomatik biçimlendirme sırasında öğe ve özniteliklerin adlara varsayılan bir büyük/küçük harf biçimi uygulayabilir. Otomatik **Biçimlendirme Uygula** ayarları, otomatik yeniden biçimlendirmenin oluştuğu zamanı belirler.

> [!WARNING]
> XML büyük/büyük/büyük harfe duyarlıdır. Varsayılan durum ayarı XML ayrıştırıcılarını etkileyene kadar devam ediyor olabilir.

### <a name="uielement-list"></a>UIElement listesi

**Sunucu etiketi, Sunucu öznitelikleri**

Bu seçenekler, Web sunucusu denetimleri için işaretlemenin büyük harfle nasıl büyük harfe nasıl hazır olduğunu belirtir.

|Seçenek|Sonuç|
|---------------------------------|------------------------------|
|**Girildi olarak**|Öğe durumu, tam olarak sizin girdiklerin durumudur.|
|**Büyük harfe**|Öğe adları büyük harfe yeniden biçimlendirildi.|
|**Küçük harf**|Öğe adları küçük harfe yeniden biçimlendirildi.|
|**Derleme tanımı**|Öğe durumu, öğenin karşılık gelen tür sınıfında nasıl tanımlandığına göre belirlenir.|

**İstemci etiketi, İstemci öznitelikleri**

Bu seçenekler, otomatik biçimlendirmenin HTML özniteliklerinin ve özelliklerinin adlarını büyük harf veya küçük harf olarak değiştirip değiştirmeyeceklerini veya girildik şekilde tutarlarını belirtir.

|Seçenek|Sonuç|
|---------------------------------|------------------------------|
|**Girildi olarak**|Öznitelik durumu, tam olarak sizin girdiklerin durumuna göredir.|
|**Büyük harfe**|Öznitelik adları büyük harfe yeniden biçimlendirildi.|
|**Küçük harf**|Öznitelik adları küçük harfe yeniden biçimlendirildi.|

## <a name="automatic-formatting-options"></a>Otomatik biçimlendirme seçenekleri

Bu seçenekler, Kaynak görünümü düzenleyicisinin otomatik biçimlendirme sırasında fiziksel satır sonlarını eklemesini veya kaldırmalarını sağlar. Ayrıca düzenleyicinin özniteliklerin etrafında tırnak içine alınıp alınmayacaklarını da belirtabilirsiniz.

> [!NOTE]
> Bu ayarlar XML işaretlemesinde boşluk değiştirmez.

### <a name="uielement-list"></a>UIElement listesi

- **Yazarken öznitelik değeri tırnak içine alın**

   Bu seçenek seçildiğinde, siz yazarken düzenleyici otomatik olarak özniteliklerin etrafına tırnak işaretleri koyar (örneğin: ID="Select1"). İşaretlemenize el ile tırnak işareti eklemek isterseniz bu seçeneği silin.

   > [!NOTE]
   > Bu seçeneğin seçili olup olmadığı, işaretlemenizin tüm mevcut tırnak işaretleri korunur; tırnak işaretleri hiçbir zaman kaldırılamaz.

- **Biçimlendirmede öznitelik değeri tırnak içine alın**

   Bu seçenek seçildiğinde, otomatik biçimlendirme öznitelik değerlerinin etrafına tırnak işaretleri ekler (örneğin: ID="Select1").

   > [!NOTE]
   > Bu seçeneğin seçili olup olmadığı, işaretlemenizin tüm mevcut tırnak işaretleri korunur.

- **Otomatik ekleme kapatma etiketi**

   Bu seçenek seçildiğinde, siz açılış etiketini kapatarak düzenleyici otomatik olarak bir **\</b>** kapanış etiketi (örneğin, ) oluşturur.

## <a name="tag-wrapping"></a>Etiket sarmalama

Bu seçenekler, belirli bir uzunluktan fazla olursa düzenleyicinin etiketleri satırlara dönüştürip kesmeyeceklerini belirler.

### <a name="uielement-list"></a>UIElement listesi

- **Belirtilen uzunluğu aşarken etiketleri sarmalama**

   Bu seçildiğinde, etiket Uzunluk metin kutusunda belirttiğiniz uzunluktan fazla olursa düzenleyici etiketleri **satırlar arasında** kırar. Bu eylem yalnızca etiketi biçimlendirken gerçekleşir, yeni bir etiket yazarken değil.

   > [!NOTE]
   > Belirttiğiniz değer, minimum değer olarak kullanılır. Düzenleyici tek tek öznitelikleri kesmez.

- **Uzunluk**

   Sarmalamadan önce bir satırda görüntülemek istediğiniz karakter sayısını belirtir. Belirtilen uzunluk aşılırken etiketleri **sarmala kutusu işaretli değilse bu giriş** kutusu devre dışı bırakılır.

- **Etikete Özgü Seçenekler**

   Tek tek **etiketler veya** etiket grupları için biçimlendirme seçeneklerini ayarlamaya olanak sağlayan Etikete Özgü Seçenekler iletişim kutusunu görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
