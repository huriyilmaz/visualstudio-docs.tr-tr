---
title: Seçenekler, Metin Düzenleyicisi, HTML (Web Formları), Biçimlendirme
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
ms.openlocfilehash: 9e28caf7f71af7c7a07634d1732a1001a32a4aee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568327"
---
# <a name="options-text-editor-html-web-forms-formatting"></a>Seçenekler, Metin Düzenleyicisi, HTML (Web Formları), Biçimlendirme

Kod Düzenleyicisi'nde kodu biçimlendirmek için HTML proje seçeneklerini ayarlamak için **Biçimlendirme** seçenekleri sayfasını kullanın. Bu sayfaya erişmek için menü çubuğunda **Araçlar** > **Seçenekleri'ni**seçin ve ardından **Metin Düzenleyicisi** > **HTML (Web Formları)** > **Biçimlendirmesini genişletin.**

## <a name="capitalization"></a>Büyük harf

Bu seçenekler seçildiğinde, Kaynak görünümü ve XML düzenleyicileri, öğeler ilk oluşturulduğunda ve otomatik biçimlendirme sırasında öğelerin ve özniteliklerin adlarına varsayılan durum biçimi uygular. **Otomatik Biçimlendirme Uygula** ayarları, otomatik yeniden biçimlendirmenin oluştuğu zamanı belirler.

> [!WARNING]
> XML büyük/küçük harf duyarlıdır. Varsayılan bir servis talebi nin ayarlanması XML ayrıştıcılarını etkileyebilir.

### <a name="uielement-list"></a>UIElement listesi

**Sunucu etiketi, Sunucu öznitelikleri**

Bu seçenekler, Web sunucusu denetimleri için biçimlendirmenin nasıl büyük harfle işledir olduğunu belirtir.

|Seçenek|Sonuç|
|---------------------------------|------------------------------|
|**Girilen gibi**|Eleman durumu tam olarak girdiğiniz gibidir.|
|**Büyük harfe**|Öğe adları büyük harfe yeniden biçimlendirilir.|
|**Küçük harf**|Öğe adları küçük harfe yeniden biçimlendirilir.|
|**Montaj tanımı**|Eleman durumu, öğenin ilgili tür sınıfında nasıl tanımlandığına göre belirlenir.|

**İstemci etiketi, İstemci öznitelikleri**

Bu seçenekler, otomatik biçimlendirmenin HTML özniteliklerinin adlarını ve özelliklerini büyük veya küçük harfle değiştirip değiştirmediğini veya girilen olarak tutup tutmayacağını belirtir.

|Seçenek|Sonuç|
|---------------------------------|------------------------------|
|**Girilen gibi**|Öznitelik örneği tam olarak girdiğiniz gibidir.|
|**Büyük harfe**|Öznitelik adları büyük harfe yeniden biçimlendirilir.|
|**Küçük harf**|Öznitelik adları küçük harfe yeniden biçimlendirilir.|

## <a name="automatic-formatting-options"></a>Otomatik biçimlendirme seçenekleri

Bu seçenekler, Kaynak görünüm düzenleyicisinin otomatik biçimlendirme sırasında fiziksel satır sonları eklemesine veya kaldırmasına neden olur. Düzenleyicinin özniteliklere tırnak ekleyip eklmeyeceğini de belirtebilirsiniz.

> [!NOTE]
> Bu ayarlar XML biçimlendirmesi içindeki beyaz alanı değiştirmez.

### <a name="uielement-list"></a>UIElement listesi

- **Yazarken öznitelik değer tırnak ekleme**

   Bu seçenek seçildiğinde, düzenleyici siz yazarken otomatik olarak teklif işaretlerini özniteliklerin etrafına koyar (örneğin: ID="Select1"). İşaretlemenize el ile teklif işaretleri eklemeyi tercih ederseniz bu seçeneği temizleyin.

   > [!NOTE]
   > Bu seçenek seçilip seçilmediği, biçimlendirmenizdeki varolan tüm tırnak işaretleri korunur; tırnak işaretleri hiçbir zaman kaldırılmaz.

- **Biçimlendirme yaparken öznitelik değer tırnak larını ekleme**

   Bu seçenek seçildiğinde, otomatik biçimlendirme öznitelik değerlerinin etrafına teklif işaretleri ekler (örneğin: ID="Select1").

   > [!NOTE]
   > Bu seçenek seçilip seçilmediği, biçimlendirmenizdeki varolan tüm tırnak işaretleri korunur.

- **Otomatik ekleme yakın etiketi**

   Bu seçenek seçildiğinde, açılış etiketini kapattığınızda düzenleyici otomatik olarak bir kapanış etiketi (örneğin, ** \</b>) **oluşturur.

## <a name="tag-wrapping"></a>Etiket sarma

Bu seçenekler, düzenleyicinin etiketleri belirli bir uzunluğun ötesine geçmesi durumunda satırlara ayırıp ayırmadığını belirler.

### <a name="uielement-list"></a>UIElement listesi

- **Belirtilen uzunluğu aştığında etiketleri kaydırma**

   Seçildiğinde, etiket **Uzunluk** metin kutusunda belirttiğiniz uzunluğun ötesine geçerse, düzenleyici etiketleri satırlar arasında ayırır. Bu eylem, yalnızca etiketi biçimlendirirken oluşur, yeni bir etiket yazarken değil.

   > [!NOTE]
   > Belirttiğiniz değer minimum değer olarak kullanılır. Editör bireysel öznitelikleri ayırmaz.

- **Uzunluk**

   Sarmadan önce bir satırda görüntülenecek karakter sayısını belirtir. Belirtilen uzunluk kutusunu **aştığında Kaydırma etiketleri** işaretlenmedikçe bu giriş kutusu devre dışı bırakılır.

- **Belirli Seçenekleri Etiketle**

   Tek tek etiketler veya etiket grupları için biçimlendirme seçenekleri ayarlamanızı sağlayan **Etikete Özgü Seçenekler** iletişim kutusunu görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
