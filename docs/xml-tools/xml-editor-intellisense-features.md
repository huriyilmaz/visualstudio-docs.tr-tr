---
title: XML Düzenleyicisi IntelliSense özellikleri
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2b26f214-cc3a-46bf-b260-14eb8e599182
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 609684452190bf7471f90fee75f66dbb2fcbec8e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592392"
---
# <a name="xml-editor-intellisense-features"></a>XML düzenleyicisi IntelliSense özellikleri

XML Düzenleyicisi, Visual Studio 'da sağlanan diğer dil düzenleyicilerle karşılaştırılabilir tam IntelliSense özellikleri sağlar. Bu bölümde, IntelliSense 'i XML şeması tanım dili (XSD) ve XSLT belgeleriyle nasıl kullanabileceğiniz açıklanmaktadır.

## <a name="intellisense-in-an-xsd-document"></a>XSD belgesinde IntelliSense

Bir şema belgeyle ilişkilendirildikten sonra, `"<"` her seferinde beklenen öğelerin açılan listesini alır veya XML Düzenleyicisi araç çubuğundaki bir **nesne üye listesini görüntüle** düğmesine tıklayabilirsiniz.

![Nesne üye listesini görüntüle düğmesi](media/display-object-member-list-xml.png)

Şemaları XML belgeleriyle ilişkilendirme hakkında daha fazla bilgi için bkz. [XML belge doğrulaması](../xml-tools/xml-document-validation.md).

Başlangıç etiketinin içinden boşluk yazdığınızda, geçerli öğeye eklenebilen tüm öznitelikleri gösteren bir açılan liste da alırsınız.

Bir öznitelik değeri için `"="` yazdığınızda veya değerin açılış tırnak işareti söz konusu öznitelik için olası değerlerin listesini de alırsınız. Değerler yalnızca şema `xsd:enumeration` modelleri aracılığıyla numaralandırılmış değerler sağlıyorsa veya öznitelik bir `Boolean` türü ise sağlanır. Bilinen dil kodlarının IntelliSense listesi, `xml:lang` veya `xsd:language`türetilen `simpleType` için de sağlanır. Bilinen `targetNamespace` değerlerinin IntelliSense listesi, ad alanı bildirimleri için verilmiştir.

Öğe bir `simpleType`ise başlangıç etiketini kapatmak için `">"` yazdığınızda, olası değerlerin bir IntelliSense listesi de sağlanır. Öğelerin davranışı, önceki paragrafta açıklanan özniteliklerin davranışına benzerdir.

Araç Ipuçları Ayrıca bu IntelliSense listelerinde, ilişkili şemada bulunan `xsd:annotation` ve `xsd:documentation` bilgilerine göre de görünür.

## <a name="intellisense-in-an-xslt-document"></a>XSLT belgesinde IntelliSense

XSLT belgenize adlandırılmış bir şablon veya öznitelik ekledikten sonra, aşağıdakini eklemek için IntelliSense 'i kullanabilirsiniz:

- Öznitelik kümesi adları.

- Şablon modları.

- Şablon adları.

- Belirli bir mod için parametre adları.

- Belirli bir adlandırılmış şablon için parametre adları.

Daha fazla bilgi için bkz. [Izlenecek yol: XSLT IntelliSense 'ı kullanma](../xml-tools/walkthrough-using-xslt-intellisense.md) konusu.

## <a name="auto-completion"></a>Otomatik tamamlama

XML Düzenleyicisi, sizin için gerekli XML söz dizimini doldurarak XML düzenlemesini daha da kolaylaştırır. Örneğin, aşağıdaki başlangıç etiketini yazarsanız:

`<book>`

XML Düzenleyicisi bitiş etiketini doldurur ve imleci başlangıç etiketinden sonra konumlandırır. Aşağıda buna bir örnek verilmiştir ("&#124;" imleç konumunu not edin):

`<book>`&#124;`</book>`

Öznitelik değerleri her zaman tırnak içine sahip olması gerektiğinden, XML Düzenleyicisi teklifleri sizin için doldurur. Örneğin, şunu yazarsanız:

`<book title=`

XML Düzenleyicisi, tırnakları ekler ve imleci tırnak arasına yerleştirir:

`<book title="`&#124;`"`

Benzer şekilde, XML Düzenleyicisi sizin için otomatik olarak aşağıdaki XML sözdizimini de ekler:

- Bir işleme yönergesini sonlandır: `?>`

- CDATA bloğunu sonlandır: `]]>`

- Açıklamayı bitir: `-->`

- Bir DTD bildirimini sonlandır: `>`

Bir IntelliSense listesinden nitelenmiş bir ad alanı veya öznitelik seçerseniz ve bu öğenin veya özniteliğin ad alanı henüz kapsamda değilse, XML Düzenleyicisi de bir ad alanı bildirimi ekleyebilme özelliğine sahiptir.

Örneğin, bir IntelliSense listesinden `e:Book` öğesini seçerseniz, önekinin, belgede bildirilmemiş `http://books` ad alanına bağlandığı, XML Düzenleyicisi sizin için gerekli olan ad alanı bildirimini ekler. Elde edilen XML metni aşağıda verilmiştir:

`<e:Book xmlns:e="http://books"`

## <a name="brace-matching"></a>Ayraç eşleştirme

XML Düzenleyicisi, az önce kapattığınız öğeler hakkında anında geri bildirim sağlamak için küme ayracı vurgulamasını sağlar. Ayrıca, bir küme ayracından eşleşen küme ayracına geçmek için klavye kısayolunu (**Ctrl**+ **]** ) de kullanabilirsiniz.

XML Düzenleyicisi bunu aşağıdaki öğeler için yapar:

- Eşleşen başlangıç ve bitiş etiketleri.

- Herhangi bir çift "\<" veya ">" açılı ayraçlar.

- Yorumların başlangıcı ve sonu.

- İşlem yönergelerinin başlangıcı ve sonu.

- CDATA blokları başlangıcı ve sonu.

- DTD bildirimlerinin başlangıcı ve sonu.

- Özniteliklerde tırnak açma ve kapatma.

## <a name="modify-the-intellisense-options"></a>IntelliSense seçeneklerini değiştirme

IntelliSense ve otomatik tamamlama özellikleri varsayılan olarak etkindir. Ancak, **araçlar** > **seçenekleri** ayarlarını değiştirerek bunu değiştirebilirsiniz.

**Çeşitli** sayfasının **Otomatik Ekle** bölümü aşağıdaki davranışı denetler:

|Name|Açıklama|
|-|-----------------|
|Etiketleri kapat|Yeni öğeler için kapatma etiketleri ekler.|
|Öznitelik teklifleri|Yeni bir öznitelik adı girdiğinizde öznitelik değeri tırnakları ekler.|
|Diğer biçimlendirme|Açıklamaları, CDATA, DOCTYPE, işleme yönergelerini ve diğer biçimlendirme bildirimlerini tamamlar.|

### <a name="to-change-the-auto-completion-behavior"></a>Otomatik tamamlama davranışını değiştirmek için

1. Seçin **seçenekleri** gelen **Araçları** menüsü.

2. **Metin düzenleyiciyi**genişletin, **XML**' i genişletin ve **çeşitli**' ı seçin.

3. **Otomatik ekleme** bölümünde herhangi bir değişiklik yapıp **Tamam**' a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [XML Düzenleyicisi](../xml-tools/xml-editor.md)
- [IntelliSense Kullanma](../ide/using-intellisense.md)
- [İzlenecek Yol: XSLT IntelliSense Kullanma](../xml-tools/walkthrough-using-xslt-intellisense.md)
