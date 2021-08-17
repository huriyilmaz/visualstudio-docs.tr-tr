---
title: XML düzenleyicisi IntelliSense Özellikleri
description: Visual Studio'de XML düzenleyicisinin IntelliSense özelliklerini ve bunları XML Şeması tanımlama dili (XSD) ve XSLT belgeleriyle nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2b26f214-cc3a-46bf-b260-14eb8e599182
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: ae04f877467f24a31446c832af34b96c30bd92f6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122031906"
---
# <a name="xml-editor-intellisense-features"></a>XML düzenleyicisi IntelliSense özellikleri

XML düzenleyicisi, veri kaynağında sağlanan diğer dil düzenleyicileri ile karşılaştırılabilir tam IntelliSense Visual Studio. Bu bölümde, XML Şeması tanımlama dili (XSD) ve XSLT belgeleriyle IntelliSense'i nasıl kullanabileceğiniz açıklandı.

## <a name="intellisense-in-an-xsd-document"></a>XSD belgesinde IntelliSense

Belgeniz ile bir şema ilişkilendirildikten sonra, xml düzenleyicisi araç çubuğundaki Nesne Üye Listesini Görüntüle düğmesine her yazıldığında veya tıklarsanız beklenen öğelerin bir açılan `"<"` listesini elde  edersiniz.

![Nesne üye listesini görüntüle düğmesi](media/display-object-member-list-xml.png)

Şemaları XML belgeleriyle ilişkilendirme hakkında bilgi için bkz. [XML belge doğrulaması.](../xml-tools/xml-document-validation.md)

Bir başlangıç etiketinin içinden SPACE yazarak, geçerli öğeye eklen all özniteliklerini gösteren bir açılan liste de elde olur.

Bir öznitelik değeri veya değerin açılış teklifi için yazarak ilgili öznitelik `"="` için olası değerlerin listesini de elde edersiniz. Değerler yalnızca şema, facets aracılığıyla numara verilen değerler sağlarsa veya öznitelik `xsd:enumeration` bir türse `Boolean` sağlanır. bilinen dil kodlarının IntelliSense listesi de veya `xml:lang` 'den `simpleType` türetilen herhangi biri için `xsd:language` sağlanır. Ad alanı bildirimleri için bilinen değerlerin IntelliSense `targetNamespace` listesi sağlanır.

Öğe bir ise bir başlangıç etiketini kapatmak için yazarak olası değerlerin IntelliSense `">"` listesi de `simpleType` sağlanır. Öğelerin davranışı, önceki paragrafta açıklanan özniteliklerin davranışına benzer.

ToolTips, ilişkili şemada bulunan ve bilgileri temel alan bu IntelliSense `xsd:annotation` `xsd:documentation` listelerinde de görünür.

## <a name="intellisense-in-an-xslt-document"></a>XSLT belgesinde IntelliSense

XSLT belgenize adlandırılmış şablon veya öznitelik ekledikten sonra IntelliSense'i kullanarak aşağıdakileri ekleyebilirsiniz:

- Öznitelik kümesi adları.

- Şablon modları.

- Şablon adları.

- Verilen mod için parametre adları.

- Verilen adlandırılmış şablon için parametre adları.

Daha fazla bilgi için [bkz. Adım adım kılavuz: XSLT IntelliSense kullanma](../xml-tools/walkthrough-using-xslt-intellisense.md) konusu.

## <a name="auto-completion"></a>Otomatik tamamlama

XML düzenleyicisi, gerekli XML söz dizimlerini sizin için doldurarak XML düzenlemeyi de kolaylaştırır. Örneğin, aşağıdaki başlangıç etiketini yazın:

`<book>`

XML düzenleyicisi, bitiş etiketini doldurur ve imleci başlangıç etiketinin ardından konumlar. Aşağıda buna bir örnek ve ardından "&#124;" imleç konumunu not alır):

`<book>`&#124;`</book>`

Öznitelik değerlerinin her zaman tırnak değerleri olması gerekir, çünkü XML düzenleyicisi tırnakları sizin için doldurur. Örneğin, aşağıdakini yazın:

`<book title=`

XML düzenleyicisi tırnakları ekler ve imleci tırnak içine alır:

`<book title="`&#124;`"`

Benzer şekilde, XML düzenleyicisi sizin için aşağıdaki XML söz dizimlerini de otomatik olarak ekler:

- İşleme yönergesi sona erer:  `?>`

- CDATA bloğu sona erer: `]]>`

- Bir açıklamayı sona er: `-->`

- DTD bildirimini sona erdirin: `>`

IntelliSense listesinden bir ad alanı niteli öğesi veya özniteliğini seçmeniz ve bu öğe veya özniteliğin ad alanı henüz kapsamda değilse XML düzenleyicisi bir ad alanı bildirimi ekleme özelliğine de sahip.

Örneğin, ön ekin belgede bildir edilmemiş olan ad alanına bağlı olduğu IntelliSense listesinden öğeyi seçersiniz, XML düzenleyicisi sizin için gerekli ad alanı `e:Book` `http://books` bildirimini ekler. Sonuçta elde edilen XML metni aşağıdaki gibidir:

`<e:Book xmlns:e="http://books"`

## <a name="brace-matching"></a>Küme ayracı eşleştirme

XML düzenleyicisi, kapatmış olduğunuz öğelerle ilgili anında geri bildirim vermek için küme ayracı vurgulaması sağlar. Bir ayraçtan eşleşen küme ayracına atlamak için klavye kısayolunu (**Ctrl** + **]**) da kullanabilirsiniz.

XML düzenleyicisi bunu aşağıdaki öğeler için yapar:

- Başlangıç ve bitiş etiketlerini eşleştirme.

- Herhangi bir çift " \<" or "> " açılı ayraç.

- Yorumların başlangıcı ve bitişi.

- İşlem başlatma ve bitiş yönergeleri.

- CDATA bloklarının başlangıç ve bitişi.

- DTD bildirimlerinin başlangıç ve bitişi.

- Özniteliklerde tırnak açma ve kapatma.

## <a name="modify-the-intellisense-options"></a>IntelliSense seçeneklerini değiştirme

IntelliSense ve otomatik tamamlama özellikleri varsayılan olarak etkindir. Ancak, Araç Seçenekleri ayarlarınızı değiştirerek **bunu**  >  **değiştirebilirsiniz.**

Çeşitli **sayfanın** Otomatik **Ekle bölümü aşağıdaki** davranışı kontrol eder:

|Ad|Açıklama|
|-|-----------------|
|Etiketleri kapatma|Yeni öğeler için kapatma etiketleri ekler.|
|Öznitelik tırnakları|Yeni bir öznitelik adı girerken öznitelik değeri tırnak içine ekler.|
|Diğer işaretleme|Yorumları, CDATA'yi, DOCTYPE'ı, işleme yönergelerini ve diğer işaretleme bildirimlerini tamamlar.|

### <a name="to-change-the-auto-completion-behavior"></a>Otomatik tamamlama davranışını değiştirmek için

1. Araçlar **menüsünden** **Seçenekler'i** seçin.

2. Metin **Düzenleyici'yi** genişletin, **XML'i** genişletin **ve Çeşitli'yi seçin.**

3. Otomatik ekleme bölümünde herhangi bir **değişiklik yapın ve** Tamam'a **tıklayın.**

## <a name="see-also"></a>Ayrıca bkz.

- [XML düzenleyicisi](../xml-tools/xml-editor.md)
- [IntelliSense'i kullanma](../ide/using-intellisense.md)
- [İzlenecek Yol: XSLT IntelliSense Kullanma](../xml-tools/walkthrough-using-xslt-intellisense.md)
